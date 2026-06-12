---
title: "hauppauge wintv pvr2 not working"
date: 2010-03-07
forum: Multimedia Software
---

### Post by havmaage on 2010-03-07
Hi im a newbie to ubuntu and just changed my install from ms xp to ubuntu, im having problem get my tv tuner to work, it is a hauppauge wintv pvr2 

i  have done following to configure it, 
enabled the driver in the kernel ( recompile) 
downloaded and installed the firmware from ivtv 
my dmesg looks ok 
[   10.698215] pvrusb2: Attached sub-driver tuner
[   10.720703] tveeprom 2-0050: Hauppauge model 29039, rev D157, serial# 8037959
[   10.720706] tveeprom 2-0050: tuner model is Philips FM1216 ME MK3 (idx 57, type 38)
[   10.720709] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   10.720712] tveeprom 2-0050: audio processor is MSP3415 (idx 6)
[   10.720715] tveeprom 2-0050: decoder processor is SAA7115 (idx 19)
[   10.720717] tveeprom 2-0050: has radio, has IR receiver, has no IR transmitter
[   10.720725] pvrusb2: Supported video standard(s) reported available in hardware: PAL-B/B1/D/D1/G/H/I/K;SECAM-B/D/G/H/K/K
[   10.720732] pvrusb2: Mapping standards mask=0xff00ff (PAL-B/B1/D/D1/G/H/I/K;SECAM-B/D/G/H/K/K1/L/LC)
[   10.720735] pvrusb2: Setting up 20 unique standard(s)
[   10.720739] pvrusb2: Set up standard idx=0 name=PAL-B/G
[   10.720742] pvrusb2: Set up standard idx=1 name=PAL-D/K
[   10.720744] pvrusb2: Set up standard idx=2 name=SECAM-B/G
[   10.720747] pvrusb2: Set up standard idx=3 name=SECAM-D/K
[   10.720749] pvrusb2: Set up standard idx=4 name=PAL-B
[   10.720751] pvrusb2: Set up standard idx=5 name=PAL-B1
[   10.720753] pvrusb2: Set up standard idx=6 name=PAL-G
[   10.720756] pvrusb2: Set up standard idx=7 name=PAL-H
[   10.720758] pvrusb2: Set up standard idx=8 name=PAL-I
[   10.720760] pvrusb2: Set up standard idx=9 name=PAL-D
[   10.720762] pvrusb2: Set up standard idx=10 name=PAL-D1
[   10.720764] pvrusb2: Set up standard idx=11 name=PAL-K
[   10.720767] pvrusb2: Set up standard idx=12 name=SECAM-B
[   10.720769] pvrusb2: Set up standard idx=13 name=SECAM-D
[   10.720771] pvrusb2: Set up standard idx=14 name=SECAM-G
[   10.720773] pvrusb2: Set up standard idx=15 name=SECAM-H
[   10.720776] pvrusb2: Set up standard idx=16 name=SECAM-K
[   10.720778] pvrusb2: Set up standard idx=17 name=SECAM-K1
[   10.720780] pvrusb2: Set up standard idx=18 name=SECAM-L
[   10.720783] pvrusb2: Set up standard idx=19 name=SECAM-LC
[   10.720785] pvrusb2: Initial video standard auto-selected to PAL-B/G
[   10.720793] pvrusb2: Device initialization completed successfully.
[   10.720860] pvrusb2: registered device video0 [mpeg]
[   10.720878] pvrusb2: registered device radio0 [mpeg]
[   10.721220] usb 1-3: firmware: requesting v4l-cx2341x-enc.fw
[   11.901623] tuner-simple 2-0061: creating new instance
[   11.901629] tuner-simple 2-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   12.688554] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.600831] eth0: Media Link On 100mbps full-duplex 
[   21.645811] [drm] DAC-9: set mode  22
[   23.056011] eth0: no IPv6 routers present
[   78.460322] Marking TSC unstable due to cpufreq changes
[   78.460408] Switching to clocksource acpi_pm
pluto@pluto:~$ 
lsusb

Bus 001 Device 003: ID 2040:2900 Hauppauge 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 1532:0200 Razer USA, Ltd 
Bus 003 Device 002: ID 1532:0103 Razer USA, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c03f Logitech, Inc. UltraX Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


pluto@pluto:~$ modprobe -l | grep pvr
kernel/drivers/media/video/pvrusb2/pvrusb2.ko
pluto@pluto:~$ 

Everything seems ok but i cannot get the xawtv to work with sinces it asks for /dev/vbi when i using scantv to scan for tv channels. 

Im not interested in using mythtv because i only want to se tv at a small window on the desktop, 

can anybody help me out. 

by the way my kernel is 
Linux pluto 2.6.32.7-mk #1 SMP Sun Mar 7 13:21:28 CET 2010 i686 GNU/Linux

---

### Post by saedelaere on 2010-05-12
> **havmaage said:**
> Hi im a newbie to ubuntu and just changed my install from ms xp to ubuntu, im having problem get my tv tuner to work, it is a hauppauge wintv pvr2 

i  have done following to configure it, 
enabled the driver in the kernel ( recompile) 
downloaded and installed the firmware from ivtv 
my dmesg looks ok 
[   10.698215] pvrusb2: Attached sub-driver tuner
[   10.720703] tveeprom 2-0050: Hauppauge model 29039, rev D157, serial# 8037959
[   10.720706] tveeprom 2-0050: tuner model is Philips FM1216 ME MK3 (idx 57, type 38)
[   10.720709] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   10.720712] tveeprom 2-0050: audio processor is MSP3415 (idx 6)
[   10.720715] tveeprom 2-0050: decoder processor is SAA7115 (idx 19)
[   10.720717] tveeprom 2-0050: has radio, has IR receiver, has no IR transmitter
[   10.720725] pvrusb2: Supported video standard(s) reported available in hardware: PAL-B/B1/D/D1/G/H/I/K;SECAM-B/D/G/H/K/K
[   10.720732] pvrusb2: Mapping standards mask=0xff00ff (PAL-B/B1/D/D1/G/H/I/K;SECAM-B/D/G/H/K/K1/L/LC)
[   10.720735] pvrusb2: Setting up 20 unique standard(s)
[   10.720739] pvrusb2: Set up standard idx=0 name=PAL-B/G
[   10.720742] pvrusb2: Set up standard idx=1 name=PAL-D/K
[   10.720744] pvrusb2: Set up standard idx=2 name=SECAM-B/G
[   10.720747] pvrusb2: Set up standard idx=3 name=SECAM-D/K
[   10.720749] pvrusb2: Set up standard idx=4 name=PAL-B
[   10.720751] pvrusb2: Set up standard idx=5 name=PAL-B1
[   10.720753] pvrusb2: Set up standard idx=6 name=PAL-G
[   10.720756] pvrusb2: Set up standard idx=7 name=PAL-H
[   10.720758] pvrusb2: Set up standard idx=8 name=PAL-I
[   10.720760] pvrusb2: Set up standard idx=9 name=PAL-D
[   10.720762] pvrusb2: Set up standard idx=10 name=PAL-D1
[   10.720764] pvrusb2: Set up standard idx=11 name=PAL-K
[   10.720767] pvrusb2: Set up standard idx=12 name=SECAM-B
[   10.720769] pvrusb2: Set up standard idx=13 name=SECAM-D
[   10.720771] pvrusb2: Set up standard idx=14 name=SECAM-G
[   10.720773] pvrusb2: Set up standard idx=15 name=SECAM-H
[   10.720776] pvrusb2: Set up standard idx=16 name=SECAM-K
[   10.720778] pvrusb2: Set up standard idx=17 name=SECAM-K1
[   10.720780] pvrusb2: Set up standard idx=18 name=SECAM-L
[   10.720783] pvrusb2: Set up standard idx=19 name=SECAM-LC
[   10.720785] pvrusb2: Initial video standard auto-selected to PAL-B/G
[   10.720793] pvrusb2: Device initialization completed successfully.
[   10.720860] pvrusb2: registered device video0 [mpeg]
[   10.720878] pvrusb2: registered device radio0 [mpeg]
[   10.721220] usb 1-3: firmware: requesting v4l-cx2341x-enc.fw
[   11.901623] tuner-simple 2-0061: creating new instance
[   11.901629] tuner-simple 2-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   12.688554] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.600831] eth0: Media Link On 100mbps full-duplex 
[   21.645811] [drm] DAC-9: set mode  22
[   23.056011] eth0: no IPv6 routers present
[   78.460322] Marking TSC unstable due to cpufreq changes
[   78.460408] Switching to clocksource acpi_pm
pluto@pluto:~$ 
lsusb

Bus 001 Device 003: ID 2040:2900 Hauppauge 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 1532:0200 Razer USA, Ltd 
Bus 003 Device 002: ID 1532:0103 Razer USA, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c03f Logitech, Inc. UltraX Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


pluto@pluto:~$ modprobe -l | grep pvr
kernel/drivers/media/video/pvrusb2/pvrusb2.ko
pluto@pluto:~$ 

Everything seems ok but i cannot get the xawtv to work with sinces it asks for /dev/vbi when i using scantv to scan for tv channels. 

Im not interested in using mythtv because i only want to se tv at a small window on the desktop, 

can anybody help me out. 

by the way my kernel is 
Linux pluto 2.6.32.7-mk #1 SMP Sun Mar 7 13:21:28 CET 2010 i686 GNU/Linux

xawtv does not support your device but [TV-Viewer]("http://tv-viewer.sourceforge.net/") does!

Regards

---

