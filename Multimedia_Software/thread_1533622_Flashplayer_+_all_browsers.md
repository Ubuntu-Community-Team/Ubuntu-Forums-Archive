---
title: "Flashplayer + all browsers"
date: 2010-07-18
forum: Multimedia Software
---

### Post by H0lyGanGs7eR on 2010-07-18
Hello I have two machines with Ubuntu at home. I have the same problem - when I play some clips in youtube and surf in other tab in another site which uses flashplayer, my clip in youtube stops. The flash window in the page is gone like I have no flashplayer installed. Please give some issue!

---

### Post by lovinglinux on 2010-07-19
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by H0lyGanGs7eR on 2010-07-20
/usr/lib/flashplugin-nonfree/libflashplayer.so

Shockwave Flash 10.0 r45

---

### Post by lovinglinux on 2010-07-20
> **H0lyGanGs7eR said:**
> /usr/lib/flashplugin-nonfree/libflashplayer.so

Shockwave Flash 10.0 r45

That version has a critical vulnerability. You  should update it.

Install then run [FLASH-AID](http://flash-aid-extension.blogspot.com).

---

