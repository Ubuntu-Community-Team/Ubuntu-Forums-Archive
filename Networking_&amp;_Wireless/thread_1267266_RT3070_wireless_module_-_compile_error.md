---
title: "RT3070 wireless module - compile error"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by StuartN on 2009-09-15
I just bought an Edimax nLite USB High Gain EW 7711 UAn wireless adapter. I downloaded the appropriate RT3070 driver from the Edimax website, but I get a compile error:
```
/home/me/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1361: error: too few arguments to function ‘iwe_stream_add_point’
make[2]: *** [/home/me/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.o] Error 1
make[1]: *** [_module_/home/me/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-14-generic'
make: *** [LINUX] Error 2
```
Does anyone have any ideas? There is nothing more on the Edimax site.

---

### Post by StuartN on 2009-09-15
I have now found the non-branded driver RT3070STA from the Ralink website, downloaded, compiled and installed. Now I have a driver without any errors, but no wireless net connection:

"lsusb" lists a 7392:7711 device.
"sudo iwlist ra0 scan" includes my router's information
I am not getting an IP address.
I am on 32-bit Ubuntu 8.04.

What step am I missing?

---

### Post by StuartN on 2009-09-16
Edimax nLite High Gain USB adapter, product ew7711UAn, device code 7392:7711

This device works out of the box with Ubuntu 9.04 using the in-kernel RT3070 driver.

(yeah, it was easier to install a new OS and restore /home than mess with installation instructions....)

---

### Post by echo6 on 2009-09-19
Hmm, I got the same compile errors, I have the EW-7711UTn which identified with the same 7392:7711 id.

I'm using Ubuntu 9.04, but I am unable to configure the device.  It doesn't appear in NetworkManager.

---

### Post by StuartN on 2009-09-19
> **echo6 said:**
> I'm using Ubuntu 9.04, but I am unable to configure the device.  It doesn't appear in NetworkManager.

I compiled a version from the Ralink website, but it was unable to connect (recognized, scanned wireless etc, but unable to obtain an IP address via dhclient). I suspect the ra2870sta.dat file needs some fiddling.

After installing Ubuntu 9.04 it was recognized and it connected without any intervention. Unfortunately, its data speed is far worse than the cheap Belkin wireless-G that I was hoping to replace...

I am going to try wicd, which I just tried out on another PC and it connects quicker, and reconnects quicker after suspend.

---

### Post by purple_processor on 2009-11-07
Im also having the same problems with ralink 2870sta module  and the 2.6.31-14-generic kernel.

I Dhclient fails to get a lease but it works fine with my atk5k card and eth0 so dhclient does work.. my mac/hwaddr is not reported corectly 00:00:00:00:00
but if associated I can use
$ sudo ifconfig ra0 192.168.0.7
$ sudo route add default gw 192.168.0.1
and now the connection works.

dhclient -v  from the cli also fails with no offers.
Ive turned off ipv6 tried rt2800usb. tried udev rules and comping compat-wirless and rt2870 modules all fail with build error 2.

Theres a chanve that it talking wirless N and my access point is only G but Ive not been able to change the mode using /etc/Wireless/RT2870/RT2879.dat
I don't have Network-manager installed and normally use rutilt for wireless connections..

the card im using is a alfa networks  AWUS050NH lsusb reports as ralink:2770

Thanks

---

### Post by StuartN on 2009-11-09
> **purple_processor said:**
> Im also having the same problems with ralink 2870sta module  and the 2.6.31-14-generic kernel.

My card connected after upgrading to 9.04, and replacing Network Manager with Wicd is a real improvement (in fact I have replaced Network Manager on all machines now), but this card or chipset still has a very poor connection and data rate. It is not worth the effort of fault-finding for me given how cheap they are.

---

### Post by Hevydani on 2009-11-10
[U]Purple Processor-

[/U]Tried blacklisting "rt2800usb" in "/etc/modprobe.d/blacklist.conf"   ??

   cd /etc/modprobe.d

   sudo nano blacklist.conf

Add "blacklist rt2800usb" to the bottom line

   "CTRL+O" to write changes

   "CTRL+X" to escape

   REBOOT.

Worked for me, Hopefully does for someone else. ;)

---

### Post by marcris on 2009-11-15
Re blacklisting "rt2800usb" in "/etc/modprobe.d/blacklist.conf"

Thanks **Hevidani**; that worked for me too.

---

### Post by c-shadow on 2009-12-14
After a 2 afternoons of searching for drivers and compiling I finally got this adapter working in intrepid. The problem was i was compiling the wrong driver!
Somehow got mixed up in all these tutorials on the net and was building rt2870sta module while it's in fact rt3070 based adapter. It loaded fine, but the adapter wouldn't scan.
Adapter is Edimax EW-7711UAn:
[http://www.edimax.com/en/support_detail.php?pl1_idSelect=support.php%3Fpl1_id%3D1%26mwsp%3D1&pl1_id=1&pd_id=277&button=Go](http://www.edimax.com/en/support_detail.php?pl1_idSelect=support.php%3Fpl1_id%3D1%26mwsp%3D1&pl1_id=1&pd_id=277&button=Go)

Downloaded driver RT3070USB(RT307x) from here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
Compiled with the help of this thread: [http://ubuntuforums.org/showthread.php?p=8484606](http://ubuntuforums.org/showthread.php?p=8484606)

As for the error "iwe_stream_add_point" I didn't have it, but there is something in the documentation (README_STA_usb):
```

4> $make
	# compile driver source code
	# To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

```

```

uname -r
2.6.27-16-generic

```

Notice description in modinfo below, it says rt2870 :)
It seems the author took code from the existing 2870 driver, made changes to support 3070 and forgot to change the description. My adapter is the one with id 7392:7711. 
```

 modinfo rt3070sta
filename:       /lib/modules/2.6.27-16-generic/kernel/drivers/net/wireless/rt3070sta.ko
version:        2.1.2.0
license:        GPL
[COLOR="Red"]description:    RT2870 Wireless Lan Linux Driver[/COLOR]
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     490C020EB5EF0484E8F2833
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
[COLOR="Red"]alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*[/COLOR]
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.27-16-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

```

---

