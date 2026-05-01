🌾 Agri Marketplace Backend API

A full-featured backend system for a farmer-to-customer marketplace that enables:

🧑‍🌾 Farmers to sell products
🛒 Users to buy products
📦 Order management
⭐ Reviews & ratings
🔐 Secure authentication & role-based access

📌 Project Overview

This backend powers an Agri E-commerce Platform where:

Farmers list products 🌱
Customers browse & purchase 🛒
Admin manages users & orders 🛠️

Built using Node.js, Express, MongoDB, and follows a modular MVC architecture.

🚀 Key Features

🔐 Authentication & Authorization
JWT-based authentication (stored in cookies)
Role-based access:
👤 User
🌾 Farmer
🛠️ Admin

🛍️ Product Management (Farmer)

Add product with image upload
Update & delete products
View own products

🛒 Cart System (User)

Add to cart
Remove from cart
View cart with populated product details

📦 Order System

Place orders
Accept / Cancel / Complete orders
Stock auto-updated
Notifications for farmers

👉 Core order logic:


⭐ Review System
Users can review purchased products only
Rating auto-calculated
Admin can manage reviews

👉 Review logic:

👤 Profile Management
User profile
Farmer profile
Admin profile

🛠️ Admin Features

View all users
Delete users
View all orders
Delete orders

🏗️ System Architecture

Client (Frontend / Mobile App)
        ↓
Express Server (API Layer)
        ↓
Controllers (Business Logic)
        ↓
Models (MongoDB via Mongoose)
        ↓
Database (MongoDB)

⚙️ Tech Stack

Backend: Node.js, Express.js
Database: MongoDB (Mongoose)
Authentication: JWT + Cookies
File Upload: Multer
Security:
bcrypt (password hashing)
role-based middleware

📁 Project Structure

backend/
│
├── config/
│   └── db.js
│
├── controllers/
│   ├── authController.js
│   ├── productController.js
│   ├── orderController.js
│   ├── cartController.js
│   ├── reviewController.js
│   ├── adminController.js
│   └── roleController.js
│
├── middleware/
│   ├── protect.js
│   ├── roleProtect.js
│   └── upload.js
│
├── models/
│   ├── User.js
│   ├── Product.js
│   ├── Order.js
│
├── routes/
│   ├── authRoutes.js
│   ├── productRoutes.js
│   ├── orderRoutes.js
│   ├── cartRoutes.js
│   ├── adminRoutes.js
│   └── reviewRoutes.js
│
├── utils/
│   └── generateToken.js
│
├── uploads/
│
└── server.js / app.js

📡 API Endpoints

🔐 Auth Routes

POST /api/auth/register
POST /api/auth/login
POST /api/auth/logout

👤 Profile Routes

GET  /api/auth/user/profile
POST /api/auth/user/profile

GET  /api/auth/farmer/profile
POST /api/auth/farmer/profile

GET  /api/auth/admin/profile
POST /api/auth/admin/profile

🛍️ Product Routes

POST   /api/products/farmer/product
PUT    /api/products/farmer/product/:id
DELETE /api/products/farmer/product/:id
GET    /api/products/farmer/my-products

🛒 Cart Routes

POST   /api/cart/add
DELETE /api/cart/remove/:productId
GET    /api/cart/view

📦 Order Routes

POST   /api/orders
GET    /api/orders/customer/orders
GET    /api/orders/farmer/orders

PATCH  /api/orders/order/:orderId/cancel
PATCH  /api/orders/order/:orderId/cancel-by-farmer

PUT    /api/orders/accept/:orderId
PUT    /api/orders/complete/:orderId

⭐ Review Routes

POST   /api/reviews/:productId
GET    /api/reviews/my
DELETE /api/reviews/:reviewId

GET    /api/reviews/farmer
GET    /api/reviews/admin
DELETE /api/reviews/:productId/:reviewId

🛠️ Admin Routes

GET    /api/admin/orders
DELETE /api/admin/orders/:orderId

GET    /api/admin/users
DELETE /api/admin/users/:userId

🔐 Authentication Flow

User logs in
JWT token generated
Stored in HTTP-only cookie (jwt-page)
Middleware verifies token

🧠 Core Concepts

🔑 Role-Based Access Control

protect → verifies JWT
roleProtect → restricts access

🛡️ Security

Password hashing with bcrypt
HTTP-only cookies
JWT expiration

📦 Order Logic Highlights

Stock validation
Auto stock deduction
Farmer notification system

⭐ Review Logic Highlights

Only verified buyers can review
Dynamic rating calculation

🚀 Setup Instructions

1️⃣ Clone Repository

git clone https://github.com/your-username/agri-marketplace-backend.git
cd agri-marketplace-backend

2️⃣ Install Dependencies

npm install

3️⃣ Create .env File

PORT=5000
MONGO_URI=your_mongodb_connection
JWT_SECRET=your_secret_key
BASE_URL=http://localhost:5000

4️⃣ Run Server

npm start

or (for development):

npm run dev

📂 Uploads

Images stored in /uploads

Access via:

http://localhost:5000/uploads/<filename>

📈 Future Enhancements

💳 Payment Gateway Integration
📱 Mobile App Integration
🔔 Real-time notifications (Socket.IO)
📊 Analytics Dashboard
🚚 Delivery tracking
👨‍💻 Author

Developed as part of a Full Stack Agri Marketplace System

📜 License

This project is licensed under the MIT License.

⭐ Support

If you found this useful:

⭐ Star the repo
🍴 Fork it
🚀 Build on it
