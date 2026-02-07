---
name: game-mechanics-lite
description: Use this skill when building the logical core of a web game using p5.js. It handles the "Game Loop", State Machines, Entity Management, and Input Handling, ensuring the interactive part feels responsive and fun.
---

# Game Mechanics Philosophy

You are not just drawing shapes; you are simulating a world. This skill dictates HOW the game runs underneath the visuals.

## 1. The "Clean-State" Loop
Do not use messy global booleans like `isPlaying = true`. Implement a strict Switch-Case State Machine inside the p5.js `draw()` function:
- `STATE_MENU`: Render the `frontend-design` HTML overlay. Pause heavy calculations.
- `STATE_PLAY`: Run physics, collision, and score updates.
- `STATE_OVER`: Freeze the frame or run slow-motion effects. Show restart UI.

## 2. Input Handling
- **Responsive**: Use `keyIsDown()` inside the loop for smooth movement (not `keyPressed`).
- **Universal**: Map both WASD and Arrow Keys.
- **Feedback**: Every input should have a visual or audible reaction (even if just a console log for now).

## 3. The "Juice" (Game Feel)
A game must feel good to play. Implement these micro-behaviors:
- **Coyote Time**: Allow jumping slightly after leaving a platform.
- **Hit Stop**: Freeze the game for 1-2 frames when a collision occurs (adds impact).
- **Screen Shake**: Offset `translate()` randomly when damage is taken.

## 4. Entity Management
For simple games, use a clear Array-based entity system:
- `class Entity { update() { ... } draw() { ... } }`
- Separate `update()` (logic) from `draw()` (rendering) to maintain 60FPS.

## 5. Implementation Rules
- Use `p5.Vector` for all physics (position, velocity, acceleration).
- Collision: Use simple AABB (Axis-Aligned Bounding Box) or Circle-Circle distance checks. Keep it performant.
