---
title: "WebGL on Chrome / FF beta for Intel card users"
date: 2011-01-19
forum: Multimedia Software
---

### Post by thejdev on 2011-01-19
Hi, is there a way to enable WebGL on a browser in Ubuntu for Intel mobile card users ? I run Ubuntu 10.04 (Lucid) on a Dell Inspiron 1525 with a 2 GHz Core2Duo T6400 processor and 3 GB of DDR2-RAM.

When I run chrome with the --enable-webgl and --enable-plugins options and open a website like [http://bodybrowser.googlelabs.com](http://bodybrowser.googlelabs.com) , the CPU goes haywire and I get logged out by force. I sought advice on this forum before ( [http://ubuntuforums.org/showthread.php?t=1665187](http://ubuntuforums.org/showthread.php?t=1665187) ) but I couldn't get a reply.

---

### Post by fatbuttlarry on 2011-12-27
Same problem here (Ubuntu 11.10 x64).  GLX Info meets the requirements, but Chrome says WebGL is not supported on my video card.

I was able to get the [Wormhole example]("http://www.chromeexperiments.com/detail/wormhole/?f=webgl") working in Firefox, but performance was unbearable.

It's a shame, because this probably works just fine on the same hardware setup in Windows, but WebGL is advertised to work on Linux too. :)

-Tres

---

### Post by Jakesploder on 2012-06-14
i have that same problem.ubuntu 11.04 X64 intel video card.

---

### Post by Jakesploder on 2012-06-14
I FIXED IT!!!
1.) go to chrome://flags
2.)find WebGL
3.)click enable
4.)click restart browser(or do it manually)
:-)

---

### Post by Jakesploder on 2012-06-29
I restarted my system and now it doesnt work:confused::confused::confused::confused::confused::confused::confused::confused::-k

---

