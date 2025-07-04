# Landscaping
Landscaping website build 
import Link from 'next/link';

export default function Home() {
  return (
    <main className="min-h-screen flex flex-col items-center justify-center bg-gradient-to-br from-green-200 to-blue-100 p-6">
      <div className="max-w-2xl w-full bg-white rounded-xl shadow-lg p-8 text-center">
        <h1 className="text-4xl font-bold text-green-700 mb-4">GreenScape Landscaping Milton Keynes</h1>
        <p className="text-lg mb-8">Your dream garden starts here. We provide a full range of landscaping services for every season.</p>
        <nav>
          <ul className="flex flex-col md:flex-row justify-center gap-4">
            <li>
              <Link href="/services" className="text-white bg-green-600 hover:bg-green-700 px-6 py-2 rounded transition">Services</Link>
            </li>
            <li>
              <Link href="/gallery" className="text-white bg-green-600 hover:bg-green-700 px-6 py-2 rounded transition">Gallery</Link>
            </li>
            <li>
              <Link href="/contact" className="text-white bg-green-600 hover:bg-green-700 px-6 py-2 rounded transition">Contact & Booking</Link>
            </li>
          </ul>
        </nav>
      </div>
    </main>
  );
}
import Link from 'next/link';

const services = [
  "Artificial turf installation",
  "Concrete masonry",
  "Driveway landscaping",
  "Garden decorations",
  "Grading & resloping",
  "Hardscapes",
  "Landscape design",
  "Landscape installations",
  "Outdoor steps",
  "Driveway or walkway paving",
  "Retaining walls",
  "Path landscaping",
  "Stonemasonry"
];

export default function Services() {
  return (
    <main className="min-h-screen flex flex-col items-center bg-gradient-to-br from-green-100 to-blue-50 p-6">
      <div className="max-w-xl w-full bg-white rounded-xl shadow-md p-8">
        <h1 className="text-3xl font-bold text-green-700 mb-6 text-center">Our Landscaping Services</h1>
        <ul className="list-disc pl-6 space-y-2 mb-8">
          {services.map(service => <li key={service} className="text-lg">{service}</li>)}
        </ul>
        <div className="text-center">
          <Link href="/contact" className="text-white bg-green-600 hover:bg-green-700 px-6 py-2 rounded transition">Book a free consultation →</Link>
        </div>
      </div>
    </main>
  );
}
import Link from 'next/link';

export default function Gallery() {
  const images = [
    "https://placehold.co/400x300?text=Garden+Makeover",
    "https://placehold.co/400x300?text=Driveway+Paving",
    "https://placehold.co/400x300?text=Retaining+Wall"
  ];

  return (
    <main className="min-h-screen flex flex-col items-center bg-gradient-to-br from-green-100 to-blue-50 p-6">
      <div className="max-w-3xl w-full bg-white rounded-xl shadow-md p-8">
        <h1 className="text-3xl font-bold text-green-700 mb-6 text-center">Our Work Gallery</h1>
        <div className="flex flex-wrap gap-6 justify-center mb-6">
          {images.map((src, idx) => (
            <img key={idx} src={src} alt={`Landscaping project ${idx + 1}`} width={300} height={200}
              className="rounded-lg shadow-md border border-gray-200"/>
          ))}
        </div>
        <p className="text-center">See more or <Link href="/contact" className="text-green-700 underline">request a quote</Link>.</p>
      </div>
    </main>
  );
}
import { useState } from 'react';

export default function Contact() {
  const [submitted, setSubmitted] = useState(false);

  const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {
    e.preventDefault();
    setSubmitted(true);
  };

  return (
    <main className="min-h-screen flex flex-col items-center bg-gradient-to-br from-green-100 to-blue-50 p-6">
      <div className="max-w-md w-full bg-white rounded-xl shadow-md p-8">
        <h1 className="text-3xl font-bold text-green-700 mb-6 text-center">Contact & Booking</h1>
        {submitted ? (
          <p className="text-green-700 text-center text-lg">Thank you! We’ll be in touch soon.</p>
        ) : (
          <form onSubmit={handleSubmit} className="flex flex-col gap-4">
            <label className="flex flex-col">
              Name:
              <input type="text" required className="border rounded px-3 py-2 mt-1"/>
            </label>
            <label className="flex flex-col">
              Email:
              <input type="email" required className="border rounded px-3 py-2 mt-1"/>
            </label>
            <label className="flex flex-col">
              Phone Number:
              <input type="tel" required className="border rounded px-3 py-2 mt-1"/>
            </label>
            <label className="flex flex-col">
              Message / Booking Details:
              <textarea required rows={4} className="border rounded px-3 py-2 mt-1"/>
            </label>
            <button type="submit" className="bg-green-600 text-white px-6 py-2 rounded hover:bg-green-700 transition">Send</button>
          </form>
        )}
      </div>
    </main>
  );
}
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./pages/**/*.{js,ts,jsx,tsx}",
    "./components/**/*.{js,ts,jsx,tsx}"
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  @apply bg-gray-50 text-gray-900;
  font-family: 'Inter', sans-serif;
}
import '../styles/globals.css'
import type { AppProps } from 'next/app'

export default function App({ Component, pageProps }: AppProps) {
  return <Component {...pageProps} />
}
{
  "name": "landscaping-demo",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
  },
  "dependencies": {
    "next": "14.1.0",
    "react": "18.2.0",
    "react-dom": "18.2.0"
  },
  "devDependencies": {
    "autoprefixer": "^10.4.0",
    "postcss": "^8.4.0",
    "tailwindcss": "^3.4.0",
    "typescript": "^5.3.0"
  }
}
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
import { Html, Head, Main, NextScript } from 'next/document'

export default function Document() {
  return (
    <Html lang="en">
      <Head>
        <link rel="preconnect" href="https://fonts.googleapis.com"/>
        <link rel="preconnect" href="https://fonts.gstatic.com" crossOrigin="anonymous"/>
        <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet"/>
        <meta name="description" content="Landscaping Services in Milton Keynes. Book your garden transformation today!"/>
      </Head>
      <body>
        <Main />
        <NextScript />
      </body>
    </Html>
  )
}
