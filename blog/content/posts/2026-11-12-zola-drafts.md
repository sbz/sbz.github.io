+++
title = "Zola, drafts and GitHub Pages"
description = "How this blog is wired up: markdown posts, draft/published status, and deployment"
date = 2026-11-12
draft = true
tags = ["meta", "zola"]
+++

A static blog on GitHub Pages built with [Zola](https://www.getzola.org/).
Each post is a markdown file with frontmatter. Setting `draft = true` keeps a
post out of the published site, while `zola serve` still shows it locally for
preview.

```toml
+++
title = "My post"
date = 2026-11-12
draft = true   # -> hidden from public/, shown by `zola serve`
+++
```

## Code highlighting

Zola highlights code blocks with a syntax theme (here `substructure`, whose
accent matches the site). No JS needed.

```rust
fn main() {
    let x: u32 = 0x42;
    println!("hello from {} (no_std? {})", "rust", x == 66);
}
```

```c
#include <stdio.h>

int main(void) {
    /* embedded-ish */
    volatile unsigned int reg = 0xDEADBEEF;
    printf("reg = 0x%08X\n", reg);
    return 0;
}
```

## Deployment

Build with `zola build` and publish the `public/` directory. For this repo the
site already builds to `blog/`, so the result lands under `blog/public/`.

| Status | Frontmatter              | `zola build` | `zola serve` |
|--------|--------------------------|--------------|--------------|
| Draft  | `draft = true`           | hidden       | visible      |
| Live   | unset / `draft = false`  | visible      | visible      |
