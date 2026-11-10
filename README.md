# 🛒 MyShop-ECommerce

An e-commerce web application built with **ASP.NET Core MVC** and **SQL Server**, following a layered architecture. It supports product browsing, a shopping cart, user authentication and online payments through **Stripe**.

## ✨ Features <!-- verify and edit this list to match what you built -->

- Browse products and categories
- Shopping cart and checkout
- User registration and login (ASP.NET Core Identity)
- Online payment with Stripe
- Order management
- Admin area to manage products, categories and orders
- Role-based authorization (Admin / Customer)

## 🧱 Architecture

The solution is split into four projects:

| Project | Responsibility |
|---|---|
| `myshop.Web` | Presentation layer: controllers, views, areas, static files |
| `myshop.DataAccess` | EF Core `DbContext`, migrations, repositories <!-- verify: Repository / Unit of Work? --> |
| `myshop.Entities` | Domain models and view models |
| `myshop.Utilities` | Shared helpers and constants (roles, Stripe settings, etc.) |

## 🛠️ Tech Stack

- C# / ASP.NET Core MVC (.NET `<version>`) <!-- verify -->
- Entity Framework Core
- SQL Server
- ASP.NET Core Identity
- Stripe.net
- Bootstrap, HTML, CSS, JavaScript

## 🚀 Getting Started

### Prerequisites

- [.NET SDK](https://dotnet.microsoft.com/download) `<version>`
- SQL Server or SQL Server LocalDB
- Visual Studio 2022 or VS Code
- A free [Stripe account](https://dashboard.stripe.com/register) (test mode is enough)

### 1. Clone the repository

```bash
git clone https://github.com/yasserbnsayed/MyShop-ECommerce.git
cd MyShop-ECommerce
```

### 2. Configure the database

Check the connection string in `myshop.Web/appsettings.json` and change it if needed:

```json
"ConnectionStrings": {
  "DefaultConnection": "Server=.;Database=myshopDB;Trusted_Connection=True;MultipleActiveResultSets=True;TrustServerCertificate=True;"
}
```

Apply the migrations:

```bash
dotnet ef database update --project myshop.DataAccess --startup-project myshop.Web
```

### 3. Configure Stripe keys (User Secrets)

Stripe keys are **not** stored in the repository. Add your own test keys with user-secrets:

```bash
cd myshop.Web
dotnet user-secrets init
dotnet user-secrets set "stripe:Secretkey" "sk_test_xxxxxxxxxxxxxxxx"
dotnet user-secrets set "stripe:Publishablekey" "pk_test_xxxxxxxxxxxxxxxx"
```

### 4. Run the application

```bash
dotnet run --project myshop.Web
```

Then open the URL shown in the console (for example `https://localhost:5001`).

### 💳 Test payment

Use Stripe's test card: `4242 4242 4242 4242`, any future expiry date and any CVC.

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file.

## 👤 Author

**Yasser Sayed**: [GitHub](https://github.com/yasserbnsayed)
