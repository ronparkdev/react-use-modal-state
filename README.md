# 🪄 react-use-modals-state

Simplify modal management in React with ease! Seamlessly integrate modals into complex business logic, control their behavior, and create seamless user experiences.

## Features:

* 🚀 Simplified API
* 🛡 Prevents Auto-Closing
* 🎨 Customizable Modals

## Example:
```typescript
import { useModalsState } from 'react-use-modals-state';

const Page = () => {
  // Create modals state using the library
  const { open, render } = useModalsState({
    IssuableCouponModal,
    IssuedCouponModal,
  });

  // Function to initiate the coupon issuance process
  const handleCouponCheck = async () => {
    try {
      // Fetch details of the issuable coupon
      const { title } = fetchIssuableCoupon();

      // Open the IssuableCouponModal to ask the user if they want to issue the coupon
      const isUserWantsToIssueCoupon = await open('IssuableCouponModal', { title });

      if (isUserWantsToIssueCoupon) {
        // If the user wants to issue the coupon, perform the issuance
        const { expireAt } = issueCoupon();

        // Open the IssuedCouponModal to display the issuance result
        await open('IssuedCouponModal', { expireAt });
      }
    } catch (error) {
      // Handle any errors that may occur during the process
      console.error('Error:', error);
    }
  };

  return (
    <div>
      {/* Button to trigger the coupon issuance process */}
      <button onClick={handleCouponCheck}>Check Issuable Coupon</button>

      {/* Render modals */}
      {render()}
    </div>
  );
};

export default Page;
```

## Installation

To install the "react-use-modals-state" library, you can use npm or yarn:

```bash
npm install react-use-modals-state
# or
yarn add react-use-modals-state
```

## Usage

### `useModalsState(componentTypes: Record<string, React.ComponentType<any>>): { open, render }`

- Initializes modal management for your React application.

#### Parameters

- `componentTypes` (required): An object mapping modal keys to their corresponding React component types.

#### Returns

An object with the following properties:

- `open(key: string, props?: object): Promise<any>`: Opens a modal with the specified `key` and optional `props`. Returns a Promise that resolves when the modal is closed, providing the result.
- `render()`: Renders the currently active modal.

### `open(key: string, props?: object): Promise<any>`

- Opens a modal with the specified `key` and optional `props`.

#### Parameters

- `key` (required): The key of the modal to open, as defined in the `componentTypes` object.
- `props` (optional): Additional props to pass to the modal component.

#### Returns

A Promise that resolves when the modal is closed, providing the result.

### `render()`

- Renders the currently active modal.
