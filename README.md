# Bartın 24 - Local News Website

## About

Bartın 24 is a local news website covering Bartın and Amasra. It is built with PHP, MySQL and a responsive layout, and was developed as a learning project.

## Features

### General

- Responsive design that works on desktop, tablet and mobile
- Clean, easy-to-use interface
- User authentication with hashed passwords
- News filtering by category
- Image upload and display

### User Roles

1. Admin
   - Full user management
   - Create and delete editor and admin accounts
   - Manage all content

2. Editor
   - Add, edit and delete news articles
   - Upload images
   - Assign categories to articles

3. User (Member)
   - Read news
   - Comment on articles (planned)

### Technical Stack

- Backend: PHP 7.4+
- Database: MySQL / MariaDB
- Frontend: HTML5, CSS3, vanilla JavaScript
- Security:
  - Password hashing (`PASSWORD_DEFAULT`)
  - PDO prepared statements (SQL injection protection)
  - Session management
  - CSRF protection

## Installation

### Requirements

- PHP 7.4 or higher
- MySQL 5.7 or MariaDB 10.2+
- Apache or Nginx
- WAMP, XAMPP or LAMP (recommended)

### Steps

#### 1. Clone the repository

```bash
git clone https://github.com/sugoizoe/haber-sitesi.git
cd haber-sitesi
```

#### 2. Configure the database

Create a `config.php` file in the project root:

```php
<?php
$db_host = 'localhost';
$db_name = 'habersitesi';
$db_user = 'root';
$db_pass = '';
$db_charset = 'utf8mb4';
?>
```

You can also copy `config.sample.php` and edit it.

#### 3. Create the database

Open the following address in your browser:

```
http://localhost/habersitesi/init-db.php
```

This script:

- Creates the `habersitesi` database
- Creates the required tables
- Adds demo articles and users

#### 4. Run the site

Open the home page:

```
http://localhost/habersitesi/
```

## Default Accounts

After setup you can log in with the following demo accounts:

| Role   | Username | Password  |
|--------|----------|-----------|
| Admin  | admin    | admin123  |
| Editor | editor   | editor123 |
| User   | user     | user123   |

These accounts are for local testing only. Change the passwords or remove the accounts before deploying anywhere public.

## Project Structure

```
habersitesi/
├── index.php              # Main router
├── config.php             # Database settings (ignored by git)
├── init-db.php            # Database setup script
├── .gitignore
├── README.md
├── pages/                 # Page modules
│   ├── home.php           # Home page
│   ├── categories.php     # Category list
│   ├── latest.php         # Latest news
│   ├── admin.php          # Admin panel
│   ├── editor.php         # Editor panel
│   └── logout.php         # Logout handler
└── uploads/               # Uploaded images
    ├── amasra-1.jpg
    ├── amasra ağlayan ağaç.jpg
    ├── amasra mendirek.jpg
    ├── bartın çarşı.jpg
    ├── çekiciler sokağı.jpg
    └── inkumu.jpg
```

## Database Schema

### Tables

`admin_users`: admin and editor accounts
- id, name, username, email, password, role, is_active, created_at, updated_at

`users`: site members
- id, username, email, password, is_active, created_at

`categories`: news categories (General, Culture, Local)
- id, name, slug, description, created_at

`news`: articles
- id, title, content, excerpt, image_url, admin_user_id, category_id, is_published, views, created_at, updated_at

`comments`: comments (planned)
- id, news_id, user_id, author_name, author_email, content, status, created_at

## Technologies Used

- PHP: server-side scripting
- MySQL: relational database
- HTML5: markup
- CSS3: styling and layout (Flexbox, Grid, animations)
- JavaScript: modals and form handling
- PDO: database access
- Git: version control

## Security

1. Password hashing with `password_hash()`
2. Prepared statements to prevent SQL injection
3. Session management
4. Output escaping with `htmlspecialchars()` to prevent XSS
5. Role-based access control

## Responsive Design

The site works on desktop, tablet and mobile:

- Flexbox-based layout
- CSS Grid for news cards
- Media queries for mobile
- Touch-friendly buttons and links

## Roadmap

- [ ] Comment system (with admin approval)
- [ ] News search
- [ ] Article detail page
- [ ] Social media share buttons
- [ ] View count tracking
- [ ] Email notifications
- [ ] RSS feed
- [ ] Multi-language support

## Notes

- `config.php` is listed in `.gitignore`, so it has to be created manually.
- The `uploads/` folder contains the demo images and is included in the repository.
- Demo data is loaded automatically by `init-db.php`.
- HTTPS is recommended in production to keep session cookies secure.

## Author

Arda Emire - [github.com/sugoizoe](https://github.com/sugoizoe)

Year: 2025

## License

This project was developed for educational purposes.

---

Note: The project was tested on WAMP/XAMPP. Review the security settings before using it in production.
