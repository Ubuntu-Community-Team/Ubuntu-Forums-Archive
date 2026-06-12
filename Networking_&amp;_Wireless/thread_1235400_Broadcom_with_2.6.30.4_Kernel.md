---
title: "Broadcom with 2.6.30.4 Kernel"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by jonathanmotes on 2009-08-09
Hello all,

I upgraded Ubuntu 9.04 netbook remix to the 2.6.30.4 kernel to fix sound, Ethernet, and webcam issues on a HP mini 1000 (works wonders)...However, it of course broke my broadcom 4312 wireless card. 

I have tried installing b43-fwcutter. I let it download the firmware that I needed and after I rebooted I opened up the Hardware Drivers app. It said that the Broadcom driver was in use, but I have no wireless. Are more steps required here?

From lspci, here's my card:
```
01:00.0 Network Controller: Broadcom BCM4312 802.11b/g (rev 01)
``` 

Thanks everyone for your help and let me know if you need for info...

---

### Post by arky on 2009-08-09
try connecting to wifi with iwconfig commands.


$ iwconfig wlan0 mode managed
$ iwconfig wlan0 essid “WIFI”
$ iwconfig wlan0 key 1111-2222-3333-4444
$ iwconfig wlan0 channel auto

---

### Post by kevdog on 2009-08-09
I understand your frustration.  Do you know what driver you were using in the older kernel?  If you are really stumped you can boot to the older kernel selecting it from the grub menu at boot, and then take a look.  Most likely you will need to reinstall the wireless driver since its not included in the new kernel by default.  You will have to do this with every kernel upgrade, since technically some of the wireless driver are considered "custom".  Some custom kernel modules are included by default with the kernel and are simply not loaded at boot, other require recompilation and reinstallation (like ndiswrapper for example).

---

### Post by snowpine on 2009-08-09
I would recommend blacklisting b43 and using wl instead. It's the official Broadcom driver for your card. 

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Easiest way is if you can find linux-restricted-modules for your new kernel.

---

### Post by jonathanmotes on 2009-08-09
> **arky said:**
> try connecting to wifi with iwconfig commands.


$ iwconfig wlan0 mode managed
$ iwconfig wlan0 essid “WIFI”
$ iwconfig wlan0 key 1111-2222-3333-4444
$ iwconfig wlan0 channel auto

Running the first command gives me this: 
```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; No such device.
```

Thanks!

---

### Post by jonathanmotes on 2009-08-09
> **snowpine said:**
> I would recommend blacklisting b43 and using wl instead. It's the official Broadcom driver for your card. 

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Easiest way is if you can find linux-restricted-modules for your new kernel.
I'm a little confused on using that driver....does this mean I don't need b43-fwcutter?

I did try the instructions here for installing it: [http://ubuntuforums.org/showthread.php?t=896713&highlight=fwcutter+broadcom](http://ubuntuforums.org/showthread.php?t=896713&highlight=fwcutter+broadcom), but this command returned errors:
```
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`
```

I substituted `uname -r` for the kernel version, so that wasn't the problem....

---

### Post by snowpine on 2009-08-09
Try booting into the old kernel (with working wireless, right?) and using lsmod to see whether it uses b43 or wl... that is the module you'll want to use with the new kernel, too.

---

### Post by kevdog on 2009-08-09
Its likely you don't need b43cutter since that technology is fading a bit.  Its still a valid driver, but is quickly being replaced.

---

### Post by arky on 2009-08-09
You need to replace 'wlan0' with the name of wireless interface. Do a 'ifconfig' or 'iwconfig' to find out the details.

---

### Post by jonathanmotes on 2009-08-09
> **snowpine said:**
> Try booting into the old kernel (with working wireless, right?) and using lsmod to see whether it uses b43 or wl... that is the module you'll want to use with the new kernel, too.
It only shows the wl module...so does this mean I need to find a way to compile the driver for my kernel or do I just need to "link" the module? Sorry, I don't know a whole lot about how this works.

Thanks :)

---

### Post by jonathanmotes on 2009-08-09
> **arky said:**
> You need to replace 'wlan0' with the name of wireless interface. Do a 'ifconfig' or 'iwconfig' to find out the details.

With the old kernel the wireless is eth1 (which I found strange). With the new one eth1 doesn't show up.

---

### Post by snowpine on 2009-08-09
> **jonathanmotes said:**
> It only shows the wl module...so does this mean I need to find a way to compile the driver for my kernel or do I just need to "link" the module? Sorry, I don't know a whole lot about how this works.

Thanks :)

You will need to re-compile the wl driver each time you install a new kernel on your own other than the "official" Ubuntu kernel.

I see that Ayuthia is helping you in the other thread... hope that does the trick. :)

---

### Post by jambel on 2009-08-15
Hi, I had also a wifi problem and I've create a tutorial with steps I followed, hope that helps...
[http://jambelnet.blogspot.com/2009/08/ubuntu-904-jaunty-jackalope-with-26304.html](http://jambelnet.blogspot.com/2009/08/ubuntu-904-jaunty-jackalope-with-26304.html)

---

### Post by jonathanmotes on 2009-08-15
> **jambel said:**
> Hi, I had also a wifi problem and I've create a tutorial with steps I followed, hope that helps...
[http://jambelnet.blogspot.com/2009/08/ubuntu-904-jaunty-jackalope-with-26304.html](http://jambelnet.blogspot.com/2009/08/ubuntu-904-jaunty-jackalope-with-26304.html)

Wow...awesome job man! I learned a lot from your post. I was trying something similar, but was just missing some parts (and I was trying Gentoo patches - I didn't know where to get the Debian ones!). I will give this a try as soon as I can. 

Thanks!

---

### Post by jambel on 2009-08-17
> **jonathanmotes said:**
> Wow...awesome job man! I learned a lot from your post. I was trying something similar, but was just missing some parts (and I was trying Gentoo patches - I didn't know where to get the Debian ones!). I will give this a try as soon as I can. 

Thanks!

You're welcome, I'm really glad that help!

---

### Post by flemmingbjerke on 2009-11-29
In Karmic, Kubuntu, BCM4312 (wireless on hp 550) does not work out the box. System > hardwaredrivers finds two drivers for the card. The free driver (b43) does not work. The proprietary one (wl) works, but the very installation freeze your box. After reboot, it seems to fine. 

Thus, there is no need to compile your kernel, etc.

NB: Before you activate the proprietary driver, you must deactivate the free driver. Else, your kernel may be destroyed!!! (That was what happened on my box. My luck was that there was an older kernel in the grub menu. Else, I would have been a bit annoyed!!!)

---

### Post by arky on 2009-11-29
How to Configure Broadcom Wireless Drivers - [http://playingwithsid.blogspot.com/2009/09/configure-broadcom-wireless-drivers.html](http://playingwithsid.blogspot.com/2009/09/configure-broadcom-wireless-drivers.html)

---

