---
title: "Toshiba Satellite A215-S7422 Wireless Internet Help"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by Bone Crusher on 2009-11-11
Hello, I am new to xubuntu. I noticed my wireless internet is not working. I also don't see anywhere where i can adjust the volume for my speakers. For the wireless internet, I tried to download the drivers, I just can get them to install. I also downloaded this mousepad file that is supposed to install it and it says command failed. I downloaded Wi-Fi Radar and it does pick up any network. Any one know how I can solve this problem?

---

### Post by Bone Crusher on 2009-11-12
If I find the drivers for windows, is there a way to make it some how work? I can't find the correct drivers for my specific computer.

---

### Post by Bone Crusher on 2009-11-18
If any one is able to tell me step by step what to do, that would be awsome.

---

### Post by Dude-PWB- on 2009-11-18
You can install ndsiwrapper from synaptic and download the windows drivers for your wireless device and use them in ndiswrapper to make your wireless work.

Realtek does have linux drivers for their wireless chipsets but we will need to know which chipset you have to know which driver you need.

---

### Post by eremyja on 2009-11-18
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) says:
> 
To determine what wireless card/chipset you have, open up a terminal and type the following. 
lspci -v | less
Then, scroll to find your wireless device and note down its details. For USB devices, type lsusb instead.


this should tell you your chipset

---

### Post by Bone Crusher on 2009-11-18
This is what it told me.

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: f8000000-f81fffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=0d, sec-latency=0
        I/O behind bridge: 0000a000-0000afff

---

### Post by eremyja on 2009-11-18
ok that cant be right because thats just video stuff try this:
```

lspci -v > ~/lspci.txt

```

then upload lspci.txt from you home directory or just copy and paste the contents of it here

---

