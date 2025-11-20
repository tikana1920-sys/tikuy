# Professional Surveyor Company Website

A modern, interactive website for a surveying and mapping company with advanced features including coordinate calculation, 2D/3D terrain visualization, and data import/export capabilities.

## Features

### Core Pages
- **Home** - Professional hero section with service overview and CTA
- **About Us** - Company background, expertise, and equipment information
- **Services** - Detailed service descriptions (topographic survey, polygon establishment, contours, GIS, etc.)
- **Calculator** - Advanced surveying calculation tool with interactive visualization
- **Contact** - Contact form with company information

### Calculator Features
- **Polygon Point Management** - Define control points (A, B, C, etc.)
- **Detail Points Calculation** - Calculate detail points using azimuth, distance, and elevation
- **IDW Interpolation** - Smooth surface interpolation for contour generation
- **2D Visualization** - Canvas-based 2D terrain visualization with:
  - Grid background (millimeter paper style)
  - Polygon visualization (red lines)
  - Contour lines with customizable intervals
  - Detail point markers with elevations
  - Azimuth rays
  
- **3D Visualization** - Three.js powered 3D terrain view with:
  - Interactive rotation and camera control
  - Terrain mesh with lighting
  - Polygon and point overlays
  
- **Data Management**
  - CSV import for batch point entry
  - CSV export of calculated coordinates
  - PNG export of visualizations
  - Survey statistics (min/max elevation, area span, etc.)

## Tech Stack

- **Frontend**: Next.js 16 (App Router) + React
- **Styling**: Tailwind CSS v4 with semantic design tokens
- **Canvas**: HTML5 Canvas for 2D visualization
- **3D Graphics**: Three.js for 3D terrain visualization
- **State Management**: React hooks (useState)
- **Data Processing**: Custom TypeScript utilities for IDW interpolation and contour extraction
- **Deployment**: Vercel

## Project Structure

\`\`\`
├── app/
│   ├── page.tsx                 # Home page
│   ├── about/
│   │   └── page.tsx            # About page
│   ├── services/
│   │   └── page.tsx            # Services page
│   ├── contact/
│   │   └── page.tsx            # Contact page
│   ├── calculator/
│   │   └── page.tsx            # Calculator page
│   ├── layout.tsx              # Root layout with navbar
│   └── globals.css             # Global styles & theme
├── components/
│   ├── navbar.tsx              # Navigation component
│   ├── home/
│   │   ├── hero.tsx           # Hero section
│   │   ├── services.tsx       # Services overview
│   │   └── cta.tsx            # Call-to-action
│   └── calculator/
│       ├── form.tsx           # Input form for points
│       ├── results.tsx        # Results table & stats
│       ├── visualization-2d.tsx # 2D canvas visualization
│       └── visualization-3d.tsx # 3D Three.js visualization
├── lib/
│   └── survey-utils.ts        # Core surveying calculations
└── package.json               # Dependencies
\`\`\`

## Installation & Setup

### Option 1: Using Vercel CLI (Recommended)

\`\`\`bash
# Clone and deploy to Vercel
npx create-next-app@latest my-surveyor-app --example [repo-url]
cd my-surveyor-app
vercel
\`\`\`

### Option 2: Local Development

\`\`\`bash
# Clone the repository
git clone [repo-url]
cd surveyor-website

# Install dependencies
npm install

# Run development server
npm run dev

# Open browser at http://localhost:3000
\`\`\`

### Option 3: Download & Run Locally

\`\`\`bash
# Extract the downloaded ZIP file
unzip surveyor-website.zip
cd surveyor-website

# Install and run
npm install
npm run dev
\`\`\`

## Building & Deployment

### Build for Production

\`\`\`bash
npm run build
npm start
\`\`\`

### Deploy to Vercel

\`\`\`bash
vercel deploy --prod
\`\`\`

Or connect your GitHub repository to Vercel for automatic deployments.

## Usage Guide

### Calculator Page

1. **Define Polygon Points**: Default points A, B, C are provided
2. **Add Detail Points**:
   - Enter point name (e.g., a1, b1, c1)
   - Select origin point
   - Set azimuth (0-360°)
   - Enter distance (meters)
   - Set elevation (meters)
   - Click "Add Point"

3. **Adjust Visualization**:
   - **Contour Interval**: Controls spacing between contour lines (1-20m)
   - **Grid Resolution**: Affects interpolation smoothness (5-50m)

4. **View & Export**:
   - Switch between 2D and 3D views using toggle buttons
   - Download coordinates as CSV
   - Export visualization as PNG
   - View survey statistics

### CSV Import

Format your CSV file as follows:

\`\`\`csv
name,origin,azimuth_deg,distance_m,elevation_m
a1,A,45,50,10
a2,A,90,75,15
b1,B,180,60,12
\`\`\`

Then use the "Import Data" section in the form to upload the file.

## Calculation Formulas

### Detail Point Coordinate Calculation

\`\`\`
azimuth_rad = azimuth_deg × π / 180

x_detail = x_origin + distance × sin(azimuth_rad)
y_detail = y_origin + distance × cos(azimuth_rad)
z_detail = elevation_input
\`\`\`

### IDW Interpolation (for Contour Generation)

\`\`\`
z_interpolated = Σ(w_i × z_i) / Σ(w_i)
where w_i = 1 / d_i^2
and d_i = distance from point to grid cell
\`\`\`

## Browser Compatibility

- Chrome/Edge 90+
- Firefox 88+
- Safari 14+

## Future Enhancements

- TIN (Triangulated Irregular Network) support for triangulation
- PDF report generation
- Cloud storage integration
- Real-time collaboration
- Multiple project management
- Advanced GIS analysis tools

## Support

For issues or questions, please contact: info@surveypro.com

## License

Proprietary - All rights reserved
