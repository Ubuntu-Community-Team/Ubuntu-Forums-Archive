---
title: "ati drivers messing up x11"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by br men on 2006-06-05
with a clean install i can install wine.
Winecfg works then.

however, after installing the ati drivers i get this error
```

br_men@desktop:~$ winecfg
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

```
tried method 1 and 2 of this site:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I tried re-installing the entire system and install wine and ati drivers again, same problem.

What am i doing wrong?

ps: using the patched wine for WoW

---

### Post by tmilam on 2006-06-05
Do you have other information that leads you to believe that's related to your video card drivers?

Forgive me for not seeing it....

[edit] ok, i see now! 

is that the 'ati' driver or 'fglrx' driver?

---

### Post by br men on 2006-06-06
its the fglrx drivers.

---

### Post by br men on 2006-06-06
Anyone?

---

### Post by br men on 2006-06-06
Anyone at all?

---

### Post by gederoth on 2006-07-29
i get the EXACT SAME MESSAGE!!!!  

only i'm running an nvidia 6800gs.  Everything else works fine with my gfx drivers.  twinview, xgl, compiz.  they all run great.

wine 0.9.18 is what i setup.  not a glitch on setup at all.  can't find a thing wrong...  except that stupid error message.

---

