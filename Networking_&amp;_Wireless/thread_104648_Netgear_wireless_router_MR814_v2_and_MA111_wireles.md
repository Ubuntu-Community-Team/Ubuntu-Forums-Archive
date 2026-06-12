---
title: "Netgear wireless router MR814 v2 and MA111 wireless USB adaptor."
date: 2005-12-16
forum: Networking &amp; Wireless
---

### Post by br14n on 2005-12-16
This connects OK to router via USB adaptor when using XP on my Medion MD 2592 Notebook but I've been unable to connect when using Ubuntu. Any ideas please?

---

### Post by thezerogroup on 2005-12-16
Maybe this How To can help you: 

[http://www.linuxquestions.org/questions/answers/239]("http://www.linuxquestions.org/questions/answers/239")

Please post any problems you may encounter

---

### Post by br14n on 2005-12-20
Thanks for your help, I haven't replied before because I couldn't remember where I'd put the question.
I've unpacked the source in  /usr/src but when I  did make config I got make command not found! I think I don't have the kernel source. How do I get this. Sorry to ask so many questions but it is  several years and several different distro's ago since I complied any kernel code!

---

### Post by br14n on 2005-12-20
Thanks for your help, I haven't replied before because I couldn't remember where I'd put the question.
I've unpacked the source in  /usr/src but when I  did make config I got make command not found! I think I don't have the kernel source. How do I get this. Sorry to ask so many questions but it is  several years and several different distro's ago since I complied any kernel code!

---

### Post by br14n on 2005-12-20
Thanks for your help, I haven't replied before because I couldn't remember where I'd put the question.
I've unpacked the source in  /usr/src but when I  did make config I got make command not found! I think I don't have the kernel source. How do I get this. Sorry to ask so many questions but it is  several years and several different distro's ago since I complied any kernel code!

---

### Post by Lambert on 2005-12-20
You need to install a couple packages.

build-essentials
gcc 3.4
linux-headers-`uname -r`

---

### Post by br14n on 2005-12-21
I downut loaded the 2 files but make config gave me :- no rule to make target.
The device ID is 0845:4110, lshw -C generic gives configuration: driver=prism2_usb,
sudo lsmod | grep pr gives :- prism2_usb etc,
But I saw that Breezy won't work with v2 .
I  tried ndiswrapper but I  got over  my head so  I think that I   will give up for now.
So thanks for  your  tim!e & trouble.

---

### Post by nijinsky on 2005-12-21
[QUOTE=br14n]I downut loaded the 2 files but make config gave me :- no rule to make target.
The device ID is 0845:4110, lshw -C generic gives configuration: driver=prism2_usb,
sudo lsmod | grep pr gives :- prism2_usb etc,
But I saw that Breezy won't work with v2 .
I  tried ndiswrapper but I  got over  my head so  I think that I   will give up for now.
So thanks for  your  tim!e & trouble.[/QUOTE]

OK I'm a copmplete newbie and failed miserably with other methods of getting my belkin usb key working.

Until this morning whern I was pointed to this site.
[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

If you know where the windows .inf is then you can addapt this method to get it working. I managed to get onto my work wireless and a MS exchange server using it.

ATB
Bob

---

