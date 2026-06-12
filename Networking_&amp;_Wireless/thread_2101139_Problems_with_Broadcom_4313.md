---
title: "Problems with Broadcom 4313"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by jvano on 2013-01-03
> **Bucky Ball said:**
> Good news. Please mark thread as solved from 'Thread tools' at top right of this page to help others. Cheers, and enjoy the OS and the forums. ;)


Not working for me. my computer is one Aspire S3 -951.

Just after fresh installing 12.10 x64 , automatic software upgrade and broadcom bcm4313 disappear!.

Some dea ??

---

### Post by chili555 on 2013-01-03
Please let us see:```
lspci -nn | grep 0280
rfkill list all
dmesg | grep b43
```

---

### Post by jvano on 2013-01-03
> **chili555 said:**
> Please let us see:```
lspci -nn | grep 0280
rfkill list all
dmesg | grep b43
```

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

 rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

(i&#7743; using a ralink usb stick just now)

dmesg | grep b43 returns nothing

:popcorn:

---

### Post by chili555 on 2013-01-03
Although the original poster titled the thread 4313, as you see above, he has a 431**2**.> Broadcom Corporation [COLOR="Red"]BCM4312[/COLOR] 802.11b/g LP-PHY [[COLOR="Red"]14e4:4315[/COLOR]] (rev 01)You have a *different* device; an actual 4313:> Broadcom Corporation [COLOR="Red"]BCM4313[/COLOR] 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]]Your fix is to hook up the ethernet temporarily and do:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Detach the ethernet and your wireless should be working.

---

### Post by Bucky Ball on 2013-01-03
@ jvano: Your post has been moved to a thread of its own.

Please post new threads for your problems rather than hijacking already solved ones. You dilute your chances of getting help. Thanks.

PS: You can change the title of this new thread by clicking 'Go Advanced'.

---

### Post by jweber53 on 2013-01-03
This same card came in my new Acer Aspire One 725, and although the fix suggested here does get the drivers loaded, the performance is very poor. I'm running 12.10 with the new kernel that just came out today. 3.5.0-22 64 bit. I've also noticed it disconnecting and reconnecting occasionally. I watch the speed on System Monitor while I download. I see an initial burst of maybe 750 KiB/s and then sustained at only about 300 KiB/s. I'm curious to know if you notice the same behavior. 

I replaced it with a bcm4312 which seems quite happy with the wl module and I get sustained download close to 900 KiB/s, which is about my DSL maximum.

Another note is that with every new kernel I must repeat the steps of install the kernel headers and rebuilding the modules (wl.ko) as given above. I build the module differently than the procedure above:
```

dpkg-reconfigure bcmwl-kernel-source

```
Probably equivalent.

---

### Post by jvano on 2013-01-04
> **chili555 said:**
> Although the original poster titled the thread 4313, as you see above, he has a 431**2**.You have a *different* device; an actual 4313:Your fix is to hook up the ethernet temporarily and do:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Detach the ethernet and your wireless should be working.

oh !, you are absolutely right .

the istructions worked for me, but with a paintfull low speed.
I can attach my computer to the wify network, but inmediately the
transfer speed decreases from hundred kb/s to some kb/s.
Unusable at all.

---

### Post by jvano on 2013-01-04
[QUOTE=jweber53;12436832]This same card came in my new Acer Aspire One 725, and although the fix suggested here does get the drivers loaded, the performance is very poor. I'm running 12.10 with the new kernel that just came out today. 3.5.0-22 64 bit. I've also noticed it disconnecting and reconnecting occasionally. I watch the speed on System Monitor while I download. I see an initial burst of maybe 750 KiB/s and then sustained at only about 300 KiB/s. I'm curious to know if you notice the same behavior. 

I replaced it with a bcm4312 which seems quite happy with the wl module and I get sustained download close to 900 KiB/s, which is about my DSL maximum.

Another note is that with every new kernel I must repeat the steps of install the kernel headers and rebuilding the modules (wl.ko) as given above. I build the module differently than the procedure above:
[CODE]
dpkg-reconfigure bcmwl-kernel-source


after fix, i experiment the same behavior that you have described.

the speed oscilates and fall down to some kB/s .

(just removing the twelve screws on the bottom of my Aspire S3 to replace the b4313 board)

---

### Post by jweber53 on 2013-01-04
> **jvano said:**
> 

after fix, i experiment the same behavior that you have described.

the speed oscilates and fall down to some kB/s .

(just removing the twelve screws on the bottom of my Aspire S3 to replace the b4313 board)

Thank you for the confirmation. It's good to know I'm not crazy :)

Do you also have problems controlling the display backlight brightness? If so, see the thread I started here: 

[ Can't adjust display backlight on Acer Aspire One 725-0884]("http://ubuntuforums.org/showthread.php?t=2101078")


My Aspire One only has one cover screw:)

---

