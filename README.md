<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>LuxeBazaar — India's Premier Lifestyle & Tech Store</title>

  <!-- Google Font: Inter -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet" />

  <!-- Tailwind CSS via CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: {
        extend: {
          fontFamily: {
            sans: ['Inter', 'system-ui', '-apple-system', 'sans-serif'],
          },
          colors: {
            brand: {
              50: '#eef2ff',
              100: '#e0e7ff',
              200: '#c7d2fe',
              300: '#a5b4fc',
              400: '#818cf8',
              500: '#6366f1',
              600: '#4f46e5',
              700: '#4338ca',
              800: '#3730a3',
              900: '#312e81',
            },
          },
          keyframes: {
            slideInRight: {
              '0%': { transform: 'translateX(100%)' },
              '100%': { transform: 'translateX(0)' },
            },
            fadeUp: {
              '0%': { opacity: '0', transform: 'translateY(12px)' },
              '100%': { opacity: '1', transform: 'translateY(0)' },
            },
            popIn: {
              '0%': { opacity: '0', transform: 'scale(0.95)' },
              '100%': { opacity: '1', transform: 'scale(1)' },
            },
          },
          animation: {
            slideInRight: 'slideInRight 0.28s cubic-bezier(0.16, 1, 0.3, 1)',
            fadeUp: 'fadeUp 0.25s ease-out',
            popIn: 'popIn 0.22s ease-out',
          },
        },
      },
    };
  </script>

  <!-- Lucide Icons via CDN -->
  <script src="https://unpkg.com/lucide@latest"></script>
</head>
<body class="bg-slate-50 text-slate-900 dark:bg-slate-950 dark:text-slate-100 font-sans antialiased selection:bg-brand-500 selection:text-white overflow-x-hidden transition-colors duration-200">

  <!-- ==================== TOP ANNOUNCEMENT STRIP ==================== -->
  <div class="bg-brand-600 text-white text-xs sm:text-sm py-2 px-4 text-center font-medium">
    <div class="max-w-7xl mx-auto flex flex-wrap items-center justify-center gap-x-3 gap-y-1">
      <span>🎉 Mega Festive Sale Live! Free Express Delivery above ₹999</span>
      <span class="hidden sm:inline opacity-50">|</span>
      <button onclick="copyPromoCode('WELCOME200')" class="inline-flex items-center gap-1 bg-white/15 hover:bg-white/25 px-2.5 py-0.5 rounded-full text-xs font-semibold transition cursor-pointer">
        <span>Code: WELCOME200</span>
        <i data-lucide="copy" class="w-3 h-3"></i>
      </button>
    </div>
  </div>

  <!-- ==================== STICKY GLASSMORPHISM HEADER ==================== -->
  <header class="sticky top-0 z-40 bg-white/80 dark:bg-slate-900/80 backdrop-blur-xl border-b border-slate-200/80 dark:border-slate-800/80 transition-colors">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16 gap-3">
        <!-- Brand Logo -->
        <a href="#top" onclick="resetFilters()" class="flex items-center gap-2.5 shrink-0 group">
          <div class="w-9 h-9 rounded-xl bg-gradient-to-br from-brand-600 to-violet-600 flex items-center justify-center text-white shadow-md shadow-brand-500/25 group-hover:scale-105 transition-transform">
            <i data-lucide="shopping-bag" class="w-5 h-5"></i>
          </div>
          <div class="leading-tight">
            <span class="text-lg sm:text-xl font-extrabold tracking-tight bg-gradient-to-r from-slate-900 to-slate-600 dark:from-white dark:to-slate-300 bg-clip-text text-transparent">LuxeBazaar</span>
            <span class="hidden sm:inline-block ml-1 text-[10px] font-bold uppercase tracking-wider px-1.5 py-0.5 rounded bg-brand-100 text-brand-700 dark:bg-brand-900/60 dark:text-brand-300 align-top">IN</span>
          </div>
        </a>

        <!-- Desktop Live Search Bar -->
        <div class="hidden md:flex flex-1 max-w-xl mx-4 relative">
          <i data-lucide="search" class="w-4 h-4 text-slate-400 absolute left-3.5 top-1/2 -translate-y-1/2 pointer-events-none"></i>
          <input
            id="desktopSearchInput"
            type="text"
            placeholder="Search headphones, watches, smartphones, kurta..."
            class="w-full pl-10 pr-10 py-2.5 text-sm rounded-xl bg-slate-100 dark:bg-slate-800/90 border border-transparent focus:border-brand-500 focus:bg-white dark:focus:bg-slate-900 focus:ring-2 focus:ring-brand-500/20 outline-none transition"
          />
          <button
            id="desktopClearSearch"
            onclick="clearSearch()"
            class="hidden absolute right-3 top-1/2 -translate-y-1/2 text-slate-400 hover:text-slate-600 dark:hover:text-slate-200 p-1"
            aria-label="Clear search"
          >
            <i data-lucide="x" class="w-4 h-4"></i>
          </button>
        </div>

        <!-- Header Action Buttons -->
        <div class="flex items-center gap-1.5 sm:gap-2">
          <!-- Dark/Light Theme Toggle -->
          <button
            id="themeToggleBtn"
            onclick="toggleTheme()"
            class="p-2.5 rounded-xl text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800 transition"
            title="Toggle Dark / Light Mode"
            aria-label="Toggle theme"
          >
            <i data-lucide="moon" class="w-5 h-5 dark:hidden"></i>
            <i data-lucide="sun" class="w-5 h-5 hidden dark:block text-amber-400"></i>
          </button>

          <!-- Order History Button -->
          <button
            onclick="openOrdersModal()"
            class="relative p-2.5 rounded-xl text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800 transition"
            title="My Orders"
            aria-label="Order History"
          >
            <i data-lucide="package" class="w-5 h-5"></i>
            <span id="ordersBadge" class="hidden absolute -top-0.5 -right-0.5 min-w-[18px] h-[18px] px-1 rounded-full bg-emerald-500 text-white text-[10px] font-bold flex items-center justify-center shadow">0</span>
          </button>

          <!-- Wishlist Drawer Button -->
          <button
            onclick="openWishlistDrawer()"
            class="relative p-2.5 rounded-xl text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800 transition"
            title="Wishlist"
            aria-label="Open Wishlist"
          >
            <i data-lucide="heart" class="w-5 h-5"></i>
            <span id="wishlistBadge" class="hidden absolute -top-0.5 -right-0.5 min-w-[18px] h-[18px] px-1 rounded-full bg-rose-500 text-white text-[10px] font-bold flex items-center justify-center shadow">0</span>
          </button>

          <!-- Cart Drawer Button -->
          <button
            onclick="openCartDrawer()"
            class="relative flex items-center gap-2 px-3 sm:px-4 py-2.5 rounded-xl bg-slate-900 dark:bg-brand-600 hover:bg-slate-800 dark:hover:bg-brand-500 text-white font-semibold text-sm shadow-sm transition"
            aria-label="Open Shopping Cart"
          >
            <i data-lucide="shopping-cart" class="w-4 h-4"></i>
            <span class="hidden sm:inline">Cart</span>
            <span id="cartBadge" class="min-w-[20px] h-5 px-1.5 rounded-full bg-white text-slate-900 dark:text-brand-700 text-xs font-bold flex items-center justify-center">0</span>
          </button>
        </div>
      </div>

      <!-- Mobile Live Search Bar -->
      <div class="md:hidden pb-3">
        <div class="relative">
          <i data-lucide="search" class="w-4 h-4 text-slate-400 absolute left-3.5 top-1/2 -translate-y-1/2 pointer-events-none"></i>
          <input
            id="mobileSearchInput"
            type="text"
            placeholder="Search products, brands, categories..."
            class="w-full pl-10 pr-9 py-2.5 text-sm rounded-xl bg-slate-100 dark:bg-slate-800 border border-transparent focus:border-brand-500 focus:bg-white dark:focus:bg-slate-900 outline-none transition"
          />
          <button
            id="mobileClearSearch"
            onclick="clearSearch()"
            class="hidden absolute right-2.5 top-1/2 -translate-y-1/2 text-slate-400 p-1"
            aria-label="Clear search"
          >
            <i data-lucide="x" class="w-4 h-4"></i>
          </button>
        </div>
      </div>
    </div>
  </header>

  <!-- ==================== MAIN CONTENT ==================== -->
  <main id="top" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6 sm:py-8 space-y-8">

    <!-- ==================== HERO & FLASH SALE BANNER ==================== -->
    <section class="relative overflow-hidden rounded-3xl bg-gradient-to-br from-slate-900 via-brand-900 to-violet-900 text-white shadow-xl">
      <!-- Decorative Glow Blobs -->
      <div class="absolute -top-24 -right-24 w-72 h-72 bg-brand-500/30 rounded-full blur-3xl pointer-events-none"></div>
      <div class="absolute -bottom-24 -left-24 w-72 h-72 bg-fuchsia-500/20 rounded-full blur-3xl pointer-events-none"></div>

      <div class="relative z-10 grid grid-cols-1 lg:grid-cols-12 gap-8 p-6 sm:p-10 lg:p-12 items-center">
        <!-- Left Copy -->
        <div class="lg:col-span-7 space-y-5">
          <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-white/10 backdrop-blur-md border border-white/15 text-xs sm:text-sm font-semibold text-amber-300">
            <i data-lucide="zap" class="w-4 h-4 fill-amber-300"></i>
            <span>FLASH SALE LIVE — UP TO 65% OFF</span>
          </div>

          <h1 class="text-3xl sm:text-4xl lg:text-5xl font-extrabold tracking-tight leading-tight">
            Elevate Your Everyday with <span class="text-transparent bg-clip-text bg-gradient-to-r from-amber-300 via-rose-300 to-indigo-200">LuxeBazaar</span>
          </h1>

          <p class="text-slate-200/90 text-sm sm:text-base max-w-xl leading-relaxed">
            Curated flagship tech, luxury timepieces, acoustic audio, and artisanal Indian fashion — backed by instant UPI checkout and lightning-fast pan-India delivery.
          </p>

          <!-- Countdown Timer -->
          <div class="flex flex-wrap items-center gap-3 pt-1">
            <span class="text-xs uppercase tracking-wider text-slate-300 font-semibold">Deal ends in:</span>
            <div class="flex items-center gap-2">
              <div class="bg-white/10 backdrop-blur-md border border-white/15 rounded-xl px-3 py-2 text-center min-w-[54px]">
                <div id="timerHours" class="text-lg sm:text-xl font-extrabold tabular-nums leading-none">05</div>
                <div class="text-[10px] text-slate-300 uppercase mt-1">Hrs</div>
              </div>
              <span class="font-bold text-slate-400">:</span>
              <div class="bg-white/10 backdrop-blur-md border border-white/15 rounded-xl px-3 py-2 text-center min-w-[54px]">
                <div id="timerMinutes" class="text-lg sm:text-xl font-extrabold tabular-nums leading-none">42</div>
                <div class="text-[10px] text-slate-300 uppercase mt-1">Min</div>
              </div>
              <span class="font-bold text-slate-400">:</span>
              <div class="bg-white/10 backdrop-blur-md border border-white/15 rounded-xl px-3 py-2 text-center min-w-[54px]">
                <div id="timerSeconds" class="text-lg sm:text-xl font-extrabold tabular-nums leading-none text-amber-300">19</div>
                <div class="text-[10px] text-slate-300 uppercase mt-1">Sec</div>
              </div>
            </div>
          </div>

          <!-- CTA Buttons -->
          <div class="flex flex-wrap items-center gap-3 pt-2">
            <a href="#catalog" class="inline-flex items-center gap-2 px-6 py-3 rounded-xl bg-white text-slate-900 hover:bg-slate-100 font-bold text-sm shadow-lg transition">
              <span>Shop Flash Deals</span>
              <i data-lucide="arrow-right" class="w-4 h-4"></i>
            </a>
            <button onclick="copyPromoCode('SAVE10')" class="inline-flex items-center gap-2 px-5 py-3 rounded-xl bg-white/10 hover:bg-white/20 border border-white/20 text-white font-semibold text-sm backdrop-blur-md transition">
              <i data-lucide="ticket-percent" class="w-4 h-4 text-amber-300"></i>
              <span>Copy SAVE10 (10% Off)</span>
            </button>
          </div>
        </div>

        <!-- Right Visual Showcase Card -->
        <div class="lg:col-span-5 hidden sm:block">
          <div class="relative rounded-2xl bg-white/10 backdrop-blur-lg border border-white/15 p-5 shadow-2xl">
            <div class="flex items-center justify-between mb-3">
              <span class="text-xs font-bold uppercase tracking-wider px-2.5 py-1 rounded-lg bg-amber-400 text-slate-950">Spotlight Deal</span>
              <span class="text-xs font-semibold text-emerald-300">Save ₹8,000</span>
            </div>
            <div class="aspect-[16/10] rounded-xl overflow-hidden bg-slate-800 mb-4">
              <img
                src="https://images.unsplash.com/photo-1505740420928-5e560c06d30e?auto=format&fit=crop&w=900&q=80"
                alt="Sony WH-1000XM5 Headphones"
                onerror="this.onerror=null;this.src='https://placehold.co/800x500/1e293b/ffffff?text=Sony+WH-1000XM5';"
                class="w-full h-full object-cover hover:scale-105 transition duration-500"
              />
            </div>
            <div class="flex items-center justify-between gap-3">
              <div>
                <p class="text-xs text-slate-300">Audio • Flagship ANC</p>
                <h3 class="font-bold text-base text-white">Sony WH-1000XM5 Wireless</h3>
                <div class="flex items-baseline gap-2 mt-0.5">
                  <span class="text-lg font-extrabold text-amber-300">₹26,990</span>
                  <span class="text-xs line-through text-slate-400">₹34,990</span>
                </div>
              </div>
              <button onclick="openQuickView(1)" class="px-4 py-2.5 rounded-xl bg-brand-500 hover:bg-brand-400 text-white text-xs font-bold transition shrink-0">
                Quick View
              </button>
            </div>
          </div>
        </div>
      </div>

      <!-- Trust Strip -->
      <div class="relative z-10 border-t border-white/10 bg-black/20 backdrop-blur-md px-6 py-4">
        <div class="grid grid-cols-2 lg:grid-cols-4 gap-4 text-xs sm:text-sm">
          <div class="flex items-center gap-2.5">
            <div class="p-2 rounded-lg bg-white/10 text-emerald-300 shrink-0"><i data-lucide="truck" class="w-4 h-4"></i></div>
            <div>
              <p class="font-semibold text-white">Free Delivery</p>
              <p class="text-[11px] text-slate-300">On orders above ₹999</p>
            </div>
          </div>
          <div class="flex items-center gap-2.5">
            <div class="p-2 rounded-lg bg-white/10 text-sky-300 shrink-0"><i data-lucide="refresh-cw" class="w-4 h-4"></i></div>
            <div>
              <p class="font-semibold text-white">7-Day Replacement</p>
              <p class="text-[11px] text-slate-300">Hassle-free returns</p>
            </div>
          </div>
          <div class="flex items-center gap-2.5">
            <div class="p-2 rounded-lg bg-white/10 text-amber-300 shrink-0"><i data-lucide="shield-check" class="w-4 h-4"></i></div>
            <div>
              <p class="font-semibold text-white">Secure UPI & Cards</p>
              <p class="text-[11px] text-slate-300">GPay, PhonePe, Paytm, COD</p>
            </div>
          </div>
          <div class="flex items-center gap-2.5">
            <div class="p-2 rounded-lg bg-white/10 text-violet-300 shrink-0"><i data-lucide="award" class="w-4 h-4"></i></div>
            <div>
              <p class="font-semibold text-white">100% Genuine</p>
              <p class="text-[11px] text-slate-300">Brand warranty & GST bill</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ==================== CATEGORY TABS & FILTERS ==================== -->
    <section id="catalog" class="space-y-5">
      <!-- Category Pills -->
      <div class="flex items-center justify-between flex-wrap gap-3">
        <div id="categoryTabs" class="flex items-center gap-2 overflow-x-auto pb-1 w-full lg:w-auto">
          <!-- Populated dynamically via JS -->
        </div>
        <div class="text-xs sm:text-sm text-slate-500 dark:text-slate-400 font-medium">
          Showing <span id="resultCount" class="font-bold text-slate-900 dark:text-white">0</span> products
        </div>
      </div>

      <!-- Filter & Sort Bar -->
      <div class="bg-white dark:bg-slate-900 border border-slate-200/80 dark:border-slate-800 rounded-2xl p-4 shadow-sm">
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 items-center">
          <!-- Price Range Slider -->
          <div class="space-y-1.5">
            <div class="flex items-center justify-between text-xs font-semibold">
              <span class="text-slate-500 dark:text-slate-400">Max Price</span>
              <span id="priceRangeLabel" class="text-brand-600 dark:text-brand-400 font-bold">₹1,50,000</span>
            </div>
            <input
              id="priceRangeSlider"
              type="range"
              min="1000"
              max="150000"
              step="1000"
              value="150000"
              class="w-full accent-brand-600 cursor-pointer"
            />
          </div>

          <!-- Minimum Rating Filter -->
          <div class="space-y-1">
            <label for="ratingFilter" class="block text-xs font-semibold text-slate-500 dark:text-slate-400">Customer Rating</label>
            <select
              id="ratingFilter"
              class="w-full text-sm rounded-xl bg-slate-100 dark:bg-slate-800 border border-transparent focus:border-brand-500 px-3 py-2 outline-none font-medium"
            >
              <option value="0">All Ratings</option>
              <option value="4.7">4.7★ & above</option>
              <option value="4.5">4.5★ & above</option>
              <option value="4.0">4.0★ & above</option>
            </select>
          </div>

          <!-- Sort Dropdown -->
          <div class="space-y-1">
            <label for="sortSelect" class="block text-xs font-semibold text-slate-500 dark:text-slate-400">Sort By</label>
            <select
              id="sortSelect"
              class="w-full text-sm rounded-xl bg-slate-100 dark:bg-slate-800 border border-transparent focus:border-brand-500 px-3 py-2 outline-none font-medium"
            >
              <option value="featured">Featured</option>
              <option value="price-asc">Price: Low to High</option>
              <option value="price-desc">Price: High to Low</option>
              <option value="rating-desc">Top Rated</option>
              <option value="discount-desc">Biggest Discount</option>
            </select>
          </div>

          <!-- Reset Button -->
          <div class="flex sm:justify-end items-end h-full">
            <button
              onclick="resetFilters()"
              class="w-full sm:w-auto inline-flex items-center justify-center gap-1.5 px-4 py-2 rounded-xl border border-slate-200 dark:border-slate-700 hover:bg-slate-100 dark:hover:bg-slate-800 text-xs sm:text-sm font-semibold transition"
            >
              <i data-lucide="rotate-ccw" class="w-4 h-4"></i>
              <span>Reset Filters</span>
            </button>
          </div>
        </div>
      </div>

      <!-- Product Grid -->
      <div id="productGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-5">
        <!-- Rendered dynamically via JS -->
      </div>

      <!-- Empty Search State -->
      <div id="emptyState" class="hidden text-center py-16 px-4 bg-white dark:bg-slate-900 rounded-3xl border border-slate-200 dark:border-slate-800">
        <div class="w-16 h-16 mx-auto rounded-2xl bg-slate-100 dark:bg-slate-800 flex items-center justify-center text-slate-400 mb-4">
          <i data-lucide="search-x" class="w-8 h-8"></i>
        </div>
        <h3 class="text-lg font-bold">No matching products found</h3>
        <p class="text-sm text-slate-500 dark:text-slate-400 mt-1 max-w-md mx-auto">Try adjusting your search keywords, category, or price range filter.</p>
        <button onclick="resetFilters()" class="mt-5 px-5 py-2.5 rounded-xl bg-brand-600 hover:bg-brand-700 text-white text-sm font-semibold transition">
          Show All Products
        </button>
      </div>
    </section>
  </main>

  <!-- ==================== FOOTER ==================== -->
  <footer class="mt-16 border-t border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-900/70">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
        <div class="md:col-span-2 space-y-3">
          <div class="flex items-center gap-2.5">
            <div class="w-8 h-8 rounded-xl bg-gradient-to-br from-brand-600 to-violet-600 flex items-center justify-center text-white">
              <i data-lucide="shopping-bag" class="w-4 h-4"></i>
            </div>
            <span class="text-lg font-extrabold tracking-tight">LuxeBazaar</span>
          </div>
          <p class="text-sm text-slate-500 dark:text-slate-400 max-w-md leading-relaxed">
            India's trusted destination for flagship electronics, luxury watches, signature audio, and curated lifestyle essentials. Every order includes a valid 18% GST invoice.
          </p>
          <div class="flex flex-wrap gap-2 pt-2">
            <span class="px-2.5 py-1 rounded-lg bg-slate-100 dark:bg-slate-800 text-xs font-semibold">UPI / GPay</span>
            <span class="px-2.5 py-1 rounded-lg bg-slate-100 dark:bg-slate-800 text-xs font-semibold">PhonePe</span>
            <span class="px-2.5 py-1 rounded-lg bg-slate-100 dark:bg-slate-800 text-xs font-semibold">RuPay / Visa</span>
            <span class="px-2.5 py-1 rounded-lg bg-slate-100 dark:bg-slate-800 text-xs font-semibold">Cash on Delivery</span>
          </div>
        </div>

        <div>
          <h4 class="font-bold text-sm mb-3">Shop Categories</h4>
          <ul class="space-y-2 text-sm text-slate-500 dark:text-slate-400">
            <li><button onclick="selectCategory('Electronics')" class="hover:text-brand-600 transition">Electronics</button></li>
            <li><button onclick="selectCategory('Audio')" class="hover:text-brand-600 transition">Audio & Headphones</button></li>
            <li><button onclick="selectCategory('Watches')" class="hover:text-brand-600 transition">Luxury Watches</button></li>
            <li><button onclick="selectCategory('Fashion')" class="hover:text-brand-600 transition">Fashion & Footwear</button></li>
            <li><button onclick="selectCategory('Home & Living')" class="hover:text-brand-600 transition">Home & Living</button></li>
          </ul>
        </div>

        <div>
          <h4 class="font-bold text-sm mb-3">Customer Care</h4>
          <ul class="space-y-2 text-sm text-slate-500 dark:text-slate-400">
            <li class="flex items-center gap-2"><i data-lucide="phone" class="w-4 h-4 text-brand-500"></i> 1800-120-LUXE (Toll Free)</li>
            <li class="flex items-center gap-2"><i data-lucide="mail" class="w-4 h-4 text-brand-500"></i> care@luxebazaar.in</li>
            <li class="flex items-center gap-2"><i data-lucide="map-pin" class="w-4 h-4 text-brand-500"></i> Connaught Place, New Delhi</li>
          </ul>
        </div>
      </div>

      <div class="border-t border-slate-200 dark:border-slate-800 mt-10 pt-6 flex flex-col sm:flex-row items-center justify-between gap-3 text-xs text-slate-500 dark:text-slate-400">
        <p>© 2026 LuxeBazaar Retail Pvt. Ltd. All rights reserved. Made for India 🇮🇳</p>
        <p>Active Coupons: <strong class="text-slate-700 dark:text-slate-200">SAVE10</strong> • <strong class="text-slate-700 dark:text-slate-200">WELCOME200</strong></p>
      </div>
    </div>
  </footer>

  <!-- ==================== PRODUCT QUICK VIEW MODAL ==================== -->
  <div id="quickViewModal" class="hidden fixed inset-0 z-50 flex items-center justify-center p-3 sm:p-6 bg-slate-950/60 backdrop-blur-sm">
    <div class="relative w-full max-w-4xl max-h-[92vh] overflow-y-auto bg-white dark:bg-slate-900 rounded-3xl shadow-2xl border border-slate-200 dark:border-slate-800 animate-popIn">
      <button onclick="closeQuickView()" class="sticky top-4 float-right mr-4 z-20 p-2 rounded-full bg-slate-100/90 dark:bg-slate-800/90 hover:bg-slate-200 dark:hover:bg-slate-700 transition" aria-label="Close quick view">
        <i data-lucide="x" class="w-5 h-5"></i>
      </button>
      <div id="quickViewContent" class="p-5 sm:p-8">
        <!-- Populated dynamically -->
      </div>
    </div>
  </div>

  <!-- ==================== SLIDE-OVER CART DRAWER ==================== -->
  <div id="cartDrawerOverlay" class="hidden fixed inset-0 z-50 bg-slate-950/60 backdrop-blur-sm flex justify-end">
    <div class="w-full max-w-md bg-white dark:bg-slate-900 h-full flex flex-col shadow-2xl animate-slideInRight">
      <!-- Cart Header -->
      <div class="px-5 py-4 border-b border-slate-200 dark:border-slate-800 flex items-center justify-between">
        <div class="flex items-center gap-2">
          <i data-lucide="shopping-cart" class="w-5 h-5 text-brand-600 dark:text-brand-400"></i>
          <h2 class="text-lg font-bold">Shopping Cart</h2>
          <span id="cartDrawerCount" class="text-xs font-bold px-2 py-0.5 rounded-full bg-brand-100 dark:bg-brand-900/60 text-brand-700 dark:text-brand-300">0</span>
        </div>
        <button onclick="closeCartDrawer()" class="p-2 rounded-xl hover:bg-slate-100 dark:hover:bg-slate-800 transition" aria-label="Close cart">
          <i data-lucide="x" class="w-5 h-5"></i>
        </button>
      </div>

      <!-- Free Shipping Progress Bar -->
      <div id="shippingBarContainer" class="px-5 py-3 bg-slate-50 dark:bg-slate-800/60 border-b border-slate-200 dark:border-slate-800">
        <!-- Dynamically populated -->
      </div>

      <!-- Cart Items Scroll Area -->
      <div id="cartItemsContainer" class="flex-1 overflow-y-auto px-5 py-4 space-y-4">
        <!-- Dynamically populated -->
      </div>

      <!-- Cart Footer: Coupon & Price Summary -->
      <div id="cartFooter" class="border-t border-slate-200 dark:border-slate-800 p-5 bg-slate-50/90 dark:bg-slate-900 space-y-4">
        <!-- Dynamically populated -->
      </div>
    </div>
  </div>

  <!-- ==================== SLIDE-OVER WISHLIST DRAWER ==================== -->
  <div id="wishlistDrawerOverlay" class="hidden fixed inset-0 z-50 bg-slate-950/60 backdrop-blur-sm flex justify-end">
    <div class="w-full max-w-md bg-white dark:bg-slate-900 h-full flex flex-col shadow-2xl animate-slideInRight">
      <div class="px-5 py-4 border-b border-slate-200 dark:border-slate-800 flex items-center justify-between">
        <div class="flex items-center gap-2">
          <i data-lucide="heart" class="w-5 h-5 text-rose-500 fill-rose-500"></i>
          <h2 class="text-lg font-bold">My Wishlist</h2>
        </div>
        <button onclick="closeWishlistDrawer()" class="p-2 rounded-xl hover:bg-slate-100 dark:hover:bg-slate-800 transition" aria-label="Close wishlist">
          <i data-lucide="x" class="w-5 h-5"></i>
        </button>
      </div>
      <div id="wishlistItemsContainer" class="flex-1 overflow-y-auto p-5 space-y-3">
        <!-- Dynamically populated -->
      </div>
    </div>
  </div>

  <!-- ==================== MULTI-STEP CHECKOUT MODAL ==================== -->
  <div id="checkoutModal" class="hidden fixed inset-0 z-50 flex items-center justify-center p-3 sm:p-6 bg-slate-950/70 backdrop-blur-sm">
    <div class="w-full max-w-2xl max-h-[92vh] overflow-y-auto bg-white dark:bg-slate-900 rounded-3xl shadow-2xl border border-slate-200 dark:border-slate-800 animate-popIn">
      <!-- Checkout Header -->
      <div class="sticky top-0 z-10 bg-white/95 dark:bg-slate-900/95 backdrop-blur-md px-6 py-4 border-b border-slate-200 dark:border-slate-800 flex items-center justify-between">
        <div>
          <h2 class="text-lg font-bold">Secure Checkout</h2>
          <p class="text-xs text-slate-500 dark:text-slate-400">256-bit Encrypted • GST Invoice Included</p>
        </div>
        <button onclick="closeCheckoutModal()" class="p-2 rounded-xl hover:bg-slate-100 dark:hover:bg-slate-800 transition" aria-label="Close checkout">
          <i data-lucide="x" class="w-5 h-5"></i>
        </button>
      </div>

      <!-- Step Indicator -->
      <div class="px-6 pt-5 pb-2">
        <div class="flex items-center justify-between max-w-md mx-auto text-xs font-semibold">
          <div id="stepIndicator1" class="flex items-center gap-2 text-brand-600 dark:text-brand-400">
            <span class="w-6 h-6 rounded-full bg-brand-600 text-white flex items-center justify-center text-xs font-bold">1</span>
            <span>Address</span>
          </div>
          <div class="flex-1 h-0.5 bg-slate-200 dark:bg-slate-700 mx-3"></div>
          <div id="stepIndicator2" class="flex items-center gap-2 text-slate-400">
            <span class="w-6 h-6 rounded-full bg-slate-200 dark:bg-slate-800 text-slate-500 flex items-center justify-center text-xs font-bold">2</span>
            <span>Payment</span>
          </div>
          <div class="flex-1 h-0.5 bg-slate-200 dark:bg-slate-700 mx-3"></div>
          <div id="stepIndicator3" class="flex items-center gap-2 text-slate-400">
            <span class="w-6 h-6 rounded-full bg-slate-200 dark:bg-slate-800 text-slate-500 flex items-center justify-center text-xs font-bold">3</span>
            <span>Confirmed</span>
          </div>
        </div>
      </div>

      <!-- Checkout Body -->
      <div id="checkoutBody" class="p-6">
        <!-- Dynamically rendered by step -->
      </div>
    </div>
  </div>

  <!-- ==================== ORDER HISTORY MODAL ==================== -->
  <div id="ordersModal" class="hidden fixed inset-0 z-50 flex items-center justify-center p-3 sm:p-6 bg-slate-950/60 backdrop-blur-sm">
    <div class="w-full max-w-3xl max-h-[90vh] flex flex-col bg-white dark:bg-slate-900 rounded-3xl shadow-2xl border border-slate-200 dark:border-slate-800 animate-popIn">
      <div class="px-6 py-4 border-b border-slate-200 dark:border-slate-800 flex items-center justify-between">
        <div class="flex items-center gap-2.5">
          <i data-lucide="package-check" class="w-5 h-5 text-brand-600 dark:text-brand-400"></i>
          <h2 class="text-lg font-bold">Order History</h2>
        </div>
        <button onclick="closeOrdersModal()" class="p-2 rounded-xl hover:bg-slate-100 dark:hover:bg-slate-800 transition" aria-label="Close orders">
          <i data-lucide="x" class="w-5 h-5"></i>
        </button>
      </div>
      <div id="ordersListContainer" class="flex-1 overflow-y-auto p-6 space-y-4">
        <!-- Dynamically populated -->
      </div>
    </div>
  </div>

  <!-- ==================== TOAST NOTIFICATION CONTAINER ==================== -->
  <div id="toastContainer" class="fixed bottom-4 right-4 z-[60] flex flex-col gap-2.5 max-w-xs sm:max-w-sm w-full pointer-events-none"></div>

  <!-- ==================== APPLICATION SCRIPT ==================== -->
  <script>
    /*************************************************************************
     * 1. PRODUCT CATALOG DATA (14 Curated Products for Indian Market)
     *************************************************************************/
    const PRODUCTS = [
      {
        id: 1,
        name: "Sony WH-1000XM5 Wireless ANC Headphones",
        brand: "Sony",
        category: "Audio",
        price: 26990,
        mrp: 34990,
        rating: 4.9,
        reviews: 1842,
        image: "https://images.unsplash.com/photo-1505740420928-5e560c06d30e?auto=format&fit=crop&w=800&q=80",
        variantLabel: "Color",
        variants: ["Midnight Black", "Platinum Silver", "Midnight Blue"],
        description: "Industry-leading Dual Noise Sensor technology with 8 microphones, crystal clear hands-free calling, and up to 30 hours of battery life with quick USB-PD charging.",
        specs: ["8-Mic Industry-Leading ANC", "30 Hours Battery + Quick Charge", "Multipoint Bluetooth 5.2", "1 Year Sony India Warranty"]
      },
      {
        id: 2,
        name: "Apple Watch Series 10 GPS 46mm",
        brand: "Apple",
        category: "Watches",
        price: 44900,
        mrp: 49900,
        rating: 4.8,
        reviews: 964,
        image: "https://images.unsplash.com/photo-1546868871-7041f2a55e12?auto=format&fit=crop&w=800&q=80",
        variantLabel: "Finish",
        variants: ["Jet Black", "Rose Gold", "Silver Aluminium"],
        description: "Our thinnest Apple Watch ever with our biggest Wide-Angle OLED display. Track ECG, sleep apnea notifications, water depth, and daily workouts effortlessly.",
        specs: ["Wide-Angle Always-On Retina OLED", "S10 SiP Chip with Double Tap", "50m Water Resistant & Swimproof", "Fast Charge: 80% in 30 mins"]
      },
      {
        id: 3,
        name: "Samsung Galaxy S25 Ultra 5G (256GB)",
        brand: "Samsung",
        category: "Electronics",
        price: 119999,
        mrp: 134999,
        rating: 4.9,
        reviews: 2150,
        image: "https://images.unsplash.com/photo-1610945265064-0e34e5519bbf?auto=format&fit=crop&w=800&q=80",
        variantLabel: "Color",
        variants: ["Titanium Gray", "Titanium Black", "Titanium Silverblue"],
        description: "Engineered with a Grade 5 Titanium frame, built-in S Pen, 200MP ProVisual quad-camera system, and Snapdragon 8 Elite processor tailored for Galaxy AI.",
        specs: ["6.9\" QHD+ Dynamic AMOLED 2X", "200MP Quad Telephoto Camera", "Built-in S Pen & Galaxy AI", "5000mAh Battery • 45W Fast Charge"]
      },
      {
        id: 4,
        name: "MacBook Air M3 13-inch (16GB / 512GB)",
        brand: "Apple",
        category: "Electronics",
        price: 114900,
        mrp: 134900,
        rating: 4.9,
        reviews: 1290,
        image: "https://images.unsplash.com/photo-1517336714731-489689fd1ca8?auto=format&fit=crop&w=800&q=80",
        variantLabel: "Color",
        variants: ["Midnight", "Starlight", "Space Gray"],
        description: "Supercharged by the M3 chip, MacBook Air blazes through work and play with silent fanless design, Liquid Retina display, and up to 18 hours of all-day battery.",
        specs: ["Apple M3 8-Core CPU / 10-Core GPU", "16GB Unified Memory • 512GB SSD", "13.6\" Liquid Retina Display", "MagSafe 3 + Dual Thunderbolt Ports"]
      },
      {
        id: 5,
        name: "boAt Airdopes 141 ANC True Wireless",
        brand: "boAt",
        category: "Audio",
        price: 1499,
        mrp: 4490,
        rating: 4.3,
        reviews: 14520,
        image: "https://images.unsplash.com/photo-1590658268037-6bf12165a8df?auto=format&fit=crop&w=800&q=80",
        variantLabel: "Color",
        variants: ["Active Black", "Olive Green", "Pure White"],
        description: "Experience immersive boAt Signature Sound with 32dB Active Noise Cancellation, BEAST™ low-latency gaming mode, and massive 42-hour total playback.",
        specs: ["Up to 32dB Active Noise Cancellation", "42 Hours Total Playback • ASAP Charge", "50ms Low-Latency Gaming Mode", "IPX5 Sweat & Splash Resistant"]
      },
      {
        id: 6,
        name: "Titan Edge Ceramic Quartz Watch",
        brand: "Titan",
        category: "Watches",
        price: 18995,
        mrp: 22495,
        rating: 4.7,
        reviews: 518,
        image: "https://images.unsplash.com/photo-1524592094714-0f0654e20314?auto=format&fit=crop&w=800&q=80",
        variantLabel: "Finish",
        variants: ["Matte Black Ceramic", "Midnight Blue", "Ivory Gold"],
        description: "Crafted from scratch-resistant zirconia ceramic with an ultra-slim 4.4mm profile and sapphire crystal glass—a masterpiece of Indian horology.",
        specs: ["Ultra-Slim 4.4mm Ceramic Case", "Scratch-Resistant Sapphire Crystal", "Precision In-House Quartz Movement", "2 Years Titan Pan-India Warranty"]
      },
      {
        id: 7,
        name: "Fabindia Handloom Cotton Silk Kurta Set",
        brand: "Fabindia",
        category: "Fashion",
        price: 2799,
        mrp: 3999,
        rating: 4.6,
        reviews: 734,
        image: "https://images.unsplash.com/photo-1596755094514-f87e34085b2c?auto=format&fit=crop&w=800&q=80",
        variantLabel: "Size",
        variants: ["S", "M", "L", "XL"],
        description: "Woven by master artisans using breathable cotton-silk blend. Features a refined mandarin collar, mother-of-pearl buttons, and tailored churidar silhouette.",
        specs: ["70% Handloom Cotton, 30% Mulberry Silk", "Breathable All-Season Festive Weave", "Includes Matching Tapered Pyjama", "Dry Clean / Gentle Cold Wash"]
      },
      {
        id: 8,
        name: "Nike Air Jordan 1 Low SE Sneakers",
        brand: "Nike",
        category: "Fashion",
        price: 10795,
        mrp: 12995,
        rating: 4.8,
        reviews: 1120,
        image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?auto=format&fit=crop&w=800&q=80",
        variantLabel: "UK Size",
        variants: ["UK 7", "UK 8", "UK 9", "UK 10"],
        description: "Inspired by the original 1985 icon, combining full-grain leather overlays with encapsulated Air-Sole cushioning for timeless street-ready comfort.",
        specs: ["Genuine Leather & Synthetic Upper", "Encapsulated Air-Sole Heel Unit", "Solid Rubber Pivot-Circle Outsole", "Embroidered Wings Logo on Heel"]
      },
      {
        id: 9,
        name: "Ray-Ban Aviator Classic Polarized",
        brand: "Ray-Ban",
        category: "Fashion",
        price: 8490,
        mrp: 10590,
        rating: 4.7,
        reviews: 892,
        image: "https://images.unsplash.com/photo-1511499767150-a48a237f0083?auto=format&fit=crop&w=800&q=80",
        variantLabel: "Frame",
        variants: ["Gold / G-15 Green", "Matte Black / Grey", "Gunmetal / Blue"],
        description: "Iconic pilot silhouette with crystal polarized lenses that block 99% of reflected glare and offer 100% UV400 protection for Indian summers.",
        specs: ["100% UV400 Polarized Crystal Lenses", "Lightweight Metal Alloy Frame", "Includes Leather Case & Microfiber Cloth", "2 Years Luxottica India Warranty"]
      },
      {
        id: 10,
        name: "Marshall Emberton II Portable Speaker",
        brand: "Marshall",
        category: "Audio",
        price: 14999,
        mrp: 19999,
        rating: 4.8,
        reviews: 640,
        image: "https://images.unsplash.com/photo-1608043152269-423dbba4e7e1?auto=format&fit=crop&w=800&q=80",
        variantLabel: "Color",
        variants: ["Black & Brass", "Cream Vintage"],
        description: "Rich, clear, and loud 360° True Stereophonic sound in a rugged IP67 dust-and-waterproof enclosure with 30+ hours of portable playtime.",
        specs: ["360° True Stereophonic Sound", "30+ Hours Portable Battery Life", "IP67 Dust & Waterproof Rating", "Stack Mode Multi-Speaker Pairing"]
      },
      {
        id: 11,
        name: "Dyson Purifier Cool Gen1 TP10",
        brand: "Dyson",
        category: "Home & Living",
        price: 32900,
        mrp: 39900,
        rating: 4.7,
        reviews: 815,
        image: "https://images.unsplash.com/photo-1585771724684-38269d6639fd?auto=format&fit=crop&w=800&q=80",
        variantLabel: "Finish",
        variants: ["White / Silver", "Prussian Blue"],
        description: "Automatically senses and captures 99.95% of ultrafine PM2.5 pollutants, allergens, and gases with a fully sealed HEPA H13 filtration system—ideal for Indian metros.",
        specs: ["Sealed HEPA H13 + Activated Carbon", "Captures 99.95% PM2.5 & Allergens", "350° Oscillation & Night Mode", "2 Years Dyson Home-Visit Warranty"]
      },
      {
        id: 12,
        name: "Philips Espresso Bean-to-Cup Coffee Maker",
        brand: "Philips",
        category: "Home & Living",
        price: 42499,
        mrp: 54995,
        rating: 4.6,
        reviews: 412,
        image: "https://images.unsplash.com/photo-1517668808822-9ebb02f2a0e6?auto=format&fit=crop&w=800&q=80",
        variantLabel: "Color",
        variants: ["Matte Black", "Brushed Chrome"],
        description: "Brew café-grade Espresso, Cappuccino, and Americano from fresh beans at the touch of a button with 100% ceramic grinders and classic milk frother.",
        specs: ["15-Bar Italian Pressure Pump", "12-Step 100% Ceramic Grinders", "Intuitive Touch Display", "AquaClean Filter (Up to 5000 Cups)"]
      },
      {
        id: 13,
        name: "Wakefit Orthopedic Memory Foam Pillow (Set of 2)",
        brand: "Wakefit",
        category: "Home & Living",
        price: 1199,
        mrp: 2199,
        rating: 4.4,
        reviews: 6320,
        image: "https://images.unsplash.com/photo-1584100936595-c0654b55a2e2?auto=format&fit=crop&w=800&q=80",
        variantLabel: "Size",
        variants: ["Standard (24x16 in)", "King (27x17 in)"],
        description: "Engineered with breathable aerospace-grade memory foam that contours to your neck and spine for deep, pain-free restorative sleep.",
        specs: ["Adaptive High-Density Memory Foam", "Removable Washable Tencel Cover", "Hypoallergenic & Dust-Mite Resistant", "1 Year Manufacturer Warranty"]
      },
      {
        id: 14,
        name: "Casio G-Shock GA-2100 'CasiOak' Watch",
        brand: "Casio",
        category: "Watches",
        price: 8995,
        mrp: 10995,
        rating: 4.8,
        reviews: 1540,
        image: "https://images.unsplash.com/photo-1523275335684-37898b6baf30?auto=format&fit=crop&w=800&q=80",
        variantLabel: "Color",
        variants: ["Stealth Black", "Utility Olive", "Royal Navy"],
        description: "Carbon Core Guard octagonal bezel design blending legendary G-Shock 200m water resistance with a sleek, minimalist analog-digital dial.",
        specs: ["Carbon Core Guard Shock Resistance", "200-Meter Water Resistance", "World Time (31 Time Zones) & LED", "2 Years Casio India Warranty"]
      }
    ];

    const CATEGORIES = ["All", "Electronics", "Audio", "Watches", "Fashion", "Home & Living"];

    const COUPONS = {
      SAVE10: { code: "SAVE10", type: "percent", value: 10, minOrder: 0, label: "10% instant discount" },
      WELCOME200: { code: "WELCOME200", type: "flat", value: 200, minOrder: 999, label: "₹200 flat off (min order ₹999)" }
    };

    const INDIAN_STATES = [
      "Delhi", "Maharashtra", "Karnataka", "Tamil Nadu", "Telangana", "Gujarat",
      "West Bengal", "Uttar Pradesh", "Rajasthan", "Haryana", "Punjab", "Kerala",
      "Madhya Pradesh", "Bihar", "Odisha", "Assam", "Chandigarh", "Goa"
    ];

    /*************************************************************************
     * 2. APPLICATION STATE & LOCALSTORAGE PERSISTENCE
     *************************************************************************/
    const STORAGE_KEYS = {
      CART: 'luxebazaar_cart_v1',
      WISHLIST: 'luxebazaar_wishlist_v1',
      ORDERS: 'luxebazaar_orders_v1',
      THEME: 'luxebazaar_theme_v1'
    };

    let state = {
      cart: [],             // [{ productId, variant, qty }]
      wishlist: [],         // [productId]
      orders: [],           // [{ id, date, items, totals, address, paymentMethod, status, deliveryDate }]
      appliedCoupon: null,  // 'SAVE10' | 'WELCOME200' | null
      selectedCategory: "All",
      searchQuery: "",
      maxPrice: 150000,
      minRating: 0,
      sortBy: "featured",
      quickViewProductId: null,
      quickViewVariant: null,
      checkoutStep: 1,
      checkoutAddress: {
        fullName: "",
        phone: "",
        pincode: "",
        street: "",
        city: "",
        state: "Delhi"
      },
      checkoutPayment: "UPI",
      lastOrder: null
    };

    function safeStorageGet(key, fallback) {
      try {
        const raw = localStorage.getItem(key);
        return raw ? JSON.parse(raw) : fallback;
      } catch (e) {
        return fallback;
      }
    }

    function safeStorageSet(key, value) {
      try {
        localStorage.setItem(key, JSON.stringify(value));
      } catch (e) {
        // Ignore storage quota / iframe privacy restrictions
      }
    }

    function loadPersistedState() {
      state.cart = safeStorageGet(STORAGE_KEYS.CART, []);
      state.wishlist = safeStorageGet(STORAGE_KEYS.WISHLIST, []);
      state.orders = safeStorageGet(STORAGE_KEYS.ORDERS, []);

      const savedTheme = safeStorageGet(STORAGE_KEYS.THEME, null);
      if (savedTheme === 'dark' || (!savedTheme && window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
        document.documentElement.classList.add('dark');
      } else {
        document.documentElement.classList.remove('dark');
      }
    }

    function persistCart() { safeStorageSet(STORAGE_KEYS.CART, state.cart); }
    function persistWishlist() { safeStorageSet(STORAGE_KEYS.WISHLIST, state.wishlist); }
    function persistOrders() { safeStorageSet(STORAGE_KEYS.ORDERS, state.orders); }

    /*************************************************************************
     * 3. FORMATTING & CALCULATION HELPERS
     *************************************************************************/
    const inrFormatter = new Intl.NumberFormat('en-IN', {
      style: 'currency',
      currency: 'INR',
      maximumFractionDigits: 0
    });

    function formatINR(amount) {
      return inrFormatter.format(Math.round(amount || 0));
    }

    function getDiscountPercent(mrp, price) {
      if (!mrp || mrp <= price) return 0;
      return Math.round(((mrp - price) / mrp) * 100);
    }

    function getEstimatedDeliveryDate(daysToAdd = 4) {
      const date = new Date();
      date.setDate(date.getDate() + daysToAdd);
      return date.toLocaleDateString('en-IN', { weekday: 'short', day: 'numeric', month: 'short' });
    }

    /**
     * Computes complete cart financials including Indian GST (18% included in selling price)
     */
    function calculateCartTotals() {
      let totalMrp = 0;
      let sellingSubtotal = 0;
      let totalItems = 0;

      state.cart.forEach(item => {
        const product = PRODUCTS.find(p => p.id === item.productId);
        if (product) {
          totalMrp += product.mrp * item.qty;
          sellingSubtotal += product.price * item.qty;
          totalItems += item.qty;
        }
      });

      const mrpDiscount = totalMrp - sellingSubtotal;

      // Validate active coupon against current subtotal
      let couponDiscount = 0;
      if (state.appliedCoupon && COUPONS[state.appliedCoupon]) {
        const c = COUPONS[state.appliedCoupon];
        if (sellingSubtotal >= c.minOrder) {
          couponDiscount = c.type === 'percent'
            ? Math.round((sellingSubtotal * c.value) / 100)
            : c.value;
        } else {
          state.appliedCoupon = null;
        }
      }

      const discountedSubtotal = Math.max(0, sellingSubtotal - couponDiscount);
      const freeShippingThreshold = 999;
      const deliveryCharge = discountedSubtotal === 0 || discountedSubtotal >= freeShippingThreshold ? 0 : 79;
      const finalPayable = discountedSubtotal + deliveryCharge;

      // 18% GST included in prices (standard Indian B2C MRP-inclusive GST calculation)
      const includedGst = Math.round(discountedSubtotal - (discountedSubtotal / 1.18));
      const totalSavings = mrpDiscount + couponDiscount + (deliveryCharge === 0 && discountedSubtotal > 0 ? 79 : 0);

      return {
        totalItems,
        totalMrp,
        sellingSubtotal,
        mrpDiscount,
        couponDiscount,
        discountedSubtotal,
        deliveryCharge,
        freeShippingThreshold,
        includedGst,
        finalPayable,
        totalSavings
      };
    }

    /*************************************************************************
     * 4. UI UTILITIES: TOASTS, THEME, CLIPBOARD, FLASH TIMER
     *************************************************************************/
    function showToast(message, type = 'success') {
      const container = document.getElementById('toastContainer');
      const id = 'toast-' + Date.now() + Math.random().toString(36).slice(2, 6);

      const palette = {
        success: 'bg-slate-900 dark:bg-white text-white dark:text-slate-900 border-emerald-500/40',
        info: 'bg-slate-900 dark:bg-white text-white dark:text-slate-900 border-brand-500/40',
        error: 'bg-rose-600 text-white border-rose-400/40'
      };
      const iconName = type === 'error' ? 'alert-circle' : (type === 'info' ? 'info' : 'check-circle-2');
      const iconColor = type === 'error' ? 'text-white' : (type === 'info' ? 'text-brand-400 dark:text-brand-600' : 'text-emerald-400 dark:text-emerald-600');

      const toast = document.createElement('div');
      toast.id = id;
      toast.className = `pointer-events-auto flex items-center gap-3 px-4 py-3 rounded-2xl shadow-xl border ${palette[type] || palette.success} animate-fadeUp text-sm font-medium`;
      toast.innerHTML = `
        <i data-lucide="${iconName}" class="w-4 h-4 shrink-0 ${iconColor}"></i>
        <span class="flex-1">${message}</span>
      `;
      container.appendChild(toast);
      lucide.createIcons();

      setTimeout(() => {
        toast.style.opacity = '0';
        toast.style.transform = 'translateY(8px)';
        toast.style.transition = 'all 0.25s ease';
        setTimeout(() => toast.remove(), 260);
      }, 2800);
    }

    function toggleTheme() {
      const isDark = document.documentElement.classList.toggle('dark');
      safeStorageSet(STORAGE_KEYS.THEME, isDark ? 'dark' : 'light');
      showToast(isDark ? 'Dark mode enabled' : 'Light mode enabled', 'info');
    }

    function copyPromoCode(code) {
      try {
        const tempInput = document.createElement('textarea');
        tempInput.value = code;
        tempInput.style.position = 'fixed';
        tempInput.style.opacity = '0';
        document.body.appendChild(tempInput);
        tempInput.select();
        document.execCommand('copy');
        document.body.removeChild(tempInput);
        showToast(`Coupon "${code}" copied! Apply it in your cart.`);
      } catch (e) {
        showToast(`Use coupon code: ${code}`, 'info');
      }
    }

    function startFlashSaleTimer() {
      // 5 hours, 42 minutes, 19 seconds countdown loop
      let remaining = (5 * 3600) + (42 * 60) + 19;
      const updateDisplay = () => {
        const hrs = Math.floor(remaining / 3600);
        const mins = Math.floor((remaining % 3600) / 60);
        const secs = remaining % 60;
        const hEl = document.getElementById('timerHours');
        const mEl = document.getElementById('timerMinutes');
        const sEl = document.getElementById('timerSeconds');
        if (hEl && mEl && sEl) {
          hEl.textContent = String(hrs).padStart(2, '0');
          mEl.textContent = String(mins).padStart(2, '0');
          sEl.textContent = String(secs).padStart(2, '0');
        }
        remaining = remaining > 0 ? remaining - 1 : (5 * 3600) + (59 * 60);
      };
      updateDisplay();
      setInterval(updateDisplay, 1000);
    }

    /*************************************************************************
     * 5. CATALOG FILTERING & PRODUCT GRID RENDERING
     *************************************************************************/
    function renderCategoryTabs() {
      const container = document.getElementById('categoryTabs');
      container.innerHTML = CATEGORIES.map(cat => {
        const active = state.selectedCategory === cat;
        const classes = active
          ? 'bg-slate-900 dark:bg-brand-600 text-white shadow-sm'
          : 'bg-white dark:bg-slate-900 text-slate-600 dark:text-slate-300 border border-slate-200 dark:border-slate-800 hover:bg-slate-100 dark:hover:bg-slate-800';
        return `
          <button
            onclick="selectCategory('${cat}')"
            class="px-4 py-2 rounded-xl text-xs sm:text-sm font-semibold whitespace-nowrap transition ${classes}"
          >
            ${cat}
          </button>
        `;
      }).join('');
    }

    function selectCategory(cat) {
      state.selectedCategory = cat;
      renderCategoryTabs();
      renderProducts();
      document.getElementById('catalog').scrollIntoView({ behavior: 'smooth', block: 'start' });
    }

    function clearSearch() {
      state.searchQuery = "";
      document.getElementById('desktopSearchInput').value = "";
      document.getElementById('mobileSearchInput').value = "";
      document.getElementById('desktopClearSearch').classList.add('hidden');
      document.getElementById('mobileClearSearch').classList.add('hidden');
      renderProducts();
    }

    function resetFilters() {
      state.selectedCategory = "All";
      state.searchQuery = "";
      state.maxPrice = 150000;
      state.minRating = 0;
      state.sortBy = "featured";

      document.getElementById('desktopSearchInput').value = "";
      document.getElementById('mobileSearchInput').value = "";
      document.getElementById('desktopClearSearch').classList.add('hidden');
      document.getElementById('mobileClearSearch').classList.add('hidden');
      document.getElementById('priceRangeSlider').value = 150000;
      document.getElementById('priceRangeLabel').textContent = formatINR(150000);
      document.getElementById('ratingFilter').value = "0";
      document.getElementById('sortSelect').value = "featured";

      renderCategoryTabs();
      renderProducts();
    }

    function getFilteredProducts() {
      const q = state.searchQuery.trim().toLowerCase();
      let list = PRODUCTS.filter(p => {
        const matchCat = state.selectedCategory === "All" || p.category === state.selectedCategory;
        const matchPrice = p.price <= state.maxPrice;
        const matchRating = p.rating >= state.minRating;
        const matchSearch = !q ||
          p.name.toLowerCase().includes(q) ||
          p.brand.toLowerCase().includes(q) ||
          p.category.toLowerCase().includes(q) ||
          p.description.toLowerCase().includes(q);
        return matchCat && matchPrice && matchRating && matchSearch;
      });

      if (state.sortBy === 'price-asc') list.sort((a, b) => a.price - b.price);
      else if (state.sortBy === 'price-desc') list.sort((a, b) => b.price - a.price);
      else if (state.sortBy === 'rating-desc') list.sort((a, b) => b.rating - a.rating || b.reviews - a.reviews);
      else if (state.sortBy === 'discount-desc') {
        list.sort((a, b) => getDiscountPercent(b.mrp, b.price) - getDiscountPercent(a.mrp, a.price));
      }
      return list;
    }

    function getProductCartEntry(productId) {
      return state.cart.find(item => item.productId === productId);
    }

    function renderProducts() {
      const grid = document.getElementById('productGrid');
      const emptyState = document.getElementById('emptyState');
      const filtered = getFilteredProducts();

      document.getElementById('resultCount').textContent = filtered.length;

      if (filtered.length === 0) {
        grid.innerHTML = '';
        emptyState.classList.remove('hidden');
        lucide.createIcons();
        return;
      }

      emptyState.classList.add('hidden');
      grid.innerHTML = filtered.map(product => {
        const discount = getDiscountPercent(product.mrp, product.price);
        const isWishlisted = state.wishlist.includes(product.id);
        const cartEntry = getProductCartEntry(product.id);
        const safeFallback = `https://placehold.co/600x450/e2e8f0/475569?text=${encodeURIComponent(product.brand)}`;

        return `
          <article class="group bg-white dark:bg-slate-900 border border-slate-200/80 dark:border-slate-800 rounded-2xl overflow-hidden shadow-sm hover:shadow-xl hover:-translate-y-0.5 transition-all duration-300 flex flex-col">
            <!-- Image Container -->
            <div class="relative aspect-[4/3] bg-slate-100 dark:bg-slate-800 overflow-hidden">
              <img
                src="${product.image}"
                alt="${product.name}"
                loading="lazy"
                onerror="this.onerror=null;this.src='${safeFallback}';"
                onclick="openQuickView(${product.id})"
                class="w-full h-full object-cover group-hover:scale-105 transition duration-500 cursor-pointer"
              />

              <!-- Discount Badge -->
              ${discount > 0 ? `
                <span class="absolute top-3 left-3 px-2.5 py-1 rounded-lg bg-emerald-600 text-white text-[11px] font-bold shadow">
                  ${discount}% OFF
                </span>
              ` : ''}

              <!-- Wishlist Toggle -->
              <button
                onclick="toggleWishlist(${product.id})"
                class="absolute top-3 right-3 p-2 rounded-full bg-white/90 dark:bg-slate-900/90 backdrop-blur-md shadow hover:scale-110 transition"
                aria-label="Toggle wishlist"
              >
                <i data-lucide="heart" class="w-4 h-4 ${isWishlisted ? 'text-rose-500 fill-rose-500' : 'text-slate-600 dark:text-slate-300'}"></i>
              </button>

              <!-- Quick View Pill -->
              <button
                onclick="openQuickView(${product.id})"
                class="absolute bottom-3 left-1/2 -translate-x-1/2 opacity-0 group-hover:opacity-100 translate-y-2 group-hover:translate-y-0 transition-all duration-200 px-3.5 py-1.5 rounded-full bg-slate-900/90 text-white text-xs font-semibold flex items-center gap-1.5 shadow-lg backdrop-blur-md whitespace-nowrap"
              >
                <i data-lucide="eye" class="w-3.5 h-3.5"></i>
                <span>Quick View</span>
              </button>
            </div>

            <!-- Card Content -->
            <div class="p-4 flex-1 flex flex-col justify-between gap-3">
              <div>
                <div class="flex items-center justify-between gap-2 text-xs text-slate-500 dark:text-slate-400 mb-1">
                  <span class="font-semibold uppercase tracking-wider text-[10px] text-brand-600 dark:text-brand-400">${product.category}</span>
                  <div class="inline-flex items-center gap-1 px-1.5 py-0.5 rounded-md bg-amber-50 dark:bg-amber-500/10 text-amber-600 dark:text-amber-400 font-bold text-[11px]">
                    <i data-lucide="star" class="w-3 h-3 fill-amber-400 text-amber-400"></i>
                    <span>${product.rating}</span>
                    <span class="font-normal text-slate-400">(${product.reviews.toLocaleString('en-IN')})</span>
                  </div>
                </div>

                <h3
                  onclick="openQuickView(${product.id})"
                  class="font-bold text-sm sm:text-base text-slate-900 dark:text-white line-clamp-2 hover:text-brand-600 dark:hover:text-brand-400 cursor-pointer transition"
                >
                  ${product.name}
                </h3>
              </div>

              <div class="space-y-3">
                <!-- Price Row -->
                <div class="flex items-baseline gap-2 flex-wrap">
                  <span class="text-lg font-extrabold text-slate-900 dark:text-white">${formatINR(product.price)}</span>
                  <span class="text-xs text-slate-400 line-through">${formatINR(product.mrp)}</span>
                  <span class="text-[11px] font-semibold text-emerald-600 dark:text-emerald-400">Save ${formatINR(product.mrp - product.price)}</span>
                </div>

                <!-- Add to Cart OR Quantity Stepper -->
                ${cartEntry ? `
                  <div class="flex items-center justify-between rounded-xl border-2 border-brand-600 dark:border-brand-500 bg-brand-50/70 dark:bg-brand-950/50 p-1">
                    <button
                      onclick="updateCartQty(${product.id}, '${cartEntry.variant}', -1)"
                      class="w-9 h-8 rounded-lg bg-white dark:bg-slate-800 hover:bg-brand-100 dark:hover:bg-slate-700 text-brand-700 dark:text-brand-300 font-bold flex items-center justify-center shadow-sm transition"
                      aria-label="Decrease quantity"
                    >
                      <i data-lucide="minus" class="w-4 h-4"></i>
                    </button>
                    <span class="font-bold text-sm text-brand-700 dark:text-brand-300">${cartEntry.qty} in Cart</span>
                    <button
                      onclick="updateCartQty(${product.id}, '${cartEntry.variant}', 1)"
                      class="w-9 h-8 rounded-lg bg-brand-600 hover:bg-brand-700 text-white font-bold flex items-center justify-center shadow-sm transition"
                      aria-label="Increase quantity"
                    >
                      <i data-lucide="plus" class="w-4 h-4"></i>
                    </button>
                  </div>
                ` : `
                  <div class="flex items-center gap-2">
                    <button
                      onclick="addToCart(${product.id}, '${product.variants[0]}')"
                      class="flex-1 py-2.5 px-3 rounded-xl bg-slate-900 dark:bg-brand-600 hover:bg-brand-600 dark:hover:bg-brand-500 text-white text-xs sm:text-sm font-semibold flex items-center justify-center gap-2 transition"
                    >
                      <i data-lucide="shopping-bag" class="w-4 h-4"></i>
                      <span>Add to Cart</span>
                    </button>
                    <button
                      onclick="openQuickView(${product.id})"
                      class="p-2.5 rounded-xl border border-slate-200 dark:border-slate-700 hover:bg-slate-100 dark:hover:bg-slate-800 text-slate-600 dark:text-slate-300 transition sm:hidden"
                      aria-label="Quick view"
                    >
                      <i data-lucide="eye" class="w-4 h-4"></i>
                    </button>
                  </div>
                `}
              </div>
            </div>
          </article>
        `;
      }).join('');

      lucide.createIcons();
    }

    /*************************************************************************
     * 6. CART & WISHLIST LOGIC
     *************************************************************************/
    function addToCart(productId, variant, silent = false) {
      const product = PRODUCTS.find(p => p.id === productId);
      if (!product) return;
      const chosenVariant = variant || product.variants[0];

      const existing = state.cart.find(item => item.productId === productId && item.variant === chosenVariant);
      if (existing) {
        existing.qty += 1;
      } else {
        state.cart.push({ productId, variant: chosenVariant, qty: 1 });
      }

      persistCart();
      updateHeaderBadges();
      renderProducts();
      renderCartDrawer();
      if (!silent) showToast(`Added "${product.name.slice(0, 28)}..." to cart`);
    }

    function updateCartQty(productId, variant, delta) {
      const idx = state.cart.findIndex(item => item.productId === productId && item.variant === variant);
      if (idx === -1) return;

      state.cart[idx].qty += delta;
      if (state.cart[idx].qty <= 0) {
        state.cart.splice(idx, 1);
        showToast('Item removed from cart', 'info');
      }

      persistCart();
      updateHeaderBadges();
      renderProducts();
      renderCartDrawer();
    }

    function removeFromCart(productId, variant) {
      state.cart = state.cart.filter(item => !(item.productId === productId && item.variant === variant));
      persistCart();
      updateHeaderBadges();
      renderProducts();
      renderCartDrawer();
      showToast('Item removed from cart', 'info');
    }

    function toggleWishlist(productId) {
      const idx = state.wishlist.indexOf(productId);
      const product = PRODUCTS.find(p => p.id === productId);
      if (idx > -1) {
        state.wishlist.splice(idx, 1);
        showToast('Removed from wishlist', 'info');
      } else {
        state.wishlist.push(productId);
        showToast(`Saved "${product ? product.brand : 'Item'}" to wishlist`);
      }
      persistWishlist();
      updateHeaderBadges();
      renderProducts();
      renderWishlistDrawer();
    }

    function moveWishlistToCart(productId) {
      const product = PRODUCTS.find(p => p.id === productId);
      if (!product) return;
      addToCart(productId, product.variants[0], true);
      state.wishlist = state.wishlist.filter(id => id !== productId);
      persistWishlist();
      updateHeaderBadges();
      renderWishlistDrawer();
      renderProducts();
      showToast('Moved item from wishlist to cart!');
    }

    function updateHeaderBadges() {
      const totalCartQty = state.cart.reduce((sum, item) => sum + item.qty, 0);
      document.getElementById('cartBadge').textContent = totalCartQty;
      document.getElementById('cartDrawerCount').textContent = totalCartQty;

      const wishBadge = document.getElementById('wishlistBadge');
      if (state.wishlist.length > 0) {
        wishBadge.textContent = state.wishlist.length;
        wishBadge.classList.remove('hidden');
      } else {
        wishBadge.classList.add('hidden');
      }

      const ordersBadge = document.getElementById('ordersBadge');
      if (state.orders.length > 0) {
        ordersBadge.textContent = state.orders.length;
        ordersBadge.classList.remove('hidden');
      } else {
        ordersBadge.classList.add('hidden');
      }
    }

    /*************************************************************************
     * 7. PRODUCT QUICK VIEW MODAL & PINCODE CHECKER
     *************************************************************************/
    function openQuickView(productId) {
      const product = PRODUCTS.find(p => p.id === productId);
      if (!product) return;

      state.quickViewProductId = productId;
      state.quickViewVariant = product.variants[0];

      const discount = getDiscountPercent(product.mrp, product.price);
      const safeFallback = `https://placehold.co/800x600/e2e8f0/475569?text=${encodeURIComponent(product.brand)}`;

      document.getElementById('quickViewContent').innerHTML = `
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 lg:gap-8">
          <!-- Left: Product Image -->
          <div class="space-y-3">
            <div class="relative aspect-square rounded-2xl overflow-hidden bg-slate-100 dark:bg-slate-800 border border-slate-200 dark:border-slate-700">
              <img
                src="${product.image}"
                alt="${product.name}"
                onerror="this.onerror=null;this.src='${safeFallback}';"
                class="w-full h-full object-cover"
              />
              ${discount > 0 ? `<span class="absolute top-3 left-3 px-3 py-1 rounded-lg bg-emerald-600 text-white text-xs font-bold">${discount}% OFF</span>` : ''}
            </div>
            <div class="grid grid-cols-3 gap-2 text-center text-[11px] font-medium text-slate-600 dark:text-slate-300">
              <div class="p-2 rounded-xl bg-slate-50 dark:bg-slate-800/80">✅ Genuine Product</div>
              <div class="p-2 rounded-xl bg-slate-50 dark:bg-slate-800/80">🔄 7-Day Replace</div>
              <div class="p-2 rounded-xl bg-slate-50 dark:bg-slate-800/80">🧾 GST Invoice</div>
            </div>
          </div>

          <!-- Right: Details -->
          <div class="space-y-4">
            <div>
              <div class="flex items-center gap-2 text-xs font-bold text-brand-600 dark:text-brand-400 uppercase tracking-wider">
                <span>${product.brand}</span>
                <span>•</span>
                <span>${product.category}</span>
              </div>
              <h2 class="text-xl sm:text-2xl font-extrabold mt-1 leading-snug">${product.name}</h2>
              <div class="flex items-center gap-2 mt-2">
                <span class="inline-flex items-center gap-1 px-2 py-0.5 rounded-lg bg-emerald-600 text-white text-xs font-bold">
                  ${product.rating} <i data-lucide="star" class="w-3 h-3 fill-white"></i>
                </span>
                <span class="text-xs text-slate-500 dark:text-slate-400">${product.reviews.toLocaleString('en-IN')} Verified Ratings</span>
              </div>
            </div>

            <!-- Price -->
            <div class="p-3.5 rounded-2xl bg-slate-50 dark:bg-slate-800/70 border border-slate-200/70 dark:border-slate-700/70">
              <div class="flex items-baseline gap-2.5 flex-wrap">
                <span class="text-2xl sm:text-3xl font-extrabold">${formatINR(product.price)}</span>
                <span class="text-sm text-slate-400 line-through">${formatINR(product.mrp)}</span>
                <span class="text-xs font-bold text-emerald-600 dark:text-emerald-400">You save ${formatINR(product.mrp - product.price)}</span>
              </div>
              <p class="text-[11px] text-slate-500 dark:text-slate-400 mt-1">Inclusive of all taxes (18% GST included)</p>
            </div>

            <!-- Description -->
            <p class="text-sm text-slate-600 dark:text-slate-300 leading-relaxed">${product.description}</p>

            <!-- Highlights -->
            <div>
              <h4 class="text-xs font-bold uppercase tracking-wider text-slate-500 dark:text-slate-400 mb-2">Key Highlights</h4>
              <ul class="space-y-1.5 text-xs sm:text-sm text-slate-700 dark:text-slate-300">
                ${product.specs.map(s => `
                  <li class="flex items-center gap-2">
                    <i data-lucide="check-circle-2" class="w-4 h-4 text-emerald-500 shrink-0"></i>
                    <span>${s}</span>
                  </li>
                `).join('')}
              </ul>
            </div>

            <!-- Selectable Variants -->
            <div>
              <h4 class="text-xs font-bold uppercase tracking-wider text-slate-500 dark:text-slate-400 mb-2">Select ${product.variantLabel}</h4>
              <div id="quickViewVariants" class="flex flex-wrap gap-2">
                ${product.variants.map((v, i) => `
                  <button
                    onclick="selectQuickViewVariant('${v}')"
                    data-variant="${v}"
                    class="qv-variant-btn px-3.5 py-2 rounded-xl text-xs font-semibold border transition ${i === 0 ? 'border-brand-600 bg-brand-50 dark:bg-brand-900/40 text-brand-700 dark:text-brand-300 ring-2 ring-brand-500/20' : 'border-slate-200 dark:border-slate-700 hover:border-slate-400'}"
                  >
                    ${v}
                  </button>
                `).join('')}
              </div>
            </div>

            <!-- Indian Pincode Delivery Checker -->
            <div class="p-3.5 rounded-2xl border border-slate-200 dark:border-slate-700 space-y-2">
              <label class="text-xs font-bold flex items-center gap-1.5">
                <i data-lucide="map-pin" class="w-4 h-4 text-brand-600 dark:text-brand-400"></i>
                <span>Check Delivery & COD Availability</span>
              </label>
              <div class="flex gap-2">
                <input
                  id="qvPincodeInput"
                  type="text"
                  maxlength="6"
                  inputmode="numeric"
                  placeholder="Enter 6-digit Pincode (e.g. 110001)"
                  class="flex-1 px-3 py-2 text-xs sm:text-sm rounded-xl bg-slate-100 dark:bg-slate-800 border border-transparent focus:border-brand-500 outline-none"
                />
                <button
                  onclick="checkPincodeDelivery()"
                  class="px-4 py-2 rounded-xl bg-slate-900 dark:bg-slate-700 hover:bg-brand-600 text-white text-xs font-bold transition"
                >
                  Check
                </button>
              </div>
              <div id="qvPincodeResult" class="text-xs"></div>
            </div>

            <!-- Action Buttons -->
            <div class="grid grid-cols-2 gap-3 pt-1">
              <button
                onclick="addFromQuickView(false)"
                class="py-3 px-4 rounded-xl border-2 border-slate-900 dark:border-brand-500 text-slate-900 dark:text-white hover:bg-slate-100 dark:hover:bg-brand-950 font-bold text-sm flex items-center justify-center gap-2 transition"
              >
                <i data-lucide="shopping-cart" class="w-4 h-4"></i>
                <span>Add to Cart</span>
              </button>
              <button
                onclick="addFromQuickView(true)"
                class="py-3 px-4 rounded-xl bg-brand-600 hover:bg-brand-700 text-white font-bold text-sm flex items-center justify-center gap-2 shadow-lg shadow-brand-600/25 transition"
              >
                <i data-lucide="zap" class="w-4 h-4"></i>
                <span>Buy Now</span>
              </button>
            </div>
          </div>
        </div>
      `;

      document.getElementById('quickViewModal').classList.remove('hidden');
      document.body.classList.add('overflow-hidden');
      lucide.createIcons();
    }

    function selectQuickViewVariant(variant) {
      state.quickViewVariant = variant;
      document.querySelectorAll('.qv-variant-btn').forEach(btn => {
        const isSelected = btn.getAttribute('data-variant') === variant;
        btn.className = `qv-variant-btn px-3.5 py-2 rounded-xl text-xs font-semibold border transition ${
          isSelected
            ? 'border-brand-600 bg-brand-50 dark:bg-brand-900/40 text-brand-700 dark:text-brand-300 ring-2 ring-brand-500/20'
            : 'border-slate-200 dark:border-slate-700 hover:border-slate-400'
        }`;
      });
    }

    function checkPincodeDelivery() {
      const input = document.getElementById('qvPincodeInput');
      const result = document.getElementById('qvPincodeResult');
      const pin = (input.value || '').trim();

      if (!/^[1-9][0-9]{5}$/.test(pin)) {
        result.innerHTML = `<span class="text-rose-500 font-semibold">Please enter a valid 6-digit Indian pincode (e.g., 110001, 400001, 560001).</span>`;
        return;
      }

      // Map common Indian metro prefixes for realistic experience
      const prefixMap = {
        '11': { city: 'New Delhi / NCR', days: 2 },
        '40': { city: 'Mumbai / Navi Mumbai', days: 2 },
        '56': { city: 'Bengaluru', days: 2 },
        '60': { city: 'Chennai', days: 3 },
        '70': { city: 'Kolkata', days: 3 },
        '50': { city: 'Hyderabad', days: 3 },
        '41': { city: 'Pune', days: 3 },
        '38': { city: 'Ahmedabad', days: 3 }
      };
      const info = prefixMap[pin.slice(0, 2)] || { city: `Pincode ${pin}`, days: 4 };
      const eta = getEstimatedDeliveryDate(info.days);

      result.innerHTML = `
        <div class="mt-1 p-2.5 rounded-xl bg-emerald-50 dark:bg-emerald-950/50 border border-emerald-200 dark:border-emerald-800 text-emerald-700 dark:text-emerald-300 space-y-0.5">
          <p class="font-bold">✓ Express Delivery to ${info.city} by ${eta}</p>
          <p class="text-[11px] opacity-90">Cash on Delivery & 7-Day Easy Replacement available.</p>
        </div>
      `;
    }

    function addFromQuickView(buyNow) {
      if (!state.quickViewProductId) return;
      addToCart(state.quickViewProductId, state.quickViewVariant, buyNow);
      closeQuickView();
      if (buyNow) {
        openCheckoutModal();
      }
    }

    function closeQuickView() {
      document.getElementById('quickViewModal').classList.add('hidden');
      document.body.classList.remove('overflow-hidden');
    }

    /*************************************************************************
     * 8. CART DRAWER & COUPON SYSTEM
     *************************************************************************/
    function openCartDrawer() {
      renderCartDrawer();
      document.getElementById('cartDrawerOverlay').classList.remove('hidden');
      document.body.classList.add('overflow-hidden');
    }

    function closeCartDrawer() {
      document.getElementById('cartDrawerOverlay').classList.add('hidden');
      document.body.classList.remove('overflow-hidden');
    }

    function applyCouponCode(manualCode) {
      const inputEl = document.getElementById('couponInput');
      const code = (manualCode || (inputEl ? inputEl.value : '')).trim().toUpperCase();

      if (!code) {
        showToast('Please enter a coupon code', 'error');
        return;
      }

      const coupon = COUPONS[code];
      if (!coupon) {
        showToast(`Invalid coupon "${code}". Try SAVE10 or WELCOME200.`, 'error');
        return;
      }

      const totals = calculateCartTotals();
      if (totals.sellingSubtotal < coupon.minOrder) {
        showToast(`Minimum order of ${formatINR(coupon.minOrder)} required for ${code}`, 'error');
        return;
      }

      state.appliedCoupon = code;
      renderCartDrawer();
      showToast(`Coupon ${code} applied! (${coupon.label})`);
    }

    function removeCoupon() {
      state.appliedCoupon = null;
      renderCartDrawer();
      showToast('Coupon removed', 'info');
    }

    function renderCartDrawer() {
      const shippingBar = document.getElementById('shippingBarContainer');
      const itemsContainer = document.getElementById('cartItemsContainer');
      const footer = document.getElementById('cartFooter');
      const totals = calculateCartTotals();

      // Free Shipping Progress Bar
      if (totals.totalItems === 0) {
        shippingBar.classList.add('hidden');
      } else {
        shippingBar.classList.remove('hidden');
        const remaining = Math.max(0, totals.freeShippingThreshold - totals.discountedSubtotal);
        const pct = Math.min(100, Math.round((totals.discountedSubtotal / totals.freeShippingThreshold) * 100));
        shippingBar.innerHTML = remaining > 0 ? `
          <div class="space-y-1.5">
            <p class="text-xs font-medium">Add <strong class="text-brand-600 dark:text-brand-400">${formatINR(remaining)}</strong> more for <strong class="text-emerald-600 dark:text-emerald-400">FREE Express Delivery</strong></p>
            <div class="w-full h-2 rounded-full bg-slate-200 dark:bg-slate-700 overflow-hidden">
              <div class="h-full bg-brand-600 rounded-full transition-all duration-300" style="width: ${pct}%"></div>
            </div>
          </div>
        ` : `
          <div class="flex items-center gap-2 text-xs font-semibold text-emerald-600 dark:text-emerald-400">
            <i data-lucide="check-circle-2" class="w-4 h-4 shrink-0"></i>
            <span>Yay! You've unlocked FREE Express Delivery across India!</span>
          </div>
        `;
      }

      // Empty Cart State
      if (state.cart.length === 0) {
        itemsContainer.innerHTML = `
          <div class="h-full flex flex-col items-center justify-center text-center py-12">
            <div class="w-16 h-16 rounded-2xl bg-slate-100 dark:bg-slate-800 flex items-center justify-center text-slate-400 mb-4">
              <i data-lucide="shopping-bag" class="w-8 h-8"></i>
            </div>
            <h3 class="font-bold text-base">Your cart is empty</h3>
            <p class="text-xs text-slate-500 dark:text-slate-400 mt-1 max-w-xs">Explore our curated tech, audio, watches, and fashion deals to fill your bag.</p>
            <button onclick="closeCartDrawer()" class="mt-5 px-5 py-2.5 rounded-xl bg-brand-600 hover:bg-brand-700 text-white text-sm font-semibold transition">
              Start Shopping
            </button>
          </div>
        `;
        footer.innerHTML = '';
        footer.classList.add('hidden');
        lucide.createIcons();
        return;
      }

      footer.classList.remove('hidden');

      // Cart Items List
      itemsContainer.innerHTML = state.cart.map(item => {
        const product = PRODUCTS.find(p => p.id === item.productId);
        if (!product) return '';
        const safeFallback = `https://placehold.co/150x150/e2e8f0/475569?text=${encodeURIComponent(product.brand)}`;
        return `
          <div class="flex gap-3 p-3 rounded-2xl bg-white dark:bg-slate-800/70 border border-slate-200/80 dark:border-slate-700/80">
            <img
              src="${product.image}"
              alt="${product.name}"
              onerror="this.onerror=null;this.src='${safeFallback}';"
              class="w-20 h-20 rounded-xl object-cover bg-slate-100 shrink-0"
            />
            <div class="flex-1 min-w-0 flex flex-col justify-between">
              <div class="flex items-start justify-between gap-2">
                <div class="min-w-0">
                  <h4 class="font-bold text-xs sm:text-sm line-clamp-1">${product.name}</h4>
                  <p class="text-[11px] text-slate-500 dark:text-slate-400">${product.variantLabel}: ${item.variant}</p>
                </div>
                <button
                  onclick="removeFromCart(${product.id}, '${item.variant}')"
                  class="text-slate-400 hover:text-rose-500 p-1 transition"
                  aria-label="Remove item"
                >
                  <i data-lucide="trash-2" class="w-4 h-4"></i>
                </button>
              </div>
              <div class="flex items-center justify-between mt-2">
                <div>
                  <span class="font-extrabold text-sm">${formatINR(product.price * item.qty)}</span>
                  <span class="text-[11px] text-slate-400 line-through ml-1">${formatINR(product.mrp * item.qty)}</span>
                </div>
                <div class="flex items-center gap-1 bg-slate-100 dark:bg-slate-900 rounded-lg p-0.5 border border-slate-200 dark:border-slate-700">
                  <button onclick="updateCartQty(${product.id}, '${item.variant}', -1)" class="w-7 h-7 rounded-md hover:bg-white dark:hover:bg-slate-800 flex items-center justify-center transition">
                    <i data-lucide="minus" class="w-3.5 h-3.5"></i>
                  </button>
                  <span class="w-6 text-center text-xs font-bold">${item.qty}</span>
                  <button onclick="updateCartQty(${product.id}, '${item.variant}', 1)" class="w-7 h-7 rounded-md hover:bg-white dark:hover:bg-slate-800 flex items-center justify-center transition">
                    <i data-lucide="plus" class="w-3.5 h-3.5"></i>
                  </button>
                </div>
              </div>
            </div>
          </div>
        `;
      }).join('');

      // Cart Footer: Coupon & Breakdown
      footer.innerHTML = `
        <!-- Coupon Input -->
        <div class="space-y-2">
          ${state.appliedCoupon ? `
            <div class="flex items-center justify-between px-3 py-2 rounded-xl bg-emerald-50 dark:bg-emerald-950/60 border border-emerald-200 dark:border-emerald-800 text-xs">
              <div class="flex items-center gap-2 text-emerald-700 dark:text-emerald-300 font-semibold">
                <i data-lucide="ticket-check" class="w-4 h-4"></i>
                <span>${state.appliedCoupon} applied (-${formatINR(totals.couponDiscount)})</span>
              </div>
              <button onclick="removeCoupon()" class="text-rose-500 hover:underline font-bold">Remove</button>
            </div>
          ` : `
            <div class="flex gap-2">
              <input
                id="couponInput"
                type="text"
                placeholder="Coupon code (SAVE10 / WELCOME200)"
                class="flex-1 px-3 py-2 text-xs rounded-xl bg-white dark:bg-slate-800 border border-slate-200 dark:border-slate-700 uppercase outline-none focus:border-brand-500"
              />
              <button onclick="applyCouponCode()" class="px-4 py-2 rounded-xl bg-slate-900 dark:bg-slate-700 hover:bg-brand-600 text-white text-xs font-bold transition">
                Apply
              </button>
            </div>
            <div class="flex items-center gap-2 text-[11px]">
              <span class="text-slate-500">Quick apply:</span>
              <button onclick="applyCouponCode('SAVE10')" class="px-2 py-0.5 rounded-md bg-brand-50 dark:bg-brand-900/40 text-brand-700 dark:text-brand-300 font-bold hover:underline">SAVE10</button>
              <button onclick="applyCouponCode('WELCOME200')" class="px-2 py-0.5 rounded-md bg-brand-50 dark:bg-brand-900/40 text-brand-700 dark:text-brand-300 font-bold hover:underline">WELCOME200</button>
            </div>
          `}
        </div>

        <!-- Price Summary -->
        <div class="space-y-1.5 text-xs sm:text-sm border-t border-slate-200 dark:border-slate-800 pt-3">
          <div class="flex justify-between text-slate-600 dark:text-slate-400">
            <span>Total MRP</span>
            <span>${formatINR(totals.totalMrp)}</span>
          </div>
          <div class="flex justify-between text-emerald-600 dark:text-emerald-400">
            <span>Discount on MRP</span>
            <span>-${formatINR(totals.mrpDiscount)}</span>
          </div>
          ${totals.couponDiscount > 0 ? `
            <div class="flex justify-between text-emerald-600 dark:text-emerald-400 font-medium">
              <span>Coupon (${state.appliedCoupon})</span>
              <span>-${formatINR(totals.couponDiscount)}</span>
            </div>
          ` : ''}
          <div class="flex justify-between text-slate-600 dark:text-slate-400">
            <span>Delivery Charge</span>
            <span class="${totals.deliveryCharge === 0 ? 'text-emerald-600 dark:text-emerald-400 font-semibold' : ''}">
              ${totals.deliveryCharge === 0 ? 'FREE' : formatINR(totals.deliveryCharge)}
            </span>
          </div>
          <div class="flex justify-between text-[11px] text-slate-500 dark:text-slate-400">
            <span>Included GST (18%)</span>
            <span>${formatINR(totals.includedGst)}</span>
          </div>
          <div class="flex justify-between text-base font-extrabold pt-2 border-t border-slate-200 dark:border-slate-800">
            <span>Total Payable</span>
            <span>${formatINR(totals.finalPayable)}</span>
          </div>
        </div>

        <button
          onclick="proceedToCheckout()"
          class="w-full py-3.5 rounded-xl bg-brand-600 hover:bg-brand-700 text-white font-bold text-sm flex items-center justify-center gap-2 shadow-lg shadow-brand-600/25 transition"
        >
          <span>Proceed to Checkout</span>
          <i data-lucide="arrow-right" class="w-4 h-4"></i>
        </button>
      `;

      lucide.createIcons();
    }

    /*************************************************************************
     * 9. WISHLIST DRAWER
     *************************************************************************/
    function openWishlistDrawer() {
      renderWishlistDrawer();
      document.getElementById('wishlistDrawerOverlay').classList.remove('hidden');
      document.body.classList.add('overflow-hidden');
    }

    function closeWishlistDrawer() {
      document.getElementById('wishlistDrawerOverlay').classList.add('hidden');
      document.body.classList.remove('overflow-hidden');
    }

    function renderWishlistDrawer() {
      const container = document.getElementById('wishlistItemsContainer');
      if (state.wishlist.length === 0) {
        container.innerHTML = `
          <div class="h-full flex flex-col items-center justify-center text-center py-12">
            <div class="w-16 h-16 rounded-2xl bg-rose-50 dark:bg-rose-950/40 flex items-center justify-center text-rose-400 mb-4">
              <i data-lucide="heart" class="w-8 h-8"></i>
            </div>
            <h3 class="font-bold text-base">Your wishlist is empty</h3>
            <p class="text-xs text-slate-500 dark:text-slate-400 mt-1 max-w-xs">Tap the heart icon on any product to save it here for later.</p>
          </div>
        `;
        lucide.createIcons();
        return;
      }

      container.innerHTML = state.wishlist.map(id => {
        const product = PRODUCTS.find(p => p.id === id);
        if (!product) return '';
        const safeFallback = `https://placehold.co/150x150/e2e8f0/475569?text=${encodeURIComponent(product.brand)}`;
        return `
          <div class="flex gap-3 p-3 rounded-2xl bg-slate-50 dark:bg-slate-800/70 border border-slate-200/80 dark:border-slate-700/80">
            <img
              src="${product.image}"
              alt="${product.name}"
              onerror="this.onerror=null;this.src='${safeFallback}';"
              class="w-20 h-20 rounded-xl object-cover shrink-0"
            />
            <div class="flex-1 min-w-0 flex flex-col justify-between">
              <div>
                <h4 class="font-bold text-xs sm:text-sm line-clamp-1">${product.name}</h4>
                <div class="flex items-baseline gap-2 mt-0.5">
                  <span class="font-extrabold text-sm">${formatINR(product.price)}</span>
                  <span class="text-[11px] text-slate-400 line-through">${formatINR(product.mrp)}</span>
                </div>
              </div>
              <div class="flex items-center gap-2 mt-2">
                <button
                  onclick="moveWishlistToCart(${product.id})"
                  class="flex-1 py-1.5 px-3 rounded-lg bg-slate-900 dark:bg-brand-600 hover:bg-brand-600 text-white text-xs font-semibold transition"
                >
                  Move to Cart
                </button>
                <button
                  onclick="toggleWishlist(${product.id})"
                  class="p-1.5 rounded-lg border border-slate-200 dark:border-slate-700 hover:text-rose-500 transition"
                  aria-label="Remove from wishlist"
                >
                  <i data-lucide="trash-2" class="w-4 h-4"></i>
                </button>
              </div>
            </div>
          </div>
        `;
      }).join('');

      lucide.createIcons();
    }

    /*************************************************************************
     * 10. MULTI-STEP CHECKOUT FLOW (Address -> Payment -> Confirmation)
     *************************************************************************/
    function proceedToCheckout() {
      closeCartDrawer();
      openCheckoutModal();
    }

    function openCheckoutModal() {
      if (state.cart.length === 0) {
        showToast('Your cart is empty!', 'error');
        return;
      }
      state.checkoutStep = 1;
      renderCheckoutStep();
      document.getElementById('checkoutModal').classList.remove('hidden');
      document.body.classList.add('overflow-hidden');
    }

    function closeCheckoutModal() {
      document.getElementById('checkoutModal').classList.add('hidden');
      document.body.classList.remove('overflow-hidden');
    }

    function updateStepIndicators() {
      for (let i = 1; i <= 3; i++) {
        const el = document.getElementById(`stepIndicator${i}`);
        const badge = el.querySelector('span');
        if (i < state.checkoutStep) {
          el.className = 'flex items-center gap-2 text-emerald-600 dark:text-emerald-400';
          badge.className = 'w-6 h-6 rounded-full bg-emerald-600 text-white flex items-center justify-center text-xs font-bold';
          badge.textContent = '✓';
        } else if (i === state.checkoutStep) {
          el.className = 'flex items-center gap-2 text-brand-600 dark:text-brand-400';
          badge.className = 'w-6 h-6 rounded-full bg-brand-600 text-white flex items-center justify-center text-xs font-bold';
          badge.textContent = String(i);
        } else {
          el.className = 'flex items-center gap-2 text-slate-400';
          badge.className = 'w-6 h-6 rounded-full bg-slate-200 dark:bg-slate-800 text-slate-500 flex items-center justify-center text-xs font-bold';
          badge.textContent = String(i);
        }
      }
    }

    function renderCheckoutStep() {
      updateStepIndicators();
      const body = document.getElementById('checkoutBody');
      const totals = calculateCartTotals();

      if (state.checkoutStep === 1) {
        const addr = state.checkoutAddress;
        body.innerHTML = `
          <form id="addressForm" onsubmit="handleAddressSubmit(event)" class="space-y-4">
            <h3 class="font-bold text-base">Step 1: Delivery Address</h3>
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <div>
                <label class="block text-xs font-semibold mb-1">Full Name *</label>
                <input name="fullName" required value="${addr.fullName}" placeholder="e.g. Aarav Sharma" class="w-full px-3.5 py-2.5 text-sm rounded-xl bg-slate-100 dark:bg-slate-800 border border-transparent focus:border-brand-500 outline-none" />
              </div>
              <div>
                <label class="block text-xs font-semibold mb-1">10-Digit Mobile Number *</label>
                <input name="phone" required maxlength="10" inputmode="numeric" value="${addr.phone}" placeholder="9876543210" class="w-full px-3.5 py-2.5 text-sm rounded-xl bg-slate-100 dark:bg-slate-800 border border-transparent focus:border-brand-500 outline-none" />
              </div>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
              <div>
                <label class="block text-xs font-semibold mb-1">6-Digit Pincode *</label>
                <input name="pincode" required maxlength="6" inputmode="numeric" value="${addr.pincode}" placeholder="110001" class="w-full px-3.5 py-2.5 text-sm rounded-xl bg-slate-100 dark:bg-slate-800 border border-transparent focus:border-brand-500 outline-none" />
              </div>
              <div>
                <label class="block text-xs font-semibold mb-1">City *</label>
                <input name="city" required value="${addr.city}" placeholder="New Delhi" class="w-full px-3.5 py-2.5 text-sm rounded-xl bg-slate-100 dark:bg-slate-800 border border-transparent focus:border-brand-500 outline-none" />
              </div>
              <div>
                <label class="block text-xs font-semibold mb-1">State *</label>
                <select name="state" class="w-full px-3.5 py-2.5 text-sm rounded-xl bg-slate-100 dark:bg-slate-800 border border-transparent focus:border-brand-500 outline-none">
                  ${INDIAN_STATES.map(s => `<option value="${s}" ${addr.state === s ? 'selected' : ''}>${s}</option>`).join('')}
                </select>
              </div>
            </div>

            <div>
              <label class="block text-xs font-semibold mb-1">Flat / House No., Building, Street *</label>
              <textarea name="street" required rows="2" placeholder="House 42, Sector 18, Near Metro Station" class="w-full px-3.5 py-2.5 text-sm rounded-xl bg-slate-100 dark:bg-slate-800 border border-transparent focus:border-brand-500 outline-none">${addr.street}</textarea>
            </div>

            <div id="addressError" class="hidden text-xs font-semibold text-rose-500"></div>

            <div class="flex items-center justify-between pt-3 border-t border-slate-200 dark:border-slate-800">
              <div class="text-xs">
                <span class="text-slate-500">Payable Total:</span>
                <span class="text-base font-extrabold ml-1">${formatINR(totals.finalPayable)}</span>
              </div>
              <button type="submit" class="px-6 py-3 rounded-xl bg-brand-600 hover:bg-brand-700 text-white font-bold text-sm flex items-center gap-2 transition">
                <span>Continue to Payment</span>
                <i data-lucide="arrow-right" class="w-4 h-4"></i>
              </button>
            </div>
          </form>
        `;
      } else if (state.checkoutStep === 2) {
        const pm = state.checkoutPayment;
        body.innerHTML = `
          <form id="paymentForm" onsubmit="handlePaymentSubmit(event)" class="space-y-5">
            <div class="flex items-center justify-between">
              <h3 class="font-bold text-base">Step 2: Select Payment Method</h3>
              <button type="button" onclick="state.checkoutStep=1;renderCheckoutStep();" class="text-xs font-semibold text-brand-600 dark:text-brand-400 hover:underline">
                ← Edit Address
              </button>
            </div>

            <!-- Payment Method Options -->
            <div class="space-y-3">
              <!-- UPI Option -->
              <label onclick="selectPaymentMethod('UPI')" class="block p-4 rounded-2xl border-2 cursor-pointer transition ${pm === 'UPI' ? 'border-brand-600 bg-brand-50/50 dark:bg-brand-950/40' : 'border-slate-200 dark:border-slate-800'}">
                <div class="flex items-center justify-between">
                  <div class="flex items-center gap-3">
                    <input type="radio" name="paymentMethod" value="UPI" ${pm === 'UPI' ? 'checked' : ''} class="accent-brand-600 w-4 h-4" />
                    <div>
                      <p class="font-bold text-sm">UPI (GPay / PhonePe / Paytm)</p>
                      <p class="text-xs text-slate-500 dark:text-slate-400">Instant zero-fee verification</p>
                    </div>
                  </div>
                  <span class="px-2 py-0.5 rounded-md bg-emerald-100 dark:bg-emerald-900/50 text-emerald-700 dark:text-emerald-300 text-[10px] font-bold">FASTEST</span>
                </div>
                ${pm === 'UPI' ? `
                  <div class="mt-3 pl-7 space-y-2">
                    <input id="upiIdInput" type="text" placeholder="Enter UPI ID (e.g. aarav@okaxis or 9876543210@ybl)" class="w-full px-3.5 py-2 text-sm rounded-xl bg-white dark:bg-slate-900 border border-slate-300 dark:border-slate-700 focus:border-brand-500 outline-none" />
                    <div class="flex gap-2 text-[11px]">
                      <button type="button" onclick="document.getElementById('upiIdInput').value='customer@okhdfcbank'" class="px-2.5 py-1 rounded-lg bg-white dark:bg-slate-800 border border-slate-200 dark:border-slate-700 font-semibold">GPay</button>
                      <button type="button" onclick="document.getElementById('upiIdInput').value='customer@ybl'" class="px-2.5 py-1 rounded-lg bg-white dark:bg-slate-800 border border-slate-200 dark:border-slate-700 font-semibold">PhonePe</button>
                      <button type="button" onclick="document.getElementById('upiIdInput').value='customer@paytm'" class="px-2.5 py-1 rounded-lg bg-white dark:bg-slate-800 border border-slate-200 dark:border-slate-700 font-semibold">Paytm</button>
                    </div>
                  </div>
                ` : ''}
              </label>

              <!-- Card Option -->
              <label onclick="selectPaymentMethod('CARD')" class="block p-4 rounded-2xl border-2 cursor-pointer transition ${pm === 'CARD' ? 'border-brand-600 bg-brand-50/50 dark:bg-brand-950/40' : 'border-slate-200 dark:border-slate-800'}">
                <div class="flex items-center gap-3">
                  <input type="radio" name="paymentMethod" value="CARD" ${pm === 'CARD' ? 'checked' : ''} class="accent-brand-600 w-4 h-4" />
                  <div>
                    <p class="font-bold text-sm">Credit / Debit Card</p>
                    <p class="text-xs text-slate-500 dark:text-slate-400">RuPay, Visa, Mastercard, Amex</p>
                  </div>
                </div>
                ${pm === 'CARD' ? `
                  <div class="mt-3 pl-7 grid grid-cols-2 gap-2.5">
                    <input id="cardNumberInput" type="text" maxlength="19" placeholder="Card Number (16 digits)" class="col-span-2 px-3.5 py-2 text-sm rounded-xl bg-white dark:bg-slate-900 border border-slate-300 dark:border-slate-700 outline-none" />
                    <input id="cardExpiryInput" type="text" maxlength="5" placeholder="MM/YY" class="px-3.5 py-2 text-sm rounded-xl bg-white dark:bg-slate-900 border border-slate-300 dark:border-slate-700 outline-none" />
                    <input id="cardCvvInput" type="password" maxlength="4" placeholder="CVV" class="px-3.5 py-2 text-sm rounded-xl bg-white dark:bg-slate-900 border border-slate-300 dark:border-slate-700 outline-none" />
                  </div>
                ` : ''}
              </label>

              <!-- COD Option -->
              <label onclick="selectPaymentMethod('COD')" class="block p-4 rounded-2xl border-2 cursor-pointer transition ${pm === 'COD' ? 'border-brand-600 bg-brand-50/50 dark:bg-brand-950/40' : 'border-slate-200 dark:border-slate-800'}">
                <div class="flex items-center gap-3">
                  <input type="radio" name="paymentMethod" value="COD" ${pm === 'COD' ? 'checked' : ''} class="accent-brand-600 w-4 h-4" />
                  <div>
                    <p class="font-bold text-sm">Cash on Delivery (COD)</p>
                    <p class="text-xs text-slate-500 dark:text-slate-400">Pay via cash or UPI QR upon delivery</p>
                  </div>
                </div>
              </label>
            </div>

            <!-- Compact Bill Breakdown -->
            <div class="p-4 rounded-2xl bg-slate-50 dark:bg-slate-800/70 space-y-1.5 text-xs">
              <div class="flex justify-between">
                <span class="text-slate-500">Items (${totals.totalItems})</span>
                <span>${formatINR(totals.sellingSubtotal)}</span>
              </div>
              ${totals.couponDiscount > 0 ? `
                <div class="flex justify-between text-emerald-600 dark:text-emerald-400">
                  <span>Coupon (${state.appliedCoupon})</span>
                  <span>-${formatINR(totals.couponDiscount)}</span>
                </div>
              ` : ''}
              <div class="flex justify-between">
                <span class="text-slate-500">Delivery</span>
                <span>${totals.deliveryCharge === 0 ? 'FREE' : formatINR(totals.deliveryCharge)}</span>
              </div>
              <div class="flex justify-between text-slate-500">
                <span>Included GST (18%)</span>
                <span>${formatINR(totals.includedGst)}</span>
              </div>
              <div class="flex justify-between text-sm font-extrabold pt-2 border-t border-slate-200 dark:border-slate-700">
                <span>Total Amount</span>
                <span>${formatINR(totals.finalPayable)}</span>
              </div>
            </div>

            <div id="paymentError" class="hidden text-xs font-semibold text-rose-500"></div>

            <button type="submit" class="w-full py-3.5 rounded-xl bg-emerald-600 hover:bg-emerald-700 text-white font-bold text-sm flex items-center justify-center gap-2 shadow-lg shadow-emerald-600/25 transition">
              <i data-lucide="shield-check" class="w-4 h-4"></i>
              <span>${pm === 'COD' ? `Place Order (${formatINR(totals.finalPayable)})` : `Pay ${formatINR(totals.finalPayable)} & Place Order`}</span>
            </button>
          </form>
        `;
      } else if (state.checkoutStep === 3 && state.lastOrder) {
        const order = state.lastOrder;
        body.innerHTML = `
          <div class="text-center space-y-5 py-2">
            <div class="w-16 h-16 mx-auto rounded-full bg-emerald-100 dark:bg-emerald-900/50 text-emerald-600 dark:text-emerald-400 flex items-center justify-center">
              <i data-lucide="check-circle-2" class="w-10 h-10"></i>
            </div>
            <div>
              <span class="px-3 py-1 rounded-full bg-emerald-100 dark:bg-emerald-900/50 text-emerald-700 dark:text-emerald-300 text-xs font-bold">Order Confirmed</span>
              <h3 class="text-2xl font-extrabold mt-2">Thank you, ${order.address.fullName.split(' ')[0]}!</h3>
              <p class="text-sm text-slate-500 dark:text-slate-400 mt-1">
                Order ID <strong class="text-slate-900 dark:text-white">${order.id}</strong> • Est. Delivery by <strong>${order.deliveryDate}</strong>
              </p>
            </div>

            <div class="text-left p-4 rounded-2xl bg-slate-50 dark:bg-slate-800/70 border border-slate-200 dark:border-slate-700 space-y-3 text-xs sm:text-sm">
              <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 pb-3 border-b border-slate-200 dark:border-slate-700">
                <div>
                  <p class="text-[11px] uppercase font-bold text-slate-400">Delivering To</p>
                  <p class="font-semibold mt-0.5">${order.address.fullName}</p>
                  <p class="text-xs text-slate-500 dark:text-slate-400">${order.address.street}, ${order.address.city}, ${order.address.state} - ${order.address.pincode}</p>
                </div>
                <div>
                  <p class="text-[11px] uppercase font-bold text-slate-400">Payment Mode</p>
                  <p class="font-semibold mt-0.5">${order.paymentMethod}</p>
                  <p class="text-xs text-emerald-600 dark:text-emerald-400">18% GST (${formatINR(order.totals.includedGst)}) included</p>
                </div>
              </div>

              <div class="space-y-1.5">
                ${order.items.map(it => `
                  <div class="flex justify-between text-xs">
                    <span class="truncate pr-3">${it.name} (${it.variant}) × ${it.qty}</span>
                    <span class="font-semibold shrink-0">${formatINR(it.price * it.qty)}</span>
                  </div>
                `).join('')}
              </div>

              <div class="flex justify-between font-extrabold text-base pt-2 border-t border-slate-200 dark:border-slate-700">
                <span>Total Paid</span>
                <span>${formatINR(order.totals.finalPayable)}</span>
              </div>
            </div>

            <div class="flex flex-col sm:flex-row gap-3 pt-2">
              <button onclick="closeCheckoutModal();openOrdersModal();" class="flex-1 py-3 rounded-xl border border-slate-200 dark:border-slate-700 hover:bg-slate-100 dark:hover:bg-slate-800 font-bold text-sm transition">
                View Order History
              </button>
              <button onclick="closeCheckoutModal()" class="flex-1 py-3 rounded-xl bg-brand-600 hover:bg-brand-700 text-white font-bold text-sm transition">
                Continue Shopping
              </button>
            </div>
          </div>
        `;
      }

      lucide.createIcons();
    }

    function selectPaymentMethod(method) {
      if (state.checkoutPayment === method) return;
      state.checkoutPayment = method;
      renderCheckoutStep();
    }

    function handleAddressSubmit(e) {
      e.preventDefault();
      const form = new FormData(e.target);
      const errEl = document.getElementById('addressError');

      const phone = form.get('phone').trim();
      const pincode = form.get('pincode').trim();

      if (!/^[6-9][0-9]{9}$/.test(phone)) {
        errEl.textContent = 'Please enter a valid 10-digit Indian mobile number.';
        errEl.classList.remove('hidden');
        return;
      }
      if (!/^[1-9][0-9]{5}$/.test(pincode)) {
        errEl.textContent = 'Please enter a valid 6-digit Indian pincode.';
        errEl.classList.remove('hidden');
        return;
      }

      state.checkoutAddress = {
        fullName: form.get('fullName').trim(),
        phone,
        pincode,
        city: form.get('city').trim(),
        state: form.get('state'),
        street: form.get('street').trim()
      };

      state.checkoutStep = 2;
      renderCheckoutStep();
    }

    function handlePaymentSubmit(e) {
      e.preventDefault();
      const errEl = document.getElementById('paymentError');
      let paymentDetail = state.checkoutPayment;

      if (state.checkoutPayment === 'UPI') {
        const upiId = (document.getElementById('upiIdInput')?.value || '').trim();
        if (!/^[\w.-]+@[\w.-]+$/.test(upiId)) {
          errEl.textContent = 'Please enter a valid UPI ID (e.g. name@okaxis or mobile@ybl).';
          errEl.classList.remove('hidden');
          return;
        }
        paymentDetail = `UPI (${upiId})`;
      } else if (state.checkoutPayment === 'CARD') {
        const num = (document.getElementById('cardNumberInput')?.value || '').replace(/\s+/g, '');
        const exp = (document.getElementById('cardExpiryInput')?.value || '').trim();
        const cvv = (document.getElementById('cardCvvInput')?.value || '').trim();
        if (num.length < 12 || !/^\d{2}\/\d{2}$/.test(exp) || cvv.length < 3) {
          errEl.textContent = 'Please enter valid card number, expiry (MM/YY), and CVV.';
          errEl.classList.remove('hidden');
          return;
        }
        paymentDetail = `Card ending •••• ${num.slice(-4)}`;
      } else {
        paymentDetail = 'Cash on Delivery (COD)';
      }

      const totals = calculateCartTotals();
      const orderItems = state.cart.map(item => {
        const p = PRODUCTS.find(prod => prod.id === item.productId);
        return {
          productId: item.productId,
          name: p ? p.name : 'Product',
          image: p ? p.image : '',
          variant: item.variant,
          qty: item.qty,
          price: p ? p.price : 0
        };
      });

      const orderId = `#LB-2026-${Math.floor(1000 + Math.random() * 9000)}`;
      const newOrder = {
        id: orderId,
        date: new Date().toLocaleString('en-IN', { day: 'numeric', month: 'short', year: 'numeric', hour: '2-digit', minute: '2-digit' }),
        deliveryDate: getEstimatedDeliveryDate(3),
        status: 'Confirmed',
        paymentMethod: paymentDetail,
        address: { ...state.checkoutAddress },
        items: orderItems,
        totals
      };

      state.orders.unshift(newOrder);
      state.lastOrder = newOrder;
      state.cart = [];
      state.appliedCoupon = null;

      persistOrders();
      persistCart();
      updateHeaderBadges();
      renderProducts();
      renderCartDrawer();

      state.checkoutStep = 3;
      renderCheckoutStep();
      showToast(`Order ${orderId} placed successfully!`);
    }

    /*************************************************************************
     * 11. ORDER HISTORY MODAL
     *************************************************************************/
    function openOrdersModal() {
      renderOrdersModal();
      document.getElementById('ordersModal').classList.remove('hidden');
      document.body.classList.add('overflow-hidden');
    }

    function closeOrdersModal() {
      document.getElementById('ordersModal').classList.add('hidden');
      document.body.classList.remove('overflow-hidden');
    }

    function renderOrdersModal() {
      const container = document.getElementById('ordersListContainer');
      if (state.orders.length === 0) {
        container.innerHTML = `
          <div class="text-center py-12">
            <div class="w-16 h-16 mx-auto rounded-2xl bg-slate-100 dark:bg-slate-800 flex items-center justify-center text-slate-400 mb-4">
              <i data-lucide="package-open" class="w-8 h-8"></i>
            </div>
            <h3 class="font-bold text-base">No orders placed yet</h3>
            <p class="text-xs text-slate-500 dark:text-slate-400 mt-1">Once you complete checkout, all your orders and GST receipts will appear here.</p>
          </div>
        `;
        lucide.createIcons();
        return;
      }

      container.innerHTML = state.orders.map(order => `
        <div class="p-4 sm:p-5 rounded-2xl bg-slate-50 dark:bg-slate-800/60 border border-slate-200 dark:border-slate-700 space-y-3">
          <div class="flex flex-wrap items-center justify-between gap-2 pb-3 border-b border-slate-200 dark:border-slate-700">
            <div>
              <div class="flex items-center gap-2">
                <span class="font-extrabold text-sm sm:text-base">${order.id}</span>
                <span class="px-2.5 py-0.5 rounded-full bg-emerald-100 dark:bg-emerald-900/60 text-emerald-700 dark:text-emerald-300 text-[11px] font-bold">${order.status}</span>
              </div>
              <p class="text-xs text-slate-500 dark:text-slate-400 mt-0.5">Placed on ${order.date} • Est. Delivery ${order.deliveryDate}</p>
            </div>
            <div class="text-right">
              <p class="text-xs text-slate-500 dark:text-slate-400">${order.paymentMethod}</p>
              <p class="font-extrabold text-base">${formatINR(order.totals.finalPayable)}</p>
            </div>
          </div>

          <div class="space-y-2">
            ${order.items.map(it => `
              <div class="flex items-center justify-between gap-3 text-xs sm:text-sm">
                <div class="flex items-center gap-2.5 min-w-0">
                  <img src="${it.image}" alt="${it.name}" onerror="this.onerror=null;this.src='https://placehold.co/80x80/e2e8f0/475569?text=Item';" class="w-10 h-10 rounded-lg object-cover shrink-0" />
                  <div class="min-w-0">
                    <p class="font-semibold truncate">${it.name}</p>
                    <p class="text-[11px] text-slate-500 dark:text-slate-400">${it.variant} • Qty: ${it.qty}</p>
                  </div>
                </div>
                <span class="font-bold shrink-0">${formatINR(it.price * it.qty)}</span>
              </div>
            `).join('')}
          </div>

          <div class="pt-2 border-t border-slate-200 dark:border-slate-700 flex flex-wrap items-center justify-between gap-2 text-[11px] text-slate-500 dark:text-slate-400">
            <span>Ship to: ${order.address.fullName}, ${order.address.city} (${order.address.pincode})</span>
            <span>Incl. 18% GST: ${formatINR(order.totals.includedGst)}</span>
          </div>
        </div>
      `).join('');

      lucide.createIcons();
    }

    /*************************************************************************
     * 12. EVENT LISTENERS & INITIALIZATION
     *************************************************************************/
    function bindEvents() {
      // Live Search Sync (Desktop & Mobile)
      const handleSearch = (val) => {
        state.searchQuery = val;
        document.getElementById('desktopSearchInput').value = val;
        document.getElementById('mobileSearchInput').value = val;
        document.getElementById('desktopClearSearch').classList.toggle('hidden', !val);
        document.getElementById('mobileClearSearch').classList.toggle('hidden', !val);
        renderProducts();
      };

      document.getElementById('desktopSearchInput').addEventListener('input', e => handleSearch(e.target.value));
      document.getElementById('mobileSearchInput').addEventListener('input', e => handleSearch(e.target.value));

      // Price Slider
      document.getElementById('priceRangeSlider').addEventListener('input', e => {
        state.maxPrice = Number(e.target.value);
        document.getElementById('priceRangeLabel').textContent = formatINR(state.maxPrice);
        renderProducts();
      });

      // Rating Filter
      document.getElementById('ratingFilter').addEventListener('change', e => {
        state.minRating = Number(e.target.value);
        renderProducts();
      });

      // Sort Dropdown
      document.getElementById('sortSelect').addEventListener('change', e => {
        state.sortBy = e.target.value;
        renderProducts();
      });

      // Close drawers/modals when clicking backdrop
      document.getElementById('cartDrawerOverlay').addEventListener('click', e => {
        if (e.target.id === 'cartDrawerOverlay') closeCartDrawer();
      });
      document.getElementById('wishlistDrawerOverlay').addEventListener('click', e => {
        if (e.target.id === 'wishlistDrawerOverlay') closeWishlistDrawer();
      });
      document.getElementById('quickViewModal').addEventListener('click', e => {
        if (e.target.id === 'quickViewModal') closeQuickView();
      });
      document.getElementById('ordersModal').addEventListener('click', e => {
        if (e.target.id === 'ordersModal') closeOrdersModal();
      });

      // Escape key closes open overlays
      document.addEventListener('keydown', e => {
        if (e.key === 'Escape') {
          closeQuickView();
          closeCartDrawer();
          closeWishlistDrawer();
          closeOrdersModal();
        }
      });
    }

    // Boot Application
    window.addEventListener('DOMContentLoaded', () => {
      loadPersistedState();
      bindEvents();
      renderCategoryTabs();
      renderProducts();
      updateHeaderBadges();
      startFlashSaleTimer();
      lucide.createIcons();
    });
  </script>
</body>
</html>
