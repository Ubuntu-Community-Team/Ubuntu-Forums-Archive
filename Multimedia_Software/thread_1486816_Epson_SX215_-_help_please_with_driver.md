---
title: "Epson SX215 - help please with driver"
date: 2010-05-18
forum: Multimedia Software
---

### Post by _Smiler_ on 2010-05-18
Hey, sorry if this is the wrong part of the forum, I can't see a part where printer problems would fit...let me know if you want it moved!

So, my problem is: I have 10.04 and an Epson SX215. Using the advice given [here]("http://ubuntuforums.org/showthread.php?p=8511014"), I found SX100 Gutenburg driver using the Printing utility in System>Administration. This picks up the printer, but when printing a test page, it just shoots out paper, sometimes ruining it with loads of jibberish symbols. So I clicked a few more links on that thread and ended up [here]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do") where I downloaded the tar.gz file of the "Epson ME Office 510, Epson Stylus NX215/SX210/SX215/TX210/TX213/TX219 " under "Image Scan! for Linux & Photo Image Print System Lite".

I navigated to the folder and ./configure

and it ended with:
```
cups-config missing
```

So I downloaded "libcupsys2-dev" after which ./configure ended with
```
checking for GDK_IMLIB... configure: error: Package requirements (imlibgdk) were not met:

No package 'imlibgdk' found
```

Where do I go from here? I hope I've provided enough info (sorry if it's too much). I'm still a bit of a newbie!

Oh, and I Googled "imlibgdk" and I came [here]("http://hany.sk/~hany/RPM/pkgconfig%28imlibgdk%29.html") so I searched for pkgconfig in Synaptic which gave me libextutils-pkgconfig-perl. Might that help? I don't like installing random things willy nilly even if I uninstall when I realise they're not needed as it seems to me it still clogs the system.

Am I going about all this the right way? When it comes to Ubuntu, I seem to spend more time on Google and this forum :S

---

