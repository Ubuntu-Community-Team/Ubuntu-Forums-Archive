---
title: "Intel Wifi Link 5100AGN"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by commandergc on 2010-02-17
I just bought a netbook that sadly came with a wireless chip that is yet to be fully supported on linux, so i decided to swap it for an Intel 5100 AGN 512_HMW.

Linux picks up the card but the module fails to load. here is the output of dmesg | grep iw:
```
[   32.011663] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   32.011671] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   32.011865] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.011912] iwlagn 0000:02:00.0: setting latency timer to 64
[   32.012009] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x50
[   32.060685] iwlagn 0000:02:00.0: Unsupported (too old) EEPROM VER=0x114 < 0x11a CALIB=0x1 < 0x4
[   32.060729] iwlagn 0000:02:00.0: PCI INT A disabled
[   32.060986] iwlagn: probe of 0000:02:00.0 failed with error -22
```

after reading that message i downloaded the latest firmware from [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads) and extracted it to /lib/firmware but it still does not work.

i have also tried the latest compat-wireless too and again no luck. 

is their anything else i could try?

---

### Post by OanaGad on 2010-02-17
Need to contact manufacturer.

---

### Post by walt.smith1960 on 2010-02-17
Would NDISwrapper be worth a shot? A search should yield a wealth of information.  External WiFi adapters are a bother, especially on notebooks & netbooks.  I found this thread with what looks like a fix.  [http://ubuntuforums.org/showthread.php?t=1300560](http://ubuntuforums.org/showthread.php?t=1300560).   What version of Ubuntu are you using? It  might also be worth enabling backports.

---

### Post by commandergc on 2010-02-17
After more searching it looks like it may have something to do with the cards board revision. cards with REV: 0x50 seem to not work with iw* drivers and sadly it seems to not work with ndiswrapper either ](*,). I haven't tried the backports yet but i doubt they would work.

it looks like I'll have to stick with the RealTek 8192e that my netbook came with. this will mean having the inconvenience of recompiling the driver every time the kernel is updated that is until it's added to the mainstream kernel, Something i really wanted to avoid.

Does anyone have a recommendation as to what Half Mini PCIe wireless N card to get? that will work out of the box with ubuntu 9.10?

---

### Post by wjgeorge on 2010-02-17
same problem here. It does say "EEPROM" so maybe it's field programmable.

works fine under winblows

---

### Post by wjgeorge on 2010-02-18
I dont think you need to recompile the realtek driver. I've just been copying to the right driver directory.

It just doesnt work well on batteries

---

### Post by heidar on 2010-03-03
> **OanaGad said:**
> Need to contact manufacturer.


This is correct.

To explain this a bit; if you get this error, it normally means that you are using an experimental version of the card which was somehow leaked to the public. These cards normally originate from dubious sources like eBay.

I have the same card and the same issue. I contacted an Intel employee to make sure if there is anything that can be done to fix the issue, since the card works perfectly fine under Windows. If there's nothing I can do though, I am planning on sending the person I purchased the laptop from an angry message and demanding a replacement ASAP.

I'll let you know if there is a way to fix this, if there isn't then you should probably do the same.

---

### Post by el mariachi on 2010-04-29
I have the same card, same revision. Did you buy it on eBay? I did.
I already sent an email to Intel to find out if these are really experimental cards that shouldn't be out for sale. Anyways, I see this ending with me losing money.

ISn't there a way to "update" the card? :(

---

### Post by commandergc on 2010-04-30
Sadly their isn't much that can be done as the card can't be flashed.

---

### Post by el mariachi on 2010-04-30
> **commandergc said:**
> Sadly their isn't much that can be done as the card can't be flashed.
I can always ask for a refund :D

---

