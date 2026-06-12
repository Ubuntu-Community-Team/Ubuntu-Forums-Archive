---
title: "Kworld USB 315U Help"
date: 2009-04-08
forum: Multimedia Software
---

### Post by wlbragg on 2009-04-08
Anyone successfully install a Kworld USB 315U? 
Would [http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)
have enough info or is it the right place to start looking to get this card working in Linux?
I don't know where to start. Even a pointer in the right direction to get started would be greatly appreciated.

---

### Post by xc3RnbFO8P on 2009-04-09
Read this:
[http://lists-archives.org/video4linux/26364-kworld-315u-help.html]("http://lists-archives.org/video4linux/26364-kworld-315u-help.html")
and here if they get it working:
[http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_315U]("http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_315U")

---

### Post by fmeng on 2009-06-06
I added experimental support for this board and submitted the changes.  Unfortunately I was only able to get the digital working.  Hopefully someone will step up and get the analog working in the future.  Check out the wiki for the location of the source tree.

---

### Post by CobaltSS on 2009-10-19
> **fmeng said:**
> I added experimental support for this board and submitted the changes.  Unfortunately I was only able to get the digital working.  Hopefully someone will step up and get the analog working in the future.  Check out the wiki for the location of the source tree.

any update on this? I also would really like to have this working.

---

### Post by fmeng on 2009-10-20
Digital is working..  No analog or input connector support yet (I haven't figured this part  out yet).  You will need to use the latest v4l tree and compile from source.

---

