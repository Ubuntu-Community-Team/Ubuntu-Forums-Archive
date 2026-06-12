---
title: "Karmic wi-fi issues"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by totallnoob on 2009-11-06
I need some help. I just updated to Karmic and all of a sudden i ran into a bunch of problems the biggest is it doesn't recognized that i have a wireless device. i dual boot and know for a fact that the signal is in range. the wireless device is Intel(R) WiFi Link 5100 AGN. I'm not very linux savy but all help is appreciated. 
Thanks a lot.

---

### Post by Crafty Kisses on 2009-11-07
You need the firmware, you can get the firmware from the Intel wireless website, here is the link: [http://intellinuxwireless.org/](http://intellinuxwireless.org/). I'm pretty sure I already found the firmware you need right [**here**]("http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz"). So download that then you need to make sure you have the build-essential package installed, you can do that by running:
```
apt-get install build-essential
```
Then once you have that installed, you can actually install the firmware by running:
```
tar -xzf iwlwifi*
```
Then you need to move the file to /usr/firmware, so run:
```
mv iwlwifi*/iwlwifi* /usr/firmware/
```
Then you need to load the module by running:
```
modprobe iwlagn
```
Reboot, and see if that gets you up and running.

---

### Post by agustin.g on 2009-11-08
Same issue here. I'm running 9.10, just updated from 9.04 which was working fine. Same Intel 5100 AGN.

Here's the output given by lspci -v

```
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: fast devsel, IRQ 16
	Memory at b6000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: <access denied>
	Kernel modules: sky2

08:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
	Subsystem: Intel Corporation Device 1201
	Flags: fast devsel, IRQ 17
	Memory at b6100000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn
```

and yet network tools finds nothing but the loopback interface. I tried installing build-essential but it seems like three dependencies (g++, g++4.4.1 and libstdc++) need each other in order to be installed and having dpkg install the three at the same time wasn't doing much either.

Finally, copying the files into /usr/firmware and launching the module via modprobe didn't have any effect whatsoever.

any help would be greatly appreciated

---

### Post by agustin.g on 2009-11-10
Found a fix!

[http://ubuntuforums.org/showthread.php?t=1307396]("http://ubuntuforums.org/showthread.php?t=1307396")

is the whole thread, or simply

[http://ubuntuforums.org/showpost.php?p=8215717&postcount=9]("http://ubuntuforums.org/showpost.php?p=8215717&postcount=9")

for the post that helped me fix it. It is essentially a rollback to the 2.6.31-12 kernel instead of the 2.6.31-14 shipped with Ubuntu 9.10. 

Hope it helps

---

### Post by totallnoob on 2009-11-11
agustin, i would really like to look at that thread but for some reason neither of the links are working. thanks for your help

---

### Post by Crafty Kisses on 2009-11-11
> **totallnoob said:**
> agustin, i would really like to look at that thread but for some reason neither of the links are working. thanks for your help

The link is mistyped. Here is the correct link.

[http://ubuntuforums.org/showthread.php?t=1307396](http://ubuntuforums.org/showthread.php?t=1307396)

---

### Post by agustin.g on 2009-11-12
thanks for pointing that out, i forgot to remove the http:// before posting the link. Just corrected it.

---

