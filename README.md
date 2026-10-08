<!DOCTYPE html>
<html lang="en" class="h-full bg-slate-950 text-slate-100">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Funeral Tribute Display - Custom Order & Preview System</title>
 
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
 
  <!-- Google Fonts: Cinzel & Inter -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700;800;900&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
 
  <!-- Lucide Icons CDN -->
  <script src="https://unpkg.com/lucide@latest"></script>

  <style>
    body {
      font-family: 'Inter', sans-serif;
    }
    .font-serif-tribute {
      font-family: 'Cinzel', Georgia, serif;
    }

    ::-webkit-scrollbar {
      width: 8px;
      height: 8px;
    }
    ::-webkit-scrollbar-track {
      background: #090d16;
    }
    ::-webkit-scrollbar-thumb {
      background: #232d3f;
      border-radius: 4px;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: #36445c;
    }

    .gold-glow {
      text-shadow: 0 0 16px rgba(245, 158, 11, 0.4);
    }
   
    .vinyl-texture {
      background-image: radial-gradient(rgba(255, 255, 255, 0.08) 1.2px, transparent 1.2px);
      background-size: 14px 14px;
    }
   
    .acrylic-glass {
      background: linear-gradient(135deg, rgba(255, 255, 255, 0.22) 0%, rgba(255, 255, 255, 0.03) 45%, rgba(255, 255, 255, 0.16) 100%);
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.65), inset 0 0 20px rgba(255, 255, 255, 0.25);
      backdrop-filter: blur(8px);
    }

    .sintra-board-shadow {
      box-shadow: 10px 16px 30px rgba(0, 0, 0, 0.7), inset 0 1px 2px rgba(255, 255, 255, 0.15);
    }

    @media print {
      body {
        background: #ffffff !important;
        color: #000000 !important;
      }
      .no-print {
        display: none !important;
      }
      .print-only {
        display: block !important;
      }
      .print-card {
        border: 1px solid #d1d5db !important;
        background: #ffffff !important;
        color: #111827 !important;
        box-shadow: none !important;
      }
      .print-card * {
        color: #111827 !important;
        border-color: #e5e7eb !important;
        background-color: transparent !important;
      }
    }
  </style>
</head>
<body class="min-h-full flex flex-col bg-slate-950 text-slate-100 antialiased selection:bg-amber-500 selection:text-slate-950">

  <!-- Header Banner -->
  <header class="border-b border-slate-800 bg-slate-900/90 backdrop-blur-md sticky top-0 z-50 no-print">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-3.5 flex flex-col sm:flex-row items-center justify-between gap-3">
      <div class="flex items-center gap-3">
        <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-amber-500 to-amber-700 flex items-center justify-center text-slate-950 font-bold shadow-lg shadow-amber-500/20 shrink-0">
          <i data-lucide="flower-2" class="w-6 h-6"></i>
        </div>
        <div>
          <h1 class="text-xl font-bold font-serif-tribute tracking-wide text-amber-100">Order form</h1>
          <p class="text-xs text-slate-400">Funeral Tribute Display Order · SN TechnoPrint</p>
        </div>
      </div>
     
      <div class="flex items-center gap-2 text-xs font-medium text-amber-300 bg-amber-950/50 border border-amber-800/50 px-3.5 py-1.5 rounded-full shadow-inner">
        <i data-lucide="mail" class="w-3.5 h-3.5 text-amber-400 shrink-0"></i>
        <span>Receiving Email: <strong class="text-slate-100 font-mono select-all ml-1">sntechnoprint01@gmail.com</strong></span>
      </div>
    </div>

    <!-- Stepper Navigation -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pb-3">
      <div class="grid grid-cols-2 md:grid-cols-4 gap-2 bg-slate-950 p-1.5 rounded-2xl border border-slate-800">
        <button id="step-btn-1" onclick="goToStep(1)" class="step-tab flex items-center justify-center gap-2 py-2.5 px-3 rounded-xl text-xs sm:text-sm font-semibold transition-all duration-200 bg-amber-500 text-slate-950 shadow-md">
          <span class="w-5 h-5 rounded-full bg-slate-950/25 text-slate-950 flex items-center justify-center text-xs font-bold">1</span>
          <span class="hidden sm:inline">Loved One Details</span>
          <span class="sm:hidden">Details</span>
        </button>

        <button id="step-btn-2" onclick="goToStep(2)" class="step-tab flex items-center justify-center gap-2 py-2.5 px-3 rounded-xl text-xs sm:text-sm font-semibold transition-all duration-200 text-slate-400 hover:text-slate-200 hover:bg-slate-900/40">
          <span class="w-5 h-5 rounded-full bg-slate-800 text-slate-400 flex items-center justify-center text-xs font-bold">2</span>
          <span class="hidden sm:inline">Offer Selection</span>
          <span class="sm:hidden">Offers</span>
        </button>

        <button id="step-btn-3" onclick="goToStep(3)" class="step-tab flex items-center justify-center gap-2 py-2.5 px-3 rounded-xl text-xs sm:text-sm font-semibold transition-all duration-200 text-slate-400 hover:text-slate-200 hover:bg-slate-900/40">
          <span class="w-5 h-5 rounded-full bg-slate-800 text-slate-400 flex items-center justify-center text-xs font-bold">3</span>
          <span class="hidden sm:inline">Config & Proof</span>
          <span class="sm:hidden">Proof</span>
        </button>

        <button id="step-btn-4" onclick="goToStep(4)" class="step-tab flex items-center justify-center gap-2 py-2.5 px-3 rounded-xl text-xs sm:text-sm font-semibold transition-all duration-200 text-slate-400 hover:text-slate-200 hover:bg-slate-900/40">
          <span class="w-5 h-5 rounded-full bg-slate-800 text-slate-400 flex items-center justify-center text-xs font-bold">4</span>
          <span class="hidden sm:inline">Order Summary</span>
          <span class="sm:hidden">Summary</span>
        </button>
      </div>
    </div>
  </header>

  <main class="flex-1 max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-8">
   
    <!-- ==================== STEP 1 ==================== -->
    <section id="step-section-1" class="step-content space-y-6">
      <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 md:p-8 space-y-6 shadow-xl">
        <div class="border-b border-slate-800 pb-4">
          <h2 class="text-2xl font-bold font-serif-tribute text-amber-200 flex items-center gap-2">
            <i data-lucide="user-check" class="w-6 h-6 text-amber-400"></i>
            Step 1: Contact & Memorial Profile
          </h2>
          <p class="text-slate-400 text-sm mt-1">Provide customer contact details and personalized information for the memorial tribute print displays.</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
          <!-- Customer Contact Details -->
          <div class="space-y-4">
            <h3 class="text-xs font-semibold uppercase tracking-wider text-amber-400 border-l-2 border-amber-500 pl-2">Customer Contact Info</h3>
           
            <div>
              <label class="block text-xs font-medium text-slate-300 mb-1">Your Full Name <span class="text-amber-400">*</span></label>
              <input type="text" id="cust-name" oninput="updateState()" placeholder="e.g. Maria Santos" class="w-full bg-slate-950 border border-slate-700 rounded-xl px-4 py-2.5 text-slate-100 placeholder-slate-500 focus:outline-none focus:border-amber-500 text-sm">
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <div>
                <label class="block text-xs font-medium text-slate-300 mb-1">Contact Phone <span class="text-amber-400">*</span></label>
                <input type="tel" id="cust-phone" oninput="updateState()" placeholder="0917-XXX-XXXX" class="w-full bg-slate-950 border border-slate-700 rounded-xl px-4 py-2.5 text-slate-100 placeholder-slate-500 focus:outline-none focus:border-amber-500 text-sm">
              </div>
              <div>
                <label class="block text-xs font-medium text-slate-300 mb-1">Email Address <span class="text-amber-400">*</span></label>
                <input type="email" id="cust-email" oninput="updateState()" placeholder="yourname@gmail.com" class="w-full bg-slate-950 border border-slate-700 rounded-xl px-4 py-2.5 text-slate-100 placeholder-slate-500 focus:outline-none focus:border-amber-500 text-sm">
              </div>
            </div>

            <div class="pt-2 text-xs text-slate-400 bg-slate-950/40 p-3 rounded-xl border border-slate-800">
              <span class="text-amber-400 font-semibold block mb-0.5">Order Dispatch Confirmation</span>
              Orders and mockups will be addressed to <span class="text-slate-200 font-mono">sntechnoprint01@gmail.com</span> with your contact info.
            </div>
          </div>

          <!-- Deceased Information -->
          <div class="space-y-4">
            <h3 class="text-xs font-semibold uppercase tracking-wider text-amber-400 border-l-2 border-amber-500 pl-2">Loved One Information</h3>
           
            <div>
              <label class="block text-xs font-medium text-slate-300 mb-1">Full Name of Deceased <span class="text-amber-400">*</span></label>
              <input type="text" id="loved-name" oninput="updateState()" placeholder="e.g. Juan De La Cruz" value="Juan De La Cruz" class="w-full bg-slate-950 border border-slate-700 rounded-xl px-4 py-2.5 text-slate-100 placeholder-slate-500 focus:outline-none focus:border-amber-500 text-sm">
            </div>

            <div class="grid grid-cols-2 gap-4">
              <div>
                <label class="block text-xs font-medium text-slate-300 mb-1">Date of Birth <span class="text-amber-400">*</span></label>
                <input type="date" id="loved-dob" oninput="updateState()" value="1955-08-15" class="w-full bg-slate-950 border border-slate-700 rounded-xl px-4 py-2.5 text-slate-100 focus:outline-none focus:border-amber-500 text-sm">
              </div>
              <div>
                <label class="block text-xs font-medium text-slate-300 mb-1">Date of Passing <span class="text-amber-400">*</span></label>
                <input type="date" id="loved-dop" oninput="updateState()" value="2026-03-20" class="w-full bg-slate-950 border border-slate-700 rounded-xl px-4 py-2.5 text-slate-100 focus:outline-none focus:border-amber-500 text-sm">
              </div>
            </div>

            <div>
              <div class="flex items-center justify-between mb-1">
                <label class="block text-xs font-medium text-slate-300">Memorial Inscription / Quote</label>
                <span class="text-[10px] text-amber-400/90 font-medium">Shown on mockups</span>
              </div>
              <textarea id="loved-quote" oninput="updateState()" rows="2" placeholder="e.g. In Loving Memory & Forever in Our Hearts" class="w-full bg-slate-950 border border-slate-700 rounded-xl px-4 py-2 text-slate-100 placeholder-slate-500 focus:outline-none focus:border-amber-500 text-sm">In Loving Memory & Forever in Our Hearts</textarea>
            </div>

            <div class="space-y-1.5">
              <span class="text-[11px] text-slate-400 flex items-center gap-1">
                <i data-lucide="sparkles" class="w-3 h-3 text-amber-400"></i>
                Quick suggestions:
              </span>
              <div class="flex flex-wrap gap-1.5">
                <button type="button" onclick="setQuote('In Loving Memory & Forever in Our Hearts')" class="text-[10px] bg-slate-950 hover:bg-slate-800 text-slate-300 hover:text-amber-300 px-2.5 py-1 rounded-lg border border-slate-800 transition-colors">"In Loving Memory & Forever in Our Hearts"</button>
                <button type="button" onclick="setQuote('Forever Missed, Always Cherished & Remembered')" class="text-[10px] bg-slate-950 hover:bg-slate-800 text-slate-300 hover:text-amber-300 px-2.5 py-1 rounded-lg border border-slate-800 transition-colors">"Forever Missed, Always Cherished"</button>
                <button type="button" onclick="setQuote('May Your Sacred Soul Rest in Eternal Peace')" class="text-[10px] bg-slate-950 hover:bg-slate-800 text-slate-300 hover:text-amber-300 px-2.5 py-1 rounded-lg border border-slate-800 transition-colors">"Rest in Eternal Peace"</button>
              </div>
            </div>
          </div>
        </div>

        <div class="flex justify-end pt-4 border-t border-slate-800">
          <button onclick="goToStep(2)" class="flex items-center gap-2 bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-400 hover:to-amber-500 text-slate-950 font-bold px-6 py-3 rounded-xl shadow-lg transition-all">
            <span>Continue to Offer Selection</span>
            <i data-lucide="arrow-right" class="w-4 h-4"></i>
          </button>
        </div>
      </div>
    </section>

    <!-- ==================== STEP 2 ==================== -->
    <section id="step-section-2" class="step-content space-y-6 hidden">
      <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 md:p-8 space-y-6 shadow-xl">
        <div class="border-b border-slate-800 pb-4 flex flex-col sm:flex-row sm:items-center justify-between gap-4">
          <div>
            <h2 class="text-2xl font-bold font-serif-tribute text-amber-200 flex items-center gap-2">
              <i data-lucide="package" class="w-6 h-6 text-amber-400"></i>
              Step 2: Choose Offers & Quantities
            </h2>
            <p class="text-slate-400 text-sm mt-1">Select from standard memorial packages or order items individually.</p>
          </div>
         
          <div class="inline-flex p-1 bg-slate-950 rounded-xl border border-slate-800">
            <button id="offer-tab-bundles" onclick="switchOfferTab('bundles')" class="px-4 py-2 rounded-lg text-xs font-semibold bg-amber-500 text-slate-950 font-bold shadow">Package Bundles</button>
            <button id="offer-tab-single" onclick="switchOfferTab('single')" class="px-4 py-2 rounded-lg text-xs font-semibold text-slate-400 hover:text-slate-200">Single Items</button>
          </div>
        </div>

        <!-- Package Bundles Panel -->
        <div id="offer-panel-bundles" class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <!-- Bundle 1 -->
          <div class="bg-slate-950 border border-slate-800 hover:border-amber-500/50 rounded-2xl p-5 space-y-4 transition-all relative flex flex-col justify-between">
            <div>
              <div class="flex items-center justify-between border-b border-slate-800 pb-3 mb-3">
                <span class="text-xs font-semibold uppercase tracking-wider text-amber-400 bg-amber-950/60 px-2.5 py-1 rounded-md border border-amber-800/40">Bundle 1 · Starter Set</span>
                <span class="text-xs text-slate-400 font-medium">Intimate family wake</span>
              </div>
              <h3 class="text-lg font-bold text-slate-100 font-serif-tribute">Essential Memorial Package</h3>
              <p class="text-xs text-slate-400 mt-1">Perfect for intimate chapel vigils and immediate family tributes.</p>
              <ul class="mt-4 space-y-2 text-xs text-slate-300">
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 1x Tarpaulin Banner (2.5 x 6 ft)</li>
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 1x Sintra Board Display (22 x 28 inch)</li>
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 5x Tribute T-Shirts (Custom front print)</li>
              </ul>
            </div>
            <div class="pt-4 border-t border-slate-900 flex items-center justify-between">
              <div>
                <span class="text-xs text-slate-400 block">Package Quantity</span>
                <span class="text-[10px] text-amber-400 font-medium">Includes 5 shirts/pkg</span>
              </div>
              <div class="flex items-center gap-2">
                <button onclick="changeBundleQty(1, -1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">-</button>
                <span id="qty-bundle-1" class="w-8 text-center text-sm font-bold text-amber-400">0</span>
                <button onclick="changeBundleQty(1, 1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">+</button>
              </div>
            </div>
          </div>

          <!-- Bundle 2 -->
          <div class="bg-slate-950 border border-amber-500/80 rounded-2xl p-5 space-y-4 transition-all relative flex flex-col justify-between shadow-lg shadow-amber-500/10">
            <div>
              <div class="flex items-center justify-between border-b border-slate-800 pb-3 mb-3">
                <span class="text-xs font-semibold uppercase tracking-wider text-amber-400 bg-amber-950/60 px-2.5 py-1 rounded-md border border-amber-800/40">Bundle 2 · Most Popular</span>
                <span class="text-xs text-slate-400 font-medium">Standard chapel memorial</span>
              </div>
              <h3 class="text-lg font-bold text-slate-100 font-serif-tribute">Standard Memorial Package</h3>
              <p class="text-xs text-slate-400 mt-1">Our most requested bundle for standard church and funeral home services.</p>
              <ul class="mt-4 space-y-2 text-xs text-slate-300">
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 1x Tarpaulin Banner (2.5 x 6 ft)</li>
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 1x Acrylic Frame Display (A4 Size: 210 x 297 mm)</li>
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 1x Sintra Board Photo Board (22 x 28 inch)</li>
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 5x Tribute T-Shirts (Custom front print)</li>
              </ul>
            </div>
            <div class="pt-4 border-t border-slate-900 flex items-center justify-between">
              <div>
                <span class="text-xs text-slate-400 block">Package Quantity</span>
                <span class="text-[10px] text-amber-400 font-medium">Includes 5 shirts/pkg</span>
              </div>
              <div class="flex items-center gap-2">
                <button onclick="changeBundleQty(2, -1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">-</button>
                <span id="qty-bundle-2" class="w-8 text-center text-sm font-bold text-amber-400">1</span>
                <button onclick="changeBundleQty(2, 1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">+</button>
              </div>
            </div>
          </div>

          <!-- Bundle 3 -->
          <div class="bg-slate-950 border border-slate-800 hover:border-amber-500/50 rounded-2xl p-5 space-y-4 transition-all relative flex flex-col justify-between">
            <div>
              <div class="flex items-center justify-between border-b border-slate-800 pb-3 mb-3">
                <span class="text-xs font-semibold uppercase tracking-wider text-amber-400 bg-amber-950/60 px-2.5 py-1 rounded-md border border-amber-800/40">Bundle 3 · Family Choice</span>
                <span class="text-xs text-slate-400 font-medium">Large memorial service</span>
              </div>
              <h3 class="text-lg font-bold text-slate-100 font-serif-tribute">Premium Memorial Package</h3>
              <p class="text-xs text-slate-400 mt-1">Expanded set featuring dual display tarpaulins and acrylic tribute plaques.</p>
              <ul class="mt-4 space-y-2 text-xs text-slate-300">
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 1x Tarpaulin Banners (2.5 x 6 ft)</li>
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 1x Acrylic Frame Displays (A4 Size: 210 x 297 mm)</li>
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 1x Sintra Boards (High-resolution print) (22 x 28 inch)</li>
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 5x Tribute T-Shirts (Custom front print)</li>
              </ul>
            </div>
            <div class="pt-4 border-t border-slate-900 flex items-center justify-between">
              <div>
                <span class="text-xs text-slate-400 block">Package Quantity</span>
                <span class="text-[10px] text-amber-400 font-medium">Includes 5 shirts/pkg</span>
              </div>
              <div class="flex items-center gap-2">
                <button onclick="changeBundleQty(3, -1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">-</button>
                <span id="qty-bundle-3" class="w-8 text-center text-sm font-bold text-amber-400">0</span>
                <button onclick="changeBundleQty(3, 1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">+</button>
              </div>
            </div>
          </div>

          <!-- Bundle 4 -->
          <div class="bg-slate-950 border border-slate-800 hover:border-amber-500/50 rounded-2xl p-5 space-y-4 transition-all relative flex flex-col justify-between">
            <div>
              <div class="flex items-center justify-between border-b border-slate-800 pb-3 mb-3">
                <span class="text-xs font-semibold uppercase tracking-wider text-amber-400 bg-amber-950/60 px-2.5 py-1 rounded-md border border-amber-800/40">Bundle 4 · Grand Tribute</span>
                <span class="text-xs text-slate-400 font-medium">Comprehensive family gathering</span>
              </div>
              <h3 class="text-lg font-bold text-slate-100 font-serif-tribute">Full Grand Chapel Package</h3>
              <p class="text-xs text-slate-400 mt-1">Comprehensive tribute setup for grand halls, dual entrances, and extended relatives.</p>
              <ul class="mt-4 space-y-2 text-xs text-slate-300">
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 1x Entrance Tarpaulins (2.5 x 6 ft)</li>
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 1x Acrylic Frames (A4 Size: 210 x 297 mm)</li>
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 1x Sintra Boards (Memorial photo series) (22 x 28 inch)</li>
                <li class="flex items-center gap-2"><i data-lucide="check" class="w-4 h-4 text-amber-400 shrink-0"></i> 5x Custom Tribute T-Shirts (Custom front print)</li>
              </ul>
            </div>
            <div class="pt-4 border-t border-slate-900 flex items-center justify-between">
              <div>
                <span class="text-xs text-slate-400 block">Package Quantity</span>
                <span class="text-[10px] text-amber-400 font-medium">Includes 5 shirts/pkg</span>
              </div>
              <div class="flex items-center gap-2">
                <button onclick="changeBundleQty(4, -1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">-</button>
                <span id="qty-bundle-4" class="w-8 text-center text-sm font-bold text-amber-400">0</span>
                <button onclick="changeBundleQty(4, 1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">+</button>
              </div>
            </div>
          </div>
        </div>

        <!-- Single Items Panel -->
        <div id="offer-panel-single" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 hidden">
          <!-- Tarpaulin -->
          <div class="bg-slate-950 border border-slate-800 rounded-2xl p-5 space-y-4 flex flex-col justify-between">
            <div>
              <div class="w-10 h-10 rounded-xl bg-amber-500/10 border border-amber-500/30 text-amber-400 flex items-center justify-center mb-3">
                <i data-lucide="image" class="w-5 h-5"></i>
              </div>
              <h3 class="text-base font-bold text-slate-100 font-serif-tribute">Tarpaulin Banner</h3>
              <p class="text-xs text-amber-400 font-semibold mt-0.5">2.5 × 6 FT (76 × 183 cm)</p>
              <p class="text-xs text-slate-400 mt-2">Weather-resistant standing banner with 6 reinforced brass eyelets / grommets.</p>
            </div>
            <div class="pt-4 border-t border-slate-900 flex items-center justify-between">
              <span class="text-xs text-slate-400">Quantity</span>
              <div class="flex items-center gap-2">
                <button onclick="changeSingleQty('tarpaulin', -1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">-</button>
                <span id="qty-single-tarpaulin" class="w-8 text-center text-sm font-bold text-amber-400">0</span>
                <button onclick="changeSingleQty('tarpaulin', 1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">+</button>
              </div>
            </div>
          </div>

          <!-- Sintra Board -->
          <div class="bg-slate-950 border border-slate-800 rounded-2xl p-5 space-y-4 flex flex-col justify-between">
            <div>
              <div class="w-10 h-10 rounded-xl bg-amber-500/10 border border-amber-500/30 text-amber-400 flex items-center justify-center mb-3">
                <i data-lucide="layers" class="w-5 h-5"></i>
              </div>
              <h3 class="text-base font-bold text-slate-100 font-serif-tribute">Sintra Board Display</h3>
              <p class="text-xs text-amber-400 font-semibold mt-0.5">22 × 28 INCH (or A4)</p>
              <p class="text-xs text-slate-400 mt-2">Smooth waterproof matte PVC board, lightweight tabletop easel or wall display.</p>
            </div>
            <div class="pt-4 border-t border-slate-900 flex items-center justify-between">
              <span class="text-xs text-slate-400">Quantity</span>
              <div class="flex items-center gap-2">
                <button onclick="changeSingleQty('sintra', -1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">-</button>
                <span id="qty-single-sintra" class="w-8 text-center text-sm font-bold text-amber-400">0</span>
                <button onclick="changeSingleQty('sintra', 1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">+</button>
              </div>
            </div>
          </div>

          <!-- Acrylic Frame -->
          <div class="bg-slate-950 border border-slate-800 rounded-2xl p-5 space-y-4 flex flex-col justify-between">
            <div>
              <div class="w-10 h-10 rounded-xl bg-amber-500/10 border border-amber-500/30 text-amber-400 flex items-center justify-center mb-3">
                <i data-lucide="sparkles" class="w-5 h-5"></i>
              </div>
              <h3 class="text-base font-bold text-slate-100 font-serif-tribute">Acrylic Frame</h3>
              <p class="text-xs text-amber-400 font-semibold mt-0.5">A4 SIZE (210 x 297 mm)</p>
              <p class="text-xs text-slate-400 mt-2">Crystal clear glass plate with 4 stainless steel standoff pins for wall or tabletop.</p>
            </div>
            <div class="pt-4 border-t border-slate-900 flex items-center justify-between">
              <span class="text-xs text-slate-400">Quantity</span>
              <div class="flex items-center gap-2">
                <button onclick="changeSingleQty('acrylic', -1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">-</button>
                <span id="qty-single-acrylic" class="w-8 text-center text-sm font-bold text-amber-400">0</span>
                <button onclick="changeSingleQty('acrylic', 1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">+</button>
              </div>
            </div>
          </div>

          <!-- Tribute T-Shirt -->
          <div class="bg-slate-950 border border-slate-800 rounded-2xl p-5 space-y-4 flex flex-col justify-between">
            <div>
              <div class="w-10 h-10 rounded-xl bg-amber-500/10 border border-amber-500/30 text-amber-400 flex items-center justify-center mb-3">
                <i data-lucide="shirt" class="w-5 h-5"></i>
              </div>
              <h3 class="text-base font-bold text-slate-100 font-serif-tribute">Tribute T-Shirt</h3>
              <p class="text-xs text-slate-400 mt-0.5">Premium Cotton Memorial Shirt</p>
              <p class="text-xs text-slate-400 mt-2">Custom memorial graphic chest print available in crisp White or solemn Black.</p>
            </div>
            <div class="pt-4 border-t border-slate-900 flex items-center justify-between">
              <span class="text-xs text-slate-400">Quantity</span>
              <div class="flex items-center gap-2">
                <button onclick="changeSingleQty('tshirt', -1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">-</button>
                <span id="qty-single-tshirt" class="w-8 text-center text-sm font-bold text-amber-400">0</span>
                <button onclick="changeSingleQty('tshirt', 1)" class="w-8 h-8 rounded-lg bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-200 font-bold">+</button>
              </div>
            </div>
          </div>
        </div>

        <div class="flex items-center justify-between pt-4 border-t border-slate-800">
          <button onclick="goToStep(1)" class="flex items-center gap-2 bg-slate-800 hover:bg-slate-700 text-slate-200 font-semibold px-5 py-2.5 rounded-xl text-sm transition-all">
            <i data-lucide="arrow-left" class="w-4 h-4"></i>
            <span>Back</span>
          </button>
          <button onclick="goToStep(3)" class="flex items-center gap-2 bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-400 hover:to-amber-500 text-slate-950 font-bold px-6 py-3 rounded-xl shadow-lg transition-all">
            <span>Proceed to Configuration & Mockup Proof</span>
            <i data-lucide="arrow-right" class="w-4 h-4"></i>
          </button>
        </div>
      </div>
    </section>

    <!-- ==================== STEP 3 ==================== -->
    <section id="step-section-3" class="step-content space-y-6 hidden">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
       
        <!-- Left: T-Shirt Configurator -->
        <div class="lg:col-span-5 space-y-6">
          <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 space-y-5 shadow-xl">
            <h3 class="text-base font-bold text-amber-300 font-serif-tribute flex items-center gap-2 border-b border-slate-800 pb-3">
              <i data-lucide="shirt" class="w-5 h-5 text-amber-400"></i>
              T-Shirt Configurator
            </h3>

            <div>
              <label class="block text-xs font-semibold uppercase tracking-wider text-slate-400 mb-2">Select Shirt Base Fabric Color</label>
              <div class="grid grid-cols-2 gap-3">
                <button type="button" onclick="setShirtColor('white')" id="color-btn-white" class="py-3 px-4 rounded-xl border-2 border-amber-500 bg-slate-100 text-slate-900 font-bold flex items-center justify-center gap-2 text-sm shadow-md transition-all">
                  <span class="w-4 h-4 rounded-full bg-white border border-slate-400 inline-block shadow-sm"></span>
                  <span>Pure White</span>
                </button>
                <button type="button" onclick="setShirtColor('black')" id="color-btn-black" class="py-3 px-4 rounded-xl border-2 border-slate-800 bg-slate-950 text-slate-100 font-bold flex items-center justify-center gap-2 text-sm hover:border-slate-700 transition-all">
                  <span class="w-4 h-4 rounded-full bg-slate-900 border border-slate-600 inline-block shadow-sm"></span>
                  <span>Solemn Black</span>
                </button>
              </div>
            </div>

            <!-- Size Breakdown Input Table -->
            <div class="space-y-3">
              <div class="flex items-center justify-between">
                <label class="block text-xs font-semibold uppercase tracking-wider text-slate-400">Shirt Sizes & Quantities</label>
                <div class="flex gap-2">
                  <button onclick="addOneToAllSizes()" class="text-xs bg-slate-800 hover:bg-slate-700 text-amber-400 px-2 py-1 rounded border border-slate-700">+1 All</button>
                  <button onclick="resetSizes()" class="text-xs bg-slate-800 hover:bg-slate-700 text-slate-400 px-2 py-1 rounded border border-slate-700">Reset</button>
                </div>
              </div>

              <div class="grid grid-cols-5 gap-2">
                <div class="bg-slate-950 p-2 rounded-xl border border-slate-800 text-center">
                  <span class="text-xs font-semibold text-slate-400 block mb-1">S</span>
                  <input type="number" id="size-S" min="0" value="1" oninput="updateState()" class="w-full bg-slate-900 border border-slate-700 rounded-lg text-center py-1 text-sm font-bold text-slate-100 focus:outline-none focus:border-amber-500">
                </div>
                <div class="bg-slate-950 p-2 rounded-xl border border-slate-800 text-center">
                  <span class="text-xs font-semibold text-slate-400 block mb-1">M</span>
                  <input type="number" id="size-M" min="0" value="1" oninput="updateState()" class="w-full bg-slate-900 border border-slate-700 rounded-lg text-center py-1 text-sm font-bold text-slate-100 focus:outline-none focus:border-amber-500">
                </div>
                <div class="bg-slate-950 p-2 rounded-xl border border-slate-800 text-center">
                  <span class="text-xs font-semibold text-slate-400 block mb-1">L</span>
                  <input type="number" id="size-L" min="0" value="1" oninput="updateState()" class="w-full bg-slate-900 border border-slate-700 rounded-lg text-center py-1 text-sm font-bold text-slate-100 focus:outline-none focus:border-amber-500">
                </div>
                <div class="bg-slate-950 p-2 rounded-xl border border-slate-800 text-center">
                  <span class="text-xs font-semibold text-slate-400 block mb-1">XL</span>
                  <input type="number" id="size-XL" min="0" value="1" oninput="updateState()" class="w-full bg-slate-900 border border-slate-700 rounded-lg text-center py-1 text-sm font-bold text-slate-100 focus:outline-none focus:border-amber-500">
                </div>
                <div class="bg-slate-950 p-2 rounded-xl border border-slate-800 text-center">
                  <span class="text-xs font-semibold text-slate-400 block mb-1">2XL</span>
                  <input type="number" id="size-XXL" min="0" value="1" oninput="updateState()" class="w-full bg-slate-900 border border-slate-700 rounded-lg text-center py-1 text-sm font-bold text-slate-100 focus:outline-none focus:border-amber-500">
                </div>
              </div>

              <div>
                <label class="block text-xs font-medium text-slate-400 mb-1">Custom Measurement Instructions (Optional)</label>
                <input type="text" id="size-custom" oninput="updateState()" placeholder="e.g. 2x Kids Size 10, 1x 3XL" class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-xs text-slate-100 focus:outline-none focus:border-amber-500">
              </div>
            </div>
          </div>
        </div>

        <!-- Right: Real-Time Visual Proof Mockups Canvas -->
        <div class="lg:col-span-7">
          <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 shadow-xl space-y-5 sticky top-24">
            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3 border-b border-slate-800 pb-3">
              <div>
                <h3 class="text-lg font-bold font-serif-tribute text-amber-200 flex items-center gap-2">
                  <i data-lucide="eye" class="w-5 h-5 text-amber-400"></i>
                  Real-Time Visual Proof Mockups
                </h3>
                <p class="text-xs text-slate-400">Live render across all product display formats</p>
              </div>

              <!-- Proof Mockup View Tabs -->
              <div class="inline-flex p-1 bg-slate-950 rounded-xl border border-slate-800 self-start sm:self-auto">
                <button id="proof-tab-tshirt" onclick="switchProofTab('tshirt')" class="px-3 py-1.5 rounded-lg text-xs font-semibold bg-amber-500 text-slate-950 font-bold">T-Shirt</button>
                <button id="proof-tab-tarpaulin" onclick="switchProofTab('tarpaulin')" class="px-3 py-1.5 rounded-lg text-xs font-semibold text-slate-400 hover:text-slate-200">Tarpaulin (2.5x6 ft)</button>
                <button id="proof-tab-acrylic" onclick="switchProofTab('acrylic')" class="px-3 py-1.5 rounded-lg text-xs font-semibold text-slate-400 hover:text-slate-200">Acrylic (A4)</button>
                <button id="proof-tab-sintra" onclick="switchProofTab('sintra')" class="px-3 py-1.5 rounded-lg text-xs font-semibold text-slate-400 hover:text-slate-200">Sintra Board</button>
              </div>
            </div>

            <!-- PROOF CANVAS DISPLAY AREA -->
            <div class="bg-slate-950 border border-slate-800 rounded-2xl p-4 sm:p-6 min-h-[460px] flex items-center justify-center relative overflow-hidden">
             
              <!-- 1. T-Shirt Visual Proof Mockup -->
              <div id="proof-canvas-tshirt" class="w-full flex flex-col items-center justify-center py-2">
                <div id="tshirt-mockup-body" class="w-72 h-84 rounded-t-[4rem] rounded-b-2xl border-4 border-slate-300 bg-slate-100 text-slate-900 relative shadow-2xl transition-colors duration-300 flex flex-col items-center pt-8 px-6 overflow-hidden">
                  <div id="tshirt-collar" class="w-24 h-10 border-b-4 border-slate-300 bg-slate-200 rounded-b-full absolute top-0 shadow-inner"></div>
                  <div class="absolute -left-8 top-6 w-12 h-24 bg-slate-200 border-l-4 border-t-4 border-slate-300 -rotate-12 rounded-l-xl -z-0"></div>
                  <div class="absolute -right-8 top-6 w-12 h-24 bg-slate-200 border-r-4 border-t-4 border-slate-300 rotate-12 rounded-r-xl -z-0"></div>

                  <div class="z-10 w-44 text-center space-y-2 mt-4 bg-slate-950/5 p-3 rounded-xl backdrop-blur-[1px] border border-black/5">
                    <span class="text-[9px] font-bold uppercase tracking-widest block text-amber-700 font-serif-tribute">In Loving Memory</span>
                    <div id="tshirt-portrait-slot" class="w-20 h-20 mx-auto rounded-full border-2 border-amber-600/60 overflow-hidden bg-slate-200 shadow-md flex items-center justify-center">
                      <i data-lucide="user" class="w-8 h-8 text-slate-400"></i>
                    </div>
                    <div>
                      <h4 id="tshirt-proof-name" class="font-serif-tribute text-xs font-bold leading-tight uppercase tracking-tight text-slate-900">Juan De La Cruz</h4>
                      <p id="tshirt-proof-dates" class="text-[10px] text-slate-700 font-medium mt-0.5">1955 — 2026</p>
                    </div>
                  </div>
                </div>
                <span class="text-xs text-slate-500 mt-4">Real-time T-Shirt Chest Print Proof Preview</span>
              </div>

              <!-- 2. Tarpaulin Visual Proof Mockup (2.5 x 6 ft Vertical Standing Banner) -->
              <div id="proof-canvas-tarpaulin" class="w-full flex flex-col items-center justify-center py-2 hidden">
                <div class="relative w-56 sm:w-64 h-[440px] sm:h-[480px] bg-gradient-to-b from-slate-950 via-slate-900 to-slate-950 border-4 border-amber-600/80 rounded-md vinyl-texture p-4 flex flex-col justify-between text-center shadow-2xl overflow-hidden select-none">
                  <!-- 6 Reinforced Metal Eyelets -->
                  <div class="absolute top-2.5 left-2.5 w-5 h-5 rounded-full bg-gradient-to-tr from-slate-500 via-slate-300 to-slate-100 border-2 border-slate-700 shadow flex items-center justify-center z-20"><div class="w-2 h-2 rounded-full bg-slate-950"></div></div>
                  <div class="absolute top-2.5 right-2.5 w-5 h-5 rounded-full bg-gradient-to-tr from-slate-500 via-slate-300 to-slate-100 border-2 border-slate-700 shadow flex items-center justify-center z-20"><div class="w-2 h-2 rounded-full bg-slate-950"></div></div>
                  <div class="absolute top-1/2 -translate-y-1/2 left-2.5 w-4 h-4 rounded-full bg-slate-400 border border-slate-700 shadow flex items-center justify-center z-20"><div class="w-1.5 h-1.5 rounded-full bg-slate-950"></div></div>
                  <div class="absolute top-1/2 -translate-y-1/2 right-2.5 w-4 h-4 rounded-full bg-slate-400 border border-slate-700 shadow flex items-center justify-center z-20"><div class="w-1.5 h-1.5 rounded-full bg-slate-950"></div></div>
                  <div class="absolute bottom-2.5 left-2.5 w-5 h-5 rounded-full bg-gradient-to-tr from-slate-500 via-slate-300 to-slate-100 border-2 border-slate-700 shadow flex items-center justify-center z-20"><div class="w-2 h-2 rounded-full bg-slate-950"></div></div>
                  <div class="absolute bottom-2.5 right-2.5 w-5 h-5 rounded-full bg-gradient-to-tr from-slate-500 via-slate-300 to-slate-100 border-2 border-slate-700 shadow flex items-center justify-center z-20"><div class="w-2 h-2 rounded-full bg-slate-950"></div></div>

                  <!-- Banner Inner Content -->
                  <div class="border border-amber-500/40 h-full p-3 flex flex-col items-center justify-between rounded bg-gradient-to-b from-amber-500/[0.05] via-transparent to-amber-950/[0.1]">
                    <div class="flex flex-col items-center pt-1">
                      <span class="text-[9px] uppercase font-serif-tribute tracking-[0.25em] text-amber-300 font-semibold">In Everlasting Remembrance</span>
                      <div class="text-[12px] text-amber-400/80 mt-0.5">†</div>
                    </div>
                    <div id="tarp-portrait-slot" class="w-24 h-24 rounded-full border-2 border-amber-400 overflow-hidden bg-slate-800 shadow-xl flex items-center justify-center my-2">
                      <i data-lucide="user" class="w-12 h-12 text-slate-600"></i>
                    </div>
                    <div class="w-full px-1">
                      <h4 id="tarp-proof-name" class="font-serif-tribute text-sm sm:text-base font-bold text-amber-100 uppercase tracking-wide gold-glow leading-snug">Juan De La Cruz</h4>
                      <p id="tarp-proof-dates" class="text-xs text-amber-400 font-medium tracking-widest mt-0.5">1955 — 2026</p>
                      <p id="tarp-proof-quote" class="text-[9.5px] text-slate-300 italic font-serif-tribute line-clamp-2 mt-1.5 opacity-90 px-1">"In Loving Memory & Forever in Our Hearts"</p>
                    </div>
                    <div class="w-full pt-2 border-t border-amber-500/20 text-center">
                      <span class="text-[8.5px] text-amber-400/80 font-mono uppercase tracking-widest font-semibold">2.5 × 6 FT · Standing Chapel Banner</span>
                    </div>
                  </div>
                </div>
                <span class="text-xs text-amber-400 font-semibold mt-3">2.5 × 6 FT (76 × 183 cm) Standing Vinyl Tarpaulin Display Banner</span>
              </div>

              <!-- 3. Acrylic Frame Visual Proof Mockup (A4 Size: 210 x 297 mm) -->
              <div id="proof-canvas-acrylic" class="w-full flex flex-col items-center justify-center py-2 hidden">
                <div class="relative w-64 sm:w-72 h-[370px] sm:h-[400px] rounded-lg border border-white/40 acrylic-glass p-5 flex flex-col items-center justify-between text-center overflow-hidden">
                  <!-- 4 Standoff Pins -->
                  <div class="absolute top-3 left-3 w-4 h-4 rounded-full bg-gradient-to-tr from-slate-400 via-slate-100 to-white border border-slate-500 shadow-md"></div>
                  <div class="absolute top-3 right-3 w-4 h-4 rounded-full bg-gradient-to-tr from-slate-400 via-slate-100 to-white border border-slate-500 shadow-md"></div>
                  <div class="absolute bottom-3 left-3 w-4 h-4 rounded-full bg-gradient-to-tr from-slate-400 via-slate-100 to-white border border-slate-500 shadow-md"></div>
                  <div class="absolute bottom-3 right-3 w-4 h-4 rounded-full bg-gradient-to-tr from-slate-400 via-slate-100 to-white border border-slate-500 shadow-md"></div>

                  <div class="w-full h-full border border-amber-300/30 rounded p-4 flex flex-col items-center justify-between bg-slate-950/40">
                    <span class="text-[10px] uppercase tracking-[0.25em] text-amber-200/90 font-serif-tribute font-semibold pt-1">In Loving Memory</span>
                    <div id="acrylic-portrait-slot" class="w-24 sm:w-28 h-24 sm:h-28 rounded-full border-2 border-amber-300/80 overflow-hidden bg-slate-900 shadow-2xl flex items-center justify-center my-2">
                      <i data-lucide="user" class="w-10 h-10 text-slate-600"></i>
                    </div>
                    <div>
                      <h4 id="acrylic-proof-name" class="font-serif-tribute text-sm sm:text-base font-bold text-white uppercase tracking-tight">Juan De La Cruz</h4>
                      <p id="acrylic-proof-dates" class="text-xs text-amber-300 font-medium mt-0.5">1955 — 2026</p>
                      <p id="acrylic-proof-quote" class="text-[10px] text-slate-200 italic font-serif-tribute mt-1">"Forever in our hearts & thoughts"</p>
                    </div>
                    <div class="text-[8px] text-slate-400/80 uppercase tracking-widest pt-1 border-t border-white/10 w-full text-center">A4 Crystal Plate · 210 × 297 mm</div>
                  </div>
                </div>
                <span class="text-xs text-amber-400 font-semibold mt-3">A4 SIZE (210 x 297 mm) Crystal Clear Acrylic Plate Proof</span>
              </div>

              <!-- 4. Sintra Board Visual Proof Mockup -->
              <div id="proof-canvas-sintra" class="w-full flex flex-col items-center justify-center py-2 hidden">
                <div class="relative w-64 sm:w-72 h-[370px] sm:h-[390px] bg-slate-900 border-2 border-slate-700 rounded-lg p-5 sintra-board-shadow flex flex-col items-center justify-between text-center overflow-hidden">
                  <div class="absolute inset-0 border-4 border-slate-800/80 rounded-lg pointer-events-none"></div>
                  <div class="w-full h-full border border-amber-500/40 rounded p-4 flex flex-col items-center justify-between bg-gradient-to-b from-slate-900 via-slate-950 to-slate-900">
                    <span class="text-[10px] uppercase tracking-[0.25em] text-amber-400 font-serif-tribute font-semibold pt-1">In Sacred Memory</span>
                    <div id="sintra-portrait-slot" class="w-24 sm:w-28 h-24 sm:h-28 rounded-full border-2 border-amber-500 overflow-hidden bg-slate-950 shadow-md flex items-center justify-center my-2">
                      <i data-lucide="user" class="w-10 h-10 text-slate-600"></i>
                    </div>
                    <div>
                      <h4 id="sintra-proof-name" class="font-serif-tribute text-sm sm:text-base font-bold text-slate-100 uppercase tracking-wide">Juan De La Cruz</h4>
                      <p id="sintra-proof-dates" class="text-xs text-amber-400 font-medium mt-0.5">1955 — 2026</p>
                      <p id="sintra-proof-quote" class="text-[10px] text-slate-300 italic font-serif-tribute mt-1">"Forever in our hearts"</p>
                    </div>
                    <div class="text-[8px] text-slate-400 uppercase tracking-widest pt-1 border-t border-slate-800 w-full text-center">Matte Waterproof PVC Sintra Board (22x28 in / A4)</div>
                  </div>
                </div>
                <span class="text-xs text-slate-400 mt-3">Matte Sintra Board PVC Photo Plate Proof (22 x 28 inch)</span>
              </div>
            </div>

            <!-- Proof Badges -->
            <div class="grid grid-cols-2 sm:grid-cols-4 gap-2 text-center text-xs bg-slate-950 p-3 rounded-xl border border-slate-800">
              <div>
                <span class="text-slate-500 block">Deceased Name</span>
                <strong id="summary-badge-name" class="text-slate-200 truncate block font-serif-tribute">Juan De La Cruz</strong>
              </div>
              <div>
                <span class="text-slate-500 block">Shirt Color</span>
                <strong id="summary-badge-color" class="text-slate-200 block uppercase">White</strong>
              </div>
              <div>
                <span class="text-slate-500 block">Tarpaulin Banner</span>
                <strong class="text-amber-400 block font-semibold">2.5 × 6 FT</strong>
              </div>
              <div>
                <span class="text-slate-500 block">Acrylic Frame</span>
                <strong class="text-amber-400 block font-semibold">A4 (210×297mm)</strong>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="flex items-center justify-between pt-4 border-t border-slate-800">
        <button onclick="goToStep(2)" class="flex items-center gap-2 bg-slate-800 hover:bg-slate-700 text-slate-200 font-semibold px-5 py-2.5 rounded-xl text-sm transition-all">
          <i data-lucide="arrow-left" class="w-4 h-4"></i>
          <span>Back</span>
        </button>
        <button onclick="goToStep(4)" class="flex items-center gap-2 bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-400 hover:to-amber-500 text-slate-950 font-bold px-6 py-3 rounded-xl shadow-lg transition-all">
          <span>Review Final Order Summary</span>
          <i data-lucide="arrow-right" class="w-4 h-4"></i>
        </button>
      </div>
    </section>

    <!-- ==================== STEP 4 ==================== -->
    <section id="step-section-4" class="step-content space-y-6 hidden">
      <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 md:p-8 space-y-6 shadow-xl print-card">
       
        <div class="border-b border-slate-800 pb-4 flex flex-col sm:flex-row sm:items-center justify-between gap-4">
          <div>
            <h2 class="text-2xl font-bold font-serif-tribute text-amber-200 flex items-center gap-2">
              <i data-lucide="clipboard-list" class="w-6 h-6 text-amber-400"></i>
              Step 4: Order Specification Summary
            </h2>
            <p class="text-slate-400 text-sm mt-1">Review full customized tribute items and specifications before submitting your request.</p>
          </div>
         
          <div class="flex items-center gap-2 no-print">
            <button onclick="copyOrderSpecs()" class="flex items-center gap-1.5 bg-slate-800 hover:bg-slate-700 text-slate-200 px-3.5 py-2 rounded-xl text-xs font-semibold border border-slate-700">
              <i data-lucide="copy" class="w-4 h-4"></i>
              <span id="btn-copy-label">Copy Specs</span>
            </button>
            <button onclick="window.print()" class="flex items-center gap-1.5 bg-slate-800 hover:bg-slate-700 text-slate-200 px-3.5 py-2 rounded-xl text-xs font-semibold border border-slate-700">
              <i data-lucide="printer" class="w-4 h-4"></i>
              <span>Print Order Sheet</span>
            </button>
          </div>
        </div>

        <!-- Receiving Email Banner -->
        <div class="bg-amber-950/40 border border-amber-800/50 rounded-xl p-4 flex flex-col sm:flex-row items-start sm:items-center justify-between gap-3">
          <div class="flex items-center gap-3">
            <div class="w-10 h-10 rounded-xl bg-amber-500/20 text-amber-400 flex items-center justify-center shrink-0">
              <i data-lucide="mail-check" class="w-5 h-5"></i>
            </div>
            <div>
              <span class="text-xs text-amber-400 font-semibold block">Destination Receiving Email</span>
              <strong class="text-slate-100 text-sm sm:text-base font-mono select-all">sntechnoprint01@gmail.com</strong>
            </div>
          </div>
          <div class="text-right">
            <span id="sum-order-ref" class="text-xs text-slate-400 block font-mono">Ref: SN-TRIBUTE-2026</span>
            <span class="text-[11px] text-amber-300 font-medium">Official SN TechnoPrint Inbox</span>
          </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <!-- Client & Memorial Info -->
          <div class="bg-slate-950 rounded-xl p-5 border border-slate-800 space-y-3">
            <h3 class="text-xs font-semibold uppercase tracking-wider text-amber-400 border-l-2 border-amber-500 pl-2">Customer & Loved One Info</h3>
           
            <div class="space-y-1.5 text-xs text-slate-300">
              <div class="flex justify-between py-1 border-b border-slate-900">
                <span class="text-slate-500">Customer Name:</span>
                <strong id="sum-cust-name" class="text-slate-200">—</strong>
              </div>
              <div class="flex justify-between py-1 border-b border-slate-900">
                <span class="text-slate-500">Contact Phone:</span>
                <strong id="sum-cust-phone" class="text-slate-200">—</strong>
              </div>
              <div class="flex justify-between py-1 border-b border-slate-900">
                <span class="text-slate-500">Email Address:</span>
                <strong id="sum-cust-email" class="text-slate-200">—</strong>
              </div>
              <div class="flex justify-between py-1 border-b border-slate-900">
                <span class="text-slate-500">Loved One Name:</span>
                <strong id="sum-loved-name" class="text-amber-300 font-bold font-serif-tribute">—</strong>
              </div>
              <div class="flex justify-between py-1 border-b border-slate-900">
                <span class="text-slate-500">Memorial Dates:</span>
                <strong id="sum-loved-dates" class="text-slate-200">—</strong>
              </div>
              <div class="pt-1">
                <span class="text-slate-500 block mb-1">Inscription Quote:</span>
                <em id="sum-loved-quote" class="text-slate-300 text-xs block bg-slate-900 p-2.5 rounded-lg border border-slate-800 font-serif-tribute">"In Loving Memory & Forever in Our Hearts"</em>
              </div>
            </div>
          </div>

          <!-- Items Selected Summary Card -->
          <div class="bg-slate-950 rounded-xl p-5 border border-slate-800 space-y-3">
            <h3 class="text-xs font-semibold uppercase tracking-wider text-amber-400 border-l-2 border-amber-500 pl-2">Selected Products & Quantities</h3>
            <div id="sum-items-list" class="space-y-2 text-xs text-slate-300">
              <!-- Dynamically Populated -->
            </div>
          </div>
        </div>

        <!-- 1-40 PHOTOS UPLOAD SECTION -->
        <div class="pt-4 border-t border-slate-800 space-y-4">
          <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-2">
            <div>
              <label class="block text-xs font-semibold uppercase tracking-wider text-amber-400 border-l-2 border-amber-500 pl-2">
                Memorial Portrait Photos (1 to 40 Photos)
              </label>
              <p class="text-xs text-slate-400 mt-0.5">
                Upload 1 to 40 photos of your loved one for memorial archives and select the primary tribute display photo.
              </p>
            </div>
            <div class="flex items-center gap-2">
              <span id="photo-count-badge" class="text-xs font-semibold px-2.5 py-1 rounded-lg bg-slate-950 border border-slate-800 text-amber-400">
                0 / 40 Photos Uploaded
              </span>
              <button type="button" onclick="clearAllPhotos()" class="text-xs text-slate-500 hover:text-red-400 transition-colors underline">
                Clear All
              </button>
            </div>
          </div>

          <div class="grid grid-cols-1 sm:grid-cols-3 gap-6 items-start">
            <!-- Upload Dropzone -->
            <div class="sm:col-span-2 space-y-3">
              <label id="upload-dropzone-label" onclick="triggerFileInput()" ondragover="event.preventDefault()" ondrop="handleDropFiles(event)" class="flex flex-col items-center justify-center p-6 border-2 border-dashed border-slate-700 hover:border-amber-500/80 rounded-2xl cursor-pointer bg-slate-950/50 hover:bg-slate-950 transition-all group select-none">
                <div class="w-12 h-12 rounded-2xl bg-amber-500/10 border border-amber-500/20 text-amber-400 flex items-center justify-center mb-2 group-hover:scale-105 transition-transform">
                  <i data-lucide="upload-cloud" class="w-6 h-6"></i>
                </div>

                <span id="upload-primary-text" class="text-sm font-medium text-slate-200 group-hover:text-amber-300 text-center">
                  1-40 upload photos (Click or drag images to upload)
                </span>

                <span id="upload-sub-text" class="text-xs text-slate-400 mt-1 text-center">
                  1-40 upload photos supported (JPG, PNG, WEBP) · Add up to 40 memorial photos
                </span>

                <div class="mt-3 flex items-center gap-1.5 text-[11px] text-amber-400/90 font-medium">
                  <i data-lucide="plus" class="w-3.5 h-3.5"></i>
                  <span id="upload-remaining-text">1-40 upload photos for memorial archives</span>
                </div>

                <input id="multi-photo-input" type="file" accept="image/*" multiple class="hidden" onchange="handleMultiplePhotosUpload(event)">
              </label>

              <!-- Uploaded Photos Gallery Grid (1 to 40 photos) -->
              <div id="gallery-container" class="bg-slate-950 border border-slate-800 rounded-xl p-3 space-y-2 hidden">
                <div class="flex items-center justify-between text-xs text-slate-400">
                  <span id="gallery-header-text" class="font-semibold text-slate-300">
                    Uploaded Photo Gallery (0/40):
                  </span>
                  <span class="text-[11px] text-amber-400">
                    ★ Click photo to set as Primary Display Mockup
                  </span>
                </div>

                <div id="photos-grid" class="grid grid-cols-5 sm:grid-cols-8 gap-2 pt-1 max-h-72 overflow-y-auto pr-1">
                  <!-- Dynamically populated photos -->
                </div>
              </div>
            </div>

            <!-- Primary Photo Card -->
            <div class="flex flex-col items-center justify-center p-3 bg-slate-950 rounded-2xl border border-slate-800 min-h-[190px]">
              <div id="primary-preview-slot" class="w-full h-44 flex flex-col items-center justify-center relative overflow-hidden rounded-xl border border-slate-800 bg-slate-900">
                <i data-lucide="image" class="w-8 h-8 text-slate-600 mb-1.5"></i>
                <span class="text-xs font-medium text-slate-500">No Photo Selected</span>
                <span class="text-[10px] text-slate-600 mt-0.5">Upload 1-40 photos on the left</span>
              </div>
              <div id="primary-caption" class="text-center text-[11px] text-slate-400 mt-2">
                1-40 upload photos supported
              </div>
            </div>
          </div>
        </div>

        <!-- T-Shirt Specs -->
        <div class="bg-slate-950 rounded-xl p-5 border border-slate-800 space-y-3">
          <h3 class="text-xs font-semibold uppercase tracking-wider text-amber-400 border-l-2 border-amber-500 pl-2">T-Shirt Configuration Details</h3>
         
          <div class="grid grid-cols-1 sm:grid-cols-3 gap-4 text-xs">
            <div>
              <span class="text-slate-500 block">Shirt Base Fabric Color</span>
              <strong id="sum-tshirt-color" class="text-slate-200 font-bold uppercase">White</strong>
            </div>
            <div>
              <span class="text-slate-500 block">Size Matrix Breakdown</span>
              <strong id="sum-tshirt-sizes" class="text-slate-200">S: 1, M: 1, L: 1, XL: 1, 2XL: 1</strong>
            </div>
            <div>
              <span class="text-slate-500 block">Custom Measurements</span>
              <strong id="sum-tshirt-custom" class="text-slate-200">None specified</strong>
            </div>
          </div>
        </div>

        <!-- Delivery Notes -->
        <div>
          <label class="block text-xs font-semibold uppercase tracking-wider text-slate-400 mb-1.5">Special Instructions, Chapel Location or Delivery Notes (Optional)</label>
          <textarea id="special-notes" oninput="updateState()" rows="2" placeholder="e.g. Please expedite for Friday vigil service; chapel room located at..." class="w-full bg-slate-950 border border-slate-700 rounded-xl px-4 py-2 text-xs text-slate-100 placeholder-slate-500 focus:outline-none focus:border-amber-500"></textarea>
        </div>

        <!-- Actions -->
        <div class="pt-4 border-t border-slate-800 flex flex-col sm:flex-row items-center justify-between gap-4 no-print">
          <button onclick="goToStep(3)" class="w-full sm:w-auto flex items-center justify-center gap-2 bg-slate-800 hover:bg-slate-700 text-slate-200 font-semibold px-5 py-3 rounded-xl text-sm transition-all">
            <i data-lucide="arrow-left" class="w-4 h-4"></i>
            <span>Back to Proof Preview</span>
          </button>

          <button onclick="submitOrderViaEmail()" class="w-full sm:w-auto flex items-center justify-center gap-2 bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-400 hover:to-amber-500 text-slate-950 font-bold px-8 py-3.5 rounded-xl shadow-xl transition-all">
            <i data-lucide="send" class="w-5 h-5"></i>
            <span>Submit Order via Email (sntechnoprint01@gmail.com)</span>
          </button>
        </div>

      </div>
    </section>

  </main>

  <footer class="mt-auto border-t border-slate-800 bg-slate-950 py-6 text-center text-xs text-slate-500 no-print">
    <div class="max-w-7xl mx-auto px-4 flex flex-col sm:flex-row items-center justify-between gap-3">
      <p>&copy; 2026 SN TechnoPrint. All rights reserved. Memorial Display & Printing Services.</p>
      <p>Direct Orders Inbox: <strong class="text-amber-400 font-mono">sntechnoprint01@gmail.com</strong></p>
    </div>
  </footer>

  <!-- Core JavaScript State & Handlers -->
  <script>
    const appState = {
      currentStep: 1,
      custName: '',
      custPhone: '',
      custEmail: '',
      lovedName: 'Juan De La Cruz',
      lovedDob: '1955-08-15',
      lovedDop: '2026-03-20',
      lovedQuote: 'In Loving Memory & Forever in Our Hearts',
      specialNotes: '',
     
      // 1 to 40 photos
      photos: [],
      primaryPhotoIndex: 0,

      // Bundles (with 5 shirts each, 2.5x6 ft tarp, 22x28 in sintra)
      bundles: {
        1: 0,
        2: 1,
        3: 0,
        4: 0
      },

      // Single Products
      single: {
        tarpaulin: 0,
        sintra: 0,
        acrylic: 0,
        tshirt: 0
      },

      shirtColor: 'white',
      sizes: {
        S: 1,
        M: 1,
        L: 1,
        XL: 1,
        XXL: 1
      },
      customSizeText: '',
      orderRef: 'SN-TRIBUTE-' + Math.floor(1000 + Math.random() * 9000)
    };

    window.addEventListener('DOMContentLoaded', () => {
      lucide.createIcons();
      document.getElementById('sum-order-ref').innerText = 'Ref: ' + appState.orderRef;
      updateState();
    });

    function goToStep(step) {
      appState.currentStep = step;

      // Update tab styles
      for (let i = 1; i <= 4; i++) {
        const btn = document.getElementById('step-btn-' + i);
        const section = document.getElementById('step-section-' + i);
        if (i === step) {
          btn.className = "step-tab flex items-center justify-center gap-2 py-2.5 px-3 rounded-xl text-xs sm:text-sm font-semibold transition-all duration-200 bg-amber-500 text-slate-950 shadow-md";
          section.classList.remove('hidden');
        } else {
          btn.className = "step-tab flex items-center justify-center gap-2 py-2.5 px-3 rounded-xl text-xs sm:text-sm font-semibold transition-all duration-200 text-slate-400 hover:text-slate-200 hover:bg-slate-900/40";
          section.classList.add('hidden');
        }
      }

      window.scrollTo({ top: 0, behavior: 'smooth' });
      lucide.createIcons();
    }

    function switchOfferTab(tab) {
      const panelBundles = document.getElementById('offer-panel-bundles');
      const panelSingle = document.getElementById('offer-panel-single');
      const btnBundles = document.getElementById('offer-tab-bundles');
      const btnSingle = document.getElementById('offer-tab-single');

      if (tab === 'bundles') {
        panelBundles.classList.remove('hidden');
        panelSingle.classList.add('hidden');
        btnBundles.className = "px-4 py-2 rounded-lg text-xs font-semibold bg-amber-500 text-slate-950 font-bold shadow";
        btnSingle.className = "px-4 py-2 rounded-lg text-xs font-semibold text-slate-400 hover:text-slate-200";
      } else {
        panelBundles.classList.add('hidden');
        panelSingle.classList.remove('hidden');
        btnSingle.className = "px-4 py-2 rounded-lg text-xs font-semibold bg-amber-500 text-slate-950 font-bold shadow";
        btnBundles.className = "px-4 py-2 rounded-lg text-xs font-semibold text-slate-400 hover:text-slate-200";
      }
    }

    function switchProofTab(tab) {
      ['tshirt', 'tarpaulin', 'acrylic', 'sintra'].forEach(t => {
        const canvas = document.getElementById('proof-canvas-' + t);
        const btn = document.getElementById('proof-tab-' + t);
        if (t === tab) {
          canvas.classList.remove('hidden');
          btn.className = "px-3 py-1.5 rounded-lg text-xs font-semibold bg-amber-500 text-slate-950 font-bold shadow";
        } else {
          canvas.classList.add('hidden');
          btn.className = "px-3 py-1.5 rounded-lg text-xs font-semibold text-slate-400 hover:text-slate-200";
        }
      });
    }

    function changeBundleQty(id, delta) {
      appState.bundles[id] = Math.max(0, (appState.bundles[id] || 0) + delta);
      document.getElementById('qty-bundle-' + id).innerText = appState.bundles[id];
      updateState();
    }

    function changeSingleQty(id, delta) {
      appState.single[id] = Math.max(0, (appState.single[id] || 0) + delta);
      document.getElementById('qty-single-' + id).innerText = appState.single[id];
      updateState();
    }

    function setShirtColor(color) {
      appState.shirtColor = color;
      const btnWhite = document.getElementById('color-btn-white');
      const btnBlack = document.getElementById('color-btn-black');
      const mockup = document.getElementById('tshirt-mockup-body');
      const collar = document.getElementById('tshirt-collar');
      const proofName = document.getElementById('tshirt-proof-name');
      const proofDates = document.getElementById('tshirt-proof-dates');

      if (color === 'white') {
        btnWhite.className = "py-3 px-4 rounded-xl border-2 border-amber-500 bg-slate-100 text-slate-900 font-bold flex items-center justify-center gap-2 text-sm shadow-md transition-all";
        btnBlack.className = "py-3 px-4 rounded-xl border-2 border-slate-800 bg-slate-950 text-slate-100 font-bold flex items-center justify-center gap-2 text-sm hover:border-slate-700 transition-all";
        mockup.className = "w-72 h-84 rounded-t-[4rem] rounded-b-2xl border-4 border-slate-300 bg-slate-100 text-slate-900 relative shadow-2xl transition-colors duration-300 flex flex-col items-center pt-8 px-6 overflow-hidden";
        collar.className = "w-24 h-10 border-b-4 border-slate-300 bg-slate-200 rounded-b-full absolute top-0 shadow-inner";
        proofName.className = "font-serif-tribute text-xs font-bold leading-tight uppercase tracking-tight text-slate-900";
        proofDates.className = "text-[10px] text-slate-700 font-medium mt-0.5";
      } else {
        btnBlack.className = "py-3 px-4 rounded-xl border-2 border-amber-500 bg-slate-950 text-slate-100 font-bold flex items-center justify-center gap-2 text-sm shadow-md transition-all";
        btnWhite.className = "py-3 px-4 rounded-xl border-2 border-slate-800 bg-slate-100 text-slate-900 font-bold flex items-center justify-center gap-2 text-sm hover:border-slate-700 transition-all";
        mockup.className = "w-72 h-84 rounded-t-[4rem] rounded-b-2xl border-4 border-slate-800 bg-slate-900 text-slate-100 relative shadow-2xl transition-colors duration-300 flex flex-col items-center pt-8 px-6 overflow-hidden";
        collar.className = "w-24 h-10 border-b-4 border-slate-800 bg-slate-950 rounded-b-full absolute top-0 shadow-inner";
        proofName.className = "font-serif-tribute text-xs font-bold leading-tight uppercase tracking-tight text-amber-200";
        proofDates.className = "text-[10px] text-amber-400 font-medium mt-0.5";
      }
      document.getElementById('summary-badge-color').innerText = color;
      document.getElementById('sum-tshirt-color').innerText = color;
    }

    function addOneToAllSizes() {
      ['S', 'M', 'L', 'XL', 'XXL'].forEach(s => {
        const inp = document.getElementById('size-' + s);
        inp.value = (parseInt(inp.value) || 0) + 1;
      });
      updateState();
    }

    function resetSizes() {
      ['S', 'M', 'L', 'XL', 'XXL'].forEach(s => {
        document.getElementById('size-' + s).value = 0;
      });
      document.getElementById('size-custom').value = '';
      updateState();
    }

    function setQuote(q) {
      document.getElementById('loved-quote').value = q;
      updateState();
    }

    // 1-40 PHOTOS UPLOAD HANDLERS
    function triggerFileInput() {
      if (appState.photos.length < 40) {
        document.getElementById('multi-photo-input').click();
      }
    }

    function handleMultiplePhotosUpload(e) {
      if (e.target.files) {
        processFiles(e.target.files);
      }
      e.target.value = '';
    }

    function handleDropFiles(e) {
      e.preventDefault();
      if (e.dataTransfer.files) {
        processFiles(e.dataTransfer.files);
      }
    }

    function processFiles(files) {
      const remainingSlots = 40 - appState.photos.length;
      if (remainingSlots <= 0) {
        alert('You have reached the maximum limit of 40 photos. Remove a photo to upload a new one.');
        return;
      }

      const filesToRead = Array.from(files).slice(0, remainingSlots);
      let loaded = 0;
      filesToRead.forEach(file => {
        const reader = new FileReader();
        reader.onload = evt => {
          appState.photos.push(evt.target.result);
          loaded++;
          if (loaded === filesToRead.length) {
            renderPhotosGallery();
          }
        };
        reader.readAsDataURL(file);
      });
    }

    function renderPhotosGallery() {
      const container = document.getElementById('gallery-container');
      const grid = document.getElementById('photos-grid');
      const countBadge = document.getElementById('photo-count-badge');
      const primarySlot = document.getElementById('primary-preview-slot');
      const primaryCaption = document.getElementById('primary-caption');
      const headerText = document.getElementById('gallery-header-text');
      const primaryText = document.getElementById('upload-primary-text');
      const subText = document.getElementById('upload-sub-text');
      const remText = document.getElementById('upload-remaining-text');

      const count = appState.photos.length;
      countBadge.innerText = count + ' / 40 Photos Uploaded';
      headerText.innerText = 'Uploaded Photo Gallery (' + count + '/40):';

      if (count === 0) {
        container.classList.add('hidden');
        primaryText.innerText = '1-40 upload photos (Click or drag images to upload)';
        subText.innerText = '1-40 upload photos supported (JPG, PNG, WEBP) · Add up to 40 memorial photos';
        remText.innerText = '1-40 upload photos for memorial archives';
        primarySlot.innerHTML = `<i data-lucide="image" class="w-8 h-8 text-slate-600 mb-1.5"></i><span class="text-xs text-slate-500 font-medium">No Photo Selected</span><span class="text-[10px] text-slate-600 mt-0.5">Upload 1-40 photos on the left</span>`;
        primaryCaption.innerText = '1-40 upload photos supported';
        updateMockupsPhoto(null);
      } else {
        container.classList.remove('hidden');
        const rem = 40 - count;
        if (rem > 0) {
          primaryText.innerText = `1-40 upload photos (${count} of 40 uploaded · Click or drag to add more)`;
          subText.innerText = '1-40 upload photos supported (JPG, PNG, WEBP) · Add up to 40 memorial photos';
          remText.innerText = `${rem} photo slot(s) remaining (1-40 upload photos)`;
        } else {
          primaryText.innerText = '1-40 upload photos (Maximum 40 photos uploaded)';
          subText.innerText = '40/40 slots filled. Click any thumbnail below to set as primary proof or delete to replace.';
          remText.innerText = 'Maximum 40 photos reached';
        }

        // Render Grid
        grid.innerHTML = '';
        appState.photos.forEach((url, idx) => {
          const isPrimary = idx === appState.primaryPhotoIndex;
          const div = document.createElement('div');
          div.className = `relative group/item aspect-square rounded-xl overflow-hidden border-2 cursor-pointer transition-all ${isPrimary ? 'border-amber-400 ring-2 ring-amber-400/30 shadow-lg' : 'border-slate-800 hover:border-slate-600 opacity-80 hover:opacity-100'}`;
          div.onclick = () => setPrimaryPhoto(idx);
          div.innerHTML = `
            <img src="${url}" class="w-full h-full object-cover" />
            <div class="absolute top-1 left-1 bg-black/80 text-[10px] font-bold text-slate-200 px-1.5 py-0.5 rounded">#${idx + 1}</div>
            ${isPrimary ? '<div class="absolute bottom-1 inset-x-1 bg-amber-500 text-slate-950 text-[9px] font-bold uppercase py-0.5 text-center rounded">Primary</div>' : '<div class="absolute bottom-1 inset-x-1 bg-black/70 text-[9px] text-slate-300 py-0.5 text-center rounded opacity-0 group-hover/item:opacity-100">Set Main</div>'}
            <button onclick="event.stopPropagation(); removePhoto(${idx});" class="absolute top-1 right-1 w-5 h-5 rounded bg-black/80 hover:bg-red-600 text-white flex items-center justify-center opacity-0 group-hover/item:opacity-100 text-xs">✕</button>
          `;
          grid.appendChild(div);
        });

        // Update primary card
        const primaryUrl = appState.photos[appState.primaryPhotoIndex] || appState.photos[0];
        primarySlot.innerHTML = `
          <img src="${primaryUrl}" class="w-full h-full object-cover rounded-xl" />
          <div class="absolute bottom-2 inset-x-2 bg-black/85 py-1 px-2 rounded-lg text-center text-[10px] text-amber-300 font-semibold border border-amber-500/30">
            ★ Primary Proof (Photo #${appState.primaryPhotoIndex + 1})
          </div>
        `;
        primaryCaption.innerText = `Active Proof: Photo #${appState.primaryPhotoIndex + 1} of ${count}`;
        updateMockupsPhoto(primaryUrl);
      }
      lucide.createIcons();
    }

    function setPrimaryPhoto(idx) {
      appState.primaryPhotoIndex = idx;
      renderPhotosGallery();
    }

    function removePhoto(idx) {
      appState.photos.splice(idx, 1);
      if (appState.primaryPhotoIndex >= appState.photos.length) {
        appState.primaryPhotoIndex = Math.max(0, appState.photos.length - 1);
      }
      renderPhotosGallery();
    }

    function clearAllPhotos() {
      appState.photos = [];
      appState.primaryPhotoIndex = 0;
      renderPhotosGallery();
    }

    function updateMockupsPhoto(url) {
      const slotIds = ['tshirt-portrait-slot', 'tarp-portrait-slot', 'acrylic-portrait-slot', 'sintra-portrait-slot'];
      slotIds.forEach(id => {
        const el = document.getElementById(id);
        if (el) {
          if (url) {
            el.innerHTML = `<img src="${url}" class="w-full h-full object-cover" />`;
          } else {
            el.innerHTML = `<i data-lucide="user" class="w-8 h-8 text-slate-500"></i>`;
          }
        }
      });
      lucide.createIcons();
    }

    function updateState() {
      appState.custName = document.getElementById('cust-name').value || '';
      appState.custPhone = document.getElementById('cust-phone').value || '';
      appState.custEmail = document.getElementById('cust-email').value || '';
      appState.lovedName = document.getElementById('loved-name').value || 'Juan De La Cruz';
      appState.lovedDob = document.getElementById('loved-dob').value || '';
      appState.lovedDop = document.getElementById('loved-dop').value || '';
      appState.lovedQuote = document.getElementById('loved-quote').value || '';
      appState.specialNotes = document.getElementById('special-notes').value || '';

      appState.sizes.S = parseInt(document.getElementById('size-S').value) || 0;
      appState.sizes.M = parseInt(document.getElementById('size-M').value) || 0;
      appState.sizes.L = parseInt(document.getElementById('size-L').value) || 0;
      appState.sizes.XL = parseInt(document.getElementById('size-XL').value) || 0;
      appState.sizes.XXL = parseInt(document.getElementById('size-XXL').value) || 0;
      appState.customSizeText = document.getElementById('size-custom').value || '';

      const yDob = appState.lovedDob ? new Date(appState.lovedDob).getFullYear() : 'YYYY';
      const yDop = appState.lovedDop ? new Date(appState.lovedDop).getFullYear() : 'YYYY';
      const dateStr = `${yDob} — ${yDop}`;

      // Update proof mockups text
      ['tshirt', 'tarp', 'acrylic', 'sintra'].forEach(p => {
        const nameEl = document.getElementById(p + '-proof-name');
        const datesEl = document.getElementById(p + '-proof-dates');
        if (nameEl) nameEl.innerText = appState.lovedName;
        if (datesEl) datesEl.innerText = dateStr;
      });

      const quoteElTarp = document.getElementById('tarp-proof-quote');
      const quoteElAcry = document.getElementById('acrylic-proof-quote');
      const quoteElSin = document.getElementById('sintra-proof-quote');
      if (quoteElTarp) quoteElTarp.innerText = `"${appState.lovedQuote || 'In Loving Memory & Forever in Our Hearts'}"`;
      if (quoteElAcry) quoteElAcry.innerText = `"${appState.lovedQuote || 'Forever in our hearts & thoughts'}"`;
      if (quoteElSin) quoteElSin.innerText = `"${appState.lovedQuote || 'Forever in our hearts'}"`;

      document.getElementById('summary-badge-name').innerText = appState.lovedName;

      // Update Summary Sheet
      document.getElementById('sum-cust-name').innerText = appState.custName || '—';
      document.getElementById('sum-cust-phone').innerText = appState.custPhone || '—';
      document.getElementById('sum-cust-email').innerText = appState.custEmail || '—';
      document.getElementById('sum-loved-name').innerText = appState.lovedName || '—';
      document.getElementById('sum-loved-dates').innerText = `${appState.lovedDob || 'N/A'} to ${appState.lovedDop || 'N/A'}`;
      document.getElementById('sum-loved-quote').innerText = `"${appState.lovedQuote || 'In Loving Memory'}"`;

      document.getElementById('sum-tshirt-sizes').innerText = `S:${appState.sizes.S}, M:${appState.sizes.M}, L:${appState.sizes.L}, XL:${appState.sizes.XL}, 2XL:${appState.sizes.XXL}`;
      document.getElementById('sum-tshirt-custom').innerText = appState.customSizeText || 'None specified';

      // Build Items List
      const itemsContainer = document.getElementById('sum-items-list');
      let html = '';
      let hasItems = false;

      const bundleNames = {
        1: 'Essential Memorial Package (Bundle 1 · 5 Shirts, 2.5x6ft Tarp, 22x28in Sintra)',
        2: 'Standard Memorial Package (Bundle 2 · 5 Shirts, 2.5x6ft Tarp, A4 Acrylic, 22x28in Sintra)',
        3: 'Premium Memorial Package (Bundle 3 · 5 Shirts, 2.5x6ft Tarp, A4 Acrylic, 22x28in Sintra)',
        4: 'Full Grand Chapel Package (Bundle 4 · 5 Shirts, 2.5x6ft Tarp, A4 Acrylic, 22x28in Sintra)'
      };

      for (let b = 1; b <= 4; b++) {
        if (appState.bundles[b] > 0) {
          hasItems = true;
          html += `<div class="p-2 rounded bg-slate-900 border border-slate-800 flex justify-between items-center"><span class="text-amber-400 font-semibold">${bundleNames[b]}</span><strong class="text-slate-100 bg-slate-800 px-2 py-0.5 rounded">Qty: ${appState.bundles[b]}</strong></div>`;
        }
      }

      if (appState.single.tarpaulin > 0) {
        hasItems = true;
        html += `<div class="flex justify-between items-center py-1 border-b border-slate-900"><div><span class="text-slate-200">Tarpaulin Banner</span><span class="text-[10px] text-amber-400 block">2.5 × 6 FT (76 × 183 cm)</span></div><strong class="text-amber-400">Qty: ${appState.single.tarpaulin}</strong></div>`;
      }
      if (appState.single.sintra > 0) {
        hasItems = true;
        html += `<div class="flex justify-between items-center py-1 border-b border-slate-900"><div><span class="text-slate-200">Sintra Board Display</span><span class="text-[10px] text-amber-400 block">22 × 28 INCH</span></div><strong class="text-amber-400">Qty: ${appState.single.sintra}</strong></div>`;
      }
      if (appState.single.acrylic > 0) {
        hasItems = true;
        html += `<div class="flex justify-between items-center py-1 border-b border-slate-900"><div><span class="text-slate-200">Acrylic Frame Display</span><span class="text-[10px] text-amber-400 block">A4 SIZE (210 × 297 mm)</span></div><strong class="text-amber-400">Qty: ${appState.single.acrylic}</strong></div>`;
      }
      if (appState.single.tshirt > 0) {
        hasItems = true;
        html += `<div class="flex justify-between items-center py-1 border-b border-slate-900"><div><span class="text-slate-200">Tribute T-Shirt</span></div><strong class="text-amber-400">Qty: ${appState.single.tshirt}</strong></div>`;
      }

      if (!hasItems) {
        itemsContainer.innerHTML = '<p class="text-slate-500 italic py-2">No packages or individual items selected yet.</p>';
      } else {
        itemsContainer.innerHTML = html;
      }
    }

    function buildPlainTextSpecs() {
      let body = `FUNERAL TRIBUTE DISPLAY ORDER SPECIFICATION\n`;
      body += `==============================================\n`;
      body += `Order Reference: ${appState.orderRef}\n`;
      body += `Receiving Email: sntechnoprint01@gmail.com\n\n`;

      body += `1. CUSTOMER CONTACT INFORMATION:\n`;
      body += `- Customer Name: ${appState.custName || 'Not Provided'}\n`;
      body += `- Contact Phone: ${appState.custPhone || 'Not Provided'}\n`;
      body += `- Email Address: ${appState.custEmail || 'Not Provided'}\n\n`;

      body += `2. LOVED ONE MEMORIAL PROFILE:\n`;
      body += `- Name of Deceased: ${appState.lovedName}\n`;
      body += `- Date of Birth: ${appState.lovedDob || 'N/A'}\n`;
      body += `- Date of Passing: ${appState.lovedDop || 'N/A'}\n`;
      body += `- Inscription Quote: "${appState.lovedQuote}"\n`;
      body += `- Memorial Photos: ${appState.photos.length > 0 ? `${appState.photos.length} photo(s) uploaded (Photo #${appState.primaryPhotoIndex + 1} chosen as primary proof portrait)` : 'Photo pending upload'}\n\n`;

      body += `3. OFFERS & QUANTITIES SELECTED:\n`;
      for (let b = 1; b <= 4; b++) {
        if (appState.bundles[b] > 0) {
          body += `- Package Bundle ${b}: ${appState.bundles[b]} set(s) (Includes 5x T-Shirts, 2.5x6ft Tarpaulin, 22x28in Sintra)\n`;
        }
      }
      if (appState.single.tarpaulin > 0) body += `- Single Tarpaulin Banner (2.5 x 6 ft): ${appState.single.tarpaulin} pc(s)\n`;
      if (appState.single.sintra > 0) body += `- Single Sintra Board (22 x 28 in): ${appState.single.sintra} pc(s)\n`;
      if (appState.single.acrylic > 0) body += `- Single Acrylic Frame (A4 SIZE 210x297mm): ${appState.single.acrylic} pc(s)\n`;
      if (appState.single.tshirt > 0) body += `- Single Tribute T-Shirt: ${appState.single.tshirt} pc(s)\n`;

      body += `\n4. T-SHIRT SPECIFICATIONS:\n`;
      body += `- Base Shirt Color: ${appState.shirtColor.toUpperCase()}\n`;
      body += `- Sizes: Small (${appState.sizes.S}), Medium (${appState.sizes.M}), Large (${appState.sizes.L}), XL (${appState.sizes.XL}), 2XL (${appState.sizes.XXL})\n`;
      body += `- Custom Measurements: ${appState.customSizeText || 'None specified'}\n\n`;

      if (appState.specialNotes) {
        body += `5. SPECIAL INSTRUCTIONS & NOTES:\n`;
        body += `${appState.specialNotes}\n\n`;
      }

      body += `==============================================\n`;
      body += `Generated via SN TechnoPrint Funeral Tribute Display Order Portal\n`;
      return body;
    }

    function submitOrderViaEmail() {
      const recipient = "sntechnoprint01@gmail.com";
      const subject = `[FUNERAL TRIBUTE ORDER] - ${appState.lovedName} (${appState.custName || 'Customer'}) [${appState.orderRef}]`;
      const bodyText = buildPlainTextSpecs();
      const mailtoUrl = `mailto:${recipient}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(bodyText)}`;
      window.location.href = mailtoUrl;
    }

    function copyOrderSpecs() {
      const text = buildPlainTextSpecs();
      navigator.clipboard.writeText(text).then(() => {
        const btnLabel = document.getElementById('btn-copy-label');
        btnLabel.innerText = 'Copied!';
        setTimeout(() => { btnLabel.innerText = 'Copy Specs'; }, 2500);
      });
    }
  </script>
</body>
</html>
