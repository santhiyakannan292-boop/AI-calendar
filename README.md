# 🚀 ContentPilot AI - AI Social Media Content Calendar for Small Businesses

> A complete, professional, AI-powered SaaS web application designed for small businesses, cafes, startups, freelancers, and marketing agencies to plan, create, organize, and manage their social media content from a unified dashboard.

---

## 🌟 Key Features

### 1. 🤖 AI Content Generator
- **Multi-Platform Personalization**: Native post formats, character considerations, and hashtag conventions for **Instagram, LinkedIn, Facebook, X (Twitter), Pinterest, and YouTube**.
- **Context-Aware Inputs**: Topic, product, service, campaign goal, tone of voice (*Friendly, Professional, Funny, Luxury, Casual, Educational*), and call-to-action objectives.
- **3 Creative Angles**: Generates distinct hooks, full body copy with platform line-breaks, targeted hashtag clouds, suggested visual media ideas, and optimal posting times.
- **Seasonal & Launch Inspiration**: 1-click prompt pills for holiday sales, behind-the-scenes stories, customer reviews, and flash promotions.
- **Dual AI Engine**: Built-in intelligent dynamic generation engine (works 100% offline with zero setup) + live integration layer for **Google Gemini 1.5 Flash** or **OpenAI GPT-4o**.

### 2. 🗓️ Interactive Content Calendar
- **Monthly, Weekly, and Daily Views**: View all scheduled and published content at a glance.
- **Drag-and-Drop Rescheduling**: Drag any post card from one date cell to another; automatically updates the database in real-time.
- **Platform Badges & Color Coding**: Distinguish Instagram (pink/purple), LinkedIn (blue), X (slate), Facebook (indigo), Pinterest (rose), and YouTube (red).
- **Post Lifecycle Statuses**: `Idea`, `Draft`, `In Review`, `Approved`, `Scheduled`, `Published`.
- **Quick-View & Edit Modal**: Slide-over modal with tabbed **Live Social Mockup Preview** (Instagram feed, LinkedIn update, X tweet, Facebook post), field editing, post duplication, and deletion.

### 3. 🎯 AI Content Strategy Planner
- **Automated Roadmaps**: 7-Day, 14-Day, and 30-Day strategic cadence roadmaps.
- **4-Pillar Content Formula**: Educational (40%), Engagement (25%), Promotional (20%), and Entertaining (15%).
- **1-Click Apply to Calendar**: Automatically schedules all generated daily post concepts into the database with one click.
- **Peak Posting Heatmaps**: Day-of-week and optimal time-slot recommendations for each social platform.

### 4. 📁 Content & Asset Library
- **Reusable Captions**: Store and manage proven copy formulas and templates.
- **Brand Hashtag Sets**: Organize niche hashtag collections with 1-click clipboard copy.
- **Curated Media Assets**: High-resolution business photography library with 1-click post attachment.
- **Content Categories**: Color-coded taxonomy (*Promotions, Behind The Scenes, Tips & Guides, Community*).

### 5. 🎯 Campaigns Management
- Organize posts under multi-week campaigns (*e.g., Autumn Spice & Roast Showcase, Weekend Vinyl Brunch*).
- Track campaign timelines, budgets, measurable goals, and completion percentages.

### 6. 📊 Analytics & Audience Growth
- Weekly impressions trajectory and engagement rate curves.
- Platform distribution donut breakdown.
- Content format comparison benchmark (*Carousels vs Reels vs Single Posts vs Threads*).
- Clear labeling distinguishing sample/projected analytics from real OAuth platform sync.

### 7. 🔗 Social Accounts Hub
- Connection cards for Instagram, Facebook, LinkedIn, X, Pinterest, and YouTube.
- Sandbox Authorized demo connection mode with follower counts and health status.
- Official API requirements, OAuth scopes, and setup instructions.

### 8. 🏢 Business Profile & Onboarding Wizard
- 3-step interactive onboarding wizard: Business Name, Category, Target Audience, Location, Tone of Voice, Preferred Channels, and Posting Cadence.
- Profile settings editor allowing instant fine-tuning of AI generation variables.

---

## 🛠️ Technology Stack

| Layer | Technologies |
|---|---|
| **Frontend** | React 18, TypeScript, Vite, Tailwind CSS, Lucide Icons, Recharts |
| **Backend** | Node.js, Express.js, TypeScript, REST API |
| **Database** | SQLite / PostgreSQL via Prisma ORM |
| **Authentication** | JWT (JSON Web Tokens), bcryptjs password hashing |
| **Testing** | Node.js native test runner (`node:test`, `tsx --test`) |

---

## 🚀 Quick Start Guide

### Prerequisites
- **Node.js** >= 18.0.0
- **npm** >= 9.0.0

### 1. Installation
Clone the repository and install dependencies:
```bash
# Install root, server, and client dependencies
npm run install:all
```

### 2. Database Setup & Seeding
The project comes pre-configured with SQLite for zero-config local execution:
```bash
# Push Prisma schema to SQLite database
cd server && npx prisma db push

# Seed rich demo data (cafe profile, 10+ scheduled posts, campaigns, analytics)
npx tsx prisma/seed.ts
cd ..
```

### 3. Start the Application
Run both backend API and frontend client concurrently:
```bash
npm run dev
```
- **Frontend**: [http://localhost:5173](http://localhost:5173)
- **Backend API**: [http://localhost:5000/api/health](http://localhost:5000/api/health)

---

## 👥 Demo Accounts

ContentPilot AI includes pre-seeded demo accounts with 1-click login buttons on the login page:

| Role | Email | Password | Persona & Business |
|---|---|---|---|
| **Cafe Owner** | `demo@contentpilot.ai` | `password123` | **Sarah Jenkins** - *Bloom & Roast Specialty Cafe* (Seattle, WA) |
| **Agency Lead** | `agency@contentpilot.ai` | `password123` | **Alex Rivera** - *Nexus Digital Growth Agency* |

---

## ⚙️ Environment Variables

### `server/.env`
```env
PORT=5000
NODE_ENV=development
DATABASE_URL="file:./dev.db"
JWT_SECRET=contentpilot_super_secret_jwt_key_2026_dev

# Optional: Live Google Gemini or OpenAI API Key
# If left empty, ContentPilot AI uses its built-in intelligent dynamic generation engine!
GEMINI_API_KEY=
OPENAI_API_KEY=
```

---

## 📡 REST API Documentation

### Authentication
- `POST /api/auth/register` — Register a new business owner or agency user.
- `POST /api/auth/login` — Sign in and receive JWT bearer token.
- `GET /api/auth/me` — Retrieve active user session and business profile.

### Business Profile
- `GET /api/business` — Retrieve business profile, campaigns, and categories.
- `PUT /api/business` — Update business profile and voice parameters.
- `POST /api/business/onboard` — Complete 3-step onboarding wizard.

### Content Posts
- `GET /api/posts` — List posts with filters (`platform`, `status`, `campaignId`, `search`, `startDate`, `endDate`).
- `GET /api/posts/:id` — Retrieve single post details.
- `POST /api/posts` — Create a new post.
- `PUT /api/posts/:id` — Update post details or drag-and-drop reschedule date.
- `DELETE /api/posts/:id` — Delete a post.
- `POST /api/posts/:id/duplicate` — Duplicate post as a new draft.

### AI Generator & Strategy
- `POST /api/ai/generate` — Generate 3 targeted content variations.
- `POST /api/ai/config` — Configure custom Gemini/OpenAI API key in runtime.
- `GET /api/ai/status` — Get active AI engine status.
- `POST /api/strategy/generate` — Generate 7, 14, or 30-day strategy plan.
- `POST /api/strategy/apply` — 1-click schedule generated strategy to calendar.
- `GET /api/strategy/best-times` — Get audience peak posting times by platform.

### Campaigns & Library
- `GET /api/campaigns` — List marketing campaigns with progress % and post counts.
- `POST /api/campaigns` — Create a new marketing campaign.
- `PUT /api/campaigns/:id` — Update campaign details.
- `DELETE /api/campaigns/:id` — Delete campaign.
- `GET /api/library/templates` — List saved caption formulas.
- `POST /api/library/templates` — Save reusable caption.
- `GET /api/library/hashtags` — List brand hashtag collections.
- `POST /api/library/hashtags` — Save new hashtag collection.
- `GET /api/library/media` — Access royalty-free business photography assets.

### Analytics & Notifications
- `GET /api/analytics/summary` — Get KPI metrics, completion %, and platform share.
- `GET /api/analytics/details` — 14-day engagement curves and format multipliers.
- `GET /api/notifications` — Retrieve in-app notifications.
- `PUT /api/notifications/:id/read` — Mark notification (or all) as read.
- `DELETE /api/notifications` — Clear all notifications.

---

## 🧪 Automated Tests

Run backend unit tests:
```bash
npm test
```
The test suite validates:
1. `AIService.generateContentVariations` produces 3 rich variations with hooks, captions, hashtags, CTAs, and suggested media.
2. `AIService.generateStrategyPlan` generates balanced multi-day roadmaps across all 4 content pillars.

---

## 🚢 Production Deployment

### Option A: Unified Container / Server
1. Build both client and server:
   ```bash
   npm run build
   ```
2. Serve the `client/dist` directory as static assets or via Nginx / reverse proxy.
3. Start the Node.js production server:
   ```bash
   cd server && npm start
   ```

### Option B: Cloud Database (PostgreSQL)
To switch Prisma to PostgreSQL for production:
1. In `server/prisma/schema.prisma`, update:
   ```prisma
   datasource db {
     provider = "postgresql"
     url      = env("DATABASE_URL")
   }
   ```
2. Provide a PostgreSQL connection string in `server/.env`:
   ```env
   DATABASE_URL="postgresql://user:password@localhost:5432/contentpilot?schema=public"
   ```
3. Run `cd server && npx prisma migrate deploy && npx tsx prisma/seed.ts`.

---

## 📄 License
MIT License. Built for small businesses and modern marketing teams.
