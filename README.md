# NodeJS + Typescript + Prettier + Jest + Vscode

This is scaffolding repo to develop a myriad of different javascript apps and
libraries. It comes in different _flavors_ organized in branches, all of them
for different purposes, setups and/or platforms:

| status   | branch              | description                                                                    |
| -------- | ------------------- | ------------------------------------------------------------------------------ |
| **done** | `master`            | main features will be added here before spreading out to the other branches    |
| **done** | `node-process`      | NodeJS _long-running_ processes (like an HTTP server)                          |
| todo     | `node-lib`          | Libraries to be used as a part of process or libraries that will run on NodeJS |
| todo     | `node-browser-lib`  | Libraries that must work on both sides, NodeJS and the browser                 |
| todo     | `browser-lib`       | Libraries for the browser only                                                 |
| **done** | `react-app-browser` | Frontend React Apps based on create-react-app                                  |

## Features

All the _flavors_ above include:

- [x] The option to write code in typescript, ES2018 or both.
- [x] First class support in visual studio code:
  - [x] Linting on the IDE by using tslint and eslint
  - [x] Auto format via prettier (support files like `.ts`, `.js`, `.tsx`, `.jsx`, `.json`, `.md` and more).
  - [x] run the current file on the IDE with a simple shortcut without the need of compile (babel-node is used for regular files and jest for tests).
  - [x] easy debugging.
- [x] Convenient ways to lint, fix and auto format the source code via yarn scripts
- [x] Testing with JEST:
  - [x] support for typescript and ES2018 without the need of any previous compilation.
  - [x] support for inline snapshots via prettier.
- [x] Easy configurable GIT Hooks to make testing, linting, type checking, code fixing and formatting, etc..

## How to start

1. Create a new repo in your local machine (or clone it from your account).
2. Add a new remote to it pointing to this one (we call it _upstream_ for this
   example): `git remote add upstream git@github.com:juanmait/node-typescript-prettier-jest-vscode.git`.
3. Fetch the latest data from _upstream_: `git fetch upstream`.
4. Now let's say you want to base your work on top the `node-process` branch
   from upstream, then: `git merge upstream/node-process`

Now you _master_ branch should contain the same content as the `node-process`
branch.

## How to sync

To integrate the latest changes that may have happened on \_upstream\_\_

```bash
# update upstream data
$ git fetch upstream

# merge your branch with the same branch from upstream as before
$ git merge upstream/node-process
```

---

## Get started

```bash
$ yarn install
# install dependencies

$ yarn start
# first compile and watch for changes
```

### Recommended vscode extensions:

- [prettier-vscode] - format almost all files (`.md`, `.js`, `.ts`, `.tsx`,
  `.json`, etc..) with one simple shortcut on the IDE.
- [vscode-typescript-tslint-plugin] - show linting errors in typescript files.
- [code-runner] - used to run the current open file in the IDE. The project have
  a script that will launch the file with NodeJS or JEST depending on the file
  extension.
- [jest-snapshot-language-support] - add syntax highlighting for your Jest
  [snapshots][snapshot-testing].
- [eslint-vscode] - show linting errors in javascript files.

### Vscode shortcuts reference:

- `CTRL+i`: auto fix/format current file using [prettier].
- `CTRL+ALT+N`: run the current file with [babel-node] if ends with `.ts` or
  `.js` or with [jest] if ends with `.test.ts`.

**Note**: auto format will also run on file save and/or paste (check config at
`.vscode/settings.json`).

---

## Scripts (yarn)

```bash
$ yarn build
# build for prod (it will run prebuild automatically)

$ yarn prebuild
# run `clean`, `fix`, `lint` & `checkTypes`

$ yarn compile
# compile all the `src/` folder and place the output in the `dist/` folder. It
# also generate the declaration files for typescript

$ yarn watch
# same as compile but keep watching for file changes

$ yarn test
# run all the test files using JEST

$ yarn checkTypes
# check for typescript errors

$ yarn compile:types
# generate typescript declaration only

$ yarn lint
# check for lint errors using tslint for `.ts` files and eslint for `.js`.

$ yarn fix
# run auto format and auto fix using `prettier-tslint` and `prettier-eslint`

$ yarn checkConflicts
# detect eslint/tslint configurations that can collide with prettier

$ yarn checkTslint
# check for any conflict between `tslint` and prettier configs. Run this when
# you add new rules to your tslint.json file. It will warn you about what are
# the rules that you should avoid.

$ yarn checkEslint
# same as above but for `eslint`

$ yarn clean
# remove the build folder
```

Check `package.json` files in the `"scripts"` field for more details.

---

## Git Hooks

Includes a _pre-commit_ hook that runs `fix`, `lint` and `checkTypes` in your
**staged files** to check for errors (auto fix them when possible) and check for
typescript errors before commits. It will **abort** the commit phase if errors
prevails after the auto fixing. It uses [husky] and [lint-staged] for that.

---

## Testing with JEST

Test also can be written in typescript or ES2018. [inline-snapshots] are
supported!

```bash
$ yarn jest # run all your tests with jest
```

NOTE: You can also run the current file test in the IDE with `ctrl+alt+n`.

---

## Typescript

The typescript configuration is pretty strict. Is up to you to make it less
restrictive if you want. Check `tsconfig.json`.

---

## Fork

- Clone or create a new empty repo.
- Add it as remote _base_: `git remote add base git@github.com:juanmait/node-typescript-prettier-jest-vscode.git`.
- Fetch remote info: `git remote update`.
- merge with _base_: `git merge base/master`.
- Update your `package.json` and the README to match your preference and commit.
- Set master to your origin: `git branch --set-upstream-to=origin/master master`.
- Push to origin: `git push origin master`.

## Sync

Integrate the changes in this repo on yours.

```bash
# Place yourself in master (your repo)
$ git checkout master

# Set the **_base_** upstream
$ git remote add base git@github.com:juanmait/node-typescript-prettier-jest-vscode.git

# Update the remotes info
$ git remote update

# Merge with the branch `node-browser-lib` from **_base_**
$ git merge base/node-browser-lib

# Push to origin
$ git push origin master
```

## Links

**Dependencies:**

- [prettier]
- [eslint]
- [tslint]
- [jest]
- [babel]
- [tslint-config-prettier]
- [husky]
- [lint-staged]
- [babel-node]
- [prettier-eslint-cli]

[tslint]: https://palantir.github.io/tslint/
[prettier]: https://prettier.io/
[tslint-config-prettier]: https://github.com/prettier/tslint-config-prettier
[husky]: https://github.com/typicode/husky
[lint-staged]: https://www.npmjs.com/package/lint-staged
[jest]: https://jestjs.io/
[babel-node]: https://babeljs.io/docs/en/babel-node
[babel]: https://babeljs.io/
[eslint]: https://eslint.org/

**Vscode Extensions:**

- [prettier-vscode]
- [vscode-typescript-tslint-plugin]
- [code-runner]
- [jest-snapshot-language-support]
- [ESLint][eslint-vscode]

[prettier-vscode]: https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode
[vscode-typescript-tslint-plugin]: https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-typescript-tslint-plugin
[code-runner]: https://marketplace.visualstudio.com/items?itemName=formulahendry.code-runner
[jest-snapshot-language-support]: https://marketplace.visualstudio.com/items?itemName=tlent.jest-snapshot-language-support
[eslint-vscode]: https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint
[prettier-eslint-cli]: https://github.com/prettier/prettier-eslint-cli
[tslint]: https://palantir.github.io/tslint/

**Guides, references:**

- [snapshot-testing]
- [inline-snapshots]

[snapshot-testing]: https://jestjs.io/docs/en/snapshot-testing
[inline-snapshots]: https://jestjs.io/docs/en/snapshot-testing#inline-snapshots
