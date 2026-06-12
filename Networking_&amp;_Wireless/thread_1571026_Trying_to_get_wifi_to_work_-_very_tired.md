---
title: "Trying to get wifi to work - very tired"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by Ccc56 on 2010-09-09
I have been trying to install the driver for my Intel 5100 wireless card. I got the "correct" driver from the Intel site for Linux, but cannot figure out how to install it even after reading READ ME. So I tried ndiswrapper and couldn't figure that out either. I can't find the files it is talking about. Maybe my brain hurts too much from trying to resolve this issue for the past couple of hours. Please help.

---

### Post by MaindotC on 2010-09-09
Instead of using ndiswrapper let's get the Linux driver installed.  Please paste the link to the driver download.

---

### Post by Ccc56 on 2010-09-09
[http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz](http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz)

That is the website that the Intel site redirects to.

---

### Post by bkratz on 2010-09-09
The card should have worked out of the box I believe, you may want to look at dmesg and see if you see the same messages he/she saw. 

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1533716](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1533716)

---

### Post by MaindotC on 2010-09-09
The directions are definitely difficult for someone unfamiliar with the kernel.  I'm reading through it to see if I can figure out but I definitely don't know how to do this off the top of my head.  However as bkratz said this device should work out of the box.  You should see three iwl drivers if you do:```
modprobe -l | grep iwl
```

---

### Post by Ccc56 on 2010-09-10
You know...I just realized the wifi card is working. I was tired last night and didn't realize it, but my computer is finding networks. It just won't let me log onto my network.

It is working just fine in Windows 7, but not Ubuntu 10.04.

By the way, here was the output:

kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko

However, I now realize my problem is something else.

---

### Post by Ccc56 on 2010-09-10
Holy crap do I feel stupid. I mistyped my password by one character.

It works now.

In the future I will try to hold off on computer troubleshooting until I've had some sleep.

Thanks.

---

### Post by MaindotC on 2010-09-10
It's cool np - I've had plenty of nights like that while in college frustrating myself over a project I had to complete.  Please mark the thread as solved.

---

