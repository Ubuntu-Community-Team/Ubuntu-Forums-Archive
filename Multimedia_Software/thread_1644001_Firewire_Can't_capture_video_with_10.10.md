---
title: "Firewire: Can't capture video with 10.10"
date: 2010-12-12
forum: Multimedia Software
---

### Post by gilgongo on 2010-12-12
Ever since I installed 10.10 I can't capture video from my (admittedly very old) Sony DCR PC110 DV camera.

Linux monolake 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

I notice there's no /dev/raw1394 any more, and when I try dvgrab:

```
gilgongo@monolake:~$ sudo dvgrab -i
[sudo] password for gilgongo: 
rom1394_0 warning: read failed: 0x0000fffff0000414
error reading config rom directory for node 0
rom1394_1 warning: read failed: 0x0000fffff0000414
error reading config rom directory for node 1
Error: no camera exists
```


I see from dmesg that when I plug the camera in, I get a whole bunch of these:
```

[ 1047.430104] firewire_ohci: node ID not valid, new bus reset in progress
[ 1048.073003] firewire_core: skipped bus generations, destroying all nodes
[ 1048.570052] firewire_core: rediscovered device fw0
[ 1048.656864] firewire_core: rediscovered device fw1
[ 1048.656877] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[ 1048.670027] firewire_ohci: node ID not valid, new bus reset in progress
[ 1049.314092] firewire_core: skipped bus generations, destroying all nodes
[ 1049.810046] firewire_core: rediscovered device fw0
[ 1049.894717] firewire_core: rediscovered device fw1
[ 1049.894737] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[ 1049.910039] firewire_ohci: node ID not valid, new bus reset in progress
[ 1050.552014] firewire_core: skipped bus generations, destroying all nodes
[ 1051.051359] firewire_core: rediscovered device fw0
[ 1051.135832] firewire_core: rediscovered device fw1
[ 1051.135840] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[ 1051.150033] firewire_ohci: node ID not valid, new bus reset in progress

```


Any idea?

================================================

Looks like my Firewire card had either died or has ceased to be supported by Ubuntu. I bought another one on eBay and it worked fine. I think I bought my original one about 10 years ago, so perhaps it's not surprising.

---

### Post by apropos on 2011-01-28
Having the same problem as you on a DCR-PC100.  I realize that my hardware are old but am surprised that support for older hardware get dropped.  I thought Linux is all about supporting older hardware.  Btw, the same hardware is working on the 64 bit Ubuntu 9.10 partition.

```
kernel: [   87.561600] firewire_ohci: node ID not valid, new bus reset in progress
kernel: [   87.716287] firewire_core: skipped bus generations, destroying all nodes
kernel: [   88.216530] firewire_core: rediscovered device fw0
kernel: [   88.363421] firewire_core: created device fw1: GUID 0800460101c35019, S100
kernel: [   88.363426] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
kernel: [   88.368538] firewire_ohci: node ID not valid, new bus reset in progress
```


```
# dvgrab
rom1394_0 warning: read failed: 0x0000fffff0000414
error reading config rom directory for node 0
Error: no camera exists
```

```
# lspci | grep 1394
02:06.0 FireWire (IEEE 1394): Texas Instruments TSB12LV22 IEEE-1394 Controller (rev 01)
```

```
# lsmod | grep 1394
raw1394                22462  0 
ieee1394               81101  1 raw1394
```

---

### Post by gilgongo on 2011-02-08
I solved this by buying a new FireWire card in the end, it seems it was to do with that and not the camera itself:

[http://www.amazon.co.uk/gp/product/B000JYWEGU/ref=oss_product](http://www.amazon.co.uk/gp/product/B000JYWEGU/ref=oss_product)

(it has a TI chip, which I'm told is the safest bet for Firewire cards under Linux)

---

### Post by VoodooLoveDog on 2011-03-30
I'm confirming this problem on a machine with the following chipset:

```
05:02.4 FireWire (IEEE 1394): ALi Corporation M5253 P1394 OHCI 1.1 Controller]
```

I get the following messages:

```
[    1.424693] firewire_ohci 0000:05:02.4: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    1.680286] firewire_ohci: isochronous cycle inconsistent
[    1.700010] firewire_ohci: Added fw-ohci device 0000:05:02.4, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x1
[    1.780007] firewire_core: BM lock failed, making local node (ffc0) root.
[    1.780010] firewire_core: phy config: card 0, new root=ffc0, gap_count=5
[    2.180074] firewire_core: created device fw0: GUID 0090e62500000c6d, S400
[    2.539075] firewire_ohci: isochronous cycle inconsistent
[   32.290040] firewire_core: giving up on config rom for node id ffc1
[  845.282787] firewire_ohci: isochronous cycle inconsistent

```

I followed the pages found here:

[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

Unfortunately, I still received errors when trying capture via Kino.

I tried another machine with a VIA chipset and it worked once I loaded the raw1394 module

```
sudo modprobe raw1394
```

Kino pulled the video no problems. I'm going to pick-up a card with a TI chipset for the first machine to see if I can capture.

---

### Post by no2498 on 2011-03-31
if you type webcam in the package manager you can find programs that use 1394
this may help you get it

---

### Post by VoodooLoveDog on 2011-04-04
I swapped the Firewire card for this one Adaptec AFW-2100:

```
05:02.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)
```

Now it works great after loading the raw1394 kernel module. So I'm calling shenanigans on the ALi chipset. Which it could very well be the connection from the old camera (Sony DCR-TRV17) and not the chipset.

---

### Post by Nausser on 2011-06-14
I can't seem to make any progress on this either. I even have a Ti firewire chipset.

```
lspci | grep 1394
07:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
```
When I run kino as sudo from the terminal I get this line repeating over and over until I exit from the capture tab.
```
rom1394_0 warning: read failed: 0x0000fffff0000414
```
Also, when running dvgrab as sudo from terminal I get the following
```
sudo dvgrab -i
rom1394_0 warning: read failed: 0x0000fffff0000414
error reading config rom directory for node 0
Error: no camera exists
```
It looks as though its installing perfectly fine from the dmesg log.
```
dmesg
[  334.133452] firewire_core: skipped bus generations, destroying all nodes
[  334.630046] firewire_core: rediscovered device fw0
[  334.630056] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[  334.630270] firewire_core: skipped bus generations, destroying all nodes
[  335.090021] firewire_core: giving up on config rom for node id ffc0
[  335.130044] firewire_core: rediscovered device fw0
[  335.217164] firewire_core: created device fw1: GUID 0800460102961c00, S100
[  526.375851] lo: Disabled Privacy Extensions
[ 1317.611135] ieee1394: raw1394: /dev/raw1394 device initialized
```
Please let me know your thoughts. I also tried
```
sudo modprobe raw1394
```
Unfortunately no luck on that one either. 
I'm running Ubuntu Studio 10.10 x64.

---

### Post by minidisk on 2011-07-07
I have the same problem. what i have discovered is that the error comes up under my normal user account but if i change to sudo it works just fine. there has to be a permission issue somewhere. i thought maybe it was the actual file i was running but that is not the case.

---

### Post by minidisk on 2011-07-07
solved my problem by using the guid option and it solved my problem. hope this helps others.

---

