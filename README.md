# Nexus - Interactive Neural Network Animation

An elegant, interactive particle system that creates a mesmerizing neural network visualization using HTML5 Canvas. Particles dynamically connect and respond to mouse movement, creating a futuristic, organic visual experience.

🌐 **Live Demo:** https://suranjannandi-git.github.io/nexus/

![Nexus Animation](https://img.shields.io/badge/Status-Live-brightgreen) ![HTML5](https://img.shields.io/badge/HTML5-Canvas-orange) ![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-yellow)

---

## ✨ Features

### Core Functionality
- **120 Autonomous Particles** - Self-moving nodes with randomized velocities
- **Dynamic Connections** - Lines automatically drawn between particles within 150px range
- **Mouse Interaction** - Particles attracted to cursor within 200px radius
- **Convergence Rays** - Visual rays connecting nearby particles to mouse position
- **Responsive Design** - Automatically adapts to window resize events
- **Smooth Animations** - 60 FPS rendering using `requestAnimationFrame`

### Visual Effects
- **Radial Gradient Glow** - Particles emit soft, luminous halos
- **Distance-Based Opacity** - Connection lines fade based on particle distance
- **Mouse Proximity Enhancement** - Particles and connections glow brighter near cursor
- **Trail Effect** - Subtle motion blur for organic movement feel
- **Boundary Wrapping** - Particles seamlessly wrap around screen edges

---

## 🎮 User Interaction

- **Move Mouse** - Particles within 200px are attracted to cursor
- **Hover** - Connections near mouse glow with increased intensity
- **Leave Canvas** - Particles return to autonomous movement

---

## 🛠️ Technical Implementation

### Architecture

The application is built with vanilla JavaScript and HTML5 Canvas, structured into modular components:

#### 1. **Canvas Setup** ([`index.html:64-68`](index.html:64))
```javascript
const canvas = document.getElementById('canvas');
const ctx = canvas.getContext('2d');
```

#### 2. **Configuration Object** ([`index.html:73-84`](index.html:73))
Centralized settings for easy customization:
```javascript
const config = {
    particleCount: 120,              // Number of particles
    baseSpeed: 0.3,                  // Base movement speed
    connectionDistance: 150,         // Max distance for connections
    mouseInfluenceRadius: 200,       // Mouse attraction range
    mouseAttractionStrength: 0.02,   // Attraction force multiplier
    lineBaseWidth: 0.5,              // Minimum line thickness
    lineMaxWidth: 2,                 // Maximum line thickness
    particleBaseSize: 1.5,           // Base particle radius
    particleMaxSize: 3,              // Max particle radius
    glowIntensity: 0.6               // Glow effect strength
};
```

#### 3. **Particle Class** ([`index.html:108-193`](index.html:108))
Object-oriented particle implementation with:
- **Position & Velocity** - 2D coordinates and movement vectors
- **Mouse Attraction** - Force-based attraction calculation
- **Velocity Damping** - Smooth deceleration (0.98 multiplier)
- **Boundary Wrapping** - Seamless edge transitions
- **Dynamic Sizing** - Size scales with mouse proximity
- **Gradient Rendering** - Radial glow effect

#### 4. **Connection System** ([`index.html:206-260`](index.html:206))
Optimized O(n²/2) algorithm:
- Checks only forward particles to avoid duplicate lines
- Distance-based opacity calculation
- Mouse proximity glow enhancement
- Dual-layer rendering for intense glow effect

#### 5. **Mouse Ray System** ([`index.html:265-307`](index.html:265))
Creates convergence effect:
- Draws gradient lines from particles to cursor
- Linear gradient from particle color to white
- Mouse position glow halo (50px radius)

#### 6. **Animation Loop** ([`index.html:312-334`](index.html:312))
Render pipeline:
1. Clear canvas with trail effect (15% opacity black)
2. Update all particle positions
3. Draw connection lines
4. Draw mouse rays
5. Draw particles (on top layer)
6. Request next frame

---

## 🎨 Customization Guide

### Adjust Particle Density
```javascript
particleCount: 150  // Increase for denser network
```

### Modify Connection Range
```javascript
connectionDistance: 200  // Larger value = more connections
```

### Change Mouse Influence
```javascript
mouseInfluenceRadius: 300        // Wider attraction area
mouseAttractionStrength: 0.05    // Stronger pull force
```

### Alter Visual Style
```javascript
lineBaseWidth: 1.0    // Thicker connection lines
glowIntensity: 1.0    // More intense glow effect
```

### Color Scheme
Modify gradient colors in:
- **Particles** ([`index.html:182-188`](index.html:182)) - White to blue gradient
- **Connections** ([`index.html:244`](index.html:244)) - Light blue (`rgba(200, 220, 255, ...)`)
- **Background** ([`index.html:16`](index.html:16)) - Dark blue (`#05070a`)

---

## 🚀 Getting Started

### Run Locally
1. Clone the repository:
   ```bash
   git clone https://github.com/suranjannandi-git/nexus.git
   cd nexus
   ```

2. Open [`index.html`](index.html:1) in a modern browser:
   ```bash
   # macOS
   open index.html
   
   # Linux
   xdg-open index.html
   
   # Windows
   start index.html
   ```

3. Or use a local server:
   ```bash
   # Python 3
   python -m http.server 8000
   
   # Node.js
   npx http-server
   ```

### Browser Compatibility
- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

Requires HTML5 Canvas and ES6 support.

---

## 📊 Performance Characteristics

- **Particle Updates:** O(n) - Linear complexity
- **Connection Drawing:** O(n²/2) - Optimized quadratic (only forward checks)
- **Frame Rate:** 60 FPS on modern hardware
- **Memory Usage:** ~2-3 MB (120 particles)

### Optimization Techniques
1. **Spatial Optimization** - Only checks forward particles for connections
2. **Distance Culling** - Skips rendering for distant particles
3. **Velocity Capping** - Prevents runaway acceleration
4. **Trail Effect** - Reduces full canvas clears (performance boost)

---

## 🧩 Code Structure

```
index.html
├── Styles (lines 7-47)
│   ├── Canvas fullscreen setup
│   ├── Title overlay styling
│   └── Info text positioning
│
└── JavaScript (lines 54-355)
    ├── Canvas Setup (64-68)
    ├── Configuration (73-84)
    ├── Mouse Tracking (89-103)
    ├── Particle Class (108-193)
    │   ├── constructor & reset
    │   ├── update (physics)
    │   └── draw (rendering)
    ├── Particle Initialization (198-201)
    ├── Connection Rendering (206-260)
    ├── Mouse Ray System (265-307)
    ├── Animation Loop (312-334)
    ├── Resize Handler (339-349)
    └── Animation Start (354)
```

---

## 🎯 Use Cases

- **Landing Pages** - Eye-catching hero section
- **Portfolio Websites** - Interactive background
- **Tech Presentations** - Futuristic visual theme
- **Data Visualization** - Network/connection metaphor
- **Creative Coding** - Learning canvas animations

---

## 📝 License

This project is open source and available for personal and commercial use.

---

## 🤝 Contributing

Contributions welcome! Feel free to:
- Report bugs
- Suggest features
- Submit pull requests
- Improve documentation

---

## 👨‍💻 Author

**Suranjan Nandi**
- GitHub: [@suranjannandi-git](https://github.com/suranjannandi-git)
- Project: [Nexus](https://github.com/suranjannandi-git/nexus)

---

## 🌟 Acknowledgments

Built with vanilla JavaScript and HTML5 Canvas - no frameworks, no dependencies, just pure web technology.

**Developed with assistance from [Bob](https://github.com/cline/cline)** - An AI coding assistant that helped bring this interactive neural network visualization to life.

---

**Made with ❤️ and JavaScript**
