---
title: "abcde testing"
date: 2015-01-03
forum: Multimedia Software
---

### Post by andrew.46 on 2015-01-03
I have been working on the cd ripper abcde for the last little while and thought I would start a dedicated thread for any who would like to test patches on the git abcde that will eventually become the next release version. Rather than hijack my own and others' threads :).

First patch is one to address the issue of tagging mp3s with eyeD3 which under abcde 2.6 has been problematic: works fine with newer releases after eyeD3 0.7.0 but fails with releases in the 0.6.0 series. This patch by [Matthias Andree]("https://code.google.com/p/abcde/issues/detail?id=116") (with a small addition for the --comment option by yours truly) addresses this issue by version sniffing and setting correct options for each version. I have tested with eyeD3 0.6.14 and eyeD3 0.7.5 (which is the most recent release).

The patch numbers will be a little out as I have a few changes queued to push while sorting out my git access :(.

---

### Post by andrew.46 on 2015-01-04
Back to work tomorrow but a final preview patch where wavpack encoding is introduced to abcde. This is my own work and needs a little fine tuning yet but it certainly works as it is. Patch attached...

4 options needed for wavpack in ~/.abcde.conf:

```

WVENCODERSYNTAX=wavpack
WVENC=wavpack
WVENCOPTS='-hx3'
OUTPUTTYPE="wv"

```

And this will get things going :)

---

