---
title: "Wintv-HVR-1950"
date: 2010-04-17
forum: Multimedia Software
---

### Post by crx686 on 2010-04-17
Hi I just bought a WinTV-HVR-1950. I looked it up on linuxtv and it told me it works with it. I complied the V4L drivers and extracted the firmware from the driver CD that came with the Unit. Now I've been trying to get this to work in mythtv and I got as far as getting it to be probe and showing up in the capture card menu. Everything seems to be good The only thing that doesn't want to come on is the red light on the device. I can't get it to find any signal, when i click on watch tv it says please wait and 5 sec later it goes back to the main menu.  heres what dmesg says.

[   10.693243] pvrusb2: Hardware description: WinTV HVR-1950 Model 751xx
[   10.695050] usbcore: registered new interface driver pvrusb2
[   10.695053] pvrusb2: V4L in-tree version:Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
[   10.695055] pvrusb2: Debug mask is 31 (0x1f)
[   10.709707] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.731118] pvrusb2: Binding ir_video to i2c address 0x71.
[   10.740981] cx25840 1-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[   10.741805] pvrusb2: Attached sub-driver cx25840
[   10.754030] cfg80211: Calling CRDA to update world regulatory domain
[   10.781544] cfg80211: World regulatory domain updated:
[   10.781547]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.781549]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.781551]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.781553]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.781555]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.781557]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.799024] tuner 1-0042: chip found @ 0x84 (pvrusb2_a)
[   10.799033] pvrusb2: Attached sub-driver tuner
[   10.814604]   alloc irq_desc for 30 on node 0
[   10.814607]   alloc kstat_irqs on node 0
[   10.814616] forcedeth 0000:00:10.0: irq 30 for MSI/MSI-X
[   10.814855] eth0: no link during initialization.
[   10.815476] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.817731]   alloc irq_desc for 31 on node 0
[   10.817734]   alloc kstat_irqs on node 0
[   10.817742] forcedeth 0000:00:11.0: irq 31 for MSI/MSI-X
[   10.817936] eth1: no link during initialization.
[   10.818468] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   10.846232] cx25840 1-0044: firmware: requesting v4l-cx25840.fw
[   11.116394] phy0: Selected rate control algorithm 'minstrel'
[   11.117023] phy0: hwaddr 00:15:af:0d:75:55, RTL8187vB (default) V1 + rtl8225z2
[   11.139082] rtl8187: Customer ID is 0x00
[   11.139128] Registered led device: rtl8187-phy0::tx
[   11.139143] Registered led device: rtl8187-phy0::rx
[   11.139163] usbcore: registered new interface driver rtl8187
[   11.186481] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[   11.218180] lirc_dev: IR Remote Control driver registered, major 61 
[   11.241591] bttv: driver version 0.9.18 loaded
[   11.241595] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   11.249600] ivtv: Start initialization, version 1.4.1
[   11.249635] ivtv: End initialization
[   11.261784] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   11.261969] lirc_i2c: chip 0x0 found @ 0x71 (Hauppauge HVR1300)
[   11.261973] lirc_dev: lirc_register_driver: sample_rate: 10
[   12.546513] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:0e.1/input/input5
[   12.837751] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   12.837755] vboxdrv: Successfully done.
[   12.837757] vboxdrv: Found 2 processor cores.
[   12.837803] VBoxDrv: dbg - g_abExecMemory=ffffffffa045a420
[   12.837815] vboxdrv: fAsync=1 offMin=0x5fa57 offMax=0x5fa57
[   12.837861] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   12.837863] vboxdrv: Successfully loaded version 3.0.8_OSE (interface 0x000e0000).
[   12.843316] VBoxNetAdp: dbg - g_abExecMemory=ffffffffa05f7ac0
[   12.920488] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[   12.920493] HDA Intel 0000:02:00.1: PCI INT B -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
[   12.920518] HDA Intel 0000:02:00.1: setting latency timer to 64
[   13.414245] usplash:439 freeing invalid memtype ffffffffe0000000-ffffffffe1000000
[   13.515286] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   13.755691] tveeprom 1-00a2: Hauppauge model 75111, rev C3E9, serial# 6180465
[   13.755695] tveeprom 1-00a2: MAC address is 00:0d:fe:5e:4e:71
[   13.755697] tveeprom 1-00a2: tuner model is Philips 18271_8295 (idx 149, type 54)
[   13.755699] tveeprom 1-00a2: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   13.755701] tveeprom 1-00a2: audio processor is CX25843 (idx 37)
[   13.755703] tveeprom 1-00a2: decoder processor is CX25843 (idx 30)
[   13.755705] tveeprom 1-00a2: has radio, has IR receiver, has IR transmitter
[   13.755710] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB
[   13.755713] pvrusb2: Mapping standards mask=0x300b700 (PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB)
[   13.755715] pvrusb2: Setting up 6 unique standard(s)
[   13.755718] pvrusb2: Set up standard idx=0 name=PAL-M
[   13.755720] pvrusb2: Set up standard idx=1 name=PAL-N
[   13.755721] pvrusb2: Set up standard idx=2 name=PAL-Nc
[   13.755723] pvrusb2: Set up standard idx=3 name=NTSC-M
[   13.755725] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[   13.755726] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[   13.755729] pvrusb2: Initial video standard (determined by device type): NTSC-M
[   13.755738] pvrusb2: Device initialization completed successfully.
[   13.755793] pvrusb2: registered device video0 [mpeg]
[   13.755796] DVB: registering new adapter (pvrusb2-dvb)
[   13.763841] [drm] Setting GART location based on new memory map
[   13.779495] [drm] Loading RV630 CP Microcode
[   13.779544] [drm] Loading RV630 PFP Microcode
[   13.794573] [drm] Resetting GPU
[   13.794629] [drm] writeback test succeeded in 1 usecs
[   13.814081] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.827914] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa06121c0
[   13.901061] tda829x 1-0042: setting tuner address to 60
[   13.923279] __ratelimit: 57 callbacks suppressed
[   13.923282] type=1503 audit(1271532772.728:31): operation="open" pid=2094 parent=1 profile="/usr/sbin/ntpd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/usr/share/samba/upcase.dat"
[   13.923295] type=1503 audit(1271532772.728:32): operation="open" pid=2094 parent=1 profile="/usr/sbin/ntpd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/usr/share/samba/lowcase.dat"
[   13.924844] type=1503 audit(1271532772.728:33): operation="open" pid=2094 parent=1 profile="/usr/sbin/ntpd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/usr/share/samba/valid.dat"
[   13.967957] tda18271 1-0060: creating new instance
[   14.041440] TDA18271HD/C1 detected @ 1-0060
[   15.313482] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   15.762977] tda829x 1-0042: type set to tda8295+18271
[   20.310092] cx25840 1-0044: 0x0000 is not a valid video input!
[   20.406211] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   20.409338] tda829x 1-0042: type set to tda8295
[   20.451156] tda18271 1-0060: attaching existing instance

[  485.575769] cx25840 1-0044: firmware: requesting v4l-cx25840.fw
[  488.167158] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[  491.305487] usb 1-5: firmware: requesting v4l-cx2341x-enc.fw
[  650.803758] cx25840 1-0044: 0x0000 is not a valid video input!
[  809.278184] cx25840 1-0044: firmware: requesting v4l-cx25840.fw
[  811.791691] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[  818.563057] cx25840 1-0044: 0x0000 is not a valid video input!
[  837.043356] cx25840 1-0044: firmware: requesting v4l-cx25840.fw
[  839.560108] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[  930.371177] cx25840 1-0044: 0x0000 is not a valid video input!
[ 1612.972047] cx25840 1-0044: firmware: requesting v4l-cx25840.fw
[ 1615.481792] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[ 1654.800757] cx25840 1-0044: 0x0000 is not a valid video input!
[ 1671.147083] cx25840 1-0044: firmware: requesting v4l-cx25840.fw
[ 1673.660287] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[ 1680.650925] cx25840 1-0044: 0x0000 is not a valid video input!
[ 1701.056492] cx25840 1-0044: firmware: requesting v4l-cx25840.fw
[ 1703.571169] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[ 2309.571940] xawtv.bin[3666]: segfault at 0 ip 00007fba0a529441 sp 00007fffa00bdff8 error 4 in libc-2.10.1.so[7fba0a4aa000+166000]
[ 2447.286860] usbcore: deregistering interface driver pvrusb2
[ 2447.286916] pvrusb2: Device being rendered inoperable
[ 2447.287201] pvrusb2: unregistered device `&#65533;Si [mpeg]
[ 2447.287307] pvrusb2: unregistering DVB devices
[ 2447.289556] tda18271 1-0060: destroying instance
[ 2457.293299] pvrusb2: Hardware description: WinTV HVR-1950 Model 751xx
[ 2457.294810] usbcore: registered new interface driver pvrusb2
[ 2457.294818] pvrusb2: V4L in-tree version:Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
[ 2457.294824] pvrusb2: Debug mask is 31 (0x1f)
[ 2458.290172] usb 1-5: firmware: requesting v4l-pvrusb2-73xxx-01.fw
[ 2458.304288] pvrusb2: Device microcontroller firmware (re)loaded; it should now reset and reconnect.
[ 2458.336062] usb 1-5: USB disconnect, address 2
[ 2458.336294] pvrusb2: Device being rendered inoperable
[ 2460.130034] usb 1-5: new high speed USB device using ehci_hcd and address 4
[ 2460.292919] usb 1-5: configuration #1 chosen from 1 choice
[ 2460.293882] pvrusb2: Hardware description: WinTV HVR-1950 Model 751xx
[ 2460.338963] pvrusb2: Binding ir_video to i2c address 0x71.
[ 2460.339020] lirc_i2c: chip 0x0 found @ 0x71 (Hauppauge HVR1300)
[ 2460.339025] lirc_dev: lirc_register_driver: sample_rate: 10
[ 2460.348489] cx25840 1-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[ 2460.349490] pvrusb2: Attached sub-driver cx25840
[ 2460.360545] tuner 1-0042: chip found @ 0x84 (pvrusb2_a)
[ 2460.360560] pvrusb2: Attached sub-driver tuner
[ 2460.382594] cx25840 1-0044: firmware: requesting v4l-cx25840.fw
[ 2462.569207] cx25840 1-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[ 2462.670710] tveeprom 1-00a2: Hauppauge model 75111, rev C3E9, serial# 6180465
[ 2462.670719] tveeprom 1-00a2: MAC address is 00:0d:fe:5e:4e:71
[ 2462.670725] tveeprom 1-00a2: tuner model is Philips 18271_8295 (idx 149, type 54)
[ 2462.670732] tveeprom 1-00a2: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 2462.670738] tveeprom 1-00a2: audio processor is CX25843 (idx 37)
[ 2462.670744] tveeprom 1-00a2: decoder processor is CX25843 (idx 30)
[ 2462.670749] tveeprom 1-00a2: has radio, has IR receiver, has IR transmitter
[ 2462.670761] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB
[ 2462.670773] pvrusb2: Mapping standards mask=0x300b700 (PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB)
[ 2462.670779] pvrusb2: Setting up 6 unique standard(s)
[ 2462.670786] pvrusb2: Set up standard idx=0 name=PAL-M
[ 2462.670790] pvrusb2: Set up standard idx=1 name=PAL-N
[ 2462.670795] pvrusb2: Set up standard idx=2 name=PAL-Nc
[ 2462.670800] pvrusb2: Set up standard idx=3 name=NTSC-M
[ 2462.670805] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[ 2462.670809] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[ 2462.670816] pvrusb2: Initial video standard (determined by device type): NTSC-M
[ 2462.670834] pvrusb2: Device initialization completed successfully.
[ 2462.670968] pvrusb2: registered device video0 [mpeg]
[ 2462.670976] DVB: registering new adapter (pvrusb2-dvb)
[ 2462.741693] cx25840 1-0044: firmware: requesting v4l-cx25840.fw
[ 2464.929297] cx25840 1-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[ 2465.050666] tda829x 1-0042: setting tuner address to 60
[ 2465.083592] tda18271 1-0060: creating new instance
[ 2465.133423] TDA18271HD/C1 detected @ 1-0060
[ 2466.760615] tda829x 1-0042: type set to tda8295+18271
[ 2471.411545] usb 1-5: firmware: requesting v4l-cx2341x-enc.fw
[ 2474.723775] cx25840 1-0044: 0x0000 is not a valid video input!
[ 2474.821146] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[ 2474.824017] tda829x 1-0042: type set to tda8295
[ 2474.862468] tda18271 1-0060: attaching existing instance
[ 2477.653837] cx25840 1-0044: firmware: requesting v4l-cx25840.fw
[ 2479.847048] cx25840 1-0044: loaded v4l-cx25840.fw firmware (14264 bytes)


   Everything looks like its good to me, but then again I might be missing something, I know there's some errors but i don't know what that means. if you need more info let me know i tried explaining the best to my knowledge any help would be great thanks

  By the way I have Ubuntu 9.10 installed and its a USB device 2.0 thanks for any help

---

### Post by kdx on 2010-04-21
Try this...

```

sudo chmod 777 /dev/video0

```

---

### Post by crx686 on 2010-04-22
Thanks for the tip, but it didnt work. I think it might have to do something with the firmware cause at the bottom of the dmesg it says this

                      cx25840 1-0044: firmware: requesting v4l-cx25840.fw
[  613.513272] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[  651.063704] cx25840 1-0044: 0x0000 is not a valid video input!
[  662.503653] cx25840 1-0044: firmware: requesting v4l-cx25840.fw
[  665.014229] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)

 and at the very beging it tells me pvrusb2: Device being rendered inoperable

  Which i dont know what to do at that point

---

