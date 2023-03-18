<p align="center"><img src="https://raw.githubusercontent.com/WilliamDavidHarrison/pi/main/assets/pi.png" height="64" width="64"></p>
<h1 align="center">Calculate Pi</h1>

## Run

### CLI
You can calculate Pi from your command line, using our simple [npm package](https://www.npmjs.com/package/pi-calculator).

### Manual
Copy the following code from [index.js](https://github.com/WilliamDavidHarrison/pi/blob/main/index.js) into a file called `index.js` on your computer.

```js
function* pi() {
    let q = 1n;
    let r = 180n;
    let t = 60n;
    let i = 2n;

    while (true) {
        let digit = ((i * 27n - 12n) * q + r * 5n) / (t * 5n);

        yield Number(digit);

        let u = i * 3n;
        u = (u + 1n) * 3n * (u + 2n);
        r = u * 10n * (q * (i * 5n - 2n) + r - t * digit);
        q *= 10n * i * (i++ * 2n - 1n);
        t *= u;
    }
}

let gen = pi();
let t = 0;

setInterval(() => {
    t += 1;

    console.log(`Digit ${t}: ${gen.next().value}`);
}, 1);

```

Then in a terminal run the following command in the directory where the code is located.

```
node index.js
```

Once you run the command, the digits should begin printing in the terminal.
