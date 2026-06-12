---
title: "DVR DEVICE: : Device or resource busy"
date: 2009-12-10
forum: Multimedia Software
---

### Post by don_engtech on 2009-12-10
I am working on a headless DVR using Ubuntu server 9.04.  I have three hauppauge pvr-2250 cards in it.  Using dvbstream like so: ```
dvbstream -vsb 8 -f 695000000 -n 240 52 49 -c /dev/dvb/adapter0 -o > /media/dvr/testA.mpg
``` works fine. If i try to start another recording on another card like ```
dvbstream -vsb 8 -f 695000000 -n 240 52 49 -c /dev/dvb/adapter1 -o > /media/dvr/testB.mpg
``` then I get: ```
FRONTEND DEVICE: : Device or resource busy
Tuning to 695000000 Hz
FE_GET_INFO: : Bad file descriptor
dvbstream will stop after 240 seconds (4 minutes)
DVR DEVICE: : Device or resource busy

``` So I can only record from one card at a time. Any ideas would be greatly appreciated.

lspci:
```
00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:03.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port B)
00:04.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A)
00:05.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port B)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)
02:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)
03:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
06:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
07:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
07:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
08:07.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro 215GP (rev 5c)

```

 dmesg |grep saa7164 :
```
[   12.054472] saa7164 driver loaded
[   12.054533] saa7164 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.054900] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   12.054905] saa7164[0]/0: found at 0000:01:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xfd000000
[   12.054910] saa7164 0000:01:00.0: setting latency timer to 64
[   12.252581] saa7164_downloadfirmware() no first image
[   12.252689] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   12.252696] saa7164 0000:01:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[   13.065108] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   13.065110] saa7164_downloadfirmware() firmware loaded.
[   13.065116] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   13.065156] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   13.065157] saa7164_downloadfirmware() BSLSize = 0x0
[   13.065158] saa7164_downloadfirmware() Reserved = 0x0
[   13.065159] saa7164_downloadfirmware() Version = 0x51cc1
[   20.290115] saa7164_downloadimage() Image downloaded, booting...
[   20.400116] saa7164_downloadimage() Image booted successfully.
[   22.810078] saa7164_downloadimage() Image downloaded, booting...
[   24.243868] saa7164_downloadimage() Image booted successfully.
[   24.284437] saa7164[0]: Hauppauge eeprom: model=88061
[   25.004797] DVB: registering new adapter (saa7164)
[   29.027860] DVB: registering new adapter (saa7164)
[   29.028060] saa7164 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   29.028369] CORE saa7164[1]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   29.028374] saa7164[1]/0: found at 0000:02:00.0, rev: 129, irq: 19, latency: 0, mmio: 0xfd800000
[   29.028379] saa7164 0000:02:00.0: setting latency timer to 64
[   29.220079] saa7164_downloadfirmware() no first image
[   29.220188] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   29.220190] saa7164 0000:02:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[   29.755932] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   29.755934] saa7164_downloadfirmware() firmware loaded.
[   29.755940] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   29.755981] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   29.755982] saa7164_downloadfirmware() BSLSize = 0x0
[   29.755983] saa7164_downloadfirmware() Reserved = 0x0
[   29.755984] saa7164_downloadfirmware() Version = 0x51cc1
[   36.870117] saa7164_downloadimage() Image downloaded, booting...
[   36.980116] saa7164_downloadimage() Image booted successfully.
[   39.390081] saa7164_downloadimage() Image downloaded, booting...
[   40.820116] saa7164_downloadimage() Image booted successfully.
[   40.864207] saa7164[1]: Hauppauge eeprom: model=88061
[   41.534903] DVB: registering new adapter (saa7164)
[   44.797378] DVB: registering new adapter (saa7164)
[   44.797574] saa7164 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   44.797928] CORE saa7164[2]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   44.797933] saa7164[2]/0: found at 0000:03:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfe000000
[   44.797938] saa7164 0000:03:00.0: setting latency timer to 64
[   44.990081] saa7164_downloadfirmware() no first image
[   44.990186] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   44.990188] saa7164 0000:03:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[   45.523023] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   45.523025] saa7164_downloadfirmware() firmware loaded.
[   45.523031] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   45.523068] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   45.523069] saa7164_downloadfirmware() BSLSize = 0x0
[   45.523070] saa7164_downloadfirmware() Reserved = 0x0
[   45.523071] saa7164_downloadfirmware() Version = 0x51cc1
[   52.750115] saa7164_downloadimage() Image downloaded, booting...
[   52.860114] saa7164_downloadimage() Image booted successfully.
[   55.273830] saa7164_downloadimage() Image downloaded, booting...
[   56.700114] saa7164_downloadimage() Image booted successfully.
[   56.740884] saa7164[2]: Hauppauge eeprom: model=88061
[   57.414903] DVB: registering new adapter (saa7164)
[   60.677864] DVB: registering new adapter (saa7164)
```

Thanks,
don_engtech

---

### Post by gordintoronto on 2009-12-10
If you don't get an answer here, you might get one at
[http://forums.snapstream.com/vb/home-theater-pc-discussion/](http://forums.snapstream.com/vb/home-theater-pc-discussion/)

---

