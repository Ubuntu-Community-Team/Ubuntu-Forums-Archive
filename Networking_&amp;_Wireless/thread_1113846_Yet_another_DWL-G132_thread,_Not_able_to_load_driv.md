---
title: "Yet another DWL-G132 thread, Not able to load driver, intrepid ibex"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by Neonlajt on 2009-04-02
Hi guys, I`ve been struggling with this usb dongle forever now, and as a last resort I`m going to make a post here (sorry bout that, I know there are heaps of posts, but none touches my problem).

Im running intrepid on a 32 bit plattform, with kernel
2.6.27-11-generic #1 SMP  i686 GNU/Linux

Im using the latest version of ndiswrapper (1.54) and version 1.30 of the DWL-g132 driver. 

My G132 is revision A2 and version 1.20.

I do all the necessary steps, I make, make install, ndiswrapper -i netagu5a.inf, ndiswrapper -m, depmod -a and at last I modprobe it.

Screens :

> installing neta5agu ...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64


Creating module 

> adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************


Then depmod -a and modprobe ndiswrapper.

The problem is that the system fails to load the driver somehow

Output
> [ 2201.946217] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeNumberProcessors'
[ 2201.946331] ndiswrapper (load_sys_files:206): couldn't prepare driver 'neta5agu'
[ 2201.948460] ndiswrapper (load_wrap_driver:108): couldn't load driver neta5agu; check system log for messages from 'loadndisdriver'


what cat /var/log/messages | grep loadndisdriver outputs

> 2 17:22:55 MediaCenter loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver neta5agu

So that is what is happening, I`ve tried a few versions of ndiswrapper, not been able to make anyone work with this driver. I have however had success with the original driver, where you load athmfwnl.ini as well, but that does support WPA, or at least not on my system :(. 

If anyone had this problem on intrepid ibex and now how to solve it, please help :)

Cheers

---

### Post by reelgenius on 2009-05-21
I don't know about the DWL-G132, but I was just trying to get a WUA-2340 working and I got the exact same error about 'KeNumberProcessors'.  All I did was use the 1.40 drivers instead of the 1.50 and it worked so I think it's just a command that's not supported by ndiswrapper yet.  I'm pretty sure both drivers support WPA for me though.  Not sure if WPA support is built into Ubuntu yet.  If not just get wpa_supplicant and it should work.

---

### Post by SteMMo on 2009-05-25
Hi there,
i own a dwl-g132 usb key too.
The usb device is present on the lsusb list and also the ndiswrapper loads the driver.
A green led on the top of the key is on.
I see the wireless network name but when i click on it, i'm not able to connect with it.
The blinking led (for activity) never flash ... :(

Any idea?

thanks

---

### Post by SteMMo on 2009-05-26
More details ..
ndiswrapper 1.53

I found the athfmwdl.inf and .sys only on an old version of the drivers (1.02).
I installed both the drivers, on the second one I received forcing parameter MapRegisters from 256 to 64' for 4 times.
The power led is on and for a millisecond also the activity led.
I see a couple of network with their names but when i select one of this I'm not able to connect and the activity light is not flashing.

PS: if the wep key was incorrect, will i have a message error??

Thanks

---

