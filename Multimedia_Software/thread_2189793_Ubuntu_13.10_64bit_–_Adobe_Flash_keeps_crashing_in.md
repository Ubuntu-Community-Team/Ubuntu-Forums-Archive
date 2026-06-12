---
title: "Ubuntu 13.10 64bit – Adobe Flash keeps crashing in Firefox and Chromium"
date: 2013-11-24
forum: Multimedia Software
---

### Post by Berduchwal on 2013-11-24
Firefox 25.0.1
Flash plugin:  Shockwave Flash 11.2.202.327 (11.2 r202)

System is up to date.

When on any video on Youtube if Firefox I get: The Adobe Flash plugin has crashed. Reload the page and try again. No report available.

When on any Video on Youtube in Chromium I get: "He's Dead, Jim!"

I tried:

```

sudo apt-get --reinstall install flashplugin-installer
```

I went to:

[https://www.mozilla.org/en-GB/plugincheck/](https://www.mozilla.org/en-GB/plugincheck/)

and it says: Shockwave FlashShockwave Flash 11.2 r202	vulnerable

Any suggestion what else can I try?

---

### Post by inspiral on 2013-12-07
I have exactly the same issue and have tried reinstalling. purging etc and the problems still reamains. Help please people :-)

---

### Post by Berduchwal on 2013-12-07
Problem for me was with graphic card drivers.
I ended up reinstalling ubuntu all together as x server stopped starting.

---

