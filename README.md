# valerie-email-builder

A modern, lightweight drag-and-drop email builder component for React applications, with seamless React Email integration.

[![MIT License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![npm version](https://img.shields.io/npm/v/valerie-email-builder.svg)](https://www.npmjs.com/package/valerie-email-builder)

## Features

- 🧩 **Component-Based**: Drag and drop React Email components to build beautiful emails
- 📱 **Responsive Design**: Create emails that look great on any device
- 🔄 **Live Preview**: See your email as you build it
- 🎨 **Customizable**: Extend with your own components and themes
- 📝 **Rich Text Editing**: Powered by Lexical editor
- 🧪 **Email Client Testing**: Preview how your email will look in different clients
- 🔌 **Framework Agnostic**: Works with any React-based project (Next.js, Remix, Create React App)
- 📦 **Lightweight**: Modular architecture to keep bundle size small

## Installation

```bash
npm install valerie-email-builder react-email
# or
yarn add valerie-email-builder react-email
# or
pnpm add valerie-email-builder react-email
```

## Quick Start

```jsx
import React, { useState } from 'react';
import { EmailBuilder, defaultComponents } from 'valerie-email-builder';
import 'valerie-email-builder/styles.css';

function MyEmailEditor() {
  const [emailJson, setEmailJson] = useState(null);
  
  const handleSave = (json) => {
    setEmailJson(json);
    console.log('Email template saved:', json);
  };
  
  return (
    <div className="email-editor-container">
      <EmailBuilder 
        components={defaultComponents}
        onSave={handleSave}
        initialValue={emailJson}
      />
    </div>
  );
}

export default MyEmailEditor;
```

## Email Rendering

Convert your email JSON to React Email components:

```jsx
import { renderToReactEmail } from 'valerie-email-builder';
import { render } from '@react-email/render';

// Convert builder JSON to React Email component
const EmailComponent = renderToReactEmail(emailJson);

// Render to HTML for sending
const emailHtml = render(EmailComponent);
```

## Customization

### Adding Custom Components

```jsx
import { EmailBuilder, defaultComponents } from 'valerie-email-builder';

// Define your custom component
const CustomComponent = {
  name: 'CustomCTA',
  icon: 'bolt',
  component: ({ text, url, ...props }) => (
    <a href={url} style={{ /* styles */ }}>
      {text || 'Click Me'}
    </a>
  ),
  properties: [
    { name: 'text', type: 'string', default: 'Click Me' },
    { name: 'url', type: 'string', default: '#' }
  ]
};

// Add to components
const extendedComponents = [...defaultComponents, CustomComponent];

// Use in your builder
<EmailBuilder components={extendedComponents} onSave={handleSave} />
```

### Custom Theming

```jsx
<EmailBuilder
  theme={{
    colors: {
      primary: '#4285F4',
      secondary: '#34A853',
      accent: '#FBBC05',
      background: '#FFFFFF',
      text: '#202124'
    },
    fonts: {
      body: 'Arial, sans-serif',
      heading: 'Roboto, sans-serif'
    }
  }}
  onSave={handleSave}
/>
```

## Props

| Prop | Type | Description |
|------|------|-------------|
| `components` | Array | List of components available in the builder |
| `onSave` | Function | Callback when user saves the email |
| `onChange` | Function | Callback on any change to the email |
| `initialValue` | Object | Initial email JSON structure |
| `theme` | Object | Custom theme configuration |
| `height` | String | Height of the editor container |
| `width` | String | Width of the editor container |
| `readOnly` | Boolean | Set to true to disable editing |
| `showPreview` | Boolean | Show/hide the preview panel |
| `previewDevice` | String | 'desktop', 'mobile', or 'both' |

## Browser Support

- Chrome/Edge (latest 2 versions)
- Firefox (latest 2 versions)
- Safari (latest 2 versions)

## Development

```bash
# Clone the repository
git clone https://github.com/yourusername/valerie-email-builder.git

# Install dependencies
cd valerie-email-builder
npm install

# Start the development server
npm run dev

# Build for production
npm run build
```

## License

MIT © Theogene Junior
