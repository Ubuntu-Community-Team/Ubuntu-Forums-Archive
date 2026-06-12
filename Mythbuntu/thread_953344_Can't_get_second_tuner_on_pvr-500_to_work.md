---
title: "Can't get second tuner on pvr-500 to work"
date: 2008-10-20
forum: Mythbuntu
---

### Post by bobjimbob on 2008-10-20
Hi ivtv seems to have some trouble loading the firmware onto the second tuner but it seems to work fine on the first. Have tried switching pci slots, different versions of ivtv and different versions of mythbuntu to get this working but doesnt look like it wants to. Any help would be appreciated

Heres the relevant output of dmesg 

[   13.698897] Linux video capture interface: v2.00
[   13.772716] ivtv:  Start initialization, version 1.4.0
[   13.773726] ivtv0: Initializing card #0
[   13.773734] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   13.812758] ivtv 0000:02:08.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.812774] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   13.865369] tveeprom 1-0050: Hauppauge model 23559, rev E491, serial# 10198253
[   13.865374] tveeprom 1-0050: tuner model is Philips FQ1216AME MK4 (idx 91, type 56)
[   13.865379] tveeprom 1-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   13.865384] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   13.865388] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   13.865391] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   13.865394] tveeprom 1-0050: has radio
[   13.865398] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   14.333004] parport_pc 00:0b: reported by Plug and Play ACPI
[   14.333051] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   14.752334] cx25840 1-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   14.926707] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   14.926800] tea5767 1-0060: type set to Philips TEA5767HN FM Radio
[   15.142578] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   15.262089] tda9887 1-0043: creating new instance
[   15.262094] tda9887 1-0043: tda988[5/6/7] found
[   15.263416] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   15.263450] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   15.325486] tuner-simple 1-0061: creating new instance
[   15.325493] tuner-simple 1-0061: type set to 56 (Philips PAL/SECAM multi (FQ1216AME MK4))
[   15.349232] firmware: requesting v4l-cx25840.fw
[   21.124520] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   21.194876] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   21.195111] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   21.195333] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   21.195557] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   21.195784] ivtv0: Registered device radio0 for encoder radio
[   21.195788] ivtv0: Initialized card #0: WinTV PVR 500 (unit #1)
[   21.196050] ivtv1: Initializing card #1
[   21.196056] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   21.196163] ivtv 0000:02:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.196177] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   21.248921] tveeprom 2-0050: Hauppauge model 23559, rev E491, serial# 10198253
[   21.248926] tveeprom 2-0050: tuner model is Philips FQ1216AME MK4 (idx 91, type 56)
[   21.248931] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   21.248935] tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   21.248940] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   21.248943] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   21.248946] tveeprom 2-0050: has radio
[   21.248950] ivtv1: Correcting tveeprom data: no radio present on second unit
[   21.248953] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   21.280849] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #1)
[   21.290553] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   21.290847] tda9887 2-0043: creating new instance
[   21.290850] tda9887 2-0043: tda988[5/6/7] found
[   21.292411] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   21.292688] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   21.301396] tuner-simple 2-0061: creating new instance
[   21.301401] tuner-simple 2-0061: type set to 56 (Philips PAL/SECAM multi (FQ1216AME MK4))
[   21.318150] firmware: requesting v4l-cx25840.fw
[   24.741661] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   24.812050] ivtv1: Registered device video1 for encoder MPG (4096 kB)
[   24.812338] ivtv1: Registered device video33 for encoder YUV (2048 kB)
[   24.812606] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
[   24.812912] ivtv1: Registered device video25 for encoder PCM (320 kB)
[   24.812917] ivtv1: Initialized card #1: WinTV PVR 500 (unit #2)
[   24.815164] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   24.815171] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   24.815183] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   24.815540] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   24.817628] ivtv:  End initialization
[   26.371917] lp0: using parport0 (interrupt-driven).
[   26.687203] Adding 867500k swap on /dev/sda3.  Priority:-1 extents:1 across:867500k
[   27.395933] EXT3 FS on sda2, internal journal
[   29.154257] type=1505 audit(1224481761.931:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3862
[   29.154721] type=1505 audit(1224481761.931:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3862
[   29.211676] type=1505 audit(1224481761.987:4): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=3866
[   29.450081] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.197221] ACPI: WMI: Mapper loaded
[   32.566553] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   33.160232] NET: Registered protocol family 10
[   33.162433] lo: Disabled Privacy Extensions
[   35.413339] ppdev: user-space parallel port driver
[   43.824019] firmware: requesting v4l-cx2341x-enc.fw
[   43.883440] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   44.080136] ivtv0: Encoder revision: 0x02060039
[   45.116024] firmware: requesting v4l-cx2341x-enc.fw
[   45.151771] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   45.381485] ivtv1: Encoder mailbox not found
[   45.381497] ivtv1: Retry loading firmware
[   46.004019] firmware: requesting v4l-cx2341x-enc.fw
[   46.043743] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   46.273527] ivtv1: Encoder mailbox not found
[   46.273539] ivtv1: Failed to initialize on minor 225
[   46.278195] ivtv1: Failed to initialize on minor 1
[   46.281758] ivtv1: Failed to initialize on minor 25
[   46.285667] ivtv1: Failed to initialize on minor 33


Running on mythbuntu 8.10 beta, athlon 2500+, radeon 9200se, 512mb ram, gigabyte ga-7vm400m(f), and 330gb worth of hdd

---

### Post by GuruMadMat on 2008-11-17
I have the same problem.
dmesg | grep ivtv
```
[   37.923839] ivtv:  Start initialization, version 1.1.0
[   40.722399] ivtv0: Initializing card #0
[   40.722406] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   40.723289] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   40.788578] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   40.849222] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   40.853136] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   40.853400] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   40.886814] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   40.902863] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   40.911635] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   40.911672] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   40.911706] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   40.911736] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   40.911772] ivtv0: Registered device radio0 for encoder radio
[   40.911776] ivtv0: Initialized card #0: WinTV PVR 500 (unit #1)
[   40.911882] ivtv1: Initializing card #1
[   40.911889] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   40.912061] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   40.917888] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   40.921107] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   40.937541] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[   40.937799] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   41.004988] ivtv1: Correcting tveeprom data: no radio present on second unit
[   41.004990] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   41.025098] ivtv1: Registered device video1 for encoder MPG (4096 kB)
[   41.025163] ivtv1: Registered device video33 for encoder YUV (2048 kB)
[   41.025264] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
[   41.025330] ivtv1: Registered device video25 for encoder PCM (320 kB)
[   41.025334] ivtv1: Initialized card #1: WinTV PVR 500 (unit #2)
[   41.026058] ivtv:  End initialization
[   60.407043] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   60.608037] ivtv0: Encoder revision: 0x02060039
[   65.136753] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   65.436377] ivtv1: Encoder firmware dead!
[   65.436386] ivtv1: Retry loading firmware
[   66.079553] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   66.380882] ivtv1: Encoder firmware dead!
[   66.380901] ivtv1: Failed to initialize on minor 225
[   66.383476] ivtv1: Failed to initialize on minor 1
[   66.385951] ivtv1: Failed to initialize on minor 25
[   66.388414] ivtv1: Failed to initialize on minor 33
[   69.884027] ivtv1: Failed to initialize on minor 1
[ 1357.975719] ivtv1: Removed WinTV PVR 500 (unit #2), card #1
[ 1358.599720] ivtv0: Removed WinTV PVR 500 (unit #1), card #0
[ 1365.829221] ivtv:  Start initialization, version 1.1.0
[ 1365.829382] ivtv0: Initializing card #0
[ 1365.829387] ivtv0: Autodetected Hauppauge card (cx23416 based)
[ 1365.837205] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[ 1365.841157] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[ 1365.841442] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[ 1365.857892] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[ 1365.858162] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[ 1365.925633] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[ 1365.947520] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[ 1365.947558] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[ 1365.947588] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[ 1365.947620] ivtv0: Registered device video24 for encoder PCM (320 kB)
[ 1365.947648] ivtv0: Registered device radio0 for encoder radio
[ 1365.947652] ivtv0: Initialized card #0: WinTV PVR 500 (unit #1)
[ 1365.947748] ivtv1: Initializing card #1
[ 1365.947753] ivtv1: Autodetected Hauppauge card (cx23416 based)
[ 1365.957142] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #1)
[ 1365.961564] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[ 1365.978452] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[ 1365.978741] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[ 1366.046387] ivtv1: Correcting tveeprom data: no radio present on second unit
[ 1366.046392] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[ 1366.609682] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[ 1366.806027] ivtv0: Encoder revision: 0x02060039
[ 1370.495294] ivtv1: Registered device video1 for encoder MPG (4096 kB)
[ 1370.495336] ivtv1: Registered device video33 for encoder YUV (2048 kB)
[ 1370.495368] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
[ 1370.495398] ivtv1: Registered device video25 for encoder PCM (320 kB)
[ 1370.495402] ivtv1: Initialized card #1: WinTV PVR 500 (unit #2)
[ 1370.495428] ivtv:  End initialization
[ 1371.301252] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[ 1371.603369] ivtv1: Encoder firmware dead!
[ 1371.603377] ivtv1: Retry loading firmware
[ 1372.248972] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[ 1372.551866] ivtv1: Encoder firmware dead!
[ 1372.551875] ivtv1: Failed to initialize on minor 1
[ 1372.554600] ivtv1: Failed to initialize on minor 33
[ 1372.557258] ivtv1: Failed to initialize on minor 225
[ 1372.559901] ivtv1: Failed to initialize on minor 25
[ 1399.867919] ivtv1: Failed to initialize on minor 1

```


Running on Ubuntu 8.04 Intel P4

Does anyone know a solution

---

### Post by ian dobson on 2008-11-18
Hi,

I had similar problems with my PVR-500,for me I was seeing "select erors" in MythTV with trying to record from the second tuner.

I solved the problem by installing the bleeding edge ivtv drivers.

Have a look here [http://ubuntuforums.org/showthread.php?t=968121&highlight=pvr+500](http://ubuntuforums.org/showthread.php?t=968121&highlight=pvr+500)  post number 6.

Regards
Ian Dobson

---

### Post by bobjimbob on 2009-01-08
Thanks for the response Ian,
I tried following the instructions but I still get the same problems, I'm starting to think there maybe something wrong with one of the tuners as when I try it in windows I get the same problem.

---

### Post by ian dobson on 2009-01-09
Hi,

Try sticking the tuner in a different PCI slot, it could be a hardware conflict.

Regards
Ian Dobson

---

### Post by bobjimbob on 2009-01-09
> **bobjimbob said:**
> Have tried switching pci slots

I've tried everything even putting it in other computers but I still get the same error. I'm going to try knoppmyth and see if that makes a difference, but am running out of ideas.

---

### Post by ian dobson on 2009-01-10
Hi,

I think you should give up, the card is fubar.

Regards
Ian Dobson

---

### Post by bobjimbob on 2009-01-15
Just tried knoppmyth and it detects it perfectly! Don't know why this doesn't work in mythbuntu but it looks like I'm going to be sticking with knoppmyth.

---

