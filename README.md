<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Toko Elektronik | Belanja Online</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        :root {
            --pink: #ff63b1;
            --pink-light: #ffa5d8;
            --pink-dark: #d83e8a;
            --white: #ffffff;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background-color: #fff5f9;
            color: #333;
        }

        .btn-pink {
            background-color: var(--pink);
            color: white;
            transition: all 0.3s ease;
        }

        .btn-pink:hover {
            background-color: var(--pink-dark);
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(255, 99, 177, 0.3);
        }

        .product-card {
            transition: all 0.3s ease;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(255, 99, 177, 0.1);
        }

        .cart-item {
            transition: all 0.2s ease;
        }

        .cart-item:hover {
            background-color: rgba(255, 99, 177, 0.05);
        }

        .payment-method {
            transition: all 0.2s ease;
        }

        .payment-method:hover {
            transform: scale(1.02);
            border-color: var(--pink);
        }

        .payment-method.active {
            border: 2px solid var(--pink);
        }

        .checkout-btn {
            background-color: var(--pink);
            color: white;
            padding: 12px 24px;
            font-weight: bold;
            border-radius: 50px;
            transition: all 0.3s ease;
        }

        .checkout-btn:hover {
            background-color: var(--pink-dark);
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(255, 99, 177, 0.3);
        }

        .complete-btn {
            background-color: var(--pink);
            color: white;
            padding: 16px 32px;
            font-weight: bold;
            border-radius: 50px;
            font-size: 1.1rem;
            transition: all 0.3s ease;
        }

        .complete-btn:hover {
            background-color: var(--pink-dark);
            transform: translateY(-2px);
            box-shadow: 0 6px 16px rgba(255, 99, 177, 0.4);
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="bg-white shadow-md py-4 px-6">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <h1 class="text-2xl font-bold text-pink-600">Toko Elektronik</h1>
            <div class="flex items-center space-x-6">
                <a href="#" class="hover:text-pink-600">Beranda</a>
                <a href="#products" class="hover:text-pink-600">Produk</a>
                <button id="cart-btn" class="relative">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-pink-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z" />
                    </svg>
                    <span id="cart-count" class="absolute -top-2 -right-2 bg-pink-600 text-white rounded-full h-5 w-5 flex items-center justify-center text-xs font-bold">0</span>
                </button>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="bg-gradient-to-r from-pink-50 to-white py-16 px-6 text-center">
        <h2 class="text-4xl font-bold text-pink-600 mb-4">Selamat Datang di Toko Elektronik</h2>
        <p class="text-xl mb-8 max-w-2xl mx-auto">Temukan koleksi produk terbaik kami dengan harga spesial!</p>
        <button class="btn-pink py-3 px-8 rounded-full font-bold">Belanja Sekarang</button>
    </section>

    <!-- Products Section -->
    <section id="products" class="py-12 px-6">
        <div class="max-w-7xl mx-auto">
            <h3 class="text-2xl font-bold text-center mb-8">Produk Kami</h3>
            
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6" id="products-grid">
                <!-- Product cards will be added here by JavaScript -->
            </div>
        </div>
    </section>

    <!-- Cart Modal -->
    <div id="cart-modal" class="fixed inset-0 bg-black bg-opacity-50 z-50 flex justify-end" style="display: none;">
        <div class="bg-white w-full max-w-md h-full overflow-y-auto">
            <div class="p-6">
                <div class="flex justify-between items-center mb-6">
                    <h3 class="text-xl font-bold text-pink-600 flex items-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z" />
                        </svg>
                        Keranjang Belanja Anda
                    </h3>
                    <button id="close-cart" class="text-2xl">×</button>
                </div>
                
                <div id="cart-items" class="mb-6">
                    <!-- Cart items will be added here by JavaScript -->
                    <div id="empty-cart-message" class="text-center py-10">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-12 w-12 mx-auto mb-4 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
                        </svg>
                        <p>Keranjang Anda kosong</p>
                    </div>
                </div>
                
                <div id="cart-summary" style="display: none;">
                    <div class="border-t border-gray-200 pt-4 mb-6">
                        <div class="flex justify-between mb-2">
                            <span>Subtotal:</span>
                            <span id="cart-subtotal">Rp 0</span>
                        </div>
                        <div class="flex justify-between mb-2">
                            <span>Tax (10%):</span>
                            <span id="cart-tax">Rp 0</span>
                        </div>
                        <div class="flex justify-between font-bold text-lg">
                            <span>Total:</span>
                            <span id="cart-total">Rp 0</span>
                        </div>
                    </div>
                    
                    <button id="checkout-btn" class="checkout-btn w-full">Lanjut ke Pembayaran</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Checkout Modal -->
    <div id="checkout-modal" class="fixed inset-0 bg-black bg-opacity-50 z-50 flex justify-end" style="display: none;">
        <div class="bg-white w-full max-w-md h-full overflow-y-auto">
            <div class="p-6">
                <div class="flex justify-between items-center mb-6">
                    <h3 class="text-xl font-bold text-pink-600">Pembayaran</h3>
                    <button id="close-checkout" class="text-2xl">×</button>
                </div>
                
                <div class="mb-8">
                    <h4 class="font-bold mb-4">Informasi Pelanggan</h4>
                    <div class="space-y-4">
                        <div>
                            <label class="block text-sm font-medium mb-1">Nama Lengkap</label>
                            <input type="text" class="w-full px-4 py-2 border rounded-lg focus:ring-pink-500 focus:border-pink-500">
                        </div>
                        <div>
                            <label class="block text-sm font-medium mb-1">Email</label>
                            <input type="email" class="w-full px-4 py-2 border rounded-lg focus:ring-pink-500 focus:border-pink-500">
                        </div>
                        <div>
                            <label class="block text-sm font-medium mb-1">Phone Number</label>
                            <input type="tel" class="w-full px-4 py-2 border rounded-lg focus:ring-pink-500 focus:border-pink-500">
                        </div>
                        <div>
                            <label class="block text-sm font-medium mb-1">Alamat Pengiriman</label>
                            <textarea class="w-full px-4 py-2 border rounded-lg focus:ring-pink-500 focus:border-pink-500" rows="3"></textarea>
                        </div>
                    </div>
                </div>
                
                <div class="mb-8">
                    <h4 class="font-bold mb-4">Order Summary</h4>
                    <div id="checkout-items">
                        <!-- Order items will be added here by JavaScript -->
                    </div>
                    
                    <div class="border-t border-gray-200 pt-4 mt-4">
                        <div class="flex justify-between mb-2">
                            <span>Subtotal:</span>
                            <span id="checkout-subtotal">Rp 0</span>
                        </div>
                        <div class="flex justify-between mb-2">
                            <span>Tax (10%):</span>
                            <span id="checkout-tax">Rp 0</span>
                        </div>
                        <div class="flex justify-between font-bold text-lg">
                            <span>Total:</span>
                            <span id="checkout-total">Rp 0</span>
                        </div>
                    </div>
                </div>
                
                <div class="mb-8">
                    <h4 class="font-bold mb-4">Payment Method</h4>
                    <div class="space-y-2">
                        <div class="payment-method cursor-pointer p-4 border rounded-lg flex items-center" data-method="credit-card">
                            <input type="radio" name="payment" id="credit-card" class="mr-3">
                            <label for="credit-card" class="flex-grow flex items-center cursor-pointer">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 10h18M7 15h1m4 0h1m-7 4h12a3 3 0 003-3V8a3 3 0 00-3-3H6a3 3 0 00-3 3v8a3 3 0 003 3z" />
                                </svg>
                                Credit Card
                            </label>
                        </div>
                        
                        <div class="payment-method cursor-pointer p-4 border rounded-lg flex items-center" data-method="bank-transfer">
                            <input type="radio" name="payment" id="bank-transfer" class="mr-3">
                            <label for="bank-transfer" class="flex-grow flex items-center cursor-pointer">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 14v3m4-3v3m4-3v3m3-3h1a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v8a2 2 0 002 2h1" />
                                </svg>
                                Bank Transfer
                            </label>
                        </div>
                        
                        <div class="payment-method cursor-pointer p-4 border rounded-lg flex items-center" data-method="e-wallet">
                            <input type="radio" name="payment" id="e-wallet" class="mr-3">
                            <label for="e-wallet" class="flex-grow flex items-center cursor-pointer">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                                </svg>
                                E-Wallet
                            </label>
                        </div>
                        
                        <div class="payment-method cursor-pointer p-4 border rounded-lg flex items-center" data-method="cod">
                            <input type="radio" name="payment" id="cod" class="mr-3">
                            <label for="cod" class="flex-grow flex items-center cursor-pointer">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                                </svg>
                                Cash on Delivery
                            </label>
                        </div>
                    </div>
                </div>
                
                <button id="complete-payment-btn" class="complete-btn w-full bg-pink-600 hover:bg-pink-700">
                    Complete Payment
                </button>
            </div>
        </div>
    </div>

    <!-- Success Modal -->
    <div id="success-modal" class="fixed inset-0 bg-black bg-opacity-50 z-50 flex items-center justify-center" style="display: none;">
        <div class="bg-white p-8 rounded-lg max-w-md w-full text-center">
            <div class="flex justify-center mb-6">
                <div class="h-16 w-16 rounded-full bg-green-100 flex items-center justify-center">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-green-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                    </svg>
                </div>
            </div>
            <h3 class="text-2xl font-bold mb-4 text-pink-600">Pembayaran Berhasil!</h3>
            <p class="mb-6">Terima kasih telah berbelanja. Pesanan Anda telah dikonfirmasi.</p>
            <button id="close-success" class="btn-pink px-8 py-3 rounded-full">Kembali Belanja</button>
        </div>
    </div>

    <script>
        // Product Data
        const products = [
            {
                id: 1,
                name: "Wireless Headphones",
                price: 250000,
                image: "https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/58665afc-737f-41c0-b286-7c092bdd0e30.png",
                description: "Premium noise-canceling wireless headphones with 30-hour battery life."
            },
            {
                id: 2,
                name: "Smart Watch",
                price: 350000,
                image: "https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/1fc519ee-5fc6-4add-8f8a-c0d4969154da.png",
                description: "Fitness tracker with heart rate monitor and notification alerts."
            },
            {
                id: 3,
                name: "Bluetooth Speaker",
                price: 180000,
                image: "https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/cc525f8b-9a1d-447a-8036-690cf53d0e3f.png",
                description: "Portable waterproof speaker with 12-hour playback time."
            },
            {
                id: 4,
                name: "Wireless Earbuds",
                price: 150000,
                image: "https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/9aa76314-2620-48d9-82dc-7aac32a0e81f.png",
                description: "Compact wireless earbuds with charging case."
            },
            {
                id: 5,
                name: "Power Bank",
                price: 120000,
                image: "https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/82a26563-2034-48c1-adf5-3862c728facd.png",
                description: "10000mAh portable charger with fast charging."
            },
            {
                id: 6,
                name: "Phone Stand",
                price: 50000,
                image: "https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/466e8bf4-6715-4b47-aaa1-8c1b4151561e.png",
                description: "Adjustable phone stand for comfortable viewing."
            },
            {
                id: 7,
                name: "Wireless Charger",
                price: 120000,
                image: "https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/27b06296-cb70-4769-9f69-985c1177ecf1.png",
                description: "15W fast wireless charging pad with LED indicator."
            },
            {
                id: 8,
                name: "Smart Keyboard",
                price: 450000,
                image: "https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/f6900635-b2e1-4129-995a-dda15dc3a37d.png",
                description: "Bluetooth keyboard with multi-device support and backlit keys."
            }
        ];

        // Cart and App State
        let cart = [];
        let selectedPaymentMethod = null;

        // DOM Elements
        const cartBtn = document.getElementById('cart-btn');
        const cartCount = document.getElementById('cart-count');
        const closeCart = document.getElementById('close-cart');
        const cartModal = document.getElementById('cart-modal');
        const cartItemsContainer = document.getElementById('cart-items');
        const emptyCartMessage = document.getElementById('empty-cart-message');
        const cartSummary = document.getElementById('cart-summary');
        const cartSubtotal = document.getElementById('cart-subtotal');
        const cartTax = document.getElementById('cart-tax');
        const cartTotal = document.getElementById('cart-total');
        const productsGrid = document.getElementById('products-grid');
        const checkoutBtn = document.getElementById('checkout-btn');
        const checkoutModal = document.getElementById('checkout-modal');
        const closeCheckout = document.getElementById('close-checkout');
        const checkoutItems = document.getElementById('checkout-items');
        const checkoutSubtotal = document.getElementById('checkout-subtotal');
        const checkoutTax = document.getElementById('checkout-tax');
        const checkoutTotal = document.getElementById('checkout-total');
        const completePaymentBtn = document.getElementById('complete-payment-btn');
        const successModal = document.getElementById('success-modal');
        const closeSuccess = document.getElementById('close-success');
        const paymentMethods = document.querySelectorAll('.payment-method');

        // Render Products
        function renderProducts() {
            productsGrid.innerHTML = '';
            products.forEach(product => {
                const productCard = document.createElement('div');
                productCard.className = 'product-card bg-white rounded-lg shadow-md overflow-hidden';
                productCard.innerHTML = `
                    <img src="${product.image}" alt="${product.name}" class="w-full h-48 object-cover">
                    <div class="p-4">
                        <h4 class="font-bold mb-2">${product.name}</h4>
                        <p class="text-gray-600 mb-4">${product.description}</p>
                        <div class="flex justify-between items-center">
                            <span class="font-bold text-pink-600">Rp ${product.price.toLocaleString()}</span>
                            <button class="add-to-cart btn-pink px-4 py-2 rounded-lg" data-id="${product.id}">+ Keranjang</button>
                        </div>
                    </div>
                `;
                productsGrid.appendChild(productCard);
            });

            // Add event listeners to add-to-cart buttons
            document.querySelectorAll('.add-to-cart').forEach(button => {
                button.addEventListener('click', function() {
                    const productId = parseInt(this.getAttribute('data-id'));
                    addToCart(productId);
                    updateCartCount();
                    animateCartButton();
                });
            });
        }

        // Add to Cart
        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            const cartItem = cart.find(item => item.id === productId);

            if (cartItem) {
                cartItem.quantity += 1;
            } else {
                cart.push({
                    ...product,
                    quantity: 1
                });
            }

            renderCartItems();
        }

        // Update Cart Count
        function updateCartCount() {
            const totalItems = cart.reduce((total, item) => total + item.quantity, 0);
            cartCount.textContent = totalItems;
        }

        // Animate Cart Button
        function animateCartButton() {
            cartBtn.classList.add('animate-ping');
            setTimeout(() => {
                cartBtn.classList.remove('animate-ping');
            }, 500);
        }

        // Render Cart Items
        function renderCartItems() {
            cartItemsContainer.innerHTML = '';

            if (cart.length === 0) {
                emptyCartMessage.style.display = 'block';
                cartSummary.style.display = 'none';
                return;
            }

            emptyCartMessage.style.display = 'none';
            cartSummary.style.display = 'block';

            cart.forEach(item => {
                const cartItem = document.createElement('div');
                cartItem.className = 'cart-item bg-pink-50 rounded-lg p-4 mb-4 flex justify-between items-center';
                cartItem.innerHTML = `
                    <div class="flex items-center">
                        <img src="${item.image}" alt="${item.name}" class="w-16 h-16 object-cover rounded">
                        <div class="ml-4">
                            <h4 class="font-bold">${item.name}</h4>
                            <p class="text-pink-600">Rp ${item.price.toLocaleString()}</p>
                        </div>
                    </div>
                    <div class="flex items-center">
                        <button class="decrease-quantity px-2 py-1 bg-white rounded-l border" data-id="${item.id}">-</button>
                        <span class="px-3 py-1 bg-white border-t border-b">${item.quantity}</span>
                        <button class="increase-quantity px-2 py-1 bg-white rounded-r border" data-id="${item.id}">+</button>
                        <button class="remove-item ml-2 text-red-500" data-id="${item.id}">×</button>
                    </div>
                `;
                cartItemsContainer.appendChild(cartItem);
            });

            // Update cart summary
            const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const tax = subtotal * 0.1;
            const total = subtotal + tax;

            cartSubtotal.textContent = `Rp ${subtotal.toLocaleString()}`;
            cartTax.textContent = `Rp ${tax.toLocaleString()}`;
            cartTotal.textContent = `Rp ${total.toLocaleString()}`;

            // Add event listeners to quantity buttons
            document.querySelectorAll('.decrease-quantity').forEach(button => {
                button.addEventListener('click', function() {
                    const productId = parseInt(this.getAttribute('data-id'));
                    decreaseQuantity(productId);
                });
            });

            document.querySelectorAll('.increase-quantity').forEach(button => {
                button.addEventListener('click', function() {
                    const productId = parseInt(this.getAttribute('data-id'));
                    increaseQuantity(productId);
                });
            });

            document.querySelectorAll('.remove-item').forEach(button => {
                button.addEventListener('click', function() {
                    const productId = parseInt(this.getAttribute('data-id'));
                    removeFromCart(productId);
                });
            });
        }

        // Decrease Quantity
        function decreaseQuantity(productId) {
            const cartItem = cart.find(item => item.id === productId);
            if (cartItem.quantity > 1) {
                cartItem.quantity -= 1;
            } else {
                cart = cart.filter(item => item.id !== productId);
            }
            updateCartCount();
            renderCartItems();
        }

        // Increase Quantity
        function increaseQuantity(productId) {
            const cartItem = cart.find(item => item.id === productId);
            cartItem.quantity += 1;
            updateCartCount();
            renderCartItems();
        }

        // Remove from Cart
        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCartCount();
            renderCartItems();
        }

        // Render Checkout Items
        function renderCheckoutItems() {
            checkoutItems.innerHTML = '';

            cart.forEach(item => {
                const checkoutItem = document.createElement('div');
                checkoutItem.className = 'flex justify-between mb-4';
                checkoutItem.innerHTML = `
                    <div class="flex items-center">
                        <img src="${item.image}" alt="${item.name}" class="w-12 h-12 object-cover rounded mr-3">
                        <div>
                            <h4 class="font-bold">${item.name}</h4>
                            <p class="text-sm text-gray-500">Rp ${item.price.toLocaleString()} x ${item.quantity}</p>
                        </div>
                    </div>
                    <span class="font-bold">Rp ${(item.price * item.quantity).toLocaleString()}</span>
                `;
                checkoutItems.appendChild(checkoutItem);
            });

            // Update checkout summary
            const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const tax = subtotal * 0.1;
            const total = subtotal + tax;

            checkoutSubtotal.textContent = `Rp ${subtotal.toLocaleString()}`;
            checkoutTax.textContent = `Rp ${tax.toLocaleString()}`;
            checkoutTotal.textContent = `Rp ${total.toLocaleString()}`;
        }

        // Event Listeners
        cartBtn.addEventListener('click', () => {
            cartModal.style.display = 'block';
            renderCartItems();
        });

        closeCart.addEventListener('click', () => {
            cartModal.style.display = 'none';
        });

        checkoutBtn.addEventListener('click', () => {
            cartModal.style.display = 'none';
            checkoutModal.style.display = 'block';
            renderCheckoutItems();
        });

        closeCheckout.addEventListener('click', () => {
            checkoutModal.style.display = 'none';
        });

        completePaymentBtn.addEventListener('click', () => {
            if (!selectedPaymentMethod) {
                alert('Please select a payment method');
                return;
            }
            checkoutModal.style.display = 'none';
            successModal.style.display = 'flex';
            // In a real app, you would process payment here
            cart = [];
            updateCartCount();
        });

        closeSuccess.addEventListener('click', () => {
            successModal.style.display = 'none';
        });

        paymentMethods.forEach(method => {
            method.addEventListener('click', function() {
                paymentMethods.forEach(m => m.classList.remove('active'));
                this.classList.add('active');
                selectedPaymentMethod = this.getAttribute('data-method');
            });
        });

        // Close modals when clicking outside content
        window.addEventListener('click', (e) => {
            if (e.target === cartModal) {
                cartModal.style.display = 'none';
            }
            if (e.target === checkoutModal) {
                checkoutModal.style.display = 'none';
            }
            if (e.target === successModal) {
                successModal.style.display = 'none';
            }
        });

        // Initialize the app
        renderProducts();
    </script>
</body>
</html>
