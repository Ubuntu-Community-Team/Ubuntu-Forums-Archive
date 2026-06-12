---
title: "Texas Instruments ACX 111 - ndiswrapper - 64 bit"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by redbass on 2009-10-14
Hola 

I have an PCI Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface on my Desktop with installed Ubuntu 9.10-64.

I know that i can use Ndiswrapper, but don't have a Win driver (64bit)

With 9.04 i had use acx drivers, but in 9.10 kernel (2.6.31-13) i cant find module....

hemm... Where is it? #-o

Or... i can use some other Win 64bit driver....?

TNX

---

### Post by iliis on 2009-10-29
Hello
I've got the exact same problem (more or less, just plain old 32bit ;)): I have a US Robotics PCI Wlan Card (USR 805 416) which worked fine under Ubuntu 9.04 and before with acx, but not anymore with Ubuntu 9.10...

lspci -nn
```
05:02.0 Network controller [0280]: Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066]
```

According to the ID it may have an TNETW-1130 Chipsatz instead, but as I said, it worked perfectly fine. Is there any way to get the acx-module back? Why was it even removed?

thanks and greetings
iliis

---

### Post by dmizer on 2009-10-29
It's old, but you'll need this howto: [http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148) ... there's a link for downloading the Windows driver provided in the howto. You'll need to follow everything after the "Prepare the windows driver." section.

---

### Post by iliis on 2009-10-29
ok, I think I've found the answer: "Its not a bug, it's a feature!": _[https://bugs.launchpad.net/ubuntu/+bug/428276]("https://bugs.launchpad.net/ubuntu/+bug/428276")_

Looks like it's time to buy a new WLAN-Card (there aren't any drivers for Vista/Win7 either) or just carry on with cabling our house ;)

Ubuntu was so far a really great distro amongst others because it supported my wlan-card out of the box, but this is a bit disappointing :(

Compiling the acx-module myself fails with
```
root@Morpork:/usr/src/acx-20080210/acx-20080210# make -C /lib/modules/`uname -r`/build M=`pwd`
make: Gehe in Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'                          
  CC [M]  /usr/src/acx-20080210/acx-20080210/wlan.o                                           
In file included from /usr/src/acx-20080210/acx-20080210/acx.h:2,                             
                 from /usr/src/acx-20080210/acx-20080210/wlan.c:49:                           
/usr/src/acx-20080210/acx-20080210/wlan_compat.h:224: error: conflicting types for &#8216;irqreturn_t&#8217;
include/linux/irqreturn.h:16: note: previous declaration of &#8216;irqreturn_t&#8217; was here              
make[1]: *** [/usr/src/acx-20080210/acx-20080210/wlan.o] Fehler 1                               
make: *** [_module_/usr/src/acx-20080210/acx-20080210] Fehler 2                                 
make: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'  
```

so long, illis

Edit: just saw your post dmizer, actually i have original drivers from USRobotics, but I'll try this method...

---

### Post by dmizer on 2009-10-29
> **iliis said:**
> Edit: just saw your post dmizer, actually i have original drivers from USRobotics, but I'll try this method...

Yeah, use the Linksys drivers as I know for sure that they work.

---

### Post by iliis on 2009-10-29
Hah, get it to work! :D
The key was to use the network-manager after installing the ndiswrapper-drivers instead of just trying to force a connection per console somehow.

Thanks dmizer, you saved me some bucks ^^

---

### Post by dmizer on 2009-10-29
> **iliis said:**
> Thanks dmizer, you saved me some bucks ^^

No problem.

Do me a favor though, and PM me with the steps you took to get it working. Looks like I'll have to revive my howto ;)

---

### Post by iliis on 2009-10-29
Actually your howto worked just fine. Again many thanks for that and for your fast help :)

I tried to connect to my AP (encrypted with WEP) per command line first (editing /etc/interfaces/networking and using ifdown/ifup/ifconfig etc), but somehow that didn't gave me a connection.
So I started the network-manager (nm-applet) which I disabled a long time ago when it was still rubbish. Then I just clicked on my wlan, entered my key and done :)

greetings
illis

(I'm writing this over my wlan, so yes, it works, it even survived a restart. Somehow I have problems writing in this forum with firefox but that's a different topic...)

---

### Post by dmizer on 2009-10-29
> **iliis said:**
> Somehow I have problems writing in this forum with firefox but that's a different topic...

If you're using adblock in firefox, click on the down arrow next to the ABP icon in the navigation toolbar (far right). Then, put a checkmark in the "disable on ubuntuforums.org" option.

---

### Post by iliis on 2009-10-29
Hm, doesn't change anything, still "The message you have entered is too short. Please lengthen your message to at least 1 characters." (I've installed clearly too much plugins xD)
But really, it's ok. I've got a bunch of other browsers and I'm not writing much on ubuntuforums.org. Besides, it's completely OT ;)

EDIT: It was noscript blocking yahooapis.com ^^

---

