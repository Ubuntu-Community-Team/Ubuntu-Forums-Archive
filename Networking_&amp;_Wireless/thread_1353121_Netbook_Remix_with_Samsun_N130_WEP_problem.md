---
title: "Netbook Remix with Samsun N130 WEP problem"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by theadam on 2009-12-12
I finally got wireless working on my N130, but there is still a problem.  I can connect to a WPA network and a 40 bit WEP network through the network manager, but I cannot connect to a 128 bit WEP network.  It acts as if the WEP key is incorrect.  I can, however, connect to the same WEP network using iwconfig and dhclient, but thats just a hassle.  This is driving me crazy!  Thanks guys!

I am using ndiswrapper with the winxp realtek 8192 drivers.

---

### Post by vze326ff1 on 2009-12-19
I am have the sqme problem. I just bought a n130 samsung and I am not sure if it has a realtek or a atheros in it. I already installed ubuntu remix and updated it. I installed ndiswrapper and installed drivers for both atheros and realtek. realtek I get invalid driver and atheros I get hardware no persent. But if I go the system testing and perform network testing it saids it detects realtek semiconductor co. ltd device 8192 (rev 01) and realtek semiconductor co. ltd rtl8101e/rtl8102e pci express fast ethernet controller (rev 2) 
 I have a wireless light on and check my BIOS and it said wireless card on all the time. I hook ethernet cable up and it connects fine and I stole my kids Belkin wifi stick and it connects fine with that Please Help!!

---

### Post by theadam on 2009-12-29
I ended up emailing Realtek in order to get the r8192e pci linux drivers.  I installed them and then everything worked fine except when returning from sleep, everything froze, so what I then did was to make sure the modules were unloaded when put to sleep and reloaded when woken up.  Just make sure /usr/lib/pm-utils/sleep.d/55NetworkManager has something like this somewhere in it:

```
case "$1" in
	hibernate|suspend)
		modprobe -r r8192e_pci
		suspend_nm
		;;
	thaw|resume)
		modprobe r8192e_pci
		resume_nm
		;;
	*) exit $NA
		;;
esac
```

till now everything works great except sometimes i have to wake it up twice before its "fully" awake, but other than that, the wireless works great.

---

### Post by idavidmiller on 2010-01-12
I also used the Realtek Linux rtl8192e driver with a Samsung N130 netbook on Ubuntu 9.10  Remix and this worked for me. The details of the procedure I used can be found at:

[http://ubuntuforums.org/showpost.php?p=8644843&postcount=47](http://ubuntuforums.org/showpost.php?p=8644843&postcount=47)

I also had the sleep issues of #3 above. I used the fix shown above in #3 and so far this seems to have solved the sleep (suspend) and hibernate problems on my netbook.

I had no success with the ndiswrapper approach with 32-bit Windows XP drivers downloaded from Realtek for the rtl8192e chip. Since I was able to get Linux drivers to build and install I did not try other Windows drivers (2000, etc.) with ndiswrapper. I also was using 128-bit WEP so this may account for my problem also since the problem I had was similar to #1 and #2 above. I lost patience and switched to trying the Linux drivers instead of beating my head against the wall tying to figure out what was going on with ndiswrapper. I installed the package:

ndisgtk is a GTK+ based frontend for ndiswrapper, allowing an easy way to install Windows wireless drivers.

which works quite well for this if you want a graphical setup tool for ndiswrapper. It will probably complain about not being able to find hardware when you add the driver, but it then shows the hardware anyway when you click off the message. The network manager and panel applet show the SSID of the wireless device, but as above I was in a connect attempt loop over the WEP key. I would try to change the wireless setting to a WEP 40- bit key, but I did not try that because my wireless only supports 64- and 128-bit WEP keys. If I were stuck with ndiswrapper that is what I would try next if I could. I also did not try WPA-PSK with a passphrase instead of a key, which is the other security option my wireless device supports, so I don't know if that will work or not. If your wireless device has other options supported by Network Manager, then you might try those instead of WEP 128-bit key, if you have to use ndiswrapper.

---

