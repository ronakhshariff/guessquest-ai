# GuessQuest AI: A Modern Take on Geographic Discovery

To run (Desktop): https://guessquest-ai.onrender.com/

## Overview
GuessQuest AI redefines the classic GeoGuessr experience by combining state‐of‐the‐art AI with entirely custom-built architecture. Designed from the ground up, every aspect of the system has been engineered to deliver a unique and immersive geographic discovery game. The platform harnesses advanced machine learning, dynamic location analysis, and innovative user interface techniques to generate hints and score guesses with unparalleled precision.

## Key Innovations

### AI-Powered Hint Generation
Our proprietary hint system leverages Google Gemini AI to produce highly detailed, context-aware hints. The AI analyzes visual cues—from architectural styles and urban planning to cultural and vegetation patterns—to deliver clues that guide players without revealing the location outright. Hints are dynamically refined as the game progresses, ensuring both challenge and clarity.

### Custom Location Selection and Validation
The location algorithm uses a 70/30 split:
- **70% Dynamic Generation**: Locations are algorithmically generated from curated geographic bounding boxes, ensuring varied and challenging Street View imagery.
- **30% Hand-Picked Locations:** A manually curated list guarantees high-quality, engaging locations.

A custom-built validation mechanism rigorously tests each location for complete Street View coverage and prevents duplicate selections within a single game session.

## Innovative Scoring System
The scoring engine rewards precision and penalizes excessive movement. It combines a base score with deductions based on both distance (using an exponential decay function) and navigation movements. This system encourages strategic thinking and minimizes random guessing:

```typescript
const D_MAX = 10000; // Maximum distance threshold in km
const distanceFactor = Math.min(distance, D_MAX) / D_MAX;
const distancePenalty = 100 * (1 - Math.exp(-5 * distanceFactor));
const movementPenalty = moves * PENALTY_PER_MOVE;
const finalScore = Math.max(5, Math.round(100 - distancePenalty - movementPenalty));
```

This logic ensures that even a distant guess yields some points while rewarding careful, deliberate play.

## Advanced UI/UX Design
Built with Next.js 15.2.2, React, and Tailwind CSS, the interface delivers a modern, responsive, and visually striking experience. Custom animations, glass morphism effects, and a dark theme with cyan accents contribute to a refined and engaging user experience.

## Custom Architecture
GuessQuest AI is built from scratch, with every component custom-engineered to optimize gameplay and user interaction without relying on templates or starter kits.

## Core Technologies

### Frontend & UI Framework
- **Next.js 15.2.2** with App Router for optimal server-side rendering.
- **React 19.0.0** and **TypeScript** for robust, type-safe development.
- **Tailwind CSS** for modern, responsive design.

### Mapping and Street View
- Google Maps JavaScript API and Google Street View.

### AI Integration
- **Google Gemini AI** (primary model gemini-1.5-pro with fallbacks to gemini-1.0-pro and gemini-pro).
- Advanced prompt engineering for detailed hint creation.

## Detailed System Components

### Game Mechanics and Logic
- **Location Selection:** 70% dynamically algorithm-generated, 30% manually curated.
- **Movement Tracking:** Captures significant player movements (>5 meters) for scoring adjustments.
- **Scoring Calculation:** Combines distance and movement into a dynamic scoring system.

### AI-Powered Hint System
- Analyzes environmental, cultural, and architectural details for precise and cryptic hint generation.
- Robust fallback system ensures uninterrupted gameplay.

### User Interface and Experience
- Modern, responsive design with custom animations and glass morphism.
- Dark theme with vibrant cyan accents for enhanced visual appeal.

### Performance and Optimization
- Lazy loading for faster initial loads and efficient caching for reduced latency.
- Optimized state management through memoization and custom hooks.

### Security and Scalability
- Secure API management through environment variables, rate limiting, and access controls.
- Scalable architecture ensures robust performance under increased user load.

## Conclusion
GuessQuest AI represents a significant advancement in geographic discovery gaming, combining AI, strategic gameplay, and immersive design to set a new standard in interactive educational entertainment.

