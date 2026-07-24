# Bikeegomini-import React, { useState, useEffect } from 'react';
import { 
  Compass, Terminal, Sparkles, FolderGit2, Video, Download, 
  Share2, Mail, Sun, Moon, Search, ArrowRight, ExternalLink, 
  Youtube, Instagram, Twitter, Linkedin, Send, MessageCircle, 
  Menu, X, Check, Copy, ChevronRight, User, Cpu, BookOpen,
  ArrowUp, Globe, FileText, Bot, Layers, Zap
} from 'lucide-react';

export default function App() {
  const [darkMode, setDarkMode] = useState(false);
  const [mobileMenuOpen, setMobileMenuOpen] = useState(false);
  const [activeCategory, setActiveCategory] = useState('All');
  const [searchQuery, setSearchQuery] = useState('');
  const [copiedPromptId, setCopiedPromptId] = useState(null);
  const [contactSubmitted, setContactSubmitted] = useState(false);
  const [scrollProgress, setScrollProgress] = useState(0);
  const [showBackToTop, setShowBackToTop] = useState(false);

  // Toggle dark mode class on root & track scroll progress
  useEffect(() => {
    if (darkMode) {
      document.documentElement.classList.add('dark');
    } else {
      document.documentElement.classList.remove('dark');
    }

    const handleScroll = () => {
      const totalScroll = document.documentElement.scrollHeight - document.documentElement.clientHeight;
      const currentScroll = window.scrollY;
      setScrollProgress((currentScroll / totalScroll) * 100);
      setShowBackToTop(currentScroll > 500);
    };

    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, [darkMode]);

  const scrollToTop = () => {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  };

  // AI Tools Arsenal (15 Items requested)
  const aiTools = [
    { name: 'ChatGPT', role: 'Conversational LLM', category: 'Text & Reasoning', desc: 'Advanced multimodal intelligence for drafting, brainstorming, and logic.', url: 'https://chatgpt.com' },
    { name: 'Gemini', role: 'Multimodal AI', category: 'Text & Video', desc: 'Google’s native multimodal powerhouse with massive context windows.', url: 'https://gemini.google.com' },
    { name: 'Claude', role: 'Advanced Coding & Prose', category: 'Reasoning', desc: 'Industry-leading coding assistant and nuanced creative writing engine.', url: 'https://claude.ai' },
    { name: 'Grok', role: 'Real-time Analytics', category: 'Text & Search', desc: 'Real-time social intelligence and unfiltered web analytics.', url: 'https://x.ai' },
    { name: 'Perplexity', role: 'AI Answer Engine', category: 'Research', desc: 'Conversational search engine with live web sourcing and citation.', url: 'https://perplexity.ai' },
    { name: 'Cursor', role: 'AI Code Editor', category: 'Development', desc: 'Fork of VS Code built from the ground up for AI-first programming.', url: 'https://cursor.com' },
    { name: 'Windsurf', role: 'Agentic IDE', category: 'Development', desc: 'Advanced flow-state code editor with continuous agentic intelligence.', url: 'https://codeium.com/windsurf' },
    { name: 'Midjourney', role: 'Image Generation', category: 'Visuals', desc: 'The gold standard for photorealistic and cinematic AI art creation.', url: 'https://midjourney.com' },
    { name: 'Leonardo AI', role: 'Asset Generation', category: 'Visuals', desc: 'Customizable game assets, textures, and concept art powerhouse.', url: 'https://leonardo.ai' },
    { name: 'Runway', role: 'Generative Video', category: 'Video', desc: 'Gen-3 Alpha model turning cinematic visions into motion.', url: 'https://runwayml.com' },
    { name: 'Kling AI', role: 'Physics Video', category: 'Video', desc: 'High-fidelity video generator with deep spatial and physical realism.', url: 'https://klingai.com' },
    { name: 'Veo', role: 'Google Video Engine', category: 'Video', desc: 'High-definition cinematic video generation with precise prompt adherence.', url: 'https://deepmind.google' },
    { name: 'ElevenLabs', role: 'Voice Synthesis', category: 'Audio', desc: 'Hyper-realistic voice cloning and text-to-speech generation.', url: 'https://elevenlabs.io' },
    { name: 'CapCut', role: 'Smart Video Editor', category: 'Editing', desc: 'AI-powered auto captions, background removal, and viral formatting.', url: 'https://capcut.com' },
    { name: 'Canva', role: 'Design Suite', category: 'Design', desc: 'Magic Studio AI tools for instant social graphics and presentations.', url: 'https://canva.com' }
  ];

  // Prompt Library Data (Including Automation)
  const prompts = [
    { id: 1, title: 'Cinematic Mountain Drone Shot', category: 'Video', desc: 'Generate hyper-realistic 4K mountain sunrise drone footage with morning mist.', code: '/imagine prompt: Cinematic 4K drone shot over misty pine forests, golden hour lighting, photorealistic --ar 16:9' },
    { id: 2, title: 'Minimalist Outdoor Logo', category: 'Logo', desc: 'Clean vector logo for eco-friendly outdoor and camping gear brand.', code: 'Vector logo design, minimalist pine tree silhouette merging with mountain peaks, sage green and off-white palette, flat vector --v 6.0' },
    { id: 3, title: 'SaaS Landing Page Wireframe', category: 'Website', desc: 'High conversion modern SaaS homepage layout with glassmorphic cards.', code: 'UI/UX design for premium outdoor rental platform, sage green accents, off-white background, glassmorphism cards, Apple design style --ar 16:9' },
    { id: 4, title: 'YouTube Viral Thumbnail', category: 'Thumbnail', desc: 'High CTR bold typography thumbnail with dramatic outdoor lighting.', code: 'YouTube thumbnail background, camper van parked under starry night sky, dramatic contrast, vibrant glowing campfire, 8k resolution' },
    { id: 5, title: 'AI Code Refactoring Assistant', category: 'Coding', desc: 'System prompt to turn spaghetti JavaScript code into clean modular React components.', code: 'You are an expert React architect. Refactor the provided code into clean, modular, single-file components using Tailwind CSS and modern hooks.' },
    { id: 6, title: 'Social Media Growth Hook Generator', category: 'Marketing', desc: 'Viral hook formulas tailored for outdoor tech creators and AI enthusiasts.', code: 'Generate 10 high-retention hook sentences for a short-form video about AI tools that save 10 hours a week for creators.' },
    { id: 7, title: 'Abstract 3D Motion Graphic Loop', category: 'Motion Graphics', desc: 'Smooth flowing abstract terrain topology loop for background visuals.', code: '3D abstract motion graphic loop, minimalist topographic contour lines morphing smoothly, sage green clay render, studio lighting' },
    { id: 8, title: 'Cyber-Organic Product Mockup', category: 'Image', desc: 'Futuristic camping gadget resting on mossy forest rocks.', code: 'Photorealistic product photography, futuristic solar camping lantern on mossy forest floor, soft overcast lighting, Leica M11 --ar 4:3' },
    { id: 9, title: 'Zapier Webhook Automation Architect', category: 'Automation', desc: 'System prompt to design robust multi-step webhook syncs between CRM and Notion.', code: 'Act as an automation expert. Build a JSON payload mapping webhook events from Stripe to Notion database properties with error handling.' }
  ];

  const categories = ['All', 'Image', 'Video', 'Thumbnail', 'Logo', 'Website', 'Motion Graphics', 'Coding', 'Marketing', 'Automation'];

  const filteredPrompts = prompts.filter(item => {
    const matchesCat = activeCategory === 'All' || item.category === activeCategory;
    const matchesSearch = item.title.toLowerCase().includes(searchQuery.toLowerCase()) || item.desc.toLowerCase().includes(searchQuery.toLowerCase());
    return matchesCat && matchesSearch;
  });

  const handleCopyPrompt = (id, text) => {
    navigator.clipboard.writeText(text);
    setCopiedPromptId(id);
    setTimeout(() => setCopiedPromptId(null), 2000);
  };

  const socialLinks = [
    { name: 'YouTube', icon: <Youtube className="w-6 h-6 text-red-600" />, handle: '@BikeeGoMini', url: '#', color: 'hover:border-red-500/50 hover:bg-red-50/50 dark:hover:bg-red-950/20' },
    { name: 'Instagram', icon: <Instagram className="w-6 h-6 text-pink-600" />, handle: '@bikeegomini', url: '#', color: 'hover:border-pink-500/50 hover:bg-pink-50/50 dark:hover:bg-pink-950/20' },
    { name: 'Twitter / X', icon: <Twitter className="w-6 h-6 text-sky-500" />, handle: '@BikeeGoMini', url: '#', color: 'hover:border-sky-500/50 hover:bg-sky-50/50 dark:hover:bg-sky-950/20' },
    { name: 'LinkedIn', icon: <Linkedin className="w-6 h-6 text-blue-600" />, handle: 'in/bikeegomini', url: '#', color: 'hover:border-blue-600/50 hover:bg-blue-50/50 dark:hover:bg-blue-950/20' },
    { name: 'Telegram', icon: <Send className="w-6 h-6 text-cyan-600" />, handle: 't.me/bikeegomini', url: '#', color: 'hover:border-cyan-500/50 hover:bg-cyan-50/50 dark:hover:bg-cyan-950/20' },
    { name: 'WhatsApp', icon: <MessageCircle className="w-6 h-6 text-emerald-600" />, handle: 'Community Chat', url: '#', color: 'hover:border-emerald-500/50 hover:bg-emerald-50/50 dark:hover:bg-emerald-950/20' },
    { name: 'Facebook', icon: <Share2 className="w-6 h-6 text-blue-700" />, handle: 'BikeeGoMini Official', url: '#', color: 'hover:border-blue-600/50 hover:bg-blue-50/50 dark:hover:bg-blue-950/20' },
    { name: 'Email', icon: <Mail className="w-6 h-6 text-sage-600 dark:text-sage-400" />, handle: 'hello@bikeegomini.com', url: '#contact', color: 'hover:border-sage-500/50 hover:bg-sage-50/50 dark:hover:bg-sage-950/20' },
  ];

  return (
    <div className={`min-h-screen transition-colors duration-300 font-sans ${darkMode ? 'bg-[#181C18] text-[#F3F4F0]' : 'bg-[#FAF9F6] text-[#2C382C]'}`}>
      
      {/* Scroll Progress Bar */}
      <div className="fixed top-0 left-0 right-0 h-1 z-50 bg-transparent">
        <div className="h-full bg-sage-600 transition-all duration-150" style={{ width: `${scrollProgress}%` }}></div>
      </div>

      {/* Floating Navigation Bar */}
      <header className="fixed top-4 left-1/2 -translate-x-1/2 z-40 w-[92%] max-w-7xl">
        <div className="backdrop-blur-xl bg-white/70 dark:bg-[#222822]/70 border border-sage-200/50 dark:border-sage-800/50 shadow-lg shadow-black/[0.03] rounded-full px-6 py-3 flex items-center justify-between transition-all">
          
          <a href="#" className="flex items-center gap-2 font-bold tracking-tight text-lg">
            <div className="w-8 h-8 rounded-full bg-sage-600 text-white flex items-center justify-center font-display shadow-sm">
              B
            </div>
            <span className="font-display tracking-tight text-sage-900 dark:text-sage-100">BikeeGoMini</span>
          </a>

          {/* Desktop Nav Items */}
          <nav className="hidden xl:flex items-center gap-5 text-xs font-medium text-sage-700 dark:text-sage-300">
            <a href="#about" className="hover:text-sage-900 dark:hover:text-white transition-colors">About</a>
            <a href="#tools" className="hover:text-sage-900 dark:hover:text-white transition-colors">AI Tools</a>
            <a href="#prompts" className="hover:text-sage-900 dark:hover:text-white transition-colors">Prompt Library</a>
            <a href="#portfolio" className="hover:text-sage-900 dark:hover:text-white transition-colors">Portfolio</a>
            <a href="#youtube" className="hover:text-sage-900 dark:hover:text-white transition-colors">YouTube</a>
            <a href="#downloads" className="hover:text-sage-900 dark:hover:text-white transition-colors">Downloads</a>
            <a href="#blog" className="hover:text-sage-900 dark:hover:text-white transition-colors">Blog</a>
            <a href="#contact" className="hover:text-sage-900 dark:hover:text-white transition-colors">Contact</a>
          </nav>

          <div className="flex items-center gap-3">
            <button 
              onClick={() => setDarkMode(!darkMode)}
              className="p-2.5 rounded-full bg-sage-100/80 dark:bg-sage-800/80 text-sage-800 dark:text-sage-200 hover:scale-105 transition-transform"
              aria-label="Toggle Theme"
            >
              {darkMode ? <Sun className="w-4 h-4 text-amber-400" /> : <Moon className="w-4 h-4 text-sage-700" />}
            </button>

            <a 
              href="#prompts" 
              className="hidden sm:inline-flex items-center gap-2 bg-sage-700 hover:bg-sage-800 text-white text-xs font-semibold px-4 py-2.5 rounded-full transition-all shadow-sm hover:shadow"
            >
              <Sparkles className="w-3.5 h-3.5" />
              <span>Prompt Library</span>
            </a>

            <button 
              onClick={() => setMobileMenuOpen(!mobileMenuOpen)}
              className="xl:hidden p-2 rounded-full bg-sage-100 dark:bg-sage-800 text-sage-800 dark:text-sage-200"
            >
              {mobileMenuOpen ? <X className="w-5 h-5" /> : <Menu className="w-5 h-5" />}
            </button>
          </div>
        </div>

        {/* Mobile Dropdown Menu */}
        {mobileMenuOpen && (
          <div className="xl:hidden mt-2 backdrop-blur-2xl bg-white/95 dark:bg-[#222822]/95 border border-sage-200 dark:border-sage-800 rounded-3xl p-6 shadow-2xl flex flex-col gap-3 animate-fade-in max-h-[80vh] overflow-y-auto">
            <a href="#about" onClick={() => setMobileMenuOpen(false)} className="font-medium py-2 border-b border-sage-100 dark:border-sage-800">About</a>
            <a href="#tools" onClick={() => setMobileMenuOpen(false)} className="font-medium py-2 border-b border-sage-100 dark:border-sage-800">AI Tools</a>
            <a href="#prompts" onClick={() => setMobileMenuOpen(false)} className="font-medium py-2 border-b border-sage-100 dark:border-sage-800">Prompt Library</a>
            <a href="#portfolio" onClick={() => setMobileMenuOpen(false)} className="font-medium py-2 border-b border-sage-100 dark:border-sage-800">Portfolio</a>
            <a href="#youtube" onClick={() => setMobileMenuOpen(false)} className="font-medium py-2 border-b border-sage-100 dark:border-sage-800">YouTube Videos</a>
            <a href="#downloads" onClick={() => setMobileMenuOpen(false)} className="font-medium py-2 border-b border-sage-100 dark:border-sage-800">Free Downloads</a>
            <a href="#blog" onClick={() => setMobileMenuOpen(false)} className="font-medium py-2 border-b border-sage-100 dark:border-sage-800">Blog</a>
            <a href="#contact" onClick={() => setMobileMenuOpen(false)} className="font-medium py-2">Contact Form</a>
          </div>
        )}
      </header>

      {/* Hero Section */}
      <section className="relative min-h-screen flex items-center justify-center pt-28 pb-16 overflow-hidden px-6">
        <div className="absolute inset-0 z-0 overflow-hidden">
          <img 
            src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?q=80&w=2000&auto=format&fit=crop" 
            alt="Cinematic outdoor mountain landscape" 
            className="w-full h-full object-cover scale-105 filter brightness-[0.75] dark:brightness-[0.45] transition-transform duration-1000 ease-out hover:scale-100"
          />
          <div className="absolute inset-0 bg-gradient-to-t from-[#FAF9F6] dark:from-[#181C18] via-transparent to-black/30"></div>
        </div>

        <div className="relative z-10 max-w-4xl mx-auto text-center">
          <div className="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-white/20 dark:bg-black/30 backdrop-blur-md text-white text-xs font-medium tracking-wide mb-6 border border-white/20">
            <Compass className="w-3.5 h-3.5 text-sage-300 animate-spin-slow" />
            <span>AI Creator & Outdoor Tech Explorer</span>
          </div>
          
          <h1 className="text-4xl sm:text-6xl md:text-7xl font-extrabold tracking-tight text-white mb-6 leading-tight">
            Build Faster with AI.
          </h1>
          
          <p className="text-base sm:text-lg text-stone-200 max-w-2xl mx-auto mb-10 font-light leading-relaxed">
            AI Tools • Premium Prompts • Websites • Automation • Content Creation
          </p>

          <div className="flex flex-col sm:flex-row items-center justify-center gap-4">
            <a 
              href="#tools" 
              className="w-full sm:w-auto bg-white text-sage-900 hover:bg-sage-50 px-8 py-4 rounded-full font-bold transition-all shadow-xl hover:scale-105 flex items-center justify-center gap-2"
            >
              <span>Explore AI Tools</span>
              <ArrowRight className="w-4 h-4" />
            </a>
            <a 
              href="#prompts" 
              className="w-full sm:w-auto bg-white/10 hover:bg-white/20 text-white backdrop-blur-md border border-white/30 px-8 py-4 rounded-full font-bold transition-all flex items-center justify-center"
            >
              Prompt Library
            </a>
          </div>
        </div>
      </section>

      {/* About Section */}
      <section id="about" className="py-24 px-6 max-w-6xl mx-auto">
        <div className="backdrop-blur-xl bg-white/70 dark:bg-[#222822]/70 border border-sage-200/50 dark:border-sage-800/50 rounded-3xl p-8 sm:p-12 shadow-xl shadow-black/[0.02]">
          <div className="grid grid-cols-1 md:grid-cols-12 gap-10 items-center">
            <div className="md:col-span-5 relative group">
              <div className="absolute inset-0 bg-sage-600/20 rounded-2xl filter blur-xl group-hover:bg-sage-600/30 transition-all"></div>
              <img 
                src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?q=80&w=800&auto=format&fit=crop" 
                alt="Profile Portrait" 
                className="relative rounded-2xl w-full h-80 object-cover shadow-md group-hover:scale-[1.01] transition-transform duration-500"
              />
            </div>
            <div className="md:col-span-7 flex flex-col justify-center">
              <span className="text-sage-600 dark:text-sage-400 uppercase tracking-widest text-xs font-bold mb-3">About Me</span>
              <h2 className="text-3xl sm:text-4xl font-bold tracking-tight mb-6">Hi, I'm BikeeGoMini.</h2>
              <p className="text-sage-700 dark:text-sage-300 font-light leading-relaxed mb-6">
                Blending Apple minimalism, Notion clarity, Airbnb warmth, and rugged outdoor aesthetics to build world-class AI applications, automation pipelines, and high-retention content.
              </p>
              <div className="grid grid-cols-2 sm:grid-cols-3 gap-4 pt-4 border-t border-sage-200/60 dark:border-sage-800/60">
                <div>
                  <h4 className="font-bold text-2xl text-sage-800 dark:text-sage-100">50K+</h4>
                  <p className="text-xs text-sage-600 dark:text-sage-400 mt-1">Community Reach</p>
                </div>
                <div>
                  <h4 className="font-bold text-2xl text-sage-800 dark:text-sage-100">100+</h4>
                  <p className="text-xs text-sage-600 dark:text-sage-400 mt-1">AI Prompts Built</p>
                </div>
                <div>
                  <h4 className="font-bold text-2xl text-sage-800 dark:text-sage-100">10M+</h4>
                  <p className="text-xs text-sage-600 dark:text-sage-400 mt-1">Video Views</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* AI Tools Section (15 Tools) */}
      <section id="tools" className="py-24 px-6 max-w-7xl mx-auto">
        <div className="text-center max-w-2xl mx-auto mb-16">
          <span className="text-sage-600 dark:text-sage-400 uppercase tracking-widest text-xs font-bold mb-2 block">Ecosystem</span>
          <h2 className="text-3xl sm:text-4xl font-bold tracking-tight mb-4">My AI Tools Arsenal</h2>
          <p className="text-sage-700 dark:text-sage-300 font-light text-sm">The 15 foundational intelligence engines powering my daily creative and engineering workflows.</p>
        </div>

        <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
          {aiTools.map((tool, 


          
