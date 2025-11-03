<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Project Net-Weave Pitch Deck (v8)</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #ffffff;
            color: #1f2937;
        }
        .tab-content {
            display: none;
        }
        .tab-content.active {
            display: block;
        }
        .tab-btn {
            color: #4b5563; /* Gray */
        }
        .tab-btn.active {
            border-bottom-width: 2px;
            border-color: #2563eb; /* Blue-600 */
            color: #2563eb; /* Blue-600 */
            font-weight: 700;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 400px;
            }
        }
        .sub-tab-btn {
            background-color: #e5e7eb; /* Gray-200 */
            color: #374151; /* Gray-700 */
        }
        .sub-tab-btn.active {
            background-color: #2563eb; /* Blue-600 */
            color: #ffffff;
        }
        .hidden {
            display: none;
        }
        /* Fixed Business Model Canvas Grid */
        .bmc-grid {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            grid-template-rows: repeat(3, auto);
            gap: 0.75rem;
        }
        .bmc-block {
            background-color: #f9fafb; /* Gray-50 */
            border: 1px solid #e5e7eb; /* Gray-200 */
            padding: 1rem;
            border-radius: 0.5rem;
            height: 100%;
            display: flex;
            flex-direction: column;
        }
        .bmc-block h3 {
            font-size: 0.875rem;
            font-weight: 700;
            color: #1d4ed8; /* Blue-700 */
            margin-bottom: 0.5rem;
            text-align: center;
            text-transform: uppercase;
        }
        .bmc-block ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }
        .bmc-block li {
            font-size: 0.8rem;
            line-height: 1.4;
            color: #374151; /* Gray-700 */
            position: relative;
            padding-left: 0.75rem; /* Space for bullet */
            margin-bottom: 0.25rem;
        }
        .bmc-block li::before {
            content: '•';
            color: #2563eb; /* Blue-600 */
            position: absolute;
            left: 0;
            top: 0px; /* Aligns bullet */
            font-weight: 700;
        }
        /* BMC Grid Layout */
        .bmc-kp { grid-column: 1 / 2; grid-row: 1 / 2; }
        .bmc-ka { grid-column: 2 / 3; grid-row: 1 / 2; }
        .bmc-vp { grid-column: 3 / 4; grid-row: 1 / 3; } /* VP spans 2 rows */
        .bmc-cr { grid-column: 4 / 5; grid-row: 1 / 2; }
        .bmc-cs { grid-column: 5 / 6; grid-row: 1 / 3; } /* CS spans 2 rows */
        .bmc-kr { grid-column: 2 / 3; grid-row: 2 / 3; }
        .bmc-cc { grid-column: 4 / 5; grid-row: 2 / 3; }
        .bmc-cost { grid-column: 1 / 3; grid-row: 3 / 4; } /* Cost spans 2 cols */
        .bmc-rev { grid-column: 3 / 6; grid-row: 3 / 4; } /* Revenue spans 3 cols */
        
        /* Responsive BMC */
        @media (max-width: 768px) {
            .bmc-grid {
                grid-template-columns: 1fr;
                grid-template-rows: auto;
            }
            .bmc-kp, .bmc-ka, .bmc-vp, .bmc-cr, .bmc-cs, .bmc-kr, .bmc-cc, .bmc-cost, .bmc-rev {
                grid-column: auto;
                grid-row: auto;
            }
        }
        
        /* New Credit Simulator Styles */
        .product-card {
            background-color: #f9fafb; /* Gray-50 */
            border: 1px solid #e5e7eb; /* Gray-200 */
            border-radius: 0.5rem;
            padding: 1.5rem;
            text-align: center;
        }
        .product-card .icon {
            font-size: 3rem;
            line-height: 1;
        }
        .product-card .redeem-btn {
            background-color: #2563eb; /* Blue-600 */
            color: white;
            font-weight: 600;
            padding: 0.5rem 1rem;
            border-radius: 0.375rem;
            transition: background-color 0.2s;
        }
        .product-card .redeem-btn:hover {
            background-color: #1d4ed8; /* Blue-700 */
        }
        .product-card .redeem-btn:disabled {
            background-color: #9ca3af; /* Gray-400 */
            opacity: 0.7;
            cursor: not-allowed;
        }

    </style>
</head>
<body class="bg-white text-gray-900">

    <div class="container mx-auto px-4 py-8 max-w-7xl">

        <!-- Header -->
        <header class="text-center py-8">
            <h1 class="text-4xl md:text-5xl font-bold text-blue-700">Project Net-Weave</h1>
            <p class="mt-2 text-xl text-blue-600">Weaving a Sustainable Loop of Ocean, Community, and Capital</p>
        </header>

        <!-- Tab Navigation (NEW TAB ADDED) -->
        <nav class="sticky top-0 bg-white z-10 shadow-sm">
            <div class="flex flex-wrap justify-center border-b border-gray-200">
                <button class="tab-btn active py-4 px-6 focus:outline-none" onclick="showTab('overview')">Overview</button>
                <button class="tab-btn py-4 px-6 focus:outline-none" onclick="showTab('problem')">The Problem</button>
                <button class="tab-btn py-4 px-6 focus:outline-none" onclick="showTab('solution')">Our Solution</button>
                <button class="tab-btn py-4 px-6 focus:outline-none" onclick="showTab('credit')">The "Net-Weave" Credit</button>
                <button class="tab-btn py-4 px-6 focus:outline-none" onclick="showTab('model')">Business Model</button>
                <button class="tab-btn py-4 px-6 focus:outline-none" onclick="showTab('impact')">Our Impact</button>
                <button class="tab-btn py-4 px-6 focus:outline-none" onclick="showTab('ask')">The Ask</button>
            </div>
        </nav>

        <!-- Tab Content -->
        <main class="py-12 px-4 md:px-8">

            <!-- 1. Overview -->
            <div id="overview" class="tab-content active">
                <section class="max-w-4xl mx-auto">
                    <h2 class="text-3xl font-bold text-blue-700 mb-6 text-center">What is Net-Weave?</h2>
                    <p class="text-lg text-gray-700 mb-8 leading-relaxed">
                        Project Net-Weave is a triple-win sustainable business model. We don't just clean the ocean; we build a local ecosystem that exchanges "waste nets" for "community welfare." Fishers provide the nets, we provide high-value welfare, and we convert the nets into high-value regenerated nylon, with profits funding the entire system's sustainable operation.
                    </p>

                    <!-- Core Loop Diagram -->
                    <div class="bg-white p-6 rounded-xl shadow-lg border border-gray-200">
                        <h3 class="text-2xl font-semibold text-center text-blue-700 mb-6">The Core Value Loop (The Flywheel)</h3>
                        <div class="flex flex-col md:flex-row justify-around items-center space-y-4 md:space-y-0 md:space-x-4">
                            
                            <div class="text-center p-4 bg-blue-50 rounded-lg w-full md:w-1/4">
                                <span class="text-4xl">👨‍👩‍👧‍👦</span>
                                <h4 class="text-lg font-semibold text-blue-700 mt-2">1. Collect & Credit</h4>
                                <p class="text-sm text-gray-600">Fishers collect nets for welfare credits.</p>
                            </div>
                            
                            <div class="text-3xl font-bold text-blue-500 transform md:rotate-0 rotate-90">→</div>
                            
                            <div class="text-center p-4 bg-blue-50 rounded-lg w-full md:w-1/4">
                                <span class="text-4xl">🧵</span>
                                <h4 class="text-lg font-semibold text-blue-700 mt-2">2. B2B Sales</h4>
                                <p class="text-sm text-gray-600">Selling regenerated nylon & plastic credits.</p>
                            </div>
                            
                            <div class="text-3xl font-bold text-blue-500 transform md:rotate-0 rotate-90">→</div>
                            
                            <div class="text-center p-4 bg-blue-50 rounded-lg w-full md:w-1/4">
                                <span class="text-4xl">🛒</span>
                                <h4 class="text-lg font-semibold text-blue-700 mt-2">3. Social Return</h4>
                                <p class="text-sm text-gray-600">Profits reinvested to fund the welfare system.</p>
                            </div>
                        </div>
                        <div class="flex justify-center mt-6">
                            <div class="text-3xl font-bold text-blue-500 transform -rotate-90">↖</div>
                            <div class="px-4 text-center">
                                <h4 class="text-lg font-semibold text-blue-700">4. Flywheel Effect</h4>
                                <p class="text-sm text-gray-600">Better Welfare → Stable Supply</p>
                            </div>
                        </div>
                    </div>

                    <!-- Triple Win -->
                    <h3 class="text-2xl font-bold text-blue-700 mb-6 mt-12 text-center">The Triple Win Structure</h3>
                    <div class="grid md:grid-cols-3 gap-6">
                        <div class="bg-gray-50 p-6 rounded-xl shadow-md border border-gray-200">
                            <h4 class="text-xl font-semibold text-blue-700 mb-3">WIN 1: The Environment</h4>
                            <p class="text-gray-600">
                                Removes the deadliest "ghost nets" from the ocean, saving turtles, whales, and other marine life while reducing plastic pollution at its source.
                            </p>
                        </div>
                        <div class="bg-gray-50 p-6 rounded-xl shadow-md border border-gray-200">
                            <h4 class="text-xl font-semibold text-blue-700 mb-3">WIN 2: The Fishers</h4>
                            <p class="text-gray-600">
                                Turns waste into stable "welfare credits" redeemable for essential family needs: electricity, education, and healthcare, improving long-term quality of life.
                            </p>
                        </div>
                        <div class="bg-gray-50 p-6 rounded-xl shadow-md border border-gray-200">
                            <h4 class="text-xl font-semibold text-blue-700 mb-3">WIN 3: The Investors</h4>
                            <p class="text-gray-600">
                                Gains access to high-premium "regenerated nylon" with a powerful ESG story and generates tradable "plastic credits," achieving dual financial and sustainable returns.
                            </p>
                        </div>
                    </div>

                    <!-- NEW: Why This Bond? -->
                    <h3 class="text-2xl font-bold text-blue-700 mb-6 mt-12 text-center">Why This Bond? (The Investor Thesis)</h3>
                    <div class="grid md:grid-cols-3 gap-6">
                        <div class="bg-blue-50 p-6 rounded-xl shadow-md border border-blue-200">
                            <h4 class="text-xl font-semibold text-blue-700 mb-3">1. De-Risked & Predictable</h4>
                            <p class="text-gray-600">
                                Your return isn't just tied to the volatile nylon market. It's also secured by stable 'Plastic Credits' and 'Pay-for-Success' contracts, ensuring high predictability.
                            </p>
                        </div>
                        <div class="bg-blue-50 p-6 rounded-xl shadow-md border border-blue-200">
                            <h4 class="text-xl font-semibold text-blue-700 mb-3">2. Traceable & Auditable</h4>
                            <p class="text-gray-600">
                                100% of proceeds go to qualified, audited projects. Every ton of plastic recycled and social value generated is independently verified on our blockchain platform.
                            </p>
                        </div>
                        <div class="bg-blue-50 p-6 rounded-xl shadow-md border border-blue-200">
                            <h4 class="text-xl font-semibold text-blue-700 mb-3">3. Scalable & Profitable</h4>
                            <p class="text-gray-600">
                                A low $156k CAPEX per hub and a rapid 1.45-year payback period makes this model highly replicable, with exponential growth potential across Vietnam and Indonesia.
                            </p>
                        </div>
                    </div>
                </section>
            </div>

            <!-- 2. The Problem -->
            <div id="problem" class="tab-content">
                <section class="max-w-4xl mx-auto">
                    <h2 class="text-3xl font-bold text-blue-700 mb-6 text-center">The Problem: A Broken, High-Value Market</h2>
                    <p class="text-lg text-gray-700 mb-8 leading-relaxed">
                        640,000 tons of abandoned fishing gear ("ghost nets") are left in the ocean annually. They account for 46% of all large marine plastic debris and are the most lethal form of pollution.
                    </p>
                    <p class="text-lg text-gray-700 mb-8 leading-relaxed">
                        This is a vicious cycle of economic rationality: In remote villages in <span class="font-semibold text-blue-600">Vietnam</span>, the cost for a fisher to discard a net is zero, while the cost to bring it back is high (fuel, storage space).
                    </p>
                    <p class="text-lg text-gray-700 mb-8 leading-relaxed">
                        Meanwhile, brands like Patagonia and Adidas (many with production hubs in Vietnam) urgently need a stable, traceable supply of recycled nylon but lack a "Market Aggregator" to connect the fragmented supply.
                    </p>
                    <div class="bg-white p-6 rounded-xl shadow-lg border border-gray-200">
                        <h3 class="text-2xl font-semibold text-center text-blue-700 mb-6">Share of Large Marine Plastic Debris</h3>
                        <div class="chart-container">
                            <canvas id="problemChart"></canvas>
                        </div>
                    </div>
                </section>
            </div>

            <!-- 3. The Solution (FIXED LAYOUT) -->
            <div id="solution" class="tab-content">
                <section class="max-w-5xl mx-auto">
                    <h2 class="text-3xl font-bold text-blue-700 mb-6 text-center">Our Solution: The Net-Weave Community Hub</h2>
                    <p class="text-lg text-gray-700 mb-8 leading-relaxed text-center max-w-3xl mx-auto">
                        Our core infrastructure is the "Net-Weave Hub," an all-in-one physical center in coastal <span class="font-semibold text-blue-600">Vietnam</span> that integrates collection, energy, and welfare. This is the engine of our operation.
                    </p>
                    
                    <!-- Hub Components (FIXED) -->
                    <div class="grid md:grid-cols-3 gap-6 mb-12">
                        <div class="bg-gray-50 p-6 rounded-xl shadow-lg border border-gray-200 text-center">
                            <span class="text-5xl">🏦</span>
                            <h3 class="text-2xl font-semibold text-blue-700 my-3">The "Bank" (Collection)</h3>
                            <p class="text-gray-600">Collects, sorts, cleans, weighs, shreds, and bales waste nets. Critically, it separates high-value "Nylon 6".</p>
                        </div>
                        <div class="bg-gray-50 p-6 rounded-xl shadow-lg border border-gray-200 text-center">
                            <span class="text-5xl">☀️</span>
                            <h3 class="text-2xl font-semibold text-blue-700 my-3">The "Power" (Energy)</h3>
                            <p class="text-gray-600">A solar microgrid providing battery swaps, phone charging, and services to solve "energy poverty".</p>
                        </div>
                        <div class="bg-gray-50 p-6 rounded-xl shadow-lg border border-gray-200 text-center">
                            <span class="text-5xl">🛒</span>
                            <h3 class="text-2xl font-semibold text-blue-700 my-3">The "Store" (Welfare)</h3>
                            <p class="text-gray-600">The credit redemption center. This is where our "Net-Weave Credits" are used to access goods and services.</p>
                        </div>
                    </div>
                </section>
            </div>

            <!-- 4. NEW Credit Simulator Tab -->
            <div id="credit" class="tab-content">
                <section class="max-w-6xl mx-auto">
                    <h2 class="text-3xl font-bold text-blue-700 mb-6 text-center">The "Net-Weave" Credit Simulator</h2>
                    <p class="text-lg text-gray-700 mb-8 leading-relaxed text-center max-w-3xl mx-auto">
                        This is the engine of our social impact. See for yourself how 'waste' is transformed into 'welfare'. Our blockchain-backed system ensures every transaction is traceable, auditable, and locked to human capital.
                    </p>
                    <div class="grid md:grid-cols-12 gap-8">
                        <!-- Left Column: Calculator -->
                        <div class="md:col-span-4 bg-gray-50 p-6 rounded-xl shadow-lg border border-gray-200">
                            <h3 class="text-2xl font-semibold text-blue-700 mb-4">1. Calculate Credits</h3>
                            <div class="mb-4">
                                <label for="netWeightInput" class="block text-sm font-medium text-gray-700 mb-1">Enter Net Weight (kg)</label>
                                <input type="number" id="netWeightInput" placeholder="e.g., 20" class="w-full px-4 py-2 border border-gray-300 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 text-lg">
                            </div>
                            <button id="calculateCreditsBtn" class="bg-blue-600 text-white font-bold py-3 px-6 rounded-full text-lg shadow-lg hover:bg-blue-700 transition duration-300 w-full mb-4">
                                Calculate Credits
                            </button>
                            <hr class="border-gray-300">
                            <div class="mt-4 text-center">
                                <p class="text-lg text-gray-600">Your Credit Balance:</p>
                                <p id="creditBalance" class="text-5xl font-bold text-blue-700">0</p>
                                <p class="text-xs text-gray-500 mt-2">(Rate: 1 kg Net = 15 Credits)</p>
                            </div>
                        </div>

                        <!-- Right Column: Store -->
                        <div class="md:col-span-8">
                            <h3 class="text-2xl font-semibold text-blue-700 mb-4">2. Redeem at the Community Store</h3>
                            <div class="grid grid-cols-2 md:grid-cols-3 gap-4">
                                <!-- Rice -->
                                <div class="product-card">
                                    <div class="icon">🍚</div>
                                    <h4 class="text-lg font-semibold text-gray-800 mt-2">Rice (1kg)</h4>
                                    <p class="text-gray-600 font-bold text-blue-600">300 Credits</p>
                                    <button class="redeem-btn mt-4" data-cost="300" onclick="redeemItem(300)">Redeem</button>
                                </div>
                                <!-- Eggs -->
                                <div class="product-card">
                                    <div class="icon">🥚</div>
                                    <h4 class="text-lg font-semibold text-gray-800 mt-2">Eggs (Dozen)</h4>
                                    <p class="text-gray-600 font-bold text-blue-600">250 Credits</p>
                                    <button class="redeem-btn mt-4" data-cost="250" onclick="redeemItem(250)">Redeem</button>
                                </div>
                                <!-- Phone Charge -->
                                <div class="product-card">
                                    <div class="icon">🔋</div>
                                    <h4 class="text-lg font-semibold text-gray-800 mt-2">Phone Charge</h4>
                                    <p class="text-gray-600 font-bold text-blue-600">25 Credits</p>
                                    <button class="redeem-btn mt-4" data-cost="25" onclick="redeemItem(25)">Redeem</button>
                                </div>
                                <!-- Health Insurance -->
                                <div class="product-card">
                                    <div class="icon">❤️</div>
                                    <h4 class="text-lg font-semibold text-gray-800 mt-2">Health Insurance (1-Mo)</h4>
                                    <p class="text-gray-600 font-bold text-blue-600">1500 Credits</p>
                                    <button class="redeem-btn mt-4" data-cost="1500" onclick="redeemItem(1500)">Redeem</button>
                                </div>
                                <!-- School Fees -->
                                <div class="product-card">
                                    <div class="icon">🎓</div>
                                    <h4 class="text-lg font-semibold text-gray-800 mt-2">School Fees (1 Term)</h4>
                                    <p class="text-gray-600 font-bold text-blue-600">3000 Credits</G                                    <button class="redeem-btn mt-4" data-cost="3000" onclick="redeemItem(3000)">Redeem</button>
                                </div>
                                <!-- Skills Course -->
                                <div class="product-card">
                                    <div class="icon">🔧</div>
                                    <h4 class="text-lg font-semibold text-gray-800 mt-2">Mechanics Course</h4>
                                    <p class="text-gray-600 font-bold text-blue-600">5000 Credits</p>
                                    <button class="redeem-btn mt-4" data-cost="5000" onclick="redeemItem(5000)">Redeem</button>
                                </div>
                            </div>
                        </div>
                    </div>
                </section>
            </div>


            <!-- 5. Business Model (FIXED LAYOUT) -->
            <div id="model" class="tab-content">
                <section class="max-w-6xl mx-auto">
                    <h2 class="text-3xl font-bold text-blue-700 mb-8 text-center">Business Model Canvas</h2>
                    <div class="bmc-grid">
                        <div class="bmc-block bmc-kp">
                            <h3>8. Key Partners</h3>
                            <ul>
                                <li>Fishers & Co-ops (Vietnam)</li>
                                <li>Regeneration Plants (Aquafil)</li>
                                <li>Blockchain Developers</li>
                                <li>Bond Investors (You)</li>
                            </ul>
                        </div>
                        <div class="bmc-block bmc-ka">
                            <h3>7. Key Activities</h3>
                            <ul>
                                <li>Collect, Sort, Process</li>
                                <li>Manage Blockchain (Trust)</li>
                                <li>Secure B2B Contracts</li>
                                <li>Operate Credit Exchange</li>
                            </ul>
                        </div>
                        <div class="bmc-block bmc-vp bg-blue-100 border-blue-200">
                            <h3>2. Value Proposition</h3>
                            <ul>
                                <li><b class="text-blue-700">Brands:</b> Stable, Traceable Nylon 6</li>
                                <li><b class="text-blue-700">Corps:</b> Auditable Plastic Credits</li>
                                <li><b class="text-blue-700">Fishers:</b> Waste-to-Welfare Credits (Health, Edu, Energy)</li>
                            </ul>
                        </div>
                        <div class="bmc-block bmc-cr">
                            <h3>4. Customer Relationships</h3>
                            <ul>
                                <li>B2B: Long-term Contracts, Co-Branding, Transparency</li>
                                <li>Fishers: Community Trust</li>
                            </ul>
                        </div>
                        <div class="bmc-block bmc-cs">
                            <h3>1. Customer Segments</h3>
                            <ul>
                                <li>B2B Material Clients (Patagonia, Adidas)</li>
                                <li>B2B Impact Clients (FMCG, Corps)</li>
                            </ul>
                        </div>
                        <div class="bmc-block bmc-kr">
                            <h3>6. Key Resources</h3>
                            <ul>
                                <li>Community Hubs (Infra.)</li>
                                <li>Blockchain Platform (Trust)</li>
                                <li>B2B Contracts</li>
                            </ul>
                        </div>
                        <div class="bmc-block bmc-cc">
                            <h3>3. Channels</h3>
                            <ul>
                                <li>B2B Direct Sales Team</li>
                                <li>Credit Registries (Verra)</li>
                                <li>Community Hubs</li>
                            </ul>
                        </div>
                        <div class="bmc-block bmc-cost">
                            <h3>9. Cost Structure</h3>
                            <ul>
                                <li>CAPEX: Hubs, Microgrids, Blockchain</li>
                                <li>OPEX: Logistics (critical), Staff, Verra Fees</li>
                                <li>COGS: Credits-for-Nets</li>
                            </ul>
                        </div>
                        <div class="bmc-block bmc-rev">
                            <h3>5. Revenue Streams</h3>
                            <ul>
                                <li>1. Nylon 6 Sales (Core)</li>
                                <li>2. HDPE/PP Sales (Secondary)</li>
                                <li>3. Plastic Credit Sales (Impact)</li>
                                <li class="text-blue-600 font-medium">Risk Hedge: (1+2) vs (3)</li>
                            </ul>
                        </div>
                    </div>
                </section>
            </div>

            <!-- 6. Impact -->
            <div id="impact" class="tab-content">
                <section class="max-w-5xl mx-auto">
                    <h2 class="text-3xl font-bold text-blue-700 mb-6 text-center">Our Impact: A Dual Return</h2>
                    
                    <!-- Sub-tab Navigation (FIXED) -->
                    <div class="flex justify-center mb-8">
                        <button class="sub-tab-btn active py-2 px-6 rounded-l-full focus:outline-none" onclick="showSubTab('sustainability')">Sustainable Impact</button>
                        <button class="sub-tab-btn py-2 px-6 rounded-r-full focus:outline-none" onclick="showSubTab('financials')">Financial Return</button>
                    </div>

                    <!-- Sustainability Sub-content -->
                    <div id="sustainability" class="sub-tab-content active">
                        <div class="grid md:grid-cols-2 gap-8 items-center">
                            <div>
                                <h3 class="text-2xl font-semibold text-blue-700 mb-4">Environmental Impact (SDG 14, 12)</h3>
                                <ul class="list-disc list-inside text-gray-700 space-y-2 mb-6">
                                    <li>150+ Tons of ghost nets removed (per hub/year)</li>
                                    <li>~600 Tons CO2e mitigated (vs. virgin nylon)</li>
                                    <li>Protects turtles, whales, and marine life.</li>
                                </ul>
                                <h3 class="text-2xl font-semibold text-blue-700 mb-4">Social Impact (SDG 1, 3, 4, 7)</h3>
                                <ul class="list-disc list-inside text-gray-700 space-y-2">
                                    <li>300+ fishing families supported (per hub)</li>
                                    <li>Provides stable electricity, healthcare, & education access.</li>
                                    <li>+63.3% child study time (due to electricity).</li>
                                    <li>5 full-time local "green jobs" (per hub).</li>
                                </ul>
                            </div>
                            <div class="bg-white p-6 rounded-xl shadow-lg border border-gray-200">
                                <h3 class="text-xl font-semibold text-center text-blue-700 mb-4">Key SDG Contributions</h3>
                                <div class="chart-container" style="height: 300px; max-height: 300px;">
                                    <canvas id="sdgChart"></canvas>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Financials Sub-content -->
                    <div id="financials" class="sub-tab-content">
                        <h3 class="text-2xl font-semibold text-blue-700 mb-4 text-center">Financial Return & Projections</h3>
                        <p class="text-center text-gray-600 mb-8 max-w-3xl mx-auto">Our model is designed to be profitable, scalable, and robust. It is supported by three revenue streams, a low CAPEX per-hub, and a crucial risk hedge.</p>
                        
                        <!-- Risk Hedge -->
                        <h4 class="text-xl font-semibold text-blue-700 mb-4">Key Financial Innovation: Risk Hedge</h4>
                        <div class="grid md:grid-cols-2 gap-6 mb-8">
                            <div class="bg-gray-50 p-6 rounded-lg border border-gray-200">
                                <h5 class="font-semibold text-gray-800">A. B2B Physical Revenue</h5>
                                <p class="text-sm text-gray-600">(Regen Plastics) From Nylon 6/HDPE sales. This revenue is linked to "Crude Oil" prices, offering commodity upside but also volatility.</p>
                            </div>
                            <div class="bg-gray-50 p-6 rounded-lg border border-gray-200">
                                <h5 class="font-semibold text-gray-800">B. B2B Impact Revenue</h5>
                                <p class="text-sm text-gray-600">(Plastic Credits) From certified collection (Verra). This revenue is linked to "Corporate ESG Commitments," offering stable, non-correlated pricing.</p>
                            </div>
                        </div>

                        <!-- Financial Projections -->
                        <h4 class="text-xl font-semibold text-blue-700 mb-4">Financial Projections (Per Hub)</h4>
                        <div class="grid md:grid-cols-3 gap-6 mb-8">
                            <!-- CAPEX -->
                            <div class="bg-gray-50 p-6 rounded-lg border border-gray-200">
                                <h5 class="font-semibold text-gray-800 mb-3">CAPEX (Initial Investment)</h5>
                                <table class="w-full text-left text-sm">
                                    <tbody class="divide-y divide-gray-200">
                                        <tr><td class="py-1">Recycle Equipment</td><td class="py-1 text-right">$20,000</td></tr>
                                        <tr><td class="py-1">Energy Facility (50kW)</td><td class="py-1 text-right">$75,000</td></tr>
                                        <tr><td class="py-1">Infrastructure</td><td class="py-1 text-right">$30,000</td></tr>
                                        <tr><td class="py-1">Tech Integration</td><td class="py-1 text-right">$5,000</td></tr>
                                        <tr><td class="py-1">Contingency (20%)</td><td class="py-1 text-right">$26,000</td></tr>
                                        <tr class="font-semibold text-blue-700"><td class="py-1 pt-2">Total CAPEX</td><td class="py-1 pt-2 text-right">$156,000</td></tr>
                                    </tbody>
                                </table>
                            </div>
                            <!-- OPEX -->
                            <div class="bg-gray-50 p-6 rounded-lg border border-gray-200">
                                <h5 class="font-semibold text-gray-800 mb-3">OPEX (Annual Costs)</h5>
                                <table class="w-full text-left text-sm">
                                    <tbody class="divide-y divide-gray-200">
                                        <tr><td class="py-1">Raw Materials (COGS)</td><td class="py-1 text-right">$82,650</td></tr>
                                        <tr><td class="py-1">Logistics (Vietnam)</td><td class="py-1 text-right">$19,887</td></tr>
                                        <tr><td class="py-1">Staff (5 local)</td><td class="py-1 text-right">$25,000</td></tr>
                                        <tr><td class="py-1">Social Welfare (Profit Share)</td><td class="py-1 text-right">$7,200</td></tr>
                                        <tr><td class="py-1">Maintenance & Fees</td><td class="py-1 text-right">$15,000</td></tr>
                                        <tr class="font-semibold text-blue-700"><td class="py-1 pt-2">Total OPEX</td><td class="py-1 pt-2 text-right">$149,737</td></tr>
                                    </tbody>
                                </table>
                            </div>
                            <!-- P&L -->
                            <div class="bg-blue-50 p-6 rounded-lg border border-blue-200">
                                <h5 class="font-semibold text-gray-800 mb-3">Year 1 P&L (Conservative)</h5>
                                <table class="w-full text-left text-sm">
                                    <tbody class="divide-y divide-gray-300">
                                        <tr><td class="py-1">Revenue (Nylon 6)</td><td class="py-1 text-right">$160,200</td></tr>
                                        <tr><td class="py-1">Revenue (HDPE/PP)</td><td class="py-1 text-right">$59,880</td></tr>
                                        <tr><td class="py-1">Revenue (Plastic Credits)</td><td class="py-1 text-right">$37,500</td></tr>
                                        <tr class="font-semibold"><td class="py-1 pt-2">Total Revenue</td><td class="py-1 pt-2 text-right">$257,580</td></tr>
                                        <tr class="text-red-600"><td class="py-1">Total OPEX</td><td class="py-1 text-right">($149,737)</td></tr>
                                        <tr class="font-semibold text-blue-700 text-base"><td class="py-1 pt-2">EBITDA</td><td class="py-1 pt-2 text-right">$107,843</td></tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>

                        <!-- Summary -->
                        <h4 class="text-xl font-semibold text-blue-700 mb-4 mt-8">Investment Return Summary (Per Hub)</h4>
                        <div class="grid md:grid-cols-3 gap-6 text-center">
                            <div class="bg-white p-6 rounded-lg shadow-lg border border-gray-200">
                                <h5 class="text-lg font-semibold text-gray-700">EBITDA Margin</h5>
                                <p class="text-4xl font-bold text-blue-600">41.8%</p>
                            </div>
                            <div class="bg-white p-6 rounded-lg shadow-lg border border-gray-200">
                                <h5 class="text-lg font-semibold text-gray-700">Payback Period</h5>
                                <p class="text-4xl font-bold text-blue-600">1.45 Years</p>
                            </div>
                            <div class="bg-white p-6 rounded-lg shadow-lg border border-gray-200">
                                <h5 class="text-lg font-semibold text-gray-700">5-Year IRR (Project)</h5>
                                <p class="text-4xl font-bold text-blue-600">65.2%</p>
                            </div>
                        </div>

                        <!-- Chart -->
                        <div class="bg-white p-6 rounded-xl shadow-lg border border-gray-200 mt-8">
                            <h3 class="text-xl font-semibold text-center text-blue-700 mb-4">5-Year Revenue Projection (Per Hub)</h3>
                            <div class="chart-container">
                                <canvas id="financialsChart"></canvas>
                            </div>
                        </div>

                    </div>
                </section>
            </div>

            <!-- 7. The Ask (REMOVED AI, ADDED CALC) -->
            <div id="ask" class="tab-content">
                <section class="max-w-5xl mx-auto text-center">
                    <h2 class="text-3xl font-bold text-blue-700 mb-6">The Ask: Our Inaugural Marine Sustainability Bond</h2>
                    <p class="text-xl text-gray-700 mb-8 leading-relaxed max-w-3xl mx-auto">
                        We are skipping the seed round and moving directly to scale. We are officially issuing a <span class="font-semibold text-blue-600 text-2xl">$2,000,000 USD</span> "Net-Weave Marine Sustainability Bond" to build our first hubs in <span class="font-semibold text-blue-600">Vietnam</span>.
                    </p>
                    
                    <div class="bg-white p-8 rounded-xl shadow-lg border border-gray-200 text-left">
                        <h3 class="text-2xl font-semibold text-blue-700 mb-2 text-center">The "Impact Bond" Structure (A 4-Party Model)</h3>
                        <p class="text-lg text-gray-600 mb-6 text-center">
                            This is a "Pay-for-Success" contract. The investor return is not solely dependent on our profit, but is additionally tied to our sustainable outcomes.
                        </p>

                        <div class="grid md:grid-cols-4 gap-4 mb-6 text-center">
                            <div class="bg-gray-50 p-4 rounded-lg border border-gray-200">
                                <span class="text-3xl">🚀</span>
                                <h5 class="font-semibold text-gray-700 mt-1">1. The Operator (Us)</h5>
                                <p class="text-sm text-gray-600">Builds & operates the hubs, delivers on impact goals.</p>
                            </div>
                            <div class="bg-blue-50 p-4 rounded-lg border border-blue-200">
                                <span class="text-3xl">💼</span>
                                <h5 class="font-semibold text-blue-700 mt-1">2. The Investors (You)</h5>
                                <p class="text-sm text-gray-600">Provides the $2M upfront capital to launch.</p>
                            </div>
                            <div class="bg-blue-50 p-4 rounded-lg border border-blue-200">
                                <span class="text-3xl">🌍</span>
                                <h5 class="font-semibold text-blue-700 mt-1">3. The Outcome Payer</h5>
                                <p class="text-sm text-gray-600">A corporation that commits to paying a "success bonus" if goals are met.</p>
                            </div>
                            <div class="bg-blue-50 p-4 rounded-lg border border-blue-200">
                                <span class="text-3xl">🧐</span>
                                <h5 class="font-semibold text-blue-700 mt-1">4. The Verifier</h5>
                                <p class="text-sm text-gray-600">An independent auditor who verifies the outcomes.</p>
                            </div>
                        </div>
                        
                        <h4 class="text-xl font-semibold text-gray-800 mt-6 mb-4">The Investor's "Dual Return" Structure:</h4>
                        <div class="grid md:grid-cols-2 gap-4">
                            <div class="bg-blue-50 p-4 rounded-lg border border-blue-200">
                                <h5 class="font-semibold text-blue-700">A. Financial Return (Variable)</h5>
                                <p class="text-sm text-gray-600">From the profit share of our "Regen Nylon" B2B sales.</p>
                            </div>
                            <div class="bg-blue-50 p-4 rounded-lg border border-blue-200">
                                <h5 class="font-semibold text-blue-700">B. Impact Return (Fixed)</h5>
                                <p class="text-sm text-gray-600">The "success bonus" paid by the Outcome Payer, de-risking the investment.</p>
                            </div>
                        </div>
                    </div>

                    <!-- Investment Calculator -->
                    <div class="mt-16 border-t pt-12 border-gray-300">
                        <h3 class="text-2xl font-semibold text-blue-700 mb-4">Investment Return Calculator</h3>
                        <p class="text-lg text-gray-600 mb-6 max-w-2xl mx-auto">Simulate your potential return based on a 5-year bond term and a projected 6.5% blended annual return (fixed coupon + variable profit share).</p>
                        
                        <div class="bg-gray-50 p-8 rounded-xl shadow-lg border border-gray-200 max-w-lg mx-auto">
                            <div class="mb-4">
                                <label for="investmentInput" class="block text-sm font-medium text-gray-700 text-left mb-1">Enter Your Investment Amount (USD)</label>
                                <input type="number" id="investmentInput" placeholder="e.g., 50000" class="w-full px-4 py-2 border border-gray-300 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 text-lg">
                            </div>
                            <button id="calculateBtn" class="bg-blue-600 text-white font-bold py-3 px-8 rounded-full text-lg shadow-lg hover:bg-blue-700 transition duration-300 w-full">
                                Calculate Return
                            </button>
                            <div id="calculatorResult" class="mt-6 text-left hidden">
                                <hr class="mb-4 border-gray-300">
                                <div class="flex justify-between items-center mb-2">
                                    <span class="text-lg text-gray-600">Projected Annual Return (~6.5%):</span>
                                    <span id="annualReturn" class="text-2xl font-semibold text-blue-700">$0.00</span>
                                </div>
                                <div class="flex justify-between items-center bg-blue-50 p-4 rounded-lg">
                                    <span class="text-lg text-gray-700 font-semibold">Total Value (after 5 Years):</span>
                                    <span id="totalValue" class="text-3xl font-bold text-blue-700">$0.00</span>
                                </div>
                                <p class="text-xs text-gray-500 mt-4 text-center">This is an illustrative projection, not a guarantee of future returns. The variable portion is dependent on project performance.</p>
                            </div>
                        </div>
                    </div>

                </section>
            </div>

        </main>
    </div>

    <script>
        const tabBtns = document.querySelectorAll('.tab-btn');
        const tabContents = document.querySelectorAll('.tab-content');
        const subTabBtns = document.querySelectorAll('.sub-tab-btn');
        const subTabContents = document.querySelectorAll('.sub-tab-content');
        
        let problemChart = null;
        let sdgChart = null;
        let financialsChartInstance = null;
        let currentCreditBalance = 0;

        const financialsData = {
            conservative: {
                labels: ['Year 1', 'Year 2', 'Year 3', 'Year 4', 'Year 5'],
                datasets: [
                    {
                        label: 'Regen Nylon (Nylon 6)', // 62%
                        data: [160200, 176220, 193842, 213226, 234549],
                        backgroundColor: '#2563eb', // Blue-600
                    },
                    {
                        label: 'Other Plastics (HDPE/PP)', // 23%
                        data: [59880, 65868, 72455, 79700, 87670],
                        backgroundColor: '#60a5fa', // Blue-400
                    },
                    {
                        label: 'Plastic Credits', // 15%
                        data: [37500, 41250, 45375, 49913, 54904],
                        backgroundColor: '#93c5fd', // Blue-300
                    }
                ]
            }
        };
        
        const creditStoreItems = [
            { id: 1, name: 'Rice (1kg)', cost: 300, icon: '🍚' },
            { id: 2, name: 'Eggs (Dozen)', cost: 250, icon: '🥚' },
            { id: 3, name: 'Phone Charge', cost: 25, icon: '🔋' },
            { id: 4, name: 'Health Insurance (1-Mo)', cost: 1500, icon: '❤️' },
            { id: 5, name: 'School Fees (1 Term)', cost: 3000, icon: '🎓' },
            { id: 6, name: 'Mechanics Course', cost: 5000, icon: '🔧' }
        ];

        function wrapText(text, maxChars) {
            const words = text.split(' ');
            let lines = [];
            let currentLine = '';
            words.forEach(word => {
                if (currentLine.length + word.length <= maxChars) {
                    currentLine += word + ' ';
                } else {
                    lines.push(currentLine.trim());
                    currentLine = word + ' ';
                }
            });
            lines.push(currentLine.trim());
            return lines;
        }

        const chartOptions = {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                legend: {
                    position: 'bottom',
                },
                tooltip: {
                    callbacks: {
                        label: function(context) {
                            let label = context.dataset.label || '';
                            if (label) {
                                label += ': ';
                            }
                            if (context.parsed.y !== null) {
                                label += new Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD', minimumFractionDigits: 0 }).format(context.parsed.y);
                            }
                            return wrapText(label, 16);
                        }
                    }
                }
            },
            scales: {
                x: {
                    stacked: true,
                },
                y: {
                    stacked: true,
                    ticks: {
                        callback: function(value) {
                            return '$' + (value / 1000) + 'k';
                        }
                    }
                }
            }
        };

        function showTab(tabId) {
            tabContents.forEach(content => content.classList.remove('active'));
            tabBtns.forEach(btn => btn.classList.remove('active'));
            document.getElementById(tabId).classList.add('active');
            document.querySelector(`.tab-btn[onclick="showTab('${tabId}')"]`).classList.add('active');
        }

        function showSubTab(subTabId) {
            subTabContents.forEach(content => content.classList.remove('active'));
            subTabBtns.forEach(btn => btn.classList.remove('active'));
            document.getElementById(subTabId).classList.add('active');
            document.querySelector(`.sub-tab-btn[onclick="showSubTab('${subTabId}')"]`).classList.add('active');
        }

        function initFinancialsChart(scenario) {
            const ctx = document.getElementById('financialsChart');
            if (!ctx) return;
            if (financialsChartInstance) financialsChartInstance.destroy();
            financialsChartInstance = new Chart(ctx.getContext('2d'), {
                type: 'bar',
                data: financialsData[scenario],
                options: chartOptions
            });
        }

        function initProblemChart() {
            const ctx = document.getElementById('problemChart');
            if (!ctx) return;
            if (problemChart) problemChart.destroy();
            problemChart = new Chart(ctx.getContext('2d'), {
                type: 'bar',
                data: {
                    labels: ['Ghost Nets', 'Bottles & Cans', 'Plastic Bags', 'Straws & Cutlery'],
                    datasets: [{
                        label: 'Share of Large Marine Plastic Debris',
                        data: [46, 12, 10, 5],
                        backgroundColor: [
                            '#dc2626', // Red-600 (Highlight)
                            '#9ca3af', // Gray-400
                            '#9ca3af',
                            '#9ca3af',
                        ],
                        borderColor: '#ffffff',
                        borderWidth: 1
                    }]
                },
                options: {
                    indexAxis: 'y',
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            display: false
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return context.parsed.x + '%';
                                }
                            }
                        }
                    },
                    scales: {
                        x: {
                            ticks: {
                                callback: function(value) {
                                    return value + '%';
                                }
                            }
                        }
                    }
                }
            });
        }

        function initSdgChart() {
            const ctx = document.getElementById('sdgChart');
            if (!ctx) return;
            if (sdgChart) sdgChart.destroy();
            sdgChart = new Chart(ctx.getContext('2d'), {
                type: 'doughnut',
                data: {
                    labels: [
                        'SDG 14: Life Below Water',
                        'SDG 7: Clean Energy',
                        'SDG 1: No Poverty',
                        'SDG 4: Quality Education',
                        'SDG 8: Decent Work'
                    ],
                    datasets: [{
                        data: [40, 20, 15, 15, 10],
                        backgroundColor: [
                            '#0284c7', // Sky-600
                            '#0ea5e9', // Sky-500
                            '#3b82f6', // Blue-500
                            '#60a5fa', // Blue-400
                            '#93c5fd'  // Blue-300
                        ]
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom',
                            labels: {
                                boxWidth: 12
                            }
                        }
                    }
                }
            });
        }
        
        // Investment Calculator Logic
        function calculateReturn() {
            const inputEl = document.getElementById('investmentInput');
            const resultEl = document.getElementById('calculatorResult');
            const annualEl = document.getElementById('annualReturn');
            const totalEl = document.getElementById('totalValue');

            const amount = parseFloat(inputEl.value);
            
            if (isNaN(amount) || amount <= 0) {
                resultEl.classList.add('hidden');
                return;
            }

            const annualReturnRate = 0.065; // 6.5%
            const years = 5;
            
            const annualReturn = amount * annualReturnRate;
            const totalValue = amount + (annualReturn * years);

            const currencyFormat = { style: 'currency', currency: 'USD', minimumFractionDigits: 0, maximumFractionDigits: 0 };
            
            annualEl.innerText = annualReturn.toLocaleString('en-US', currencyFormat);
            totalEl.innerText = totalValue.toLocaleString('en-US', currencyFormat);
            
            resultEl.classList.remove('hidden');
        }
        
        // Credit Simulator Logic
        const creditBalanceEl = document.getElementById('creditBalance');
        const netWeightInputEl = document.getElementById('netWeightInput');
        const calculateCreditsBtn = document.getElementById('calculateCreditsBtn');
        const redeemBtns = document.querySelectorAll('.redeem-btn');

        function calculateCredits() {
            const weight = parseFloat(netWeightInputEl.value) || 0;
            currentCreditBalance = Math.floor(weight * 15); // 1kg = 15 credits
            creditBalanceEl.textContent = currentCreditBalance;
            updateRedeemButtons();
        }

        function redeemItem(cost) {
            if (currentCreditBalance >= cost) {
                currentCreditBalance -= cost;
                creditBalanceEl.textContent = currentCreditBalance;
                updateRedeemButtons();
                alert("Redemption successful!");
            } else {
                // This alert is redundant due to disabled button, but good fallback.
                alert("Not enough credits!");
            }
        }

        function updateRedeemButtons() {
            redeemBtns.forEach(btn => {
                const cost = parseInt(btn.getAttribute('data-cost'));
                if (currentCreditBalance >= cost) {
                    btn.disabled = false;
                    btn.classList.remove('opacity-70', 'cursor-not-allowed', 'bg-gray-400');
                    btn.classList.add('bg-blue-600', 'hover:bg-blue-700');
                } else {
                    btn.disabled = true;
                    btn.classList.add('opacity-70', 'cursor-not-allowed', 'bg-gray-400');
                    btn.classList.remove('bg-blue-600', 'hover:bg-blue-700');
                }
            });
        }

        // --- Event Listeners (FIXED) ---
        tabBtns.forEach(btn => {
            btn.addEventListener('click', () => showTab(btn.getAttribute('onclick').match(/'(.*?)'/)[1]));
        });

        subTabBtns.forEach(btn => {
            btn.addEventListener('click', () => showSubTab(btn.getAttribute('onclick').match(/'(.*?)'/)[1]));
        });

        document.getElementById('calculateBtn').addEventListener('click', calculateReturn);
        calculateCreditsBtn.addEventListener('click', calculateCredits);

        // Call init on window load to fix chart bugs
        window.onload = () => {
            initProblemChart();
            initSdgChart();
            initFinancialsChart('conservative');
            updateRedeemButtons(); // Initialize redeem buttons to disabled state
        };
    </script>
</body>
</html>
