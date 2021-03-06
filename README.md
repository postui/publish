# Publish

**Publish** your module with one command in [Deno](https://deno.land).

### Installation

```bash
deno install -A -f -n publish https://deno.land/x/publish@v1.13.1/cli.ts
```

or use [land](https://deno.land/x/land) without installation:

```
land publish
```

### Usage

```bash
$ cd $YOUR_MODULE_DIR
$ publish

  1 → v1.0.1
  2 → v1.1.0
  3 → v2.0.0
  4 → v1.0.0-alpha.1
  5 → v1.0.0-beta.1
  6 → v1.0.0-rc.1

upgrade to: ▏
```

**Publish** will create a `version.ts` file in your module root directory if it doesn't exist.

```ts
export const VERSION = '1.0.0'
```

### Hook Functions

You can add hook functions in the `version.ts` to do some tasks before or after publish:

```ts
/** `prepublish` will be invoked before publish, return `false` to prevent the publish */
export async function prepublish(version: string) {
  console.log('on prepublish', version)
}

/** `postpublish` will be invoked after published */
export async function postpublish(version: string) {
  console.log('on postpublish', version)
}
```
