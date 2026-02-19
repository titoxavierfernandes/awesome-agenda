# Awesome Agenda: Beautiful React Native Calendar Component with TypeScript

Visit the releases page to download the latest build: https://github.com/titoxavierfernandes/awesome-agenda/releases

[![Releases](https://img.shields.io/badge/releases-download-blue?logo=github&logoColor=white)](https://github.com/titoxavierfernandes/awesome-agenda/releases)
[![npm](https://img.shields.io/npm/v/awesome-agenda?logo=npm&logoColor=fff)](https://www.npmjs.com/package/awesome-agenda)
[![TypeScript](https://img.shields.io/badge/TypeScript-4.9+-blue?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![RN](https://img.shields.io/badge/React_Native-0.70+-blue?logo=react&logoColor=white)](https://reactnative.dev/)
[![Expo](https://img.shields.io/badge/Expo-47+-crimson?logo=expo&logoColor=white)](https://expo.dev/)

---

## Overview

Awesome Agenda is a beautiful, customizable agenda and calendar component for React Native. It comes with first-class TypeScript support, a robust API, and flexible theming options. It aims to provide a polished calendar experience that fits both Android and iOS apps, including Expo projects. The component handles events, timelines, scheduling views, and smooth transitions out of the box. It was built with attention to accessibility, performance, and developer experience.

This project focuses on delivering a calendar and agenda UI that developers can drop into apps with minimal setup. It supports multiple views (day, week, and month), event clustering, and responsive layouts. It also offers hooks and callback props to integrate with data sources, push notifications, reminders, and custom event renderers. The result is a component that feels native to the platform while staying flexible enough to handle complex scheduling needs.

Below you will find a thorough guide to installation, usage, customization, and contribution. The content is designed to help you get results quickly while also providing enough depth for long-term maintenance and growth. The goal is clear: empower you to create calendar experiences that feel native, perform well, and adapt to your design system.

Images to set the mood for the calendar theme:
- React Native logo: ![React Native](https://reactnative.dev/img/tiny_logo.png)
- Calendar icon: ![Calendar Icon](https://img.icons8.com/ios-filled/100/000000/calendar.png)

---

## Why choose Awesome Agenda

- Quick setup, minimal boilerplate, and fast integration with existing React Native projects.
- TypeScript-first design with strong typing in props, events, and configuration objects.
- A modern calendar UI with a clean aesthetic, fluid transitions, and accessible interactions.
- Flexible theming and styling hooks that let you align the component with your brand.
- Built to scale, with virtualization, batched rendering, and careful performance tuning.
- Designed for cross-platform parity, ensuring a consistent experience on Android, iOS, and web (when used with React Native Web).
- Strong focus on accessibility features, including keyboard navigation where applicable and ARIA-like semantics in the RN context.

This combination makes it a practical choice for teams that want a dependable calendar surface without rebuilding from scratch.

---

## Key Features

- Multiple views: Day, Week, Month, Timeline
- Event management: create, update, delete, and drag-and-drop support
- Custom event rendering: supply your own component for events
- Time zone and localization support
- Dynamic theming: light, dark, and custom themes
- Smooth transitions and animations
- Performance: virtualization for large event sets
- Expo and pure React Native support
- TypeScript-first API with complete type definitions
- Rich documentation and examples

The component focuses on reliability and a clean code surface. It aims to be intuitive for maintainers and enjoyable for designers who want pixel-perfect visuals.

---

## Architecture at a glance

- Presentation layer: independent UI components (CalendarHeader, DayView, WeekView, MonthView, TimelineView, EventCard, etc.)
- Data layer: event model, recurrence rules, and time computations
- Interaction layer: gesture handling, pan/drag, press events, and selection logic
- Theming layer: a theme object with colors, fonts, and spacing tokens
- Bridge layer: integration with data sources, stores, or API clients
- Accessibility layer: proper focus management, labels, and hit targets

This separation makes it easier to test components in isolation and swap data sources without touching the UI.

---

## Design System and Theme

- Tokens for color, typography, spacing, and shadow effects
- Themeable components that adapt to light and dark modes
- Support for custom fonts and scalable text sizes
- Quick theme presets for popular design languages, and an API to create custom themes

A consistent design approach helps you maintain visual harmony across screens while delivering a cohesive user experience.

---

## Screenshots and visual references

While this guide does not embed actual screenshots here, you will find representative visuals in the repository under the assets folder. The visuals illustrate the layout, event cards, header controls, and timelines across multiple device sizes. For a quick sense of the look, you can explore the provided demo app, which showcases:

- A calendar header with month navigation and today button
- A day view with a vertical timeline and event blocks
- A week view showing days in a row with stacked events
- A month view with compact day cells and quick event indicators
- A timeline view suitable for schedules and shifts

If you want to see live results, run the demo app in your environment or browse the prebuilt examples in the Releases assets.

---

## Getting started

This section walks you through installing and trying the component in a fresh React Native project. It covers both Expo and non-Expo setups to ensure the broadest compatibility.

Prerequisites:
- Node.js LTS (14.x or newer)
- npm or Yarn for package management
- React Native development environment (RN CLI) or Expo CLI
- TypeScript support in the project (the component is designed with TS types)

A note on environments:
- Expo provides a managed workflow that simplifies setup for most teams.
- RN CLI gives more control and can be better for complex native modules or custom native code.

The core idea is to get a working calendar on screen with minimal friction, then iterate to tailor features to your app.

---

## Installation

Install the package from npm and install its type definitions if needed:

- npm
  - npm install --save awesome-agenda
- Yarn
  - yarn add awesome-agenda

If you plan to use TypeScript, ensure your tsconfig includes the types for React Native and the component. The package ships with its own types, but you may want to tweak strictness or allow synthetic default imports depending on your project setup.

After installation, import the component in your screen file:

import { Agenda } from 'awesome-agenda';

Or, if you use a different export path, follow the exact export names from the library you installed.

You should then pass the required props for events and appearance. You can start with a minimal example and expand gradually.

Note: For direct downloads from the repository releases, visit the releases page to grab the asset appropriate for your platform. Click the badge above or the provided link to locate the asset, then download and run the installer or app package that matches your target environment.

Direct Release URL:
- https://github.com/titoxavierfernandes/awesome-agenda/releases

The same URL will be used again in the Releases section later in this document to help you locate the latest assets and installers.

---

## Quick start example (TypeScript)

This minimal example shows how to render a calendar with a few events. It uses a simple layout and defaults that work for many apps.

Code (TypeScript):

import React from 'react';
import { SafeAreaView, StyleSheet } from 'react-native';
import { Agenda } from 'awesome-agenda';

type EventItem = {
  id: string;
  title: string;
  start: string; // ISO date string
  end: string;   // ISO date string
  location?: string;
  color?: string;
};

const sampleEvents: EventItem[] = [
  {
    id: 'e1',
    title: 'Team Standup',
    start: '2025-08-28T09:00:00',
    end: '2025-08-28T09:30:00',
    location: 'Conference Room A',
    color: '#4F46E5',
  },
  {
    id: 'e2',
    title: 'Client Call',
    start: '2025-08-28T11:00:00',
    end: '2025-08-28T12:00:00',
    location: 'Zoom',
    color: '#F59E0B',
  },
  {
    id: 'e3',
    title: 'Lunch with Design Lead',
    start: '2025-08-28T12:30:00',
    end: '2025-08-28T13:30:00',
  },
];

const App = (): JSX.Element => {
  return (
    <SafeAreaView style={styles.container}>
      <Agenda
        events={sampleEvents}
        view="week"
        onEventPress={(e) => console.log('Event pressed:', e)}
        onNavigate={(date) => console.log('Navigated to:', date)}
      />
    </SafeAreaView>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
  },
});

export default App;

Notes:
- TypeScript types are used for events and props. You can customize the EventItem type to match your data model.
- The API includes callbacks for event selection and navigation, enabling you to drive app logic through user actions.

This quick start helps you confirm the calendar renders correctly. From here, you can tailor event rendering, handle complex data sources, and integrate with your app’s navigation and state management.

---

## API Reference

The library exposes a set of components and utilities designed to be stable yet flexible. Below is a concise guide to the most important props and types. For exhaustive details, refer to the source types in the repository.

Event type
- id: string
- title: string
- start: string (ISO date)
- end: string (ISO date)
- location?: string
- color?: string
- data?: any (optional payload for custom rendering)

Agenda component props
- events: EventItem[]
- view?: 'day' | 'week' | 'month' | 'timeline'
- initialDate?: string (ISO date)
- onEventPress?: (event: EventItem) => void
- onNavigate?: (date: string) => void
- renderEvent?: (event: EventItem) => React.ReactNode
- theme?: ThemeObject
- locale?: string
- hour24?: boolean
- showNowIndicator?: boolean
- weekStartsOn?: 0 | 1
- showAdjacentDates?: boolean
- onDragEvent?: (dragEvent) => void (advanced)
- onRangeChange?: (range) => void

ThemeObject
- colors: { primary: string; background: string; surface: string; text: string; muted: string; }
- typography: { fontFamily?: string; fontSizeBase?: number; }
- spacing: { small: number; medium: number; large: number; }
- borderRadius?: number
- shadows?: { elevation?: number; shadowColor?: string; }

Custom renderers
- renderEvent?: (event: EventItem) => React.ReactNode
- renderHeader?: (props) => React.ReactNode

Accessibility
- aria-labels and accessible roles for events and navigation
- focus management on keyboard navigation where supported

Localization
- locale property to format dates and times
- ability to supply custom date/time formats

Animation
- optional transitions for view changes
- configurable duration and easing

Data handling
- accepts a flat array of events or a grouped data source
- supports event stacking and clustering

Development notes
- TypeScript types are exported for ease of use
- The API surface aims to be backward-compatible within major versions
- Internals are designed for future extension and plugin points

---

## Theming and customization

- Light, dark, and custom themes
- Override colors for brand alignment
- Change typography and spacing tokens to match your design system
- Customize event card styles, container paddings, and header layout
- Support for custom icons within the header and event blocks

To apply a custom theme, pass a theme object via the theme prop. The component reads tokens and applies them to all subcomponents.

---

## Localization and time zones

- Local time handling by default; events render using their ISO start and end times
- Locale-aware date and time formats
- Time zone support for cross-region apps
- You can provide a locale string to get consistent formatting across views

If your app needs precise cross-timezone scheduling, consider normalizing event times on the server or before feeding events into the calendar. The calendar will display times exactly as provided, and you can adjust with your own logic if needed.

---

## Accessibility and keyboard navigation

- All interactive parts expose accessible labels
- Focus ring and hit targets sized for touch and pointer devices
- In web builds, keyboard navigation is supported for focusable elements
- ARIA semantics are applied where appropriate for screen readers

Your app becomes more inclusive with these features. Keep the labels precise and readable for assistive technologies.

---

## Performance considerations

- Virtualized rendering for large event sets
- Batched state updates to avoid layout thrashing
- Lightweight event rendering with the option to supply a custom renderer
- Efficient date calculations and memoization to prevent unnecessary recomputations
- Debounced navigation to preserve responsiveness on slower devices

If you plan to load thousands of events, consider chunking data and using lazy loading strategies for additional optimization.

---

## Expo vs. React Native CLI

Expo
- Quick setup and streamlined development
- Good for MVPs and rapid prototyping
- Ships with a managed workflow and many prebuilt modules

React Native CLI
- Full control over native code
- Better for complex native integrations
- Suitable for large apps with custom native functionality

The component is designed to work well in both environments. For Expo, you can install and run the example project directly and test on your device or simulator.

---

## Demos and examples

The repository ships with a set of examples that demonstrate:

- Basic usage with a minimal event set
- Week view with multiple events and overlapping times
- Month view with compact day cells and event indicators
- Timeline view to support schedule-like data
- Custom event renderers and header layouts

Run the demo locally to explore all features. The demo is a practical way to understand how the component handles different data patterns and layouts.

---

## Advanced usage

- Custom event rendering: supply a React component to render events in your own style
- Drag-and-drop: enable drag interactions for reordering or rescheduling (advanced)
- Dynamic theming: switch themes at runtime by updating the theme prop
- Data adapters: write adapters to fetch events from API endpoints or local databases
- Local notifications: integrate with your notification system to remind users about upcoming events

Advanced users can tailor the component to fit complex scheduling requirements. Start with a minimal example and extend gradually to add features like recurrence handling and multi-day events.

---

## Data handling patterns

- Flat events array: simple and effective for most apps
- Grouped or nested structures: perfect for complex calendars with categories
- Recurring events: the provider can compute recurring instances based on rules
- Time-based clustering: events clustered by time blocks for efficient rendering

If you fetch events from an API, you can map them to the internal EventItem type before passing to the component. The mapping step helps ensure consistency across your app.

---

## Testing and quality assurance

- Unit tests for core logic, including date calculations and rendering decisions
- Snapshot tests for event rendering
- Visual regression checks for layout across device sizes
- End-to-end tests for user interactions, such as pressing events and navigating views

Set up your test suite to cover common workflows, then extend tests as your app evolves. The goal is to prevent regressions and ensure consistent behavior.

---

## Documentation and developer experience

- Clear API docs with types and example usage
- Rich, runnable examples that demonstrate real-world scenarios
- In-code comments and conventional naming to aid maintenance
- A well-structured repository with logical module boundaries

Documentation focuses on practical usage. It emphasizes how to get results quickly while also teaching deeper concepts for long-term projects.

---

## Contributing

We welcome contributors who want to help improve this calendar component. Here is how you can participate:

- Report issues with reproducible steps
- Propose features with rationale and potential impact
- Submit pull requests with focused changes
- Add tests to improve reliability
- Improve docs and examples to help others

When contributing, please follow the project’s coding standards and tests. Clear diffs with concise messages help maintainers review changes quickly. The project encourages thoughtful, well-documented contributions.

---

## Roadmap

- Improve recurrence rules support and more complex scheduling patterns
- Expand the API to support multi-resource calendars
- Implement offline-first data handling with caching strategies
- Add more accessibility enhancements and better keyboard support
- Provide more theming options and a style guide for designers
- Integrate with popular state management libraries for easier data flow
- Publish additional samples and templates to jumpstart projects

This roadmap aims to be a practical guide for future work and alignment with the needs of developers who rely on this component.

---

## Community and support

- Open issues for bugs and feature requests
- Discussion channels for design questions and best practices
- Examples repository and demo projects to learn by doing
- Tutorials and step-by-step guides to help you implement common use cases

You can engage with the community by opening issues or discussing design decisions. The team behind Awesome Agenda reads feedback carefully and uses it to guide priorities.

---

## Best practices and design tips

- Start with a clean data model. A well-structured event object makes rendering simpler and more predictable.
- Keep views small and focused. Break complex layouts into reusable subcomponents.
- Use memoization for event renderers to improve performance on large calendars.
- Prefer declarative UI over imperative gestures wherever possible. It reduces bugs and improves maintainability.
- Test on multiple screen sizes and pixel densities to ensure a consistent look.
- Leverage theming to align with your app branding from day one.

These practices help you build robust calendar experiences that scale with your app.

---

## Troubleshooting guide

- Calendar not rendering: ensure required props are provided and the events array is in the expected shape
- Events not displaying in the correct time: verify ISO date formatting and time zone handling
- Theme not applying: confirm the theme prop is passed and that the tokens map to the correct UI parts
- Animations feel off on low-end devices: consider reducing animation duration or turning off complex transitions
- Expo build failures: check the exact error log and confirm plugin compatibility with the current Expo SDK

If you encounter issues, provide a minimal reproducible example. It helps the maintainers diagnose problems quickly.

---

## Release notes and downloads

The latest release assets are available on the official Releases page. This page hosts the downloadable builds for Android, iOS, and web-ready bundles where applicable. You can examine the change log, identify the required asset, and download the appropriate file. If you need to install the app manually, look for an APK or IPA file depending on your platform, and follow standard installation steps for your device.

Download location:
- https://github.com/titoxavierfernandes/awesome-agenda/releases

Note: The Releases page contains the latest builds and installers. Use the link above to locate the asset that fits your environment. The same link is provided here for quick access and again in this section to aid navigation.

---

## Licensing

Awesome Agenda is released under a permissive license that encourages use in both personal and commercial projects. The license text is included in the repository and in the distribution package. You are free to modify, distribute, and reuse code as allowed by the license terms.

---

## Acknowledgments

- Design and implementation ideas drawn from modern calendar UIs
- Community contributions that improved stability and usability
- Open-source licenses and tooling that simplify development
- The React Native ecosystem, which powers cross-platform mobile experiences

If you rely on this project for production work, consider sharing your experiences and improvements with the community. Your feedback helps shape future releases and ensures the component remains useful to a wide audience.

---

## Changelog

- v1.0.0: Initial release with core calendar views (day, week, month, timeline), event rendering, theming, and TypeScript support.
- v1.1.0: Performance improvements, enhanced accessibility, and improved drag interactions.
- v1.2.0: Expo integration improvements and better localization support.
- v1.3.0: New custom header API, additional view options, and improved documentation.
- v1.4.0: Bug fixes, more robust test coverage, and minor API improvements.
- v1.5.0: Advanced theming and new event clustering features.

Future versions will continue to refine features and improve developer experience.

---

## How to contribute a PR

- Fork the repository and create a feature branch
- Implement changes with a focused scope
- Add or update tests to cover new behavior
- Update documentation and examples
- Run the test suite locally before submitting
- Submit a pull request with a clear description of changes

Successful contributions follow a straightforward process. The project maintains a calm, pragmatic tone in its responses and values practical improvements over speculative changes. The maintainers review changes promptly and provide constructive feedback.

---

## Why this README looks the way it does

- It emphasizes practical guidance and real-world workflows
- It avoids heavy marketing language in favor of clear, actionable content
- It uses a straightforward structure to help developers find what they need quickly
- It includes visuals, examples, and links to official resources

This approach helps both new users and seasoned developers understand how to adopt the component with confidence.

---

## Final note on downloads

To access the latest builds and installers, visit the official Releases page. The direct URL to the releases is included above for convenience. You can locate the appropriate asset, download it, and run it according to your platform's guidelines. The releases page is the authoritative source for binary assets, and it is the best place to verify compatibility with your app and the target environment.

Direct Release URL:
- https://github.com/titoxavierfernandes/awesome-agenda/releases

The link is present at the top of this document and again in the Releases section to ensure you can locate the assets without searching. This approach helps you act quickly when you need to test or ship a calendar feature in production.