---
title: "Edimax EW-7318Usg USB wireless driver installation"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by hollywoodgunclub on 2009-06-06
I just built a computer for the first time and while getting it to boot and loading Jaunty was a breeze I can't finish the job with what I though would be the simplest part of the process: a little USB wireless adapter.

I used Synaptic to install the rt73 driver but nothing happened. I don't see wlan0 listed anywhere and I'm afraid if I just keep copying things in to the terminal I'm gonna screw this thing up. This is extra frustrating because Edimax says that Linux is supported by the adapter but has no documentation on it and when I loaded Jaunty on my netbook everything worked out of the box like a dream.

Any ideas? Or should I return this thing and go grab something that works out of the box from Best Buy or something? And if I go Best Buy can I get a suggestion for something similar?

---

### Post by lindsay7 on 2009-06-06
I have this adapter and it works out of the box, I did not have to add any drivers or do anything except plug it in. I bought this to replace a Linksys WUSB54GC which also worked out of the box but the range was not as good as the Edimax. There is Linux driver info on the cd that came with the camera but it needs to be compiled and I did not need it. I found out about the Edimax on Youtube and got it because it is supposed to work out of the box with Linux. You should see an icon on the top menu bar and if it is working you should see any wireless networks that are broadcasting, then you set up the wep or wpa password or passphrase in system/administration/network conncection.


Here is some more info.

[http://ubuntuforums.org/showthread.php?t=922463](http://ubuntuforums.org/showthread.php?t=922463)

---

### Post by nrvale0 on 2009-06-08
I have the same card but I've had no luck getting it to work with Jaunty. When I plug it in I get the following in dmesg:

```
Jun  8 17:44:24 **** kernel: [244732.296104] usb 2-2: new high speed USB device using ehci_hcd and address 29
Jun  8 17:44:25 **** kernel: [244732.567649] usb 2-2: configuration #1 chosen from 1 choice

```

The light on the NIC is not lit. I also don't see the device with 'lshw -C network'. rt73usb driver is loaded. 

Any ideas? :\

---

### Post by linorics on 2009-06-09
I'm having no luck also. I've started a thread to try and get to the bottom of this here 
```
[http://ubuntuforums.org/showthread.php?p=7426196#post7426196]("http://ubuntuforums.org/showthread.php?p=7426196#post7426196")
```

Could you tell me:

Where did you buy your card from?

How long ago did you buy the card?

What is the output of lsusb; before and after you insert the device?

---

### Post by nrvale0 on 2009-06-10
> Where did you buy your card from?

From NewEgg.

> How long ago did you buy the card?

About 2 weeks ago.

> What is the output of lsusb; before and after you insert the device?

Here's the diff -u:

```
--- /tmp/lsusb.1	2009-06-09 21:15:12.000000000 -0700
+++ /tmp/lsusb.2	2009-06-09 21:15:20.000000000 -0700
@@ -1,3 +1,4 @@
+Bus 002 Device 002: ID 7392:7318  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Thx for your help!

---

### Post by nrvale0 on 2009-06-26
bump

---

### Post by tuckie on 2009-06-27
I was able to get it working by modifying and compiling the drivers from [http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/) for the rt73.

I added the line ```
 {USB_DEVICE(0x7392,0x7318)},\
``` under Ralink towards the bottom of rtmp_def.h.

I've only done very preliminary testing so let me know how it goes.  The README walks you though the compile and modprobe fairly well.

edit: here's some more info on steps you might need (these are for the semi-reg version of the drivers, but most of the same should apply) [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

I'm not sure if the blacklisting is needed, due to the different device ID.

---

### Post by tuckie on 2009-06-29
whoops, wrong thread

---

### Post by n00b115 on 2009-07-12
"rtmp_def.h"  open this file 

```

/* EW-7318USg */\
{USB_DEVICE(0x7392,0x7318)},\

```

add this line.save,close & reinstall

---

### Post by ugm6hr on 2009-08-01
[http://ubuntuforums.org/showthread.php?p=7716964#post7716964](http://ubuntuforums.org/showthread.php?p=7716964#post7716964)

---

