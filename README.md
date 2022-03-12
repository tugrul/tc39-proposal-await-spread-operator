

# await spread operator

## The problem

Most complex programs have many `async` operations same time. The developers are using `Promise.all` utility function and variants to solve the problem. There would be more elegant way as you can see proposal below.

## Proposal

There is a spread operator `...` already in use and my idea is `await` operator can be suitable to use it together like this `await...`

## Examples

```js

import timers from 'timers/promises'; 

async function taskFoo() {
    await timers.setInterval(1000);
    return 'foo result';
}

async function taskBar() {
    await timers.setInterval(1000);
    return 'bar result';
}

async function main() {

    // const [foo, bar] = Promise.all([taskFoo(), taskBar()]);
    const [foo, bar] = [await...[taskFoo(), taskBar()]];

}
```

## Goal

Getting more flexible and formal way of combining async and sync operations / values.

