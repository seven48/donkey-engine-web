# Web

Web client for Donkey Engine

## Technologies

- PL: TypeScript
- Framework: React
- Linter: tslint
- Styles: CSS
- Formatter: Prettier
- Package Manager: Yarn

## File and component naming

Every React component must be placed in a separate folder. The file containing the component's code must be named "index.tsx".
Style files are named after component's name in PascalCase.

```
src/
|__|components/
|__|__Header/
|__|__|__index.tsx (Contains the Header component)
|__|__|__Header.css
|__|__|__AuthBlock/
|__|__|__|__index.tsx (Contains the AuthBlock component)
|__|__|__|__AuthBlock.css
```

## Code style

Read Airbnb's JavaScript Guide: https://github.com/airbnb/javascript
Main concepts:

- Prefer `const` over `let` when possible, never use `var`.
- Import statements must be situated at the top of a file. Don't add empty lines between them. Imports must be sorted in this order:
  ```javascript
  // Libraries
  import React from 'react';
  import axios from 'axios';
  // UI components and styles
  import Button from '../UI/Button';
  import './Header.css';
  // Child Components
  import AuthBlock from './AuthBlock';
  import Logo from '../Logo';
  ```

* Logically separate your code with an empty line and reorder variables by they purpose:

  ```javascript
  // Bad
  const [donkeys, setDonkeys] = useState(3);
  let tableRender;
  const [bananas, setBananas] = useState(9);
  const getDonkeyNames = () => {
    const res = response.data;
    const names = [];
    res.forEach((donkey) => {
      names.push(donkey.name);
    });
    return names;
  };

  // Good
  // Resorted variables by the interconnections
  const [donkeys, setDonkeys] = useState(3);
  const [bananas, setBananas] = useState(9);
  let tableRender;

  // Added an empty line between variable declarations and a new function
  const getDonkeyNames = () => {
    const res = response.data;
    const names = [];

    // An empty line before an iterator
    res.forEach((donkey) => {
      names.push(donkey.name);
    });

    // An empty line before return statement
    return names;
  };
  ```

- When creating components, prefer function components over class based components (use hooks).

- To prevent situations when a developer forgets to format his code before commiting, it's **highly** recommended to enable formatting on save in your editor.
