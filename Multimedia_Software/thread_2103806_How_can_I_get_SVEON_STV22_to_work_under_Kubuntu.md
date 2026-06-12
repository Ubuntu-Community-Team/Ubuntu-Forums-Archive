---
title: "How can I get SVEON STV22 to work under Kubuntu?"
date: 2013-01-11
forum: Multimedia Software
---

### Post by thunder130990 on 2013-01-11
Hi!

I'm trying to get my digital TV sintonizer to work under Kubuntu 12.10, and the latest post I found about it didn't end well and was from 2010 ([http://ubuntuforums.org/showthread.php?t=1458780]("http://ubuntuforums.org/showthread.php?t=1458780")). However, in the linuxtv.org wiki ([http://linuxtv.org/wiki/index.php/ITE_IT9135](http://linuxtv.org/wiki/index.php/ITE_IT9135)) I found that my device (Sveon STV22) is supported since kernel 3.2 (I'm with 3.5).

However, I do not even know which application would be better to use to watch TV if I got Kubuntu to recognize the TV sintonizer.

I'm hoping some of you guys could help me through the whole process, because I'm not sure about how to install this linuxtv.org libraries in order for them to update automatically and not give me trouble in the future, when I update the kernel.

I'll post all the information that I think may be useful for you.

- My computer is an MSI GE70 (i7-3630QM, Geforce GTX 660M, 8GB ram, 17.3" FHD) and I'm currently using bumblebee and primusrun for all the graphic intensive applications.

- I'm using kernel 3.5.0 and I try to keep it updated to the last one always. 

- dmesg | grep dvb gives the following output when I turn on my computer with the device plugged in:

```

dmesg | grep dvb
[   10.303646] dvb-usb: found a 'Sveon STV22 Dual DVB-T HDTV(IT9137)' in cold state, will try to load a firmware
[   10.304792] dvb-usb: did not find the firmware file. (dvb-usb-it9137-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)

```

- lsusb gives the following output with the sintonizer plugged in:
```

thunder@MSIGE70:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 1b80:e411 Afatech 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 004: ID 3938:1033  

```

And currently, I have not installed anything in order to get this to work, because I do not even know where to start. I hope you can help me and I promise to make a comprehensive summary of what I've done if we get it to work, so the next one finds it without all this trouble.

Thank you in advance,

---

