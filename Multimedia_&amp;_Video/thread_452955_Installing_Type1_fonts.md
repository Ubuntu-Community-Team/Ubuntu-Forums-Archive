---
title: "Installing Type1 fonts"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by UlyssesR on 2007-05-23
Here's how I managed to enable Type1 fonts in my local fonts directory.

First of all install the enscript package because you will need the mkafmmap program.

```
sudo apt-get install enscript
```

Now create the desired directory for the fonts. If it's under ~/.fonts it will be automatically recognized by the font cache.

```

mkdir ~/.fonts/afm
cd ~/.fonts/afm

```

Now copy all of your .pfb, .pfm and (perhaps) .afm files to that directory and run:

```

mkfontdir
mkfontscale
mkafmmap *
fc-cache -f -v

```

Works for me (under Feisty)!

---

### Post by kerry_s on 2007-05-23
it's suppose to be mkfontscale first then mkfontdir

---

