# 01. Difference between Interfaces and Types in Typescript

## Types

`type` is a keyword in typescript that we can use to define the shape of a data. `type aliases` provide a way of creating new names for existing type. This also includes primitive types.

```typescript
type myName = string;

type myAddress = {
  city: string;
  district: string;
  roadNo: number;
};
```

In this Example the first type alias renames already existing string type and the second Example creates a type alias with different types in it.

## Interfaces

Interfaces define a structure for an object to strictly follow. we write it using the `interface` keyword followed up with curly braces.

```typescript
interface Student {
  name: string;
  id: number;
  roll: number;
  class: number;
}
```

## Key Difference

- We can define a type alias for a primitive type but we can't do it in an interface. Therefore whenever we need to define a primitive type alias we use `type`.

```typescript
type rollNumber = number;
```

- We can define a union type using only the `type` keyword.

```typescript
type Car = "Toyota" | "Hyundai" | "Audi";
```

- To extend an existing type alias we can use the intersection operator , And to extend an existing interface we use the `extends` keyword.

```typescript
type AdminUser = User & {role: string};
interface AdminUser extends User {
    ....
}
```

- `interface` has a special feature named `declaration merging`. With declaration merging we can define an interface multiple times, and the typescript compiler will automatically merge all the declaration into a single interface definition.

```typescript
interface Person {
  name: string;
  age: number;
}

interface Person {
  name: string;
  age: number;
  country: string;
}
interface Person {
  name: string;
  age: number;
  country: string;
  gender: ["Male", "Female"];
}
```

typescript compiler will create a `Person interface` with `name`, `age`, `country` and `gender` types.

## Conclusion

In this blog post we discussed about types and interfaces. Both has their own advantages and disadvantages. In certain scenarios one is preferred over the other but in the end it all boils down to personal preference.

---

# 02. The Differences between any, unknown, and never types in typescript

## Any

`any` type is used when we have no idea what type of data the variable might hold. It is used generally when working with third party API data. When we do not know the exact shape of the data that the API might return. `any` type can cause some issues as we are basically going back to javascript by letting go off all the fancy typescript type checking features.

```typescript
    const getUserData = (value: string) : any;
```

## Unknown

When we do not know the type of a specific variable in the program but we are going assign it a type during compilation time, which can be anything , in that scenario we give it a `unknown` type.

```typescript
const mysteryValue: unknown;
```

## Never

`never` is the return type of a function that never returns any value whatsoever. Basically `never` represents values that will never occur. Like a function that will throw an error instead of returning something.

```typescript
function throwError(errMsg: string): never {
  throw new Error(errMsg);
}
```

This throwError function will never return a value that's why we can say it has a `never` return type.

## Conclusion

In this blog post we discussed some basic typescript types that may confuse beginners as they are not primitive type found in javascript. I hope you understood what they represent and when to use them.
