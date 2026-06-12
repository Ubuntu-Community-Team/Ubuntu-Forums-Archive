---
title: "Under what name do the non-proprietary BCM4318 drivers show up in lsmod? (Maverick)"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by james_mcl on 2011-04-26
Hi all,

I've just been trying to troubleshoot a problem by installing and activating the proprietary BCM4318 drivers instead of the ones that came with Maverick.

(This is in Maverick Meerkat, btw.)

I used System-Administration-Additional Drivers to install the new drivers. As far as I can tell from lsmod and [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) the new drivers are known as b43.

It didn't occur to me to run lsmod prior to this, and now I'm curious - what would the non-proprietary drivers that came with Maverick have shown as in the lsmod output?

Thanks,

James McLaughlin.

---

### Post by josephmills on 2011-04-26
hi there could we please see a ```
lsmod | grep b43 
``` and a ```
dmesg | grep b43 
``` also a ```
lspci -vnn | grep 14e4 
``` thanks

---

### Post by chili555 on 2011-04-26
> I used System-Administration-Additional Drivers to install the new drivers. As far as I can tell from lsmod and [https://help.ubuntu.com/community/Wi...Driver/bcm43xx](https://help.ubuntu.com/community/Wi...Driver/bcm43xx) the new drivers are known as b43.

It didn't occur to me to run lsmod prior to this, and now I'm curious - what would the non-proprietary drivers that came with Maverick have shown as in the lsmod output?The *non*-proprietary drivers are called b43 and ssb.

What is proprietary and installed later is the required firmware. That's why it's called 'Activate.' The drivers were and are present. The required firmware must be downloaded separately in order to activate b43. Many, but not all wireless drivers require separate firmware files. ```
$ modinfo b43
filename:       /lib/modules/2.6.35-28-generic/updates/compat-wireless-2.6.36/b43.ko
[COLOR="Red"]firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
firmware:       FW13[/COLOR]
license:        GPL

```

---

### Post by james_mcl on 2011-04-26
```

linuxuser@AMD64-ML34:~$ lsmod | grep b43
b43                   187964  0 
mac80211              267099  1 b43
cfg80211              170485  2 b43,mac80211
led_class               3393  1 b43
ssb                    46201  1 b43

```

```

linuxuser@AMD64-ML34:~$ dmesg | grep b43
[    1.195959] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   26.637805] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   26.960904] Registered led device: b43-phy0::radio
[   28.047954] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

```

```

linuxuser@AMD64-ML34:~$ lspci -vnn | grep 14e4
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```

Is there anything I can type into the terminal that will confirm that the proprietary firmware, and not whatever was on there before, is now what's running?

---

### Post by josephmills on 2011-04-26
> **james_mcl said:**
> ```

linuxuser@AMD64-ML34:~$ lsmod | grep b43
b43                   187964  0 
mac80211              267099  1 b43
cfg80211              170485  2 b43,mac80211
led_class               3393  1 b43
ssb                    46201  1 b43

```

```

linuxuser@AMD64-ML34:~$ dmesg | grep b43
[    1.195959] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   26.637805] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   26.960904] Registered led device: b43-phy0::radio
[   28.047954] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

```

```

linuxuser@AMD64-ML34:~$ lspci -vnn | grep 14e4
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```

Is there anything I can type into the terminal that will confirm that the proprietary firmware, and not whatever was on there before, is now what's running?

you wireless would not work with out what chili555 aka Jedi said that is the only proprietary part of the b43 you could remove the b43 installer and then do a ```
dmesg | grep b43
```
and you will see that the firmware is not installed you will get a error. Hope that this clears something up.:P

---

### Post by james_mcl on 2011-04-26
> 
you wireless would not work with out what chili555 aka Jedi said


There seems to be some misunderstanding here.

My wireless was working before, without my having gone to "Additional Drivers" and chosen to activate "Broadcom B43 wireless driver".

I decided to do so because, when troubleshooting a problem apparently unrelated to the wireless, I began to suspect that the wireless drivers and/or firmware were in fact involved, and decided to switch from what was currently in use to whatever proprietary options were on offer.

(If this doesn't work, I'll have to look at removing all wireless drivers and firmware of all sorts - and I'm finding this very difficult as what I can find installed in Synaptic certainly doesn't look like a complete driver and firmware.)

---

### Post by chili555 on 2011-04-26
> linuxuser@AMD64-ML34:~$ dmesg | grep b43
[    1.195959] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   26.637805] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   26.960904] Registered led device: b43-phy0::radio
[   28.047954] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)This certainly looks to me like the driver b43 and associated firmware are loaded. What is the difficulty you are having?

---

### Post by jasonmanchu on 2011-04-26
go here:
[http://ubuntuforums.org/showthread.php?t=1738740]("http://ubuntuforums.org/showthread.php?t=1738740&highlight=the+way+to+solve+bcm43xx")

An explanation of how to solve bcm43xx

---

### Post by james_mcl on 2011-04-27
@jasonmanchu,

I'm sorry, but your post is inaccurate, and is based on a significant misunderstanding of [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers). PLEASE take a look at my response in [http://ubuntuforums.org/showpost.php?p=10726162&postcount=3](http://ubuntuforums.org/showpost.php?p=10726162&postcount=3) and make some amendments; otherwise some of the people following your advice will be applying the wrong procedure for their wireless cards.

@chili555 (and anyone else who would like to know what the problem is that I'm trying to troubleshoot.)

As I said, I had no problems connecting via wireless at first, and indeed my problem appeared to be unrelated. (In fact, it may well be unrelated!)

I'm suffering from an intermittent "sticky keys"/"repeating keyboard" bug, possibly the one described at

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/124406?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/124406?comments=all) 
or
[https://bugzilla.kernel.org/show_bug.cgi?id=9448](https://bugzilla.kernel.org/show_bug.cgi?id=9448)

The bug does not affect my Ubuntu Hardy install (and did not affect its Dapper predecessor), but has affected my installations of Intrepid, Jaunty, Karmic, Lucid, and Maverick.

In trying to work out if there was any factor that might link the affected distros, it occurred to me that while I had had to use ndiswrapper to get wireless working in Hardy and Dapper, this had not been the case in more recent installs. If "more recent installs" went as far back as Intrepid (I can no longer remember) it might have been that something in the drivers/firmware installed was misbehaving, in a way that the Windows XP drivers installed by ndiswrapper had not been.

I had not hitherto gone to System - Administration - Additional Drivers to activate the proprietary Broadcom firmware, and I now decided to do so - perhaps it would be free of this problem. I then rebooted.

However, I then realised that I did not know a way of confirming that the non-proprietary firmware/whatever drivers were in use before were not running - I got the impression that the solution might involve lsmod but wasn't sure - and decided to ask the forums for help.

(I had been under the mistaken impression that it was drivers and not firmware I'd activated - my thanks to chilli555 for pointing this out.)

Although I'm still waiting for the keyboard problem to recur - it is intermittent - since activating the proprietary firmware yesterday it hasn't reared its ugly head, so I'm optimistic that this *has* had some effect - fingers crossed it stays that way!

---

