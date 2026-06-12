---
title: "Problem with Netgear WNA1100"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by WhiteDwarf on 2011-01-09
I have a problem with a Netgear WNA1100 USB Wireless Device

Lucid Lynx 10.04

Laptop Compaq Evo N620C.

lsusb output:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9030 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Lines added to etc/modprobe.d/blacklist.conf:

blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist ath_pci
blacklist ath_hal

Using drivers from a 32bit Windows 7 installation, as Netgear now wrap up their drivers in a setup program. 

athur.sys 2.0.0.36
netathur.inf  

ndiswrapper -l output:

netathur : driver installed
    device (0846:9030) present

BUT

/var/log/messages:

Jan  6 08:19:25 gil-laptop kernel: [  222.945077] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Jan  6 08:19:25 gil-laptop kernel: [  223.124082] usb 1-1: reset high speed USB device using ehci_hcd and address 2
Jan  6 08:19:25 gil-laptop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver netathur
Jan  6 08:19:25 gil-laptop kernel: [  223.373278] usbcore: registered new interface driver ndiswrapper

I tried to set up a wireless connection in System -> Preferences -> Network Connections but
iwconfig outputs:
lo        no wireless extensions.

eth0      no wireless extensions.

- which leads me to believe am wasting my time until I solve 'couldn't load driver netathur'.

Is it because the drivers came from Windows 7 ?  Does anybody have XP drivers they could send me ?

---

### Post by walt.smith1960 on 2011-01-09
You're making this much more complicated than necessary.  I would uninstall NdisWrapper and restart--you don't need it.  Then download this:
[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)

Make sure you get the right one, version 1.0.1 ...Maverick fixed.  If you update the kernel you'll need to rerun the installer. Also, be patient on the second step--it may take 3-4 minutes.

edit: I would probably undo the ath_ blacklists as well.

---

### Post by WhiteDwarf on 2011-01-10
Thanks Walt - I will give this a try.

WhiteDwarf

---

### Post by WhiteDwarf on 2011-01-10
Walt, thanks for your advice, duly followed and I'm posting this via the WNA1100.

Thanks a lot.

WhiteDwarf

---

### Post by walt.smith1960 on 2011-01-11
You're welcome. I'm glad I could help.  Kudos to Vagrale13 for creating this.  If there were similar packages for other hardware not supported in the kernel,  setting up linux would be less a black art to the everyday user.

---

### Post by BigD77 on 2011-07-23
> **walt.smith1960 said:**
> You're making this much more complicated than necessary.  I would uninstall NdisWrapper and restart--you don't need it.  Then download this:
[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)

Make sure you get the right one, version 1.0.1 ...Maverick fixed.  If you update the kernel you'll need to rerun the installer. Also, be patient on the second step--it may take 3-4 minutes.

edit: I would probably undo the ath_ blacklists as well.

Is that the actual driver or just the installer?  I downloaded that and still nothing.

---

### Post by wildmanne39 on 2011-07-23
Hi, that looks like it is just the installer click on it to install the driver.

---

### Post by BigD77 on 2011-07-24
> **wildmanne39 said:**
> Hi, that looks like it is just the installer click on it to install the driver.

I clicked on it and still nothing.  But I downloaded the latest version.  Now how do I uninstall it so I can install the earlier version?

---

### Post by wildmanne39 on 2011-07-24
Hi, I am glad you got it working.

---

### Post by BigD77 on 2011-07-24
> **wildmanne39 said:**
> Hi, I am glad you got it working.

Working?  No.

---

### Post by wildmanne39 on 2011-07-24
Hi, sorry about that I meant to post that in another thread I have been working on.

You can open synaptic and see if it is in there, if not you can use this command.
```
sudo apt-get --purge remove packagename
```
Thank you

---

### Post by BigD77 on 2011-08-07
Got it now.  Thanks.
Life is good.

---

### Post by BigD77 on 2011-09-07
Got a new question.  I did a fresh install of Ubuntu 10.10, and I have to re-install the drivers every time I turn on the machine, or else no wireless.  I have to go to Applications>System Tools>ath9k_htc installer and re-install.  What can be done to correct this?

---

### Post by wildmanne39 on 2011-09-07
Hi if ath9k_htc is the driver you can make it persistent by doing this:
```
sudo su 
echo ath9k_htc >> /etc/modules 
exit
```
if unsure if that is the driver post the results of this command
```
lsmod | grep ath
```
and
```
lsusb
```
Thank you

---

### Post by BigD77 on 2011-09-07
ath9k_htc              42935  0 
mac80211              239388  1 ath9k_htc
led_class               2633  1 ath9k_htc
ath9k_common            2563  1 ath9k_htc
ath9k_hw              285208  2 ath9k_htc,ath9k_common
ath                    13033  2 ath9k_htc,ath9k_hw
cfg80211              139875  3 ath9k_htc,mac80211,ath

dennis@dennis-Inspiron-1100:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0846:9030 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by wildmanne39 on 2011-09-07
Hi, that looks like it you can run the command in my previous post and it should work.
Thank you

---

### Post by BigD77 on 2011-09-07
> **wildmanne39 said:**
> Hi if ath9k_htc is the driver you can make it persistent by doing this:
```
sudo su 
echo ath9k_htc >> /etc/modules 
exit
```
if unsure if that is the driver post the results of this command
```
lsmod | grep ath
```
and
```
lsusb
```
Thank you

Well, after using your suggestion, I was able to shut down and turn it back on without having to re-load the drivers!  Many thanks!  :biggrin:

---

### Post by wildmanne39 on 2011-09-07
Hi, your welcome! that is great would you mind clicking on my application for ubuntu membership and showing your support for me, if you want to support my membership that is.
Thank you

---

### Post by Bango19 on 2011-10-20
I can install the package fine, but i cant get it to run the actual driver install... I'm entering

```
sudo ath9k_htc-installer
```

but I'm getting errors like no such file or directory for the logs and the compat-wireless folder.

But the deb package IS installed!  I don't know what to do now can someone help?

---

### Post by jrev on 2011-11-01
so can we have this wifi working on the Ubuntu 10.4 lucid ?

---

### Post by kurt18947 on 2011-11-01
Bear in mind that using the installer from sourceforge is a two step process.  First download and install the .deb file.  THEN, (working from memory here) Applications -> System and look for something like ath9k_HTC installer.  Click on that and be patient.  The idea being that a kernel upgrade that kills the WiFI can be repaired without doing both steps, just do the second.  It worked every time I used it.

---

### Post by jrev on 2011-11-02
that was my solution 
[http://forum.ubuntu-fr.org/viewtopic.php?id=696511&p=2](http://forum.ubuntu-fr.org/viewtopic.php?id=696511&p=2)

---

### Post by jrev on 2011-11-03
see next post

---

### Post by jrev on 2011-11-03
remove your adapter then download & install :
[http://nl.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.60_all.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.60_all.deb)
then reboot your computer :P

---

### Post by jrev on 2011-11-07
Hi, what time is it on Ubuntu

---

### Post by jrev on 2011-11-07
hi

---

