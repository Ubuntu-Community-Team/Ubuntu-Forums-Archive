---
title: "Epiphany + flash + youtube = no working..."
date: 2010-07-29
forum: Multimedia Software
---

### Post by bomanizer on 2010-07-29
This is kinda wierd... flash works everywhere expect youtube when I'm browsing with Epiphany. Anyone else seen this happen?

---

### Post by lovinglinux on 2010-07-29
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by bomanizer on 2010-07-29
Shockwave Flash

    File: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

---

### Post by lovinglinux on 2010-07-29
Does it work in Firefox?

---

### Post by bomanizer on 2010-07-29
Yes.

---

### Post by bomanizer on 2010-07-29
Boy do I feel stupid, went through my settings and saw that I had the htm5 plugin enabled... LOL :D
I disabled it and now it's ok... though I cannot see why I had it enabled in the first place...?!

---

### Post by lovinglinux on 2010-07-29
> **bomanizer said:**
> Boy do I feel stupid, went through my settings and saw that I had the htm5 plugin enabled... LOL :D
I disabled it and now it's ok... though I cannot see why I had it enabled in the first place...?!

No problem.

---

