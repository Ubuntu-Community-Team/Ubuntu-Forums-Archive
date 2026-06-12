---
title: "accelerate video card?"
date: 2011-10-02
forum: Multimedia Software
---

### Post by qwertyjjj on 2011-10-02
Is there anyway ti accelerate my video card?
I have a lot of stuttering in the video (audio fine) when playing back streamed video/TV from internet sites.
Strangely though, it works fine when playing back video on the actual hard disk through mplayer or VLC.
I had to replace my video card recently from a 256Mb down to 128

```

lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
j@-Inspiron-9300:~$ 

``` 

```

*-display
                description: VGA compatible controller
                product: M22 [Mobility Radeon X300]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:41 memory:d0000000-d7ffffff ioport:de00(size=256) memory:dfdf0000-dfdfffff memory:dfe00000-dfe1ffff

```

---

### Post by MartyBuntu on 2011-10-02
Sounds like either a Flash issue or an internet speed connection problem.

Any details on either of these?

---

### Post by qwertyjjj on 2011-10-02
> **MartyBuntu said:**
> Sounds like either a Flash issue or an internet speed connection problem.

Any details on either of these?

Could be Flash but it seems the same on Opera and FF.
Internet speed is 10Mb so shouldn't be a problem.
It's more like the video doesn;t run fast enough so it always lags the sound.

---

### Post by MartyBuntu on 2011-10-02
Have you run an online speed test?

---

### Post by qwertyjjj on 2011-10-02
> **MartyBuntu said:**
> Have you run an online speed test?

Download 10.66Mbps
Upload 1Mbps

---

### Post by qwertyjjj on 2011-10-04
any ideas on how to test the graphics card?

---

