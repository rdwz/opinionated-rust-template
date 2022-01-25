## Opinionated rust template

This is opinionated template to kick off new rust project with less than minute with best practices that I have found useful.

## Usage

### Requirements

Since this is opinionated template some tools are required to be installed for 

```shell
cargo install just cargo-deny cargo-generate cargo-readme
```

### Generate project

Run and answer the questions:
```shell
cargo generate --git github.com/xoac/opinionated-rust-template
```

Go to the project you created and list all available commands
```shell
cd <PROJECT-NAME>
just --list
```

### Improvements 

To use completions for `just` you need to generate them with `just --completions <SHELL>`. Depending from shell you are using there will be stored in different places so you need to find where to store them.

For [fish] users on Linux system you can add completions by invoke this code:
```
just --completions fish > $HOME/.config/fish/completions/just.fish
```

## What this template contains?

Useful commands can be fund with `just --list` in project dictionary.

Here are some example commands:

1. `just tag-version` will:
    - check if your code can compile
    - run lints checks
    - check if `README.md` is in sync with `src/lib.rs` or `src/main.rs`
    - run tests
    - check if all files were committed
    - check if `CHANGLOG.md` contains information about this version
    - create git tag
    - push tag to remote
2. `just tag-and-publish` will:
    - run `just tag-version`
    - run cargo publish 


### Continuous Integration/Delivery
    Once a day:
    1. audit

    Push/PR:
    1. cargo clippy (cargo check with additional checks)
    2. cargo test
    2. cargo checkfmt
    3. cargo check dependencies (for updates)
    4. cargo check licenses (with cargo deny). By default it deny know licenses that are considered [viral](https://en.wikipedia.org/wiki/Viral_license).
    5. dry check of cargo publish

    Release tag:
    1. build for linux/windows/macOS

There is no cargo publish in CD. If you want one [here](https://github.com/rust-github/template/blob/db0d14be66dcd47e34b4946111b65b74c610cf4e/template/.github/workflows/cd.yml#L106-L121) is an example.

## License

This template generate project with [BSL-1.0] license that is similar to [MIT] but require license and copyright notice only for source. This is great license for open-source project that can be widely used. If you want more information about why you should use this BSL-1.0 for FOSS projects see [this blog post](https://pdimov.github.io/blog/2020/09/06/why-use-the-boost-license/).

## Credits:

    1. https://github.com/rust-github/template
    2. https://github.com/xoac/crates-io-lib-template


[BSL-1.0]: https://choosealicense.com/licenses/bsl-1.0/
[MIT]: https://choosealicense.com/licenses/mit/
[fish]: https://fishshell.com/