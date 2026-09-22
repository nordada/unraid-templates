# unraid-templates

Community Applications template files for [nordada](https://github.com/nordada)'s Unraid apps. This repository doesn't contain any application source or Docker image itself - just the template XML Community Applications uses to list and configure each one. It exists so all of nordada's templates live in one registered CA repository instead of one per app.

- **[Domestique](https://github.com/nordada/domestique)** (`domestique.xml`) - a boutique PVR for bike racing.
- **[Paddock](https://github.com/nordada/paddock)** (`paddock.xml`) - a boutique PVR for racing events generally (cycling and Formula 1 ship built in).

For setup instructions, support, or to report an issue with either app, use that app's own repository - not this one.

## Icons

`icons/ava.png` is the shared AVA mark used as the Docker icon for nordada's
own compose-managed containers on Alcazar. Unraid can't attach a template to a
compose-created container, so those stacks set it through the
`net.unraid.docker.icon` label instead, pointing at this repo's raw URL:

```
https://raw.githubusercontent.com/nordada/unraid-templates/main/icons/ava.png
```

It lives here because the label value is rendered straight into an `<img src>`
by the Unraid webgui, so it has to be an http(s) URL the browser can reach. A
filesystem path does not work (see below), and the app repos it would otherwise
live in are private, which rules out their own raw URLs.

**A filesystem path in that label silently fails.** Both
`/mnt/user/appdata/<app>/icon.png` and `file:///mnt/user/appdata/<app>/icon.png`
were in use on Alcazar and both rendered the "?" fallback, because the browser,
not the server, is what fetches the value.
