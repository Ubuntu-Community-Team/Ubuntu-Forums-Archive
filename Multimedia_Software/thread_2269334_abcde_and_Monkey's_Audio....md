---
title: "abcde and Monkey's Audio..."
date: 2015-03-14
forum: Multimedia Software
---

### Post by andrew.46 on 2015-03-14
I would like to extend the commandline ripper abcde to include ripping and encoding to .ape. Not that difficult to add this support but a little more difficult will be adding in tagging support which seems to be essential for most people these days. The tagging should be APEv2 tags rather than ID3v* tags.

The easiest commandline tagger I have found so far is quite old: [apetag]("http://www.muth.org/Robert/Apetag/"), but it works well enough. Are there are any more modern taggers that people know of, and have some experience with, that would be more suitable than apetag?

---

### Post by andrew.46 on 2015-03-19
Looks like Robert Muth's application is the only solution at the moment and Monkey's Audio encoding has [now been added]("http://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=commit;h=b77373c6c56704f670d8d9ad9b82dd185f4dd408") to abcde:

```

Monkey's Audio encoding (re-)added

Encoding to Monkey's Audio (ape) using Monkey's Audio
Console (mac). Tagging with Robert Muth's 'apetag'.
Thanks to Shantiq for testing.

```

A very productive morning's work :)

---

