---
title: "Having problems with ndiswrapper rtl8187 driver after kernel update"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by buba13666 on 2012-05-29
Hi!
This is my first post here and I've done a lots of reading and this method worked for me. [https://wiki.archlinux.org/index.php/Rtl8187_wireless](https://wiki.archlinux.org/index.php/Rtl8187_wireless)
Now when I updated my Ubuntu 11.10 kernel my alfa AWUS036h card driver doesn't work anymore.
I installed the driver with ndiswrapper and it doesn't recognize my device anymore.
This is what I get with uname -a
3.0.0-20-generic #34-Ubuntu SMP Tue May 1 17:28:21 UTC 2012 i686 athlon i386 GNU/Linux
 
this is what I get when I enter dmesg |tail :
[ 374.408029] usb 1-2: new high speed USB device number 6 using ehci_hcd
[ 374.543465] hub 1-2:1.0: USB hub found
[ 374.543542] hub 1-2:1.0: 4 ports detected
[ 374.816170] usb 1-2.3: new high speed USB device number 7 using ehci_hcd
[ 374.996169] usb 1-2.3: reset high speed USB device number 7 using ehci_hcd
[ 375.093692] ndiswrapper (mp_init:219): couldn't initialize device: C0010006
[ 375.093701] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[ 375.093712] ndiswrapper (mp_halt:262): device f19a5480 is not initialized - not halting
[ 375.093716] ndiswrapper: device eth%d removed
[ 375.093744] ndiswrapper: probe of 1-2.3:1.0 failed with error -22
This is what I get when I type in dmesg | grep -e ndis -e wlan :
[ 14.634637] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[ 15.055791] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,03/31/2010,6.1163.0331.2010) loaded
[ 15.064167] ndiswrapper (mp_init:219): couldn't initialize device: C0010006
[ 15.064175] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[ 15.064188] ndiswrapper (mp_halt:262): device f42ac480 is not initialized - not halting
[ 15.064193] ndiswrapper: device eth%d removed
[ 15.064217] ndiswrapper: probe of 1-2.3:1.0 failed with error -22
[ 15.064571] usbcore: registered new interface driver ndiswrapper
[ 375.093692] ndiswrapper (mp_init:219): couldn't initialize device: C0010006
[ 375.093701] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[ 375.093712] ndiswrapper (mp_halt:262): device f19a5480 is not initialized - not halting
[ 375.093716] ndiswrapper: device eth%d removed
[ 375.093744] ndiswrapper: probe of 1-2.3:1.0 failed with error -22
 
 
and this is what I get with iwconfig :
lo no wireless extensions.
eth0 no wireless extensions.
 
The original linux drivers are blacklisted.
Before I restarted I had wlan1 interface and everythig worked like a charm.
Then I tried to do everything again like said in the above link, but its not working :(
This rtl8187 driver has given me real pain and sleeples nights.
Now when I finally found the solution to use windows drivers and upgraded my system, once again, everything crashed :(
Every help will be strongly appreciated.
Thank you!

---

