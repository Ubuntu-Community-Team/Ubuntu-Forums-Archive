---
title: "Belkin F5D7050 USB Wireless Help"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by ForensicsPro on 2006-02-25
I have the above usb wireless adapter. It doesn't show as a network adapter under administration - networking. 

If I go into device manager it shows like This:

         USB Controller
              Hub Interface
            Belkin 54g USB Network Adapter
                USB Vendor Specific Interface

I am trying to learn this stuff, but obviously I am missing something here. The adapter works on other windoze machines.

Any help would be appreciated. Running Ubuntu 5.10 btw.

Thanks Bill

---

### Post by mgrm on 2006-02-25
Have a similar problem, thou on my laptop the USB WIFI (Belkin) doesnt show up at all.. not in dmesg, device manager or lsusb.. and yes it works in Windows.. any one else that had this problem and solved it.. ?

---

### Post by Anomander on 2006-02-26
I got one of these working under a Suse distribution by using ndiswrapper.
Ndiswrapper comes with Ubuntu, but as yet I haven't got it working on this distribution. The version of ndiswrapper shipped with 5.10 crashes with the Belkin driver (as did Suse's distribution). The solution, I think, lies in a complete reinstallation of ndiswrapper, which requires the same version of gcc with which the Ubunto kernel was compiled.
Problem: Ubuntu ships with version 4 of gcc but was compiled with 3.34, which it doesn't put on the installation CD rom! Problems, then, compiling drivers.
Can't get on the net to get different gcc with which to recompile ndiswrapper without recompiling ndiswrapper. Catch 22.
Has anyone got the version of ndiswrapper used by Ubuntu 5.10 working with the Belkin driver?

---

### Post by lierodeath on 2007-01-08
No. I have the Belkin F5d7050 going in 6.10, but you need to use do the following to get it working:

> sudo updatedb
locate ndiswrapper
Delete all the files this displays, then

> locate loadndisdriver
Delete all those files as well.

Then download the source for the latest release of ndiswrapper from the ndiswrapper sourceforge site, compile and install (follow the INSTALL instructions found in the tarball).

Do the usual jazz with ndiswrapper -i driver.inf and so on, then use /Administration/Networking to turn your wireless interface off and on again.

This *should* work fine - although bear in mind that the windows drivers on the Belkin CD seem to cause kernel crashes every once in a while.

---

