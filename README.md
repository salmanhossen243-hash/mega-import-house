# mega-import-house
React-based e-commerce website showcasing trending imported products like fashion, skin care, and gadgets with WhatsApp order integration.
import { useState } from "react";
import { Card, CardContent } from "./components/ui/Card";
import { Button } from "./components/ui/Button";
import { ShoppingCart, CheckCircle } from "lucide-react";
import { motion } from "framer-motion";

export default function MegaImportHouse() {
  const allProducts = [
    // Gadgets
    { name: "Smart LED Watch - Xiaomi", category: "Gadgets", price: "2,500 BDT", img: "https://images.unsplash.com/photo-1511707171634-5f897ff02aa9", deal: true },
    { name: "Wireless Earbuds Pro - Redmi", category: "Gadgets", price: "3,800 BDT", img: "https://images.unsplash.com/photo-1585386959984-a41552231693" },
    { name: "Mini Portable Blender - Joyoung", category: "Gadgets", price: "2,200 BDT", img: "https://images.unsplash.com/photo-1590080876908-73f7b7c6c1c0" },
    { name: "Smartphone G12 - Huawei", category: "Gadgets", price: "12,500 BDT", img: "https://images.unsplash.com/photo-1510557880182-3f2c9c7b6c6b", deal: true },

    // Skin Care
    { name: "Organic Face Serum - Inoherb", category: "Skin Care", price: "1,200 BDT", img: "https://images.unsplash.com/photo-1612810806680-3b1eaa9a2cfe" },
    { name: "Hydrating Face Mask - Bioaqua", category: "Skin Care", price: "800 BDT", img: "https://images.unsplash.com/photo-1600185365535-1c6b6f0d72e4" },
    { name: "Vitamin C Cream - Herborist", category: "Skin Care", price: "1,500 BDT", img: "https://images.unsplash.com/photo-1612831455545-2d7f7bfa9fa3", deal: true },

    // Fashion
    { name: "Trendy Summer T-Shirt - Shein", category: "Fashion", price: "900 BDT", img: "https://images.unsplash.com/photo-1521572163474-6864f9cf17ab" },
    { name: "Stylish Hoodie - Zara", category: "Fashion", price: "1,800 BDT", img: "https://images.unsplash.com/photo-1586190848861-99aa4a171e90" },
    { name: "Elegant Dress - Mango", category: "Fashion", price: "2,500 BDT", img: "https://images.unsplash.com/photo-1520975693477-2f1d9ef3b8a0" },

    // Electronics
    { name: "Portable Speaker - Anker", category: "Electronics", price: "3,000 BDT", img: "https://images.unsplash.com/photo-1585386959985-7a41662231693" },
    { name: "LED Desk Lamp - Xiaomi", category: "Electronics", price: "1,200 BDT", img: "https://images.unsplash.com/photo-1593642634367-d91a135587b5" },
    { name: "Smart Home Camera - Xiaomi", category: "Electronics", price: "4,500 BDT", img: "https://images.unsplash.com/photo-1583225156410-dcbf9c2f8d17", deal: true },

    // Accessories
    { name: "Wireless Charger - Baseus", category: "Accessories", price: "1,500 BDT", img: "https://images.unsplash.com/photo-1593754508335-3b92db5b0eb0" },
    { name: "Smart Bracelet - Huawei", category: "Accessories", price: "2,000 BDT", img: "https://images.unsplash.com/photo-1580894908361-6b17c1c61e2f" },
  ]);

  const categories = ["All", "Gadgets", "Skin Care", "Fashion", "Electronics", "Accessories"];
  const [selectedCategory, setSelectedCategory] = useState("All");

  const filteredProducts = selectedCategory === "All"
    ? allProducts
    : allProducts.filter(p => p.category === selectedCategory);

  return (
    <div className="bg-gray-50 text-gray-800">
      {/* Hero Section */}
      <section className="text-center py-12 bg-gradient-to-r from-blue-600 to-indigo-700 text-white">
        <motion.h1 initial={{ opacity: 0, y: -30 }} animate={{ opacity: 1, y: 0 }} className="text-4xl font-bold mb-4">
          Mega Import House
        </motion.h1>
        <p className="text-lg max-w-2xl mx-auto">
          Fashion • Skin Care • Smart Gadgets – Imported Directly from China 🇨🇳 to Bangladesh 🇧🇩
        </p>
        <a
          href="https://wa.me/8801400111393"
          className="mt-6 inline-block bg-green-500 text-white px-6 py-3 rounded-2xl shadow-lg hover:bg-green-600"
        >
          Order on WhatsApp
        </a>
      </section>

      {/* Why Us */}
      <section className="py-12 text-center">
        <h2 className="text-3xl font-bold mb-6">Why Choose Us?</h2>
        <div className="grid md:grid-cols-3 gap-6 max-w-5xl mx-auto">
          {["Authentic Imported Products", "Fast & Secure Delivery", "Best Price Guarantee"].map((item, i) => (
            <Card key={i} className="p-6 shadow-lg">
              <CardContent className="flex flex-col items-center">
                <CheckCircle className="text-green-500 w-10 h-10 mb-4" />
                <p className="font-semibold">{item}</p>
              </CardContent>
            </Card>
          ))}
        </div>
      </section>

      {/* Category Filter */}
      <section className="py-6 text-center">
        {categories.map((cat) => (
          <button
            key={cat}
            onClick={() => setSelectedCategory(cat)}
            className={`mx-2 px-4 py-2 rounded-full border font-semibold ${selectedCategory === cat ? 'bg-blue-600 text-white' : 'bg-white text-gray-700 border-gray-300 hover:bg-gray-100'}`}
          >
            {cat}
          </button>
        ))}
      </section>

      {/* Products */}
      <section className="py-12 bg-white">
        <div className="grid sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 max-w-6xl mx-auto">
          {filteredProducts.map((product, index) => (
            <motion.div
              key={index}
              initial={{ opacity: 0, y: 30 }}
              animate={{ opacity: 1, y: 0 }}
              transition={{ delay: index * 0.1 }}
            >
              <Card className="rounded-2xl overflow-hidden shadow-md hover:shadow-xl transition relative">
                <img src={product.img} alt={product.name} className="h-48 w-full object-cover" />
                {product.deal && <span className="absolute top-2 left-2 bg-red-500 text-white px-2 py-1 text-xs rounded">HOT</span>}
                <CardContent className="p-4">
                  <h3 className="font-semibold text-lg">{product.name}</h3>
                  <p className="text-sm text-gray-500">{product.category}</p>
                  <p className="font-bold text-indigo-600">{product.price}</p>
                  <a
                    href={`https://wa.me/8801799061797?text=I want to order: ${product.name}`}
                    className="mt-3 inline-flex items-center bg-blue-600 text-white px-4 py-2 rounded-xl hover:bg-blue-700"
                  >
                    <ShoppingCart className="w-4 h-4 mr-2" /> Order Now
                  </a>
                </CardContent>
              </Card>
            </motion.div>
          ))}
        </div>
      </section>

      {/* Contact Section */}
      <section className="py-12 text-center bg-gray-100">
        <h2 className="text-3xl font-bold mb-4">Contact Us</h2>
        <p className="mb-2">📞 01400111393</p>
        <p className="mb-2">📞 01799061797</p>
        <div className="flex justify-center space-x-4 mt-4">
          <a href="tel:01400111393" className="bg-blue-600 text-white px-5 py-2 rounded-xl">Call Now</a>
          <a href="https://wa.me/8801400111393" className="bg-green-500 text-white px-5 py-2 rounded-xl">WhatsApp</a>
        </div>
      </section>

      {/* Footer */}
      <footer className="bg-indigo-700 text-white text-center py-6 mt-8">
        <p>© {new Date().getFullYear()} Mega Import House. All rights reserved.</p>
      </footer>
    </div>
  );
}

