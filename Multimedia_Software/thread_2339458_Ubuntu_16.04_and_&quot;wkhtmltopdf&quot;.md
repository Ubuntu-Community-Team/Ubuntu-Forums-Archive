---
title: "Ubuntu 16.04 and &quot;wkhtmltopdf&quot;"
date: 2016-10-09
forum: Multimedia Software
---

### Post by Kleenux on 2016-10-09
"**wkhtmltopdf**" is causing problems after the *16.04* upgrade (was ok on *14.04*).
> The switch --print-media-type, is not support using unpatched qt
and coredumps (wkhtmltopdf coredumps easily).

The support recommends to `purge` the package (**wkhtmltopdf 0.12.2.4**), and manually install **wkhtmltopdf 0.12.2.1** (with patched qt). 

What is Ubuntu policy regarding this:

- can we expect a "patched qt" package coming soon (*preferred*)

- or should we proceed with the manual install ?

---

