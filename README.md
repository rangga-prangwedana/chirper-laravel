# 🐦 Chirper

A Twitter-like microblogging platform built with **Laravel** as part of the [Laravel Bootcamp](https://bootcamp.laravel.com). Users can post short messages called "Chirps", edit them, delete them, and receive email notifications when new Chirps are published.

---

<!--
## 📸 Preview

> A live demo is available at [chirper.laravel.cloud](https://chirper.laravel.cloud)

---
-->
## 🧰 Tech Stack

| Layer      | Technology                          |
|------------|-------------------------------------|
| Backend    | Laravel (PHP)                       |
| Frontend   | Blade / Inertia.js (Vue or React)   |
| Styling    | Tailwind CSS                        |
| Auth       | Laravel Breeze                      |
| Database   | MySQL / SQLite                      |
| Build Tool | Vite                                |
| Package    | Composer + NPM                      |

---

## ✨ Features

- 🔐 User registration and authentication (via Laravel Breeze)
- ✍️ Create, read, update, and delete Chirps
- 🔒 Authorization — users can only edit/delete their own Chirps
- 📧 Email notifications sent when a new Chirp is published
- 🕐 Timestamps with human-readable formatting
- 📱 Fully responsive UI with Tailwind CSS

---

## ⚙️ Requirements

Make sure you have the following installed on your machine:

- **PHP** >= 8.1
- **Composer** >= 2.x
- **Node.js** >= 18.x & **NPM** >= 9.x
- **MySQL** >= 8.x or **SQLite** (for local dev)
- **Git**

---

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/chirper.git
cd chirper
```

### 2. Install PHP Dependencies

```bash
composer install
```

### 3. Install JavaScript Dependencies

```bash
npm install
```

### 4. Configure Environment

```bash
cp .env.example .env
php artisan key:generate
```

Then open `.env` and update your database credentials:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=chirper
DB_USERNAME=root
DB_PASSWORD=your_password
```

> 💡 For a quick local setup, you can use SQLite instead:
> ```env
> DB_CONNECTION=sqlite
> ```
> Then create the database file:
> ```bash
> touch database/database.sqlite
> ```

### 5. Run Database Migrations

```bash
php artisan migrate
```

### 6. (Optional) Seed the Database

```bash
php artisan db:seed
```

### 7. Build Frontend Assets

```bash
npm run build
```

For development with hot reload:

```bash
npm run dev
```

### 8. Start the Development Server

```bash
php artisan serve
```

Visit the app at [http://localhost:8000](http://localhost:8000)

---

## 🗂️ Project Structure

```
chirper/
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   │   └── ChirpController.php    # CRUD for Chirps
│   │   └── Requests/                  # Form validation
│   ├── Models/
│   │   ├── Chirp.php                  # Chirp model
│   │   └── User.php                   # User model
│   ├── Notifications/
│   │   └── NewChirp.php               # Email notification
│   └── Policies/
│       └── ChirpPolicy.php            # Authorization policy
├── database/
│   └── migrations/                    # Database migrations
├── resources/
│   ├── views/                         # Blade templates (Blade stack)
│   └── js/
│       └── Pages/                     # Inertia pages (Vue/React stack)
├── routes/
│   └── web.php                        # Application routes
└── tests/
    ├── Feature/                       # Feature tests
    └── Unit/                          # Unit tests
```

---

## 🔀 Available Stacks

The Laravel Bootcamp offers three frontend stack options for Chirper:

| Stack              | Description                          |
|--------------------|--------------------------------------|
| **Blade**          | Server-side rendering, classic PHP   |
| **Inertia + Vue**  | SPA feel with Vue.js components      |
| **Inertia + React**| SPA feel with React components       |

All stacks use **Tailwind CSS** for styling and **Laravel Breeze** for authentication scaffolding.

---

## 🧪 Running Tests

```bash
php artisan test
```

Run with coverage:

```bash
php artisan test --coverage
```

Run a specific test file:

```bash
php artisan test tests/Feature/ChirpTest.php
```

---

## 📬 Email Notifications

Chirper sends email notifications to all users when a new Chirp is posted. For local development, configure a mail driver in `.env`:

**Using Mailtrap (recommended for dev):**

```env
MAIL_MAILER=smtp
MAIL_HOST=sandbox.smtp.mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=your_mailtrap_username
MAIL_PASSWORD=your_mailtrap_password
MAIL_FROM_ADDRESS="hello@chirper.test"
MAIL_FROM_NAME="${APP_NAME}"
```

**Using log driver (simplest):**

```env
MAIL_MAILER=log
```

Emails will be written to `storage/logs/laravel.log`.

---

## 🔐 Authentication Routes

| Method | URI               | Description         |
|--------|-------------------|---------------------|
| GET    | `/register`       | Show register form  |
| POST   | `/register`       | Handle registration |
| GET    | `/login`          | Show login form     |
| POST   | `/login`          | Handle login        |
| POST   | `/logout`         | Logout user         |

---

## 🐦 Chirp Routes

| Method | URI              | Action               | Middleware        |
|--------|------------------|----------------------|-------------------|
| GET    | `/chirps`        | List all chirps      | auth, verified    |
| POST   | `/chirps`        | Store a new chirp    | auth, verified    |
| GET    | `/chirps/{chirp}`| Show a chirp         | auth, verified    |
| PUT    | `/chirps/{chirp}`| Update a chirp       | auth, verified    |
| DELETE | `/chirps/{chirp}`| Delete a chirp       | auth, verified    |

> All Chirp routes are registered via `Route::resource('chirps', ChirpController::class)` in `routes/web.php`.

---

## 🌐 Deployment

### Deploy to Laravel Cloud

1. Push your project to a GitHub repository
2. Visit [cloud.laravel.com](https://cloud.laravel.com)
3. Connect your repository
4. Configure environment variables
5. Deploy with automatic CI/CD

### Manual Server Setup

```bash
# Set environment to production
APP_ENV=production
APP_DEBUG=false

# Optimize the application
php artisan config:cache
php artisan route:cache
php artisan view:cache

# Build frontend assets for production
npm run build
```

---

## 🤝 Contributing

Thank you for considering contributing! Please read the [Laravel contribution guide](https://laravel.com/docs/contributions).

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Commit your changes: `git commit -m 'Add my feature'`
4. Push to the branch: `git push origin feature/my-feature`
5. Open a Pull Request

---

## 🛡️ Security

If you discover a security vulnerability, please send an email to [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

---

## 📄 License

Chirper is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

---

## 📚 Resources

- [Laravel Documentation](https://laravel.com/docs)
- [Laravel Bootcamp](https://bootcamp.laravel.com)
- [Laracasts](https://laracasts.com)
- [Laravel Breeze](https://github.com/laravel/breeze)
- [Inertia.js](https://inertiajs.com)
- [Tailwind CSS](https://tailwindcss.com)

---

<p align="center">Built with ❤️ using <a href="https://laravel.com">Laravel</a></p>
