---
title: "ndiswrapper query"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by vanspud on 2010-09-25
Hello,

I am trying to install windows wireless drivers using ndiswrapper to have better connectivity around my house(I can only currently get online in certain rooms, very restricted).

I have ndiswrapper installed OK, but I am a bit lost on the step where I have to browse to my windows wireless driver(a .inf file I believe), my question is how do I know where this is? I can't seem to locate it at all. I'm running on windows vista.

Any advice is most appreciated. :)

---

### Post by mrhhug on 2010-09-25
you don't need ndiswrapper if your in windows... ndiswrapper is for when your usuing linux and want to use a windows driver

---

### Post by vanspud on 2010-09-25
I know that, I m using Linux, I'm using Ubuntu...I meant my windows version is vista encase that made a difference. I dual booted Ubuntu on and am trying to get it fully functional.

---

### Post by bluesscream on 2010-09-25
identify your hardware by ```
lspci
``` or ```
lsusb
```, go to this page and try to find the fitting driver 
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)
good luck!

---

### Post by mrhhug on 2010-09-25
you can get this file from the network card manufacturers website,like if its a netgear card, then go to [www.netgear.com](www.netgear.com) , then click on support and enter your specific cards info and download the driver, the .ini will be contained in that download

---

### Post by bkratz on 2010-09-25
> **vanspud said:**
> I know that, I m using Linux, I'm using Ubuntu...I meant my windows version is vista encase that made a difference. I dual booted Ubuntu on and am trying to get it fully functional.

Please keep in mind that ndiswrapper generally really doesn't like Vista drivers, it really only works well with XP versions.

---

### Post by vanspud on 2010-09-25
I installed a driver there from a download based on the info I got from the commands I typed but its saying "invalid driver", I'll keep at it anyway now I've a bit more of an idea.

Dam vista, thanks for feedback all!

---

