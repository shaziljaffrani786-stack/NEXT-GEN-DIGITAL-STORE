# NEXT-GEN-DIGITAL-STORE
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shazil Jaffrani | Digital Workspace</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'media',
            theme: { extend: {} }
        }
    </script>
    <style>
        .glass { background: rgba(255, 255, 255, 0.05); backdrop-filter: blur(10px); }
        @media (prefers-color-scheme: dark) { body { background: #0f172a; color: #f8fafc; } }
        @media (prefers-color-scheme: light) { body { background: #f8fafc; color: #0f172a; } }
    </style>
</head>
<body class="min-h-screen transition-colors duration-300">
    
    <main class="max-w-4xl mx-auto px-6 py-16">
        <header class="mb-16">
            <h1 data-gumroad-field="name" class="text-5xl font-extrabold mb-4">Loading Name...</h1>
            <p data-gumroad-field="bio" class="text-xl opacity-80 max-w-2xl"></p>
        </header>

        <section>
            <h2 class="text-2xl font-bold mb-8">Catalog</h2>
            <div id="product-grid" class="grid grid-cols-1 md:grid-cols-2 gap-6">
                </div>
        </section>
    </main>

    <script id="gumroad-data" type="application/json">
        {"products": [], "posts": [], "pages": []}
    </script>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            try {
                const dataElement = document.getElementById("gumroad-data");
                if (!dataElement || !dataElement.textContent.trim()) return;
                
                const data = JSON.parse(dataElement.textContent);
                const grid = document.getElementById("product-grid");

                if (data.products && data.products.length > 0) {
                    grid.innerHTML = data.products.map(product => `
                        <a href="${product.url}" class="glass p-6 rounded-2xl border border-white/10 hover:border-blue-500 transition-all block">
                            <h3 class="font-bold text-lg mb-2">${product.name}</h3>
                            <p class="text-sm opacity-60 mb-4">${product.description || 'Explore this resource'}</p>
                            <span class="text-blue-400 font-semibold">${product.price || 'View Details'}</span>
                        </a>
                    `).join('');
                } else {
                    grid.innerHTML = '<p class="opacity-50">No products available at the moment.</p>';
                }
            } catch (e) {
                console.error("Error loading products:", e);
            }
        });
    </script>
</body>
</html>
