# run-node

> Run the Node.js binary no matter what

You can't always assume running `$ node file.js` will just work. The user might have the `node` binary in a non-standard location. They might be using a Node.js version manager like `nvm`, which is sourced in a subshell and not available from the outside. Or they might have `node` installed as a local dependency in an npm project. It also depends from where you're trying to run it. For example, GUI apps on macOS doesn't inherit the [`$PATH`](https://en.wikipedia.org/wiki/PATH_(variable)), so the `node` binary would not be found. Most projects that depend on Node.js just end up telling the user to manually set the full path to the `node` binary in some project specific settings. Now every project has to do this. [Ugh...](https://gist.github.com/cookrn/4015437) I prefer things to *just* work. With this module it will.

This Bash script uses some tricks to find the Node.js binary on your system and run it.

Can be used from any environment that can spawn a process (Shell, Python, Ruby, Swift, Objective-C, etc).

### npm

#### Install

```
$ npm install run-node
```

#### Usage

```
$ ./node_modules/.bin/run-node file.js
```

Or in an [npm run script](https://docs.npmjs.com/cli/run-script):

```json
{
	"start": "run-node file.js"
}
```

If the [`node`](https://www.npmjs.com/package/node) package is found in the local `node_modules` directory (for instance, if you have it installed as a [devDependency](https://docs.npmjs.com/files/package.json#devdependencies) of your npm project), this is the `node` binary that will be used.

### Manually

#### Install

Download the [run-node](run-node) file:

```
$ curl -sSLO https://github.com/sindresorhus/run-node/raw/main/run-node && chmod +x run-node
```

#### Usage

```
./run-node file.js
```

#### Customizable cache path and error message

The cache path and error message are defined by the `RUN_NODE_CACHE_PATH` and `RUN_NODE_ERROR_MSG` environment variables. You could use them in a script or add them to your `~.bashrc`.

Default config:

```sh
export RUN_NODE_ERROR_MSG="Couldn't find the Node.js binary. Ensure you have Node.js installed. Open an issue on https://github.com/sindresorhus/run-node"
export RUN_NODE_CACHE_PATH="/home/username/.node_path"
```

If the `RUN_NODE_CACHE_PATH` environment variable is defined explicitly, the script it points to will be sourced before looking for a `node` binary. You can use this script to override your `PATH` variable so that a specific `node` binary is found.

## Maintainers

- [Sindre Sorhus](https://github.com/sindresorhus)
- [Mathias Fredriksson](https://github.com/mafredri)

---

<div align="center">
	<b>
		<a href="https://tidelift.com/subscription/pkg/npm-run-node?utm_source=npm-run-node&utm_medium=referral&utm_campaign=readme">Get professional support for this package with a Tidelift subscription</a>
	</b>
	<br>
	<sub>
		Tidelift helps make open source sustainable for maintainers while giving companies<br>assurances about security, maintenance, and licensing for their dependencies.
	</sub>
</div>
