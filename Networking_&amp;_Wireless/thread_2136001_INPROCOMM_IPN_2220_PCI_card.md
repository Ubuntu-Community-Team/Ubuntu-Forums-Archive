---
title: "INPROCOMM IPN 2220 PCI card"
date: 2013-04-16
forum: Networking &amp; Wireless
---

### Post by cregy on 2013-04-16
Hi

We are trying to install the above wireless card drivers. We followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=1042480](http://ubuntuforums.org/showthread.php?t=1042480)

But when we ran sudo modprobe ndiswrapper we were getting Module ndiswrapper not found. We looked this up and found this page:
[http://askubuntu.com/questions/213360/how-to-fix-module-ndiswrapper-not-found](http://askubuntu.com/questions/213360/how-to-fix-module-ndiswrapper-not-found)

We now have ndiswrapper 1.58 installed on a lubuntu on 12.10.
iwconfig says: no wireless extensions on lo and eth0
ndiswrapper -l says:
neti2220 : driver installed
	device (17FE:2220) present

We have a graphical interface installed and this confirms we have the drivers neti2220 installed.

But we still can't see a wireless network.

Any ideas please?

Rich

---

### Post by chili555 on 2013-04-16
Are there any clues in the logs?```
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by cregy on 2013-04-19
Hi

Thanks for the prompt. Very useful. This is the answer:
ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
ndiswrapper (check_nt_hdr:147): kernel is 32 bit, but windows driver is not 32-bit; bad magic: 020B
ndiswrapper (load sys_files:199): couldn't prepare driver 'neti2220'
ndiswrapper (load_wrap_driver:121 couldn't load driver 'neti2220'
usbcore: regstered new interface driver ndiswrapper

I presume this means we are trying to load a 64 bit driver for a 32 bit system?

Thanks

Rich

---

### Post by chili555 on 2013-04-19
> I presume this means we are trying to load a 64 bit driver for a 32 bit system?Correct. Do you have the 32-bit files? I may have some if you don't. You will need to remove the files you have now before you proceed. Feel free to post back if you need additional guidance.

---

### Post by cregy on 2013-04-21
Your pointer was enough. We downloaded the correct files, installed and bingo - wireless was enabled. Thank you so much for all the help. You are a star.

Rich

---

