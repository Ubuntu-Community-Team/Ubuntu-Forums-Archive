---
title: "[SOLVED] Flash driving me bats"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by sumithar on 2007-09-18
I can watch youtube fine, and I understand that is flash based
But if I go to this site 
[http://pbskids.org/arthur/games/musicbox/music.html](http://pbskids.org/arthur/games/musicbox/music.html) 
it says I need the flash plugin.
Running feisty, firefox 2.0.0.6 on a celeron box.

I have followed all the instructions on
[http://plugindoc.mozdev.org/linux.html#Flash](http://plugindoc.mozdev.org/linux.html#Flash)
and copied the .so file to usr/lib/firefox/plugins and 
the .xpt file to usr/lib/firefox/components

to be on safe side I also copied both files to ~/.mozilla/plugins

No luck.

But if I go to 
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_15507&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_15507&sliceId=1)
It says 
Your Version Lnx 9,0,48,0

as does about:plugins

Any suggestions?

Thanks

---

### Post by Gremlinzzz on 2007-09-18
I get the same think there talking diffrent plugin like one of these
[https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)

---

### Post by w4ett on 2007-09-18
try this:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by sumithar on 2007-09-19
> **w4ett said:**
> try this:

```
sudo apt-get install flashplugin-nonfree
```



Thanks, I found that on this link later on and did that too
[http://www.psychcats.net/ubuntu/flash](http://www.psychcats.net/ubuntu/flash).

Just to be on the safe side I deleted the xpt and so file from the first go-around before I did that.  I noticed that after this process
a) both files have a later date, yesterday's oddly enough
and
b) this creates a link for both files in the /usr/lib/firefox/plugins (none in components)

Alas, no happiness!

---

### Post by sumithar on 2007-09-19
> **Gremlinzzz said:**
> I get the same think there talking diffrent plugin like one of these
[https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)

Thanks, but that link takes me to the same page as the one from the about:plugins page that I used earlier.

---

### Post by sumithar on 2007-09-19
OK- I sussed it.  The site uses Shockwave, not flash and there is no known Ubuntu support for Shock except Wine or vmWare.

---

