---
title: "b43legacy on dell 6000 wireless not working"
date: 2012-07-14
forum: Networking &amp; Wireless
---

### Post by vbdanl on 2012-07-14
hi. i have been struggling with this all day. my dell laptop usually sits too far away from router to use cable, so i have always used wireless on it, other than when installing new releases.  it was working fine with several previous versions of ubuntu, including lts 10.04.  i even had it working with 12.04 after much trial and error, but with newest kernel upgrade (3.2.0-26) it is no longer working.
```
i don't remember what i did to finally get it to working after upgrading to 12.04 from 10.04, but i do remember removing and reinstalling the b43 and firmware packages..just not sure what else i did to get it to work, and still can't seem to find the exact link that finally worked.
i have uninstalled and reinstalled the b43-fwcutter, b43-legacyinstaller, and removed the bcmwl-kernel-source packages many many times..
i have never seen anything in the "Additional Drivers" selection from Dash home.  i thought maybe i should after reinstalling these drivers, but not really sure.
i have read and tried using about every link i could find regarding my hdwe.
```

```
here are some current settings and info i hope will be useful:
dan@dell:~$ uname -a
Linux dell 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux

installed pkgs:
b43-fwcutter					install
firmware-b43-installer				install
firmware-b43legacy-installer			install

dan@dell:~$ dmesg |grep b43
[    1.718242] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.858796] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   20.974862] Registered led device: b43-phy0::tx
[   20.974995] Registered led device: b43-phy0::rx
[   20.975081] Registered led device: b43-phy0::radio
[   21.407451] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   21.407459] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   21.407465] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 3175.022141] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 3175.022149] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 3175.022155] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
dan@dell:~$
``` 

i have tried following the instructions at the website listed in dmesg, but still no luck..
thank you kindly for any help..

dan@dell:~$ lspci -vvnn |grep b43
	Kernel driver in use: b43-pci-bridge
dan@dell:~$ lspci -vvnn |grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)
dan@dell:~$

---

### Post by chili555 on 2012-07-14
Temporarily hook up the ethernet and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```Then detach the ethernet and let us have your report.

---

### Post by vbdanl on 2012-07-14
hi chili555.  thanks for the reply.
i ran the commands.. no errors.
when i unplugged the eth, i noticed the wireless option was "grayed out" or not selectable.  went into Addtl Hdwe and it still shows nothing.
am going to reboot and see if that does anything.

---

### Post by vbdanl on 2012-07-14
i plugged in eth cbl to post dmesg results:
```
dan@dell:~$ dmesg |grep b43
[    1.701523] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.014973] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   20.404703] Registered led device: b43-phy0::tx
[   20.404786] Registered led device: b43-phy0::rx
[   20.404866] Registered led device: b43-phy0::radio
[   22.001631] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   22.119540] b43-phy0: Radio hardware status changed to DISABLED
dan@dell:~$ dmesg |grep wlan
[   22.102920] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.106598] ADDRCONF(NETDEV_UP): wlan0: link is not ready
dan@dell:~$ dmesg |grep -i eth
[    0.165380] i2c-core: driver [aat2870] using legacy suspend method
[    0.165384] i2c-core: driver [aat2870] using legacy resume method
[    1.788082] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.840231] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.861127] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:11:43:7b:4c:8d
[   18.462224] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.333014] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.991905] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.003688] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  759.000237] b44 ssb1:0: eth0: Link is up at 100 Mbps, full duplex
[  759.000244] b44 ssb1:0: eth0: Flow control is off for TX and off for RX
[  759.000603] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  769.872061] eth0: no IPv6 routers present
dan@dell:~$
``` 
not sure if this matters, but is in blacklist.conf file:
# replaced by b43 and ssb.
blacklist bcm43xx

---

### Post by chili555 on 2012-07-14
```
Radio hardware status changed to DISABLED
```Interesting! May we see:```
rfkill list all
```Thanks.

---

### Post by vbdanl on 2012-07-14
i tried to boot up old ubuntu (version 6 and 9) live cd's. did not have any luck connecting to wireless with them.  wonder if i installed something that borked up my wireless during all the trial and errors i went thru..
rebooted from hd, and ran rfkill list all
0: phy0: Wireless LAN
  Soft blocked: no
  Hard blocked: yes

i am posting this from a desktop sitting next to the laptop.
my daughter has a laptop running win7 at it connects to wireless without a problem, so i know the trendnet router still works..

---

### Post by chili555 on 2012-07-14
> 0: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]That typically means the wireless switch on your laptop is set to OFF. Can you find it and turn it on?

---

### Post by vbdanl on 2012-07-14
> **chili555 said:**
> That typically means the wireless switch on your laptop is set to OFF. Can you find it and turn it on?

you r exactly right.  while i was waiting on your reply, i googled for the hardblock and found a link that described a similar problem.  they had to press fn f8 to turn on their wireless.  i have often used fn 8 to switch to my attached monitor, because the laptop monitor is toast for the most part.
the dell has a "A" type symbol over the F2 key.  i pressed it during a reboot, and now wireless works perfectly.  am sure that is what you were telling me to do also.  thanks a million for your help.

---

### Post by vbdanl on 2012-07-14
forgot to mention that at some point in time, i must of pressed fn f2 by mistake when i was trying to press ctrl alt f2 to bring up a login window or ctrl alt f1 and i just fat fingered it..  thanks again chili555 !!

---

### Post by vbdanl on 2012-07-14
here is the output now..
dan@dell:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
dan@dell:~$

---

### Post by chili555 on 2012-07-14
Glad it's working by whatever means. Have fun!

---

