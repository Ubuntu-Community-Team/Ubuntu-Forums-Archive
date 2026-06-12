---
title: "Atheros AR8162 wired Ethernet -- no driver?"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by ravenpi on 2013-04-30
Hi, all.  I just bought a new Asus X201E.  Ironically, it *came* with Linux, but before I installed Ubuntu on it myself, I live booted and checked the usual points of failure: WiFi, touchpad, etc.  Never even considered that the wired NIC might not work.  Booted up fine in Ubuntu... but no eth0.  "ifconfig -a" shows its lack.  dmesg makes no mention of the 8162.  (The only mention of Atheros is for the WiFi.)  lspci *does* show it -- so it's not like it's disabled in the BIOS or something -- but just no driver.

Anyone have any idea?  I even insmod'd all the .ko files a "locate -i atheros | grep '\.ko'" kicked back.  Stumped.

Thanks,

-Ken

---

### Post by chili555 on 2013-04-30
Please post:```
lspci -nn | grep 0200
```Thanks.

---

### Post by ravenpi on 2013-04-30
ken@lorien ~ $ lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)

---

### Post by chili555 on 2013-04-30
> Atheros Communications Inc. AR8162 Fast Ethernet [[COLOR="#FF0000"]1969:1090[/COLOR]] Your device is supported by the driver alx which isn't present in earlier Ubuntu versions but is included in linux-image 3.5.0-27 and later including Ubuntu 13.04, although early indications are that it's a bit tricky (read: non-functioning). Do you have or can you borrow any wireless capability? What version are you running?```
arch
lsb_release -d
uname -r
```

---

### Post by ravenpi on 2013-04-30
Hey -- thanks!  I was on 3.5.0-somethinglessthan27, so I just did the ol' "apt-get update;apt-get dist-upgrade", and lo!  I now have NIC.  I *am* curious, though, as to how you were able to figure out the kernel:driver correlation.  Is there a lookup table somewhere?  What info did you use to find my particular NIC?

Again, thanks!

-Ken

---

### Post by chili555 on 2013-04-30
Ha ha ha!  Mostly, a zillion years of experience. Actually, the best tool I have is the device ID, in your case 1969:1090 and Google, which gives us:  [http://www.linuxfoundation.org/collaborate/workgroups/networking/alx](http://www.linuxfoundation.org/collaborate/workgroups/networking/alx)> 1969:1090 - AR8162 Fast EthernetAnd, of course, this:  [http://ubuntuforums.org/showthread.php?t=2056129](http://ubuntuforums.org/showthread.php?t=2056129) 

Then I chech for the existence of the module on my own system:```
modinfo alx
```Which shows me:> filename:       /lib/modules/3.8.0-19-generic/kernel/ubuntu/alx/alx.ko
version:        1.2.3
license:        Dual BSD/GPL
description:    Qualcomm Atheros Gigabit Ethernet Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
srcversion:     DEB551A4F9D0281F98F5F10
alias:          pci:v00001969d000010A0sv*sd*bc*sc*i*
alias:          pci:v00001969d000010A1sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="#FF0000"]1969[/COLOR]d0000[COLOR="#FF0000"]1090[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
depends:        mdio
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions I could also check earlier kernel versions:```
chili@Think410:~$ modinfo /lib/modules/[COLOR="#FF0000"]3.5.0-27-generic[/COLOR]/kernel/ubuntu/alx/alx.ko
filename:       /lib/modules/3.5.0-27-generic/kernel/ubuntu/alx/alx.ko
version:        1.2.3
license:        Dual BSD/GPL
description:    Qualcomm Atheros Gigabit Ethernet Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
srcversion:     DEB551A4F9D0281F98F5F10
alias:          pci:v00001969d000010A0sv*sd*bc*sc*i*
alias:          pci:v00001969d000010A1sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="#FF0000"]1969[/COLOR]d0000[COLOR="#FF0000"]1090[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
depends:        mdio
intree:         Y
vermagic:       3.5.0-27-generic SMP mod_unload modversions 
```

As you and the searchers may see, the device ID, Google and modinfo are *everything*. 

Like most things, it's really easy if you know how!

---

### Post by ravenpi on 2013-04-30
Awesome -- thanks.  I admit; I usually do use the PCI ID, but I had the model number of the NIC, and thought that would be sufficient.  As for modifno, thanks -- never noticed that particular command before.

Ah, well... even an old dog can learn new tricks. ;-)

Have a good 'un!

---

