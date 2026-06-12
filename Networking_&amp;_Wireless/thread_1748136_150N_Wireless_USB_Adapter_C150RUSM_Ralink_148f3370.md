---
title: "150N Wireless USB Adapter C150RUSM Ralink 148f:3370"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by ruxerruxe on 2011-05-03
Hi all,

I've fighting for weeks with the Conceptronic C150RUSM usb wifi card:

```

ubuntu@ubuntu:~$ lsusb
Bus 002 Device 004: ID 148f:3370 Ralink Technology, Corp.

```

After trying so many things as compiling the module rt2870sta from ralink web page changing the list of devices recognise for the module or as forcing rt2870sta module to load when this device is plugged in trough modification of the udev rules, I've realized that the rt2800usb has this device in the list of compatible ID's:

```

ubuntu@ubuntu:~$ modinfo rt2800usb | grep 3370
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*

```

So this devices should work out of the box. Furthermore, it should work with a proper module which it is not in the stagging tree... so it should work fine... but it doesn't!!!

As I said before, after fight for weeks with this device, l t realized that rt2800us module is able to recognize the wifi card but it fails when it tries to load the firmware, which is:

```

ubuntu@ubuntu:~$ modinfo rt2800usb | grep firmware
firmware:       rt2870.bin

```

The solution that worked finally for me was changing the file rt2870.bin located at /lib/firmware for the one in the ralink's web page. Right now I'm writing from a live session of Ubuntu 11.04 beta2 using the C150RUSM with no more modifications than changing the firmware... and by the way, it is working great!!!!!!

I hope my experience may help anyone more than me :)

---

### Post by ruxerruxe on 2011-05-03
By the way, sorry for my English :oops:

---

### Post by ruxerruxe on 2011-05-03
Actually the device is not working as fine as I said before. It worked really nice during a while but then it became really unstable. I red lots of posts of other people who is getting problems in Natty using several wifi cards... so I think the unstability could have nothing to do with Ralink

---

### Post by lesser on 2011-05-17
My experience with this adapter in Natty (Ubuntu 11.04): 

Out of the box, the adapter is recognized, it shows up in the Networkmanager icon, but it is not operating due to "Firmware missing". This error is displayed when you click the networkmanager icon. 

Replacing the firmware (found at /lib/firmware/rt2870.bin) with the file rt2870.bin from the firmware link found in the Linux section at [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) results in loading of a bunch of modules (use lsmod to display) and a working USB stick after reboot.

One 'bug' remains: the USB stick is only recognized wen plugged in AFTER booting, if present during booting, no wireless adapter is recognized. It should not be too difficult to force autoload of the necessary modules.

---EDIT: After a few hours of experiencing poor network performance, I must conclude that the solution above is far from perfect. But, at least, it will give you network access so one can use the internet to further improve performance. Btw, networkmanager reports good connectivity and network speeds from 48 to 54 MBits/s on my 11g network, which is comparable to my realtek wifi stick.

---

### Post by lesser on 2011-05-31
Again a week further, I'm getting desperate.

 Even with the new firmware, I'm getting frequent disconnects on several different computers running 11.04 Natty. I also suffer a lot from this [bug]("https://bugs.launchpad.net/bugs/362875"), that hangs the system. I was planning to use it on a XBMC, but fetching info or controlling it from my android is hopeless: it takes ages or accepts only 1/10 of phone key presses. Another USB stick under ndiswrapper works flawlessly.

Trying ndiswrapper with any of the supplied windows drivers results in a system hang or -crash.

I compiled the "staging" (whatever that may mean) driver rt2870sta from the Ralink website. Had to patch (using rt2870sta_usb_kernel2635.patch) the source first to be able to compile without errors. Something to do with new names for variable in Natty, I believe. Blacklisted the rt2800usb driver. Copied the compiled rt2870sta.ko to replace the running kernel module (here: /lib/modules/2.6.38-8-generic-pae/kernel/drivers/net/wireless/rt2870sta.ko). Modprobed it so I'm sure its loaded. But allas: no ra0 or wlan0 or wlan1 or whatever. Also not after reboot. Now I'm stuck. Can't find anywhere how to get ra0 up. Its seems that others see it appearing in iwconfig automatically. 

BTW: to load the appropriate modules automatically after plugging in, you can play with the udev rules: look [here]("http://ubuntuforums.org/showpost.php?p=8591348&postcount=6")

Any hints how to make wireless interface ra0 available?

-Edit- Found [how to]("http://ubuntuforums.org/showthread.php?t=1622846") get ra0 up!

---

### Post by chili555 on 2011-05-31
I'd suggest that rt5370sta is correct for this device. I think rt2870sta and rt2800usb are wrong; their performance is proof.

Has anyone tried rt5370sta?

---

### Post by lesser on 2011-06-01
OK, again a bit further down a really rocky path. After I got ra0 up, the network applet in the menu bar showed 'WirelesNetworks'. However, none of the available networks were listed, and I couldn't connect even if I specified ssid, channel, whatever. 

Then, I read a post of someone who claimed that a similar USB-stick only worked when first booting into Windows, suggesting that the stick needs some firmware, or at least needs in some way to be activated. I therefore first 'activated' the stick with the rt2800usb module, removed it (sudo modprobe -r rt2800usb), loaded the staging driver (sudo modprobe rt2870sta) and yes, now it lists available networks. Does it allow me to connect? No. From my dmesg:

```
[  266.415816] rtusb init --->
[  266.416362] usbcore: registered new interface driver rt2870
[  266.417642] 
[  266.417643] 
[  266.417644] === pAd = fa2fb000, size = 512124 ===
[  266.417645] 
[  266.417886] <-- RTMPAllocTxRxRingMemory, Status=0
[  266.417936] <-- RTMPAllocAdapterBlock, Status=0
[  266.693043] -->RTUSBVenderReset
[  266.693166] <--RTUSBVenderReset
[  266.969135] Key1Str is Invalid key length(0) or Type(0)
[  266.969180] Key2Str is Invalid key length(0) or Type(0)
[  266.969225] Key3Str is Invalid key length(0) or Type(0)
[  266.969271] Key4Str is Invalid key length(0) or Type(0)
[  266.970192] 1. Phy Mode = 5
[  266.970193] 2. Phy Mode = 5
[  266.996143] phy mode> Error! The chip does not support 5G band 11!
[  266.996213] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  267.011385] 3. Phy Mode = 9
[  267.019382] MCS Set = ff 00 00 00 01
[  267.029942] <==== rt28xx_init, Status=0
[  267.031516] 0x1300 = 00064300
[  267.561480] -->RTUSBVenderReset
[  267.561605] <--RTUSBVenderReset
[  267.836706] Key1Str is Invalid key length(0) or Type(0)
[  267.836750] Key2Str is Invalid key length(0) or Type(0)
[  267.836795] Key3Str is Invalid key length(0) or Type(0)
[  267.836841] Key4Str is Invalid key length(0) or Type(0)
[  267.837766] 1. Phy Mode = 5
[  267.837768] 2. Phy Mode = 5
[  267.863334] phy mode> Error! The chip does not support 5G band 11!
[  267.863400] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  267.878699] 3. Phy Mode = 9
[  267.886698] MCS Set = ff 00 00 00 01
[  267.897251] <==== rt28xx_init, Status=0
[  267.898811] 0x1300 = 00064300
[  269.262256] Bulk Out MLME Failed, Status=-2!
[  270.024719] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 377
[  271.266255] Bulk Out MLME Failed, Status=-2!
[  272.060855] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 377
[  272.061002] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  273.008036] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=1!
[  273.278250] Bulk Out MLME Failed, Status=-2!
[  273.432296] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=2!
[  273.576348] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=3!
[  273.720277] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=4!
[  273.868574] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=5!
[  274.012757] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=6!
[  274.157182] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=7!
[  274.300362] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=8!
[  274.444290] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=9!
[  274.588467] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=10!
[  274.732271] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=11!
[  274.876325] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=12!
[  275.020252] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=13!
[  275.164312] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=14!
[  275.294241] Bulk Out MLME Failed, Status=-2!
[  275.308660] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 377
[  276.510890] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=15!
etc etc etc

```

I think the phy Mode = 5 errors are not relevant, I can get rid of those by changing regional settings in /etc/Wireless/RT2870STA/RT2870STA.dat but earching for Qidz(0) or MgmtRing errors doesn't get me anywhere. I'm afraid that this is where I give up on the rt2870sta driver. I've learned that staging drivers are sort of candidate drivers in development, that may or may not make it to the kernel. As far as I can see, this one may need some serious work.

> **chili555 said:**
> I'd suggest that rt5370sta is correct for this device. I think rt2870sta and rt2800usb are wrong; their performance is proof.

Has anyone tried rt5370sta?

I had a go just now. Funny how the readme file is copy pasted from the rt2870sta driver, not all references have been changed yet. It compiled with some warnings but no errors, but when i tried to insmod "rt5370sta.ko", I get 

```

insmod: error inserting 'rt5370sta.ko': -1 Unknown symbol in module

```

and dmesg output:

```

[  955.271322] rt5370sta: module license 'unspecified' taints kernel.
[  955.271828] rt5370sta: Unknown symbol usb_alloc_urb (err 0)
[  955.271927] rt5370sta: Unknown symbol usb_free_urb (err 0)
[  955.272148] rt5370sta: Unknown symbol usb_alloc_coherent (err 0)
[  955.272365] rt5370sta: Unknown symbol usb_register_driver (err 0)
[  955.272620] rt5370sta: Unknown symbol usb_put_dev (err 0)
[  955.272706] rt5370sta: Unknown symbol usb_get_dev (err 0)
[  955.272856] rt5370sta: Unknown symbol usb_submit_urb (err 0)
[  955.273073] rt5370sta: Unknown symbol usb_free_coherent (err 0)
[  955.273294] rt5370sta: Unknown symbol usb_control_msg (err 0)
[  955.273555] rt5370sta: Unknown symbol usb_deregister (err 0)
[  955.273910] rt5370sta: Unknown symbol usb_kill_urb (err 0)

```

I don't have a clue how to proceed. Any suggestions?

---

### Post by chili555 on 2011-06-01
> I had a go just now. Funny how the readme file is copy pasted from the rt2870sta driver, not all references have been changed yet. It compiled with some warnings but no errors, but when i tried to insmod "rt5370sta.ko", I get First, you needn't add .ko when modprobbing; it's actually:```
sudo modprobe rt5370sta
```
I'm pretty sure we can fix the errors. Here is what you need to do. Open this file in a text editor

/os/linux/usb_main_dev.c

Change this:
```
#include "rt_config.h"


// Following information will be show when you run 'modinfo'
// *** If you have a solution for the bug in current version of driver, please mail to me.
// Otherwise post to forum in ralinktech's web site(www.ralinktech.com) and let all users help you. ***
MODULE_AUTHOR("Paul Lin <paul_lin@ralinktech.com>");
MODULE_DESCRIPTION("RT2870 Wireless Lan Linux Driver");
#ifdef CONFIG_STA_SUPPORT
#ifdef MODULE_VERSION
MODULE_VERSION(STA_DRIVER_VERSION);
#endif
#endif // CONFIG_STA_SUPPORT //
```

To this:
```
#include "rt_config.h"


// Following information will be show when you run 'modinfo'
// *** If you have a solution for the bug in current version of driver, please mail to me.
// Otherwise post to forum in ralinktech's web site(www.ralinktech.com) and let all users help you. ***
MODULE_AUTHOR("Paul Lin <paul_lin@ralinktech.com>");
MODULE_DESCRIPTION("RT2870 Wireless Lan Linux Driver");
[COLOR="Red"]MODULE_LICENSE("GPL");[/COLOR]
#ifdef CONFIG_STA_SUPPORT
#ifdef MODULE_VERSION
MODULE_VERSION(STA_DRIVER_VERSION);
#endif
#endif // CONFIG_STA_SUPPORT //
```

You are adding the 'MODULE_LICENSE("GPL");' line, that is highlighted in red. The parentheses, spacing, punctuation, etc. must be exact. Save your change and close the text editor. In my version, the change is added at line 41.

Now do:```
cd Downloads/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2
```Of course, substitute wherever the file was extracted if it's not 'Downloads.' Next, do:```
sudo su
make clean
make install
modprobe rt5370sta
exit
```Any errors? How is the wireless working?

---

### Post by lesser on 2011-06-01
Hi Chili555, thanks for your help. 

I did the steps you suggested. The driver compiled OK. It results in an active WiFi stick, that lists the available networks through network manager. I can associate with an (unprotected) accesspoint, which will give me an ip address. After that, I can ping the AP and even remote internet servers like google.com. My "Ralink STA RutilT" utility shows a steady stable signal, where it would disassociate frequently with the rt2870sta I tried before.

Thats all the good news. There is one small but essential step missing: I can't browse the web, nor connect to mailservers etc :( The link is only 54Mb, instead of the 150Mb i got before (but that is my least concern).

My dmesg is filled with messages from the staging driver, but I can't figure out what they mean. 

```

[   40.128265] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1507
[   40.128506] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1507
[   43.132259] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1884
[   43.132752] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1884
[   46.136172] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1222
[   46.136248] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1222
[   49.144258] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1638
[   49.144861] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1638
[   52.144234] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1638
[   52.144317] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1638
[   55.148202] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1507
[   55.148443] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1507
[   58.152170] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1053
[   58.152374] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1053
[   61.156150] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1338
[   61.156524] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1338
[   64.160152] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1717
[   64.160640] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1717
[   67.168177] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1820
[   67.168384] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1820
[   70.168155] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1336
[   70.168228] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1336
[   73.172161] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1128
[   73.172390] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1128
[   76.176152] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1779
[   76.176910] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1779
[   79.180249] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 1987
[   79.180697] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 1987
[   82.184153] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 1987
[   82.184241] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 1987
[   85.188159] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1441
[   85.188234] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1441
[   88.192162] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1818
[   88.192664] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1818
[   91.196206] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1818
[   91.196318] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1818
[   94.204199] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1818
[   94.204335] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1818
[   97.204195] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1818
[   97.204326] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1818
[  100.208190] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 2092
[  100.208708] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 2092
[  103.212245] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 2092
[  103.212366] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 2092
[  106.228201] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1443
[  106.228311] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1443
[  109.232213] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1546
[  109.232472] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1546
[  112.236193] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1715
[  112.236454] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1715
[  115.280200] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1818
[  115.280452] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1818
[  118.256210] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1544
[  118.256333] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1544
[  121.144247] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1544
[  121.144449] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1544
[  124.200231] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1167
[  124.200501] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
[  124.200541] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1167
[  143.293066] bridge-eth0: disabling the bridge
[  143.300084] bridge-eth0: down
[  143.300090] bridge-eth0: detached
[  143.300134] /dev/vmnet: open called by PID 1160 (vmnet-bridge)
[  143.300144] /dev/vmnet: hub 0 does not exist, allocating memory.
[  143.300160] /dev/vmnet: port on hub 0 successfully opened
[  143.300167] bridge-ra0: device is wireless, enabling SMAC
[  143.300171] bridge-ra0: up
[  143.300174] bridge-ra0: attached
[  150.300982] BIRIdx(1): RXDMALen not multiple of 4.[1285], BulkInBufLen = 1140)
[  155.442228] BIRIdx(7): RXDMALen not multiple of 4.[50111], BulkInBufLen = 1480)
[  155.708492] BIRIdx(7): RXDMALen not multiple of 4.[28706], BulkInBufLen = 1480)
[  156.317108] BIRIdx(7): RXDMALen not multiple of 4.[28706], BulkInBufLen = 1480)
[  158.300861] BIRIdx(2): RXDMALen not multiple of 4.[1285], BulkInBufLen = 1140)
[  162.192862] GetPacketFromRxRing():pRxWIMPDUtotalByteCount(3673) large than RxDMALen(1452)
[  162.193602] BIRIdx(6): RXDMALen not multiple of 4.[62959], BulkInBufLen = 1460)
[  163.201854] BIRIdx(4): RXDMALen not multiple of 4.[47891], BulkInBufLen = 1460)
[  171.540466] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1505
[  171.540994] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1505
[  193.639112] BIRIdx(5): RXDMALen not multiple of 4.[17430], BulkInBufLen = 1480)
[  203.637118] BIRIdx(0): RXDMALen not multiple of 4.[29255], BulkInBufLen = 1480)
[  211.688226] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1233
[  211.688333] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1233
[  213.636619] BIRIdx(5): RXDMALen not multiple of 4.[29255], BulkInBufLen = 1480)
[  215.113618] BIRIdx(4): RXDMALen not multiple of 4.[19931], BulkInBufLen = 1480)
[  215.393873] BIRIdx(2): RXDMALen not multiple of 4.[28706], BulkInBufLen = 1480)
[  216.567746] GetPacketFromRxRing():pRxWIMPDUtotalByteCount(387) large than RxDMALen(96)
[  223.636497] BIRIdx(2): RXDMALen not multiple of 4.[17430], BulkInBufLen = 1480)
[  228.219248] BIRIdx(0): RXDMALen not multiple of 4.[63346], BulkInBufLen = 1480)
[  241.736874] BIRIdx(2): RXDMALen not multiple of 4.[30561], BulkInBufLen = 1480)
[  253.635624] BIRIdx(0): RXDMALen not multiple of 4.[29255], BulkInBufLen = 1480)
[  271.916237] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1336
[  271.916522] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1336
[  275.108880] BIRIdx(0): RXDMALen not multiple of 4.[26994], BulkInBufLen = 1480)
[  275.391256] BIRIdx(3): RXDMALen not multiple of 4.[28706], BulkInBufLen = 1480)
[  335.152641] BIRIdx(5): RXDMALen not multiple of 4.[52478], BulkInBufLen = 1480)
[  335.353019] BIRIdx(2): RXDMALen not multiple of 4.[20603], BulkInBufLen = 1480)
[  341.476894] BIRIdx(6): RXDMALen not multiple of 4.[20603], BulkInBufLen = 1480)
[  351.224256] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1505
[  351.224785] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1505
[  354.461141] BIRIdx(1): RXDMALen not multiple of 4.[29282], BulkInBufLen = 988)
[  361.060398] BIRIdx(6): RXDMALen not multiple of 4.[20603], BulkInBufLen = 1480)
[  372.366672] bridge-ra0: disabling the bridge
[  372.380124] bridge-ra0: down
[  372.380132] bridge-ra0: detached
[  372.380177] /dev/vmnet: open called by PID 1160 (vmnet-bridge)
[  372.380186] /dev/vmnet: hub 0 does not exist, allocating memory.
[  372.380202] /dev/vmnet: port on hub 0 successfully opened
[  372.380210] bridge-eth0: up
[  372.380215] bridge-eth0: attached
[  451.656327] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1610
[  451.656619] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1610
[  455.305981] bridge-eth0: disabling the bridge
[  455.316033] bridge-eth0: down
[  455.316040] bridge-eth0: detached
[  455.316083] /dev/vmnet: open called by PID 1160 (vmnet-bridge)
[  455.316093] /dev/vmnet: hub 0 does not exist, allocating memory.
[  455.316114] /dev/vmnet: port on hub 0 successfully opened
[  455.316123] bridge-ra0: device is wireless, enabling SMAC
[  455.316127] bridge-ra0: up
[  455.316131] bridge-ra0: attached
[  461.465478] BIRIdx(2): RXDMALen not multiple of 4.[55063], BulkInBufLen = 1480)
[  461.676351] BIRIdx(2): RXDMALen not multiple of 4.[55063], BulkInBufLen = 1480)
[  462.936350] BIRIdx(4): RXDMALen not multiple of 4.[60473], BulkInBufLen = 1480)
[  485.889229] BIRIdx(3): RXDMALen not multiple of 4.[28533], BulkInBufLen = 1560)
[  505.184732] BIRIdx(7): RXDMALen not multiple of 4.[28533], BulkInBufLen = 1560)
[  517.932519] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1610
[  530.912114] BIRIdx(5): RXDMALen not multiple of 4.[28533], BulkInBufLen = 1560)
[  572.124245] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1064
[  572.124330] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1064
[  655.867896] BIRIdx(6): RXDMALen not multiple of 4.[15473], BulkInBufLen = 1480)
[  659.243638] BIRIdx(2): RXDMALen not multiple of 4.[29742], BulkInBufLen = 1480)
[  691.600254] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 2090
[  691.601829] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 2090

```

Any ideas how to proceed?

Cheers

---

### Post by lesser on 2011-06-01
trying to get a little more info where the problem is:
Using wireless:

```

wget http://fly.srk.fer.hr/jpg/flyweb.jpg 
--2011-06-01 15:56:56--  http://fly.srk.fer.hr/jpg/flyweb.jpg
Resolving fly.srk.fer.hr... 161.53.74.66
Connecting to fly.srk.fer.hr|161.53.74.66|:80... connected.
HTTP request sent, awaiting response... 


```
and nothing happens.

Using wired:
```

wget http://fly.srk.fer.hr/jpg/flyweb.jpg 
--2011-06-01 15:57:41--  http://fly.srk.fer.hr/jpg/flyweb.jpg
Resolving fly.srk.fer.hr... 161.53.74.66
Connecting to fly.srk.fer.hr|161.53.74.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2505 (2.4K) [image/jpeg]
Saving to: `flyweb.jpg'

100%[======================================>] 2,505       --.-K/s   in 0s      

2011-06-01 15:57:41 (154 MB/s) - `flyweb.jpg' saved [2505/2505]


```

The accesspoint itself is OK. If I connect with my android, I have full access to the webs.

---

### Post by chili555 on 2011-06-01
> I can't browse the web, nor connect to mailservers etcLet's have a look at:```
ifconfig ra0
cat /etc/resolv.conf
route -n
```

---

### Post by lesser on 2011-06-01
```

ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:22:f7:26:8f:c5  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:f7ff:fe26:8fc5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6618293 (6.6 MB)  TX bytes:236784 (236.7 KB)


```
and
```

cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1


```
doesn't look suspicious either. However, 
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.166.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 ra0
172.16.222.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ra0

```
is something I don't understand.

---

### Post by chili555 on 2011-06-01
Do you have a virtual machine running? Are there declarations for 'vmnet' in /etc/network/interfaces? Or is Ubuntu running in a virtual machine?

???

Everything associated with ra0 looks quite normal.

---

### Post by lesser on 2011-06-01
Yes, I've a virtual machine running (although not at this moment). 

cat /etc/network/interfaces gives
```

auto lo
iface lo inet loopback

```

So for all clarity; 
I'm running 2.6.38-8-generic-pae (Ubuntu 11.04 Natty)
but I sometimes use a VM running windows to run some Windows specific software. Apparently, the vmnet is loaded at boot.

Any idea where I could look for additional help? 

Thanks again for your help. The rt5370sta driver looks a lot more stable than the rt2870sta. 

 Man, how ironic if you know that I looked everywhere for a USB stick that had out-of-the-box kernel support, and I'm now trying for weeks to get it going because the kernel support is unusable...

---

### Post by chili555 on 2011-06-01
Do all the vmnet items show up in ifconfig? Can you surf the web wirelessly, that is with the ethernet cable detached, if you do:```
sudo ifconfig vmnet1 down
sudo ifconfig vmnet?? down
```Of course, substitute the number for the interfaces you found in ifconfig.

---

### Post by lesser on 2011-06-01
Yes, the vmnet interfaces do show up in ifconfig. 

However, I'm now at different location so I can't check. I'll let you know asap. Thanks again.

---

### Post by lesser on 2011-06-02
I'm at my other computer, a Home Theater PC for which I bought the USB. It's in a more 'virgin' state than the PC I do my work on. 

Compiling the driver is no longer an issue. It connected to my home network (WEP protected) without issues. However, I have the same problem: name resolving goes OK (I can ping google.com and get a response), but I can't download anything (webpage, file, mail). Even if I try to log in to the webpage of my AP: it's stuck at: "Waiting for 192.168.1.254...)

There is one thing in the README that I skipped: 

```

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   [COLOR="Red"]=> #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
[/COLOR]	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

```
because I don't have a wpa_supplicant-x.x directory. Besides that, I'm not planning on using WPA soon. I though it would be safe to skip, but maybe I'm mistaken.

So, anybody any ideas on how to take this (hopefully) last hump?

Cheers.

---

### Post by chili555 on 2011-06-02
That part is safe to skip, even if you are using WPA. Can you open the Google web page in Firefox? Is your DNS nameserver 192.168.1.254 in resolv.conf? Do you have anything weird in /etc/hosts? Does Network Manager run on the HTPC? Did it do all the work or did you enter some settings yourself? Is /etc/network/interfaces empty except for loopback?

---

### Post by lesser on 2011-06-02
> **chili555 said:**
> Can you open the Google web page in Firefox? 
No, I cannot. However, after many minutes, it seemed to have loaded the little "G"-icon in the addressbar, but I'm not 100% sure that didn't come from cache.


> **chili555 said:**
> Is your DNS nameserver 192.168.1.254 in resolv.conf? 
Yes, and name resolving is not an issue, if I "ping google.com" it translates into an IP-address, or is that not what you meant? 

> **chili555 said:**
> Do you have anything weird in /etc/hosts? 
nope.
127.0.0.1 localhost
127.0.1.1 HTPC
and some ip6 stuff

> **chili555 said:**
> Does Network Manager run on the HTPC? Did it do all the work or did you enter some settings yourself?  Network manager is running. It took care of all settings. I have another usb stick that I use with ndiswrapper. That works fine. My netbook has exactly the same issues with this stick and the staging drivers.

> **chili555 said:**
> Is /etc/network/interfaces empty except for loopback?
I'll check, but last time I looked, there wasn't anything suspicious there.


What did strike me as a big difference between the rt2870sta and rt5370usb drivers is the number of other modules they invoke (excuse my English if that isn't the correct term). The rt5379sta is the only module that loads. Shouldn't mac80211 and cfg80211 load?

---

### Post by chili555 on 2011-06-02
> Yes, and name resolving is not an issue, if I "ping google.com" it translates into an IP-address, or is that not what you meant?
Yes, exactly.> 127.0.0.1 localhost
127.0.1.1 [COLOR="Red"]HTPC[/COLOR]And does that agree with:```
cat /etc/hostname
```A longshot, I know.

When you click the NM icon and Edit Connections, select Wireless and IPv6 is it set to Ignore? See attached.> What did strike me as a big difference between the rt2870sta and rt5370usb drivers is the number of other modules they invoke (excuse my English if that isn't the correct term). The rt5379sta is the only module that loads. Shouldn't mac80211 and cfg80211 load?Your English is just fine; I understand perfectly. The other modules that are required are listed in modinfo; for example:> $ modinfo iwl3945
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2010 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     08BA403405B97DE1DE3DA90
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
[COLOR="Red"]depends:        iwlcore,cfg80211,mac80211[/COLOR]
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software])
 (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (deprecated) (int)
parm:           fw_restart3945:restart firmware in case of error (int)
iwl3945 is the driver for my card.> $ modinfo rt5370sta
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt5370sta.ko
version:        2.5.0.1
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     BA74520E391B4D58CF44A3B
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
--- snip ---
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
[COLOR="Red"]depends: [/COLOR]       
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)

---

### Post by lesser on 2011-06-03
Yes, /etc/hostname is HTPC as well.

Do I understand from your listing that you have a working rt5370sta??? 

I stumbled across one other thing that may be a hint to what may be the problem. I control my XBMC using my android and an app called *XBMC remote*. It works over WiFi. The weird thing is, that I can control my XBMC perfectly using the rt5370sta. In rt2870sta- and rt2800usb times, that was not possible because it dropped connections all the time and you would have to wait a few seconds before it came back.

I know, this is the time where you would say; "Check your AP!", but I have half a dozen other gadgets using the same AP (several laptops, phones, a game console) that have no issue at all. Also, I get identical behaviour when I use my usb stick at a different location.

The last thing I can offer is a dmesg after reboot, I plug the usb stick at 70s and start my firefox a little later.
```

[   70.340067] usb 3-3: new high speed USB device using ehci_hcd and address 2
[   70.579660] rtusb init rt2870 --->
[   70.580075] 
[   70.580078] 
[   70.580079] === pAd = fa658000, size = 518552 ===
[   70.580081] 
[   70.580534] <-- RTMPAllocTxRxRingMemory, Status=0
[   70.580682] <-- RTMPAllocAdapterBlock, Status=0
[   70.582469] usbcore: registered new interface driver rt2870
[   70.611671] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   70.893726] RTMP_TimerListAdd: add timer obj fa69fa10!
[   70.893735] RTMP_TimerListAdd: add timer obj fa69fa58!
[   70.893739] RTMP_TimerListAdd: add timer obj fa69faa0!
[   70.893743] RTMP_TimerListAdd: add timer obj fa69f9c8!
[   70.893749] RTMP_TimerListAdd: add timer obj fa69f8f0!
[   70.893752] RTMP_TimerListAdd: add timer obj fa69f938!
[   70.893756] RTMP_TimerListAdd: add timer obj fa66a4c8!
[   70.893759] RTMP_TimerListAdd: add timer obj fa659d8c!
[   70.893763] RTMP_TimerListAdd: add timer obj fa659ddc!
[   70.893766] RTMP_TimerListAdd: add timer obj fa66a5b4!
[   70.893771] RTMP_TimerListAdd: add timer obj fa66a438!
[   70.893776] RTMP_TimerListAdd: add timer obj fa66a568!
[   70.895733] -->RTUSBVenderReset
[   70.895859] <--RTUSBVenderReset
[   71.211579] Key1Str is Invalid key length(0) or Type(0)
[   71.211619] Key2Str is Invalid key length(0) or Type(0)
[   71.211658] Key3Str is Invalid key length(0) or Type(0)
[   71.211695] Key4Str is Invalid key length(0) or Type(0)
[   71.212541] 1. Phy Mode = 5
[   71.212545] 2. Phy Mode = 5
[   71.212549] NVM is Efuse and its size =2d[2d0-2fc] 
[   71.263195] phy mode> Error! The chip does not support 5G band 11!
[   71.263400] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   71.267312] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   71.289945] 3. Phy Mode = 9
[   71.348820] MCS Set = ff 00 00 00 01
[   71.359400] <==== rt28xx_init, Status=0
[   71.361434] 0x1300 = 00064300
[   71.380920] ERROR!!! RTMPSetTimer failed, Halt in Progress!
[   71.708148] #
[   71.788139] #
[   71.868133] #
[   71.948101] #
[   72.028240] #
[   72.108219] #
[   72.188210] #
[   72.268207] #
[   72.348190] #
[   72.428189] #
[   72.433192] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Idx=0x400,pAd->Flags=0x70024442
[   72.433197] 	Request Value=0x0c81!
[   72.957969] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   73.218287] RTMP_TimerListAdd: add timer obj fa69fa10!
[   73.218297] RTMP_TimerListAdd: add timer obj fa69fa58!
[   73.218302] RTMP_TimerListAdd: add timer obj fa69faa0!
[   73.218307] RTMP_TimerListAdd: add timer obj fa69f9c8!
[   73.218312] RTMP_TimerListAdd: add timer obj fa69f8f0!
[   73.218316] RTMP_TimerListAdd: add timer obj fa69f938!
[   73.218320] RTMP_TimerListAdd: add timer obj fa66a4c8!
[   73.218323] RTMP_TimerListAdd: add timer obj fa659d8c!
[   73.218326] RTMP_TimerListAdd: add timer obj fa659ddc!
[   73.218330] RTMP_TimerListAdd: add timer obj fa66a5b4!
[   73.218335] RTMP_TimerListAdd: add timer obj fa66a438!
[   73.218341] RTMP_TimerListAdd: add timer obj fa66a568!
[   73.220073] -->RTUSBVenderReset
[   73.220176] <--RTUSBVenderReset
[   73.506911] Key1Str is Invalid key length(0) or Type(0)
[   73.506949] Key2Str is Invalid key length(0) or Type(0)
[   73.506985] Key3Str is Invalid key length(0) or Type(0)
[   73.507022] Key4Str is Invalid key length(0) or Type(0)
[   73.507618] 1. Phy Mode = 5
[   73.507621] 2. Phy Mode = 5
[   73.507625] NVM is Efuse and its size =2d[2d0-2fc] 
[   73.559520] phy mode> Error! The chip does not support 5G band 11!
[   73.559722] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   73.563765] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   73.586265] 3. Phy Mode = 9
[   73.650509] MCS Set = ff 00 00 00 01
[   73.661093] <==== rt28xx_init, Status=0
[   73.662870] 0x1300 = 00064300
[   75.808651] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 246
[   75.810584] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 246
[   77.964623] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 423
[   77.966366] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
[   77.966514] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 423
[   84.640033] ra0: no IPv6 routers present

[   97.192545] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 423
[   97.192650] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 423
[  129.042945] BIRIdx(2): RXDMALen not multiple of 4.[2589], BulkInBufLen = 1556)
[  136.340544] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 283
[  136.340740] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 283
[  196.576593] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 283
[  196.576801] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 283
[  217.716637] BIRIdx(3): RXDMALen not multiple of 4.[275], BulkInBufLen = 1488)
[  238.665761] BIRIdx(3): RXDMALen not multiple of 4.[33187], BulkInBufLen = 1500)
[  240.919595] BIRIdx(1): RXDMALen not multiple of 4.[2589], BulkInBufLen = 1556)

[  276.888794] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 283
[  276.888990] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 283
[  313.422311] BIRIdx(2): RXDMALen not multiple of 4.[3523], BulkInBufLen = 1516)
[  313.659024] BIRIdx(5): RXDMALen not multiple of 4.[32074], BulkInBufLen = 1516)
[  319.263408] BIRIdx(6): RXDMALen not multiple of 4.[39742], BulkInBufLen = 1556)
[  319.477754] BIRIdx(5): RXDMALen not multiple of 4.[21694], BulkInBufLen = 1556)
[  321.236410] BIRIdx(0): RXDMALen not multiple of 4.[21694], BulkInBufLen = 1556)
[  335.933963] BIRIdx(0): RXDMALen not multiple of 4.[33187], BulkInBufLen = 1500)
[  346.630183] BIRIdx(7): RXDMALen not multiple of 4.[6823], BulkInBufLen = 1556)
[  376.285694] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 283
[  376.285904] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 283


```
Those lines do not mean much to me, but maybe a comparison with the dmesg of a working rt5370sta can shed some light.

---

### Post by lesser on 2011-06-05
:guitar: Oh yeah!

Knowing that I was able to download using the rt2870usb driver with the same hardware, I concluded it had to be the RT5370STA driver. I went back to the ralinktech.com website and noticed that there are actually 2 (two) RT5370STA drivers. This time I took version 2.5.0.2. The code needs the addition of MODULE_LICENCE("GLP"); addition (see above). 

I did 
```

sudo make uninstall
sudo make clean

```
to get rid of previous attempts. Not sure that it is strictly necessary, but I figure it can't hurt. Then

```

sudo nano /etc/Wireless/RT2870STA/RT2870STA.dat
sudo make
sudo make install
sudo modprobe rt5370sta

```

The first line lets you edit the mentioned file. Not 100% necessary, but have a look at [this site]("https://wiki.archlinux.org/index.php/Rt2870") for more information.

Finally, after days of despair, I have my USB stick running. First impression: good sensitivity, no crashes in the first hour....



-EDIT Days later, I can say that I'm perfectly happy with this stick. Sensitive, cheap (< &#8364;10,-) and with the latest driver it is also stable.

---

### Post by narcisgarcia on 2011-07-28
Tried the RT5370 driver version 2.5.0.2 from Ralink corp:
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

They say "*Ralink is very active in the Linux community*", but they don't provide any .deb package nor APT repository to make it easy for final users.

For the moment, tried in Ubuntu 10.10 :
```
# Unpack and unpack the source package
# Enter to the source directory with a terminal
make
make install
# Reboot system
modprobe rt5370sta
```

But no *wlan* device is listed with **ifconfig**

---

### Post by narcisgarcia on 2011-07-28
Tried now with the Ubuntu 11.04 Live-CD; with only plugging the device the NetworkManager shows a line with "*device not ready (firmware missing)*"
```
# Downloaded the RT5370 driver version 2.5.0.2 from [Ralink corp]("http://www.ralinktech.com/support.php?s=2")
# Unpacked and unpacked the source package
# Entered to the source directory with a terminal
# Patched the file os/linux/usb_main_dev.c adding the GPL line (see comment #8)
sudo make
sudo make install
sudo modprobe rt5370sta
sudo service network-manager restart
```
[LIST]
[*] But NetworkManaer still shows the same error text.
[*] *wlan0* is listed with **ifconfig -a**
[/LIST]

---

### Post by narcisgarcia on 2011-07-28
Tried now with an Ubuntu 10.04.1 Live-CD; NetworkManager doesn't show anyway anything related to wireless
```
# Downloaded the RT5370 driver version 2.5.0.2 from [Ralink corp]("http://www.ralinktech.com/support.php?s=2")
# Unpacked and unpacked the source package
# Entered to the source directory with a terminal
# Patched the file os/linux/usb_main_dev.c adding the GPL line (see comment #8)
sudo make
sudo make install
sudo modprobe rt5370sta
sudo service network-manager restart

```
[LIST]
[*] NetworkManaer is still without any wireless mention
[*] *ra0* device is listed with **ifconfig -a**
[/LIST]

---

### Post by narcisgarcia on 2011-07-28
Tried now with an alpha version of Ubuntu 11.10 Live-CD; NetworkManager shows all the wireless networks but doesn't reach a connection.
I've only plugged device (no driver download nor compilation)

Some data about:
```
**uname -a**
Linux ubuntu 3.0.0-7-generic #8-Ubuntu SMP Fri Jul 22 20:24:22 UTC 2011 i686 athlon i386 GNU/Linux

**lsusb | grep -ie "ralink"**
Bus 002 Device 004: ID 148f:3370 Ralink Technology, Corp.

**lsmod | grep -ie "rt2"**
rt2800usb              22222  0 
rt2800lib              48909  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20092  1 rt2800usb
rt2x00lib              48147  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              272785  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              172344  2 rt2x00lib,mac80211

```

---

### Post by chili555 on 2011-07-28
What is the size of the firmware?```
 ls -al /lib/firmware/rt2870.bin
```On my Natty machine it's 4,096 bytes. I noticed this: [http://linuxwireless.org/en/users/Drivers/rt2800usb#device_firmware](http://linuxwireless.org/en/users/Drivers/rt2800usb#device_firmware)

When you follow the link, you get a firmware file that's 8,192 bytes. I wonder if it helps.

If you need assistance getting it installed, post back.

Yes, you can do this on a live disc.

FYI:> $ modinfo [COLOR="Red"]rt2800usb[/COLOR]
filename:       /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
[COLOR="Red"]firmware:       rt2870.bin[/COLOR]
description:    Ralink RT2800 USB Wireless LAN driver.


---

### Post by narcisgarcia on 2011-07-28
On a clean Ubuntu 10.04 Live-CD
```
ubuntu@ubuntu:~$ ls -la /lib/firmware/rt2870.bin
-rw-r--r-- 1 root root 4096 2010-05-26 16:10 /lib/firmware/rt2870.bin

ubuntu@ubuntu:~$ modinfo rt2800usb
filename:       /lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CCB48372EBF4D949A76B141
...
depends:        rt2x00lib,rt2x00usb,crc-ccitt
vermagic:       2.6.32-24-generic SMP mod_unload modversions 586 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```

On a clean Ubuntu 10.10 Live-CD
```
ubuntu@ubuntu:~$ ls -la /lib/firmware/rt2870.bin
-rw-r--r-- 1 root root 4096 2010-08-16 19:02 /lib/firmware/rt2870.bin

ubuntu@ubuntu:~$ modinfo rt2800usb
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     78DA166470C3E90F51592AF
...
depends:        rt2800lib,rt2x00usb,crc-ccitt
vermagic:       2.6.35-22-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```

On a clean Ubuntu 11.04 Live-CD
```
ubuntu@ubuntu:~$ ls -la /lib/firmware/rt2870.bin
-rw-r--r-- 1 root root 4096 2010-11-18 21:20 /lib/firmware/rt2870.bin

ubuntu@ubuntu:~$ modinfo rt2800usb
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     52008801035C9FD38B91EC7
...
depends:        rt2x00lib,rt2800lib,rt2x00usb
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```

On a clean Ubuntu 11.10 Live-CD - Today's alpha daily build
```
guest-zKodwt@ubuntu:~$ ls -la /lib/firmware/rt2870.bin
-rw-r--r-- 1 root root 8192 2011-05-26 14:58 /lib/firmware/rt2870.bin

guest-zKodwt@ubuntu:~$ modinfo rt2800usb
filename:       /lib/modules/3.0.0-7-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     31325F19154B8CA6B69C77F
...
depends:        rt2x00lib,rt2800lib,rt2x00usb
vermagic:       3.0.0-7-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```

If the good size is 8192 bytes, should I copy the file rt2870.bin from Ubuntu 11.10 and use it on older versions to get it installed?

---

### Post by chili555 on 2011-07-28
> If the good size is 8192 bytes, should I copy the file rt2870.bin from Ubuntu 11.10 and use it on older versions to get it installed?I would certainly try it. I'd blacklist rt2870sta and un-blacklist rt2800usb, load the 8K firmware and see what happens.

I might also try the 8K firmware with rt2870sta and see if some combination works well. Of course, post back so we can all learn.

We may be on to something.

---

### Post by mindfire6482 on 2011-09-22
Hiya, been reading through alot of forum posts to do with the RALINK hardware in ubuntu and thankfully i have been able to get mine working, well kind of.

After much pulling of hair and after much much surfing and trying everything i read, i now have an RT5370STA which connects, is stable, and auto loads at boot... GREAT!!

However, the USB adapter i own is supposed to be running at 150Mbps... Nothing i seem to try (even after surfing yet again for a solution) can get this bloody thing running any faster than 54Mbps.

You seem to be a bit of a guru, any ideas of a setting i need to change, a bit of termnial work maybe?

Any help you could offer would be awesome!

---

### Post by chili555 on 2011-09-22
> any ideas of a setting i need to changeNot really. Are you using the latest version?

---

### Post by narcisgarcia on 2011-09-23
mindfire6482, please tell your procedure and Ubuntu version.

---

### Post by Swearengen on 2011-10-08
> **chili555 said:**
> What is the size of the firmware?```
 ls -al /lib/firmware/rt2870.bin
```On my Natty machine it's 4,096 bytes. I noticed this: [http://linuxwireless.org/en/users/Drivers/rt2800usb#device_firmware](http://linuxwireless.org/en/users/Drivers/rt2800usb#device_firmware)

When you follow the link, you get a firmware file that's 8,192 bytes. I wonder if it helps.


Definitively it does!

Well I just have registered and post because I'd like to thank all the people that help with problems in this forum, and specially to Chilli for his great knowledge of linux and his infinite patience!! I have learn a lot from him. 

Now I&#314;l explain how did i solve my problem with my Conceptronic [C150ru(v2)]("http://www.conceptronic.net/Site/desktopdefault.aspx?tabindex=1&tabid=222&cid=20&gid=2035&pid=C150RU_V2"), chipset Ralink 3370, very little and fast dongle that was impossible to make it work in my old laptop Acer Travelmate 250. I installed firs Xubuntu 10.04, bus as it doesn't work with the 2800 driver y tried to compile the one provided by ralink on his web. After a few issues I finally could run make and makefile but in any case could modprobe the created file. As Dr Chilli said, perhaps it was a problem of compatibility with such an old version of my kernel.

So I decided to install a newer version of Xubuntu (sorry but i like a lot more than the genuine without X), downloaded and intalled this morning the 11.04 version. After install about 180 updates by a wired conexion, I connected my USB, and the situation was just like narcisgarcia related:
> 
**lsusb | grep -ie "ralink"** Bus 002 Device 004: ID 148f:3370 Ralink Technology, Corp.  **lsmod | grep -ie "rt2"** rt2800usb              22222  0  rt2800lib              48909  1 rt2800usb crc_ccitt              12595  1 rt2800lib rt2x00usb              20092  1 rt2800usb rt2x00lib              48147  3 rt2800usb,rt2800lib,rt2x00usb mac80211              272785  3 rt2800lib,rt2x00usb,rt2x00lib cfg80211              172344  2 rt2x00lib,mac80211Then i replaced the 4mb file /lib/fimware/rt2870.bin with the 8Mb downloaded one and ¡IT WORKS!

For anyone that can help I've attach a file that contains all the important information about my configuration and hardware, made with Cilli's recipe ...

For further infomation please reply and Ill give you more details

Please excuse me for my horrible english, and once more THANK YOU VERY MUCH!!!!

---

### Post by chili555 on 2011-10-08
Your English is perfectly fine.

I am very glad it's working for you and, moreover, that you shared your experience and solution with us for the benefit of the searchers. Inclusion of your details, especially your usb.id 148f:3370 makes this solution search-able. 

That you for your very kind comments.

---

### Post by speigel205 on 2012-01-28
Hi

I got a strange problem with rt5370sta, after compiling & installing I can connect fine and browse websites with wicd manager using default options. What is strange is that after some minutes the connection drop ! So I always need to reconnect back and so one each couple of minutes I get disconnected. Has someone experienced the seem thing ?

---

### Post by zaikreign on 2012-01-30
Got mine working. At first I followed the instructions at: [https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M).

I am using linux-image-3.0.0.15 and get the following response using "lsusb":
Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp.

I skipped the first method, the method with the compiling and stuff. Couldn't make it work. Just follow the instruction under "rt2800usb driver". Don't let your hopes up yet, it will only worked until shutdown and had to do the same thing over and over again. So what I did is open the terminal, modified /etc/rc.local and inserted the following before the line "exit 0"

modprobe rt2800usb
echo 148F 5370 > /sys/bus/usb/drivers/rt2800usb/new_id

After that, every time I reboot, wi-fi stays connected.

---

### Post by petermg on 2012-02-19
> **zaikreign said:**
> Got mine working. At first I followed the instructions at: [https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M).

I am using linux-image-3.0.0.15 and get the following response using "lsusb":
Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp.

I skipped the first method, the method with the compiling and stuff. Couldn't make it work. Just follow the instruction under "rt2800usb driver". Don't let your hopes up yet, it will only worked until shutdown and had to do the same thing over and over again. So what I did is open the terminal, modified /etc/rc.local and inserted the following before the line "exit 0"

modprobe rt2800usb
echo 148F 5370 > /sys/bus/usb/drivers/rt2800usb/new_id

After that, every time I reboot, wi-fi stays connected.

At that link, the second method did not work for me, but the first one worked like a charm.  Am typing this over my connection with that wifi device now!! :D

---

### Post by paulfer on 2012-06-09
:guitar: Congratulations, chili5558! You discovered the trick. 
Just like to know why Ralink has not shown   this tip in a easy way...

---

