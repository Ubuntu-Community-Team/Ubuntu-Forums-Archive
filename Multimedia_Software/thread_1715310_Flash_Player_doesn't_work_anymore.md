---
title: "Flash Player doesn't work anymore"
date: 2011-03-26
forum: Multimedia Software
---

### Post by Faoesch on 2011-03-26
So I'm running a 64-bit Maverik Meerkat and there had been lots of problems with my laptop because of the graphic card (I don't know maybe it has something to do with this).
The Problem I have is that I started kubuntu normally like every other day and started firefox. The problem is when I wanted to watch a video it told me that I have to download the newest flash player... "well that is strange" I thought because it had worked for the last 4 month. I didn't even downloaded any updates. So I tried to install it with: 
```
sudo apt-get install flashplugin-nonfree
```
It didn't work either. So I downloaded the flash player myself from adobe and installed the libflashplayer.so into
```
/usr/lib/firefox-addons/plugins/libflashplayer.so
```
that didn't work either so now I'm stuck.

Hope someone can help me. Thanks in advance :)

---

### Post by johntaylor1887 on 2011-03-27
libflashplayer.so needs to go into /usr/lib/mozilla/plugins

Remove any other flash you have on the computer first.

---

### Post by Faoesch on 2011-03-27
Well, that didn't work either.

---

### Post by beew on 2011-03-27
Try the flash-aid plugin for firefox: automatically updates and optimizes flash and remove conflicting versions.

---

### Post by Faoesch on 2011-03-27
That was it. Thanks a lot :)

---

### Post by jim.hitch on 2011-03-27
> **beew said:**
> Try the flash-aid plugin for firefox: automatically updates and optimizes flash and remove conflicting versions.

Thanks

I'd had the same issue for months on the laptop I use for work (no great need for Flash, but irritating not having it).

I didn't know this plugin existed.

Thanks and thanks again.

---

