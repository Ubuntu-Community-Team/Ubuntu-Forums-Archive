---
title: "HOWTO: Pandora as a Plugin in Rhythmbox 0.13.2"
date: 2011-12-05
forum: Multimedia Software
---

### Post by frogotronic on 2011-12-05
Hello,

  This guide was written Dec 5th, 2011 for Maverick Meerkat.

1) Install [Rhythmbox 0.13.2]("http://www.webupd8.org/2010/11/install-rhythmbox-0132-in-ubuntu-1010.html") from the WebUpD8 PPA.

2) Install the [Pandora plugin]("http://www.webupd8.org/2011/02/rhythmbox-pandora-plugin-now-available.html") from the WebUpD8 PPA.

3) Update the plugin to the one that works for Rhythmbox 0.13.3 [here]("http://www.webupd8.org/2011/05/rhythmbox-pandora-plugin-updated-for.html").

4) Install Pithos via Synaptic.

5) Fix the symlink based on this [workaround]("https://github.com/mzheng/rhythmbox-pandora/wiki/Pandora-updates").

[INDENT]With the following modifications:

You want to link to the proper libraries for Ubuntu (not Gentoo).

The proper package linkage is here:

```
ln -s /usr/share/pyshared/pithos ./pithos
```[/INDENT]

- CH

---

