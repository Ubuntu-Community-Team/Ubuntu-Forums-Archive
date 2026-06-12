---
title: "Trusty Tahr TeVii DVB-S2 card S471 (ds3000, ts2020, cx23885) hangs on firmware upload"
date: 2014-04-23
forum: Mythbuntu
---

### Post by un1 on 2014-04-23
Hi all,

I installed a TeVii S471 DVB-S2 card in my machine (modules ds3000, ts2020, cx23885 loaded).

I put the firmware file dvb-fe-ds3000.fw to /lib/firmware.

When doing ```
sudo rmmod cx23885; sudo modprobe cx23885
``` it looks like everything is correct (dmesg).

But when trying to scan for channels with mythtv or w_scan or kaffeine in dmesg I see repeatedly the following lines:

```

ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
ds3000_firmware_ondemand: Waiting for firmware upload(2)...
ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
ds3000_firmware_ondemand: Waiting for firmware upload(2)...
...
```

I also tried a cold reboot (disconnecting the power for several minutes/hours) and getting still the same.

No channels can be found/locked.

As I couldn't test the card in another environment or with other kernel I am not sure if it is a problem with the card (I bought it at ebay and the seller assured that the card worked before) or if it is a problem with kernel or something else.

Has someone this card or a similar one (S470, S480, S464, ...) running in mythbuntu 14.04 and default kernel 3.13? Any idea what I could try else?

Thanks...

---

### Post by blm-ubunet on 2014-04-23
Can you provide an uncut dmesg for a cold start ?

The firmware error must be occur there as well?

---

### Post by un1 on 2014-04-24
Hi,
here the full dmesg after a cold restart: [http://pastebin.com/gxjVXj9M](http://pastebin.com/gxjVXj9M)

Here the relevant lines:

```
dmesg | grep -E "(ds3000|DS3000|cx|ts20)"
[   17.597115] cx23885 driver version 0.0.3 loaded
[   17.597392] CORE cx23885[0]: subsystem: d471:9022, board: TeVii S471 [card=35,autodetected]
[   17.746791] cx23885_dvb_register() allocating 1 frontend(s)
[   17.755602] cx23885[0]: cx23885 based dvb card
[   17.773343] DS3000 chip version: 0.192 attached.
[   17.801571] ts2020_attach: Find tuner TS2020!
[   17.801686] DVB: registering new adapter (cx23885[0])
[   17.801693] cx23885 0000:02:00.0: DVB: registering adapter 2 frontend 0 (Montage Technology DS3000)...
[   17.802129] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   17.802138] cx23885[0]/0: found at 0000:02:00.0, rev: 2, irq: 18, latency: 0, mmio: 0xfe800000
```

No when trying to scan, the two lines from above post are appearing repeatedly but no error.

---

### Post by blm-ubunet on 2014-04-24
I don't see any firmware loading in your cold start dmesg..
Maybe it only loads on demand..

You got the firmware directly from TeVii website?
Could the downloaded file be corrupt/incomplete?
File decompressed with other archive tool?

---

### Post by un1 on 2014-04-25
After cold start no firmware is loaded, that's true. It is only loaded or at least it shows that it is loading the firmware, when I try to tune e.g. with scan or w_scan command.

Then dmesg shows:

```
ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
ds3000_firmware_ondemand: Waiting for firmware upload(2)...
```

So yes, it is on demand loading. There is also no error displayed or anything.

> You got the firmware directly from TeVii website?
Could the downloaded file be corrupt/incomplete?
File decompressed with other archive tool?

Yes downloaded from Tevii site, but also tried other sources, but all of them have the same file, I also checked the md5sum which is a32d17910c4f370073f9346e71d34b80. If I delete the firmware file from /lib/firmware then there is an error in dmesg showing that the firmware doesn't exist.


Could that be a regression in 3.13 kernel?

I also tried to set 
```
options ds3000 force_fw_upload=1
```
in modprobe.conf, but his argument is unknown in the 3.13 kernel (in kernel 3.7.x seemed to be a bug with ds3000 and there it should have worked).

Here also my result from scan (on my machine the card is adapter #2):

```
scan -x 0 -a 2 -l UNIVERSAL /usr/share/dvb/dvb-s/Astra-19.2E
scanning /usr/share/dvb/dvb-s/Astra-19.2E
using '/dev/dvb/adapter2/frontend0' and '/dev/dvb/adapter2/demux0'
initial transponder 12551500 V 22000000 5
>>> tune to: 12551:v:0:22000
DVB-S IF freq is 1951500
WARNING: >>> tuning failed!!!
>>> tune to: 12551:v:0:22000 (tuning failed)
DVB-S IF freq is 1951500
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.
```

Do you have any ideas? Do you own a S471 or similar card?

Here what I found out analyzing the kernel sources:
In 3.13 used by ubuntu the file /drivers/media/pci/cx23885/cx23885-dvb.c in line 1403 ff does something for the S470 but not for the S471 (copying mac to eeprom?) - see [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-trusty.git;a=blob;f=drivers/media/pci/cx23885/cx23885-dvb.c;h=05492053b473033da6da030fb1f64d7dcf2ea0ef;hb=d4449f80b82cb0cee40bd12a510d9bffc377c54a](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-trusty.git;a=blob;f=drivers/media/pci/cx23885/cx23885-dvb.c;h=05492053b473033da6da030fb1f64d7dcf2ea0ef;hb=d4449f80b82cb0cee40bd12a510d9bffc377c54a)

I also found the source looking a bit different (not sure whose kernel this is): [https://bitbucket.org/CrazyCat/linux-tbs-drivers/src/a6e2aef2d44ab4c9c32788913256a2b90b0c5744/linux/drivers/media/video/cx23885/cx23885-dvb.c?at=bbf](https://bitbucket.org/CrazyCat/linux-tbs-drivers/src/a6e2aef2d44ab4c9c32788913256a2b90b0c5744/linux/drivers/media/video/cx23885/cx23885-dvb.c?at=bbf) - look at line 1503 ff. - the check is done for S470 and S471 as well... Could this have something to do with my issue?

My problem is, the machine is standing at my parent's home, and wouldn't like to try kernel compiling etc remotely, because if it fails they won't be able to recover the system... Maybe it is an idea to lead the kernel to believe the card is a S470 and try it out - but how can I do this?

---

### Post by blm-ubunet on 2014-04-25
I don't have this card.

I would use kernel that works, don't see any need to use 14.04.

Don't need to build whole kernel just a few bits of it..
Easy to build v4l-dvb media as dkms kernel modules.
(easy to undo by booting previous kernel in grub or reinstall kernel in synaptic)
[http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

[https://bugzilla.redhat.com/show_bug.cgi?id=963715](https://bugzilla.redhat.com/show_bug.cgi?id=963715)
Patch
[https://patchwork.linuxtv.org/patch/19301/](https://patchwork.linuxtv.org/patch/19301/)

Doesn't appear the latest code base has this fix..

---

### Post by un1 on 2014-04-28
> **blm-ubunet said:**
> 
Doesn't appear the latest code base has this fix..

This fix does already exist in the official kernel (3.13.0-24.46) - see [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-trusty.git;a=blob;f=drivers/media/pci/cx23885/cx23885-dvb.c;h=05492053b473033da6da030fb1f64d7dcf2ea0ef;hb=d4449f80b82cb0cee40bd12a510d9bffc377c54a](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-trusty.git;a=blob;f=drivers/media/pci/cx23885/cx23885-dvb.c;h=05492053b473033da6da030fb1f64d7dcf2ea0ef;hb=d4449f80b82cb0cee40bd12a510d9bffc377c54a) (lines 1309-1311).

I also tried out yesterday the mainline kernel 3.14.1 with exactly the same results. I am starting to believe that there is a defect with the card or tuner on the card...

---

### Post by blm-ubunet on 2014-04-28
There is a difference to the kernel source & the patch 19301 at:
[https://bitbucket.org/CrazyCat/linux-tbs-drivers/src/a6e2aef2d44ab4c9c32788913256a2b90b0c5744/linux/drivers/media/video/cx23885/cx23885-dvb.c?at=bbf](https://bitbucket.org/CrazyCat/linux-tbs-drivers/src/a6e2aef2d44ab4c9c32788913256a2b90b0c5744/linux/drivers/media/video/cx23885/cx23885-dvb.c?at=bbf)
line 1503

And code at line 1208 is not replicated for S471, should it be?

The CrazyCat code reads the eeprom for both 470 & 471 variants.
Not sure that helps tho, it could..

---

### Post by un1 on 2014-04-29
The voltage setting at line 1208 is ok for S470 only as far as I investigated, reason is a different LNB control on the two cards 470 and 471, the S470 needed this setting, the S471 doesn't.

About the copy of the frontend MAC address to the eeprom - I have no idea what it is good for - but maybe this is an issue.

Yesterday we removed the card from the machine and sent it back, the seller will send a new card - then I can try it out again and post here the results. If the replaced card doesn't work either, I will try to compile the kernel with the changes from Crazycat.

Thanks for your help so far!

---

### Post by awhaiku on 2014-05-09
Success ?
I have exactly the same problem with a TeVii S464. The card worked perfect in Ubuntu 12.04 until 13.04. The problem startet with 13.10.
I just did a complete new install of 14.04 - with exactly the same problem as described here.

---

### Post by un1 on 2014-05-09
> **awhaiku said:**
> Success ?
I have exactly the same problem with a TeVii S464. The card worked perfect in Ubuntu 12.04 until 13.04. The problem startet with 13.10.
I just did a complete new install of 14.04 - with exactly the same problem as described here.

I am still waiting for a replaced card from the seller. But it sounds like it is not a problem with the card... 
If it worked for you with 13.04 - can you try the 13.04 kernel then?

---

### Post by awhaiku on 2014-05-09
I tried some more in the meantime, it seems the driver gets loaded now (for whatever reason).

I  know that the initial install in 12.10 worked right out of the box.  install firmware, reboot, start kaffeine, start channel scan - done.
Now  no channels. I checked the ubuntu wiki page for kaffeine and manually  created the section for my satellite with w_scan (no errors, did 'something' which i can not conrol content-wise).
After that, kaffeine finds 'some' channels, but no dvb-s (though it's a dvb-s card, and the w_scan file contains 'S2' lines), and almost none of the european 'private' channels.

---

### Post by manjur2 on 2014-06-04
I have fresh installation of Ubuntu Trusty Tahr 14.04 (Server) with TeVii S471. And this problem still exist, firmware doesn't load correctly.

I tried it with default trusty tahr kernel version 3.13.0 and with fresh kernel image 3.15.0 from ubuntu utopic (unstable). No changes, I see in syslog:
```

Jun  4 19:57:38 MMC kernel: [   20.714716] ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
Jun  4 19:57:38 MMC kernel: [   20.715999] ds3000_firmware_ondemand: Waiting for firmware upload(2)...

```

 Also I tried this card with Debian wheezy + kernel image 3.14.1 from debian unstable - and card works fine, firmware loaded successfully in a second. So I think it's a specific bug in kernel.

Does someone know how to get TeVii S471 working on Ubuntu 14.04?

---

### Post by jrda on 2014-06-19
I use this Card with OpenElec 4.0.5 without Problems.
My Kernel: > Linux HTPC 3.14.7 #1 SMP Sat Jun 14 17:53:15 CEST 2014 x86_64 GNU/Linux 
My DMESG:
> HTPC:~ # dmesg | grep -E "(ds3000|DS3000|cx|ts20)"
[    2.972628] cx23885 driver version 0.0.3 loaded
[    2.972853] CORE cx23885[0]: subsystem: d471:9022, board: TeVii S471 [card=35,autodetected]
[    3.103380] cx23885_dvb_register() allocating 1 frontend(s)
[    3.103389] cx23885[0]: cx23885 based dvb card
[    3.107015] DS3000 chip version: 0.192 attached.
[    3.131007] ts2020_attach: Find tuner TS2020!
[    3.131013] DVB: registering new adapter (cx23885[0])
[    3.131020] cx23885 0000:02:00.0: DVB: registering **adapter 0** frontend 0 (Montage Technology DS3000)...
[    3.131473] cx23885_dev_checkrevision() **Hardware revision = 0xa5**
[    3.131485] cx23885[0]/0: found at 0000:02:00.0, **rev: 4**, irq: 16, latency: 0, mmio: 0xf7c00000
[    3.539981] ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
[    3.541814] ds3000_firmware_ondemand: Waiting for firmware upload(2)...


Your DMESG: > dmesg | grep -E "(ds3000|DS3000|cx|ts20)"
[   17.597115] cx23885 driver version 0.0.3 loaded
[   17.597392] CORE cx23885[0]: subsystem: d471:9022, board: TeVii S471 [card=35,autodetected]
[   17.746791] cx23885_dvb_register() allocating 1 frontend(s)
[   17.755602] cx23885[0]: cx23885 based dvb card
[   17.773343] DS3000 chip version: 0.192 attached.
[   17.801571] ts2020_attach: Find tuner TS2020!
[   17.801686] DVB: registering new adapter (cx23885[0])
[   17.801693] cx23885 0000:02:00.0: DVB: registering **adapter 2** frontend 0 (Montage Technology DS3000)...
[   17.802129] cx23885_dev_checkrevision() **Hardware revision = 0xb0**
[   17.802138] cx23885[0]/0: found at 0000:02:00.0, **rev: 2**, irq: 18, latency: 0, mmio: 0xfe800000

---

### Post by un1 on 2014-06-20
I promised to reply when I get back the card. Unfortunately, the seller could not get another TeVii S471 for me and sent me a DVBSky S960 USB Box - so I cannot investigate more with the TeVii card. 
For the new box I had to compile the drivers on my own for that card but now have problems with my previously installed DVB-T cards (AVerMedia AVerTV DVB-T 771) - they are not working anymore. So I have no luck with making DVB-S2 run on my linux machine :( 

Any suggestions for a DVB-S2 card supported really out of the box on linux?

---

### Post by blm-ubunet on 2014-06-20
The [FONT=Verdana][SIZE=2][COLOR=black][FONT=Verdana][SIZE=2][COLOR=black]TBS 6981 is reported to work with the open source drivers but you need a recent kernel.
[http://www.gossamer-threads.com/lists/mythtv/users/570485?search_string=kernel;#570485](http://www.gossamer-threads.com/lists/mythtv/users/570485?search_string=kernel;#570485)
[https://github.com/ljalves/linux_media/wiki](https://github.com/ljalves/linux_media/wiki)
I have read elsewhere that the open source drivers work better (for -s2) than the TBS blob.
The TBS h/w is probably the most expensive.

The firmware loading problem is possibly the kernel bug reported that the f/w transfer block size is too large?
(can't find proper link now)

[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

