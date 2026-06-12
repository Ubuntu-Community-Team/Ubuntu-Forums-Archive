---
title: "HVR 1300 remote not working"
date: 2009-02-01
forum: Multimedia Software
---

### Post by morgan88 on 2009-02-01
Hi
I have recently successfully configured a HVR 1300 with MythTV in Ubuntu 8.10 and it works fine with analog even if I get some clics in the sound on some channels. However, I don't get the remote to work. (I've got the black version of the remote and lirc 0.8.3 installed) When I run 

cat /proc/bus/input/devices

the remote isn't listed. But when I run dmesg it seems that the remote is recognized. this is the relevant output from dmesg:

[   11.299016] Linux video capture interface: v2.00
[   11.347662] cx2388x alsa driver version 0.0.6 loaded
[   11.348351] cx88_audio 0000:03:06.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   11.348970] cx88[0]: subsystem: 0070:9601, board: Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder [card=56,autodetected]
[   11.348972] cx88[0]: TV tuner type 63, Radio tuner type -1
[   11.350787] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   11.357406] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   11.510091] tuner' 1-0043: chip found @ 0x86 (cx88[0])
[   11.522931] tda9887 1-0043: creating new instance
[   11.522932] tda9887 1-0043: tda988[5/6/7] found
[   11.526824] tuner' 1-0061: chip found @ 0xc2 (cx88[0])
[   11.527925] tuner' 1-0063: chip found @ 0xc6 (cx88[0])
[   11.582762] tveeprom 1-0050: Hauppauge model 96019, rev D6D3, serial# 5376396
[   11.582765] tveeprom 1-0050: MAC address is 00-0D-FE-52-09-8C
[   11.582767] tveeprom 1-0050: tuner model is Philips FMD1216MEX (idx 133, type 63)
[   11.582770] tveeprom 1-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   11.582772] tveeprom 1-0050: audio processor is CX882 (idx 33)
[   11.582774] tveeprom 1-0050: decoder processor is CX882 (idx 25)
[   11.582775] tveeprom 1-0050: has radio, has IR receiver, has IR transmitter
[   11.582777] cx88[0]: hauppauge eeprom: model=96019
[   11.612601] tuner-simple 1-0061: creating new instance
[   11.612605] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   11.617335] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   11.617736] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.617796] cx88[0]/2: cx2388x 8802 Driver Manager
[   11.617805] cx88-mpeg driver manager 0000:03:06.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   11.617814] cx88[0]/2: found at 0000:03:06.2, rev: 5, irq: 20, latency: 64, mmio: 0xf9000000
[   11.646192] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   11.646195] cx88/2: registering cx8802 driver, type: dvb access: shared
[   11.646198] cx88[0]/2: subsystem: 0070:9601, board: Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder [card=56]
[   11.646201] cx88[0]/2: cx2388x based DVB/ATSC card
[   11.665175] tuner-simple 1-0061: attaching existing instance
[   11.665179] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   11.667907] DVB: registering new adapter (cx88[0])
[   11.667909] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
[   11.685145] cx8800 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   11.685155] cx88[0]/0: found at 0000:03:06.0, rev: 5, irq: 20, latency: 64, mmio: 0xfb000000
[   11.693841] wm8775' 1-001b: chip found @ 0x36 (cx88[0])
[   11.701669] cx88[0]/0: registered device video0 [v4l2]
[   11.701707] cx88[0]/0: registered device vbi0
[   11.701738] cx88[0]/0: registered device radio0
[   11.789916] cx2388x blackbird driver version 0.0.6 loaded
[   11.789919] cx88/2: registering cx8802 driver, type: blackbird access: shared
[   11.789922] cx88[0]/2: subsystem: 0070:9601, board: Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder [card=56]
[   11.789925] cx88[0]/2: cx23416 based mpeg encoder (blackbird reference design)
[   11.790150] cx88[0]/2-bb: Firmware and/or mailbox pointer not initialized or corrupted
[   11.796539] firmware: requesting v4l-cx2341x-enc.fw
[   15.485227] cx88[0]/2-bb: Firmware upload successful.
[   15.494636] cx88[0]/2-bb: Firmware version is 0x02060039
[   15.504087] cx88[0]/2: registered device video1 [mpeg]
[   15.789896] lp0: using parport0 (interrupt-driven).
[   15.949963] Adding 11863960k swap on /dev/sda5.  Priority:-1 extents:1 across:11863960k
[   16.505847] EXT3 FS on sda1, internal journal
[   17.497048] type=1505 audit(1233495586.820:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4203
[   17.626015] type=1505 audit(1233495586.948:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4208
[   17.626191] type=1505 audit(1233495586.948:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4208
[   17.663750] type=1505 audit(1233495586.984:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4212
[   17.814396] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.581426] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ processors (2 cpu cores) (version 2.20.00)
[   18.582100] powernow-k8:    0 : fid 0x13 (2700 MHz), vid 0x9
[   18.582103] powernow-k8:    1 : fid 0x12 (2600 MHz), vid 0xa
[   18.582105] powernow-k8:    2 : fid 0x10 (2400 MHz), vid 0xc
[   18.582107] powernow-k8:    3 : fid 0xe (2200 MHz), vid 0xe
[   18.582108] powernow-k8:    4 : fid 0xc (2000 MHz), vid 0x10
[   18.582110] powernow-k8:    5 : fid 0xa (1800 MHz), vid 0x10
[   18.582111] powernow-k8:    6 : fid 0x2 (1000 MHz), vid 0x12
[   18.582151] powernow-k8: ph2 null fid transition 0x13
[   19.260086] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   21.335731] ppdev: user-space parallel port driver
[   22.500294] Clocksource tsc unstable (delta = -104856119 ns)
[   23.020189] NET: Registered protocol family 10
[   23.021197] lo: Disabled Privacy Extensions
[   24.342914] cx88[0]/2-bb: VIDIOC_TRY_FMT: w: 720, h: 480, f: 4
[   27.176058] Bluetooth: Core ver 2.13
[   27.177241] NET: Registered protocol family 31
[   27.177251] Bluetooth: HCI device and connection manager initialized
[   27.177259] Bluetooth: HCI socket layer initialized
[   27.197307] Bluetooth: L2CAP ver 2.11
[   27.197319] Bluetooth: L2CAP socket layer initialized
[   27.215842] Bluetooth: SCO (Voice Link) ver 0.6
[   27.215858] Bluetooth: SCO socket layer initialized
[   27.263133] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.263145] Bluetooth: BNEP filters: protocol multicast
[   27.319185] Bridge firewalling registered
[   27.589886] Bluetooth: RFCOMM socket layer initialized
[   27.589936] Bluetooth: RFCOMM TTY layer initialized
[   27.589940] Bluetooth: RFCOMM ver 1.10
[   30.721401] lirc_dev: IR Remote Control driver registered, major 61 
[   30.839980] bttv: driver version 0.9.17 loaded
[   30.839986] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   30.899049] ivtv:  Start initialization, version 1.4.0
[   30.899307] ivtv:  End initialization
[   30.910909] lirc_i2c: chip 0x1001b found @ 0x71 (Hauppauge HVR1300)
[   30.910940] lirc_dev: lirc_register_plugin: sample_rate: 10
[   31.796898] r8169: eth0: link up
[   31.796911] r8169: eth0: link up
[   31.908136] NET: Registered protocol family 17
[   34.363535] hda-intel: Invalid position buffer, using LPIB read method instead.
[   42.660020] eth0: no IPv6 routers present
 


Any help would be appreciated

---

### Post by sgeoxd on 2009-04-10
Been fighting a similiar issue myself on a card with the same chipset (Pinnacle 800i).  I'm finding it to be finnicky with what IR codes it will receive, still trying to lock down a good config for my Harmony 620.  So if anyone has a better response I would be interested.

I had to install LIRC via the normal repositories, then compile LIRC. So you may want to try:
```
sudo apt-get install lirc build-essential dialog
wget http://prdownloads.sourceforge.net/lirc/lirc-0.8.4a.tar.gz
tar -xvf lirc*
cd lirc*
sudo ./setup.sh

```

In the options, under "Driver configuration" go to "Other" then "Linux input layer".  Ok a few times, then select "Save configuration and run configure" from the main menu.  Once it is finished the usual:
```
make
sudo make install
```

Then you'll need to find out which event the IR is set to, look for the CX88 chipset and eventx:
```
cat /proc/bus/input/devices
```

Then if you have a remote that is similiar enough you can record a lircd.conf file.  Just follow the prompts after:
```
sudo irrecord -n -H /dev/input/eventx file
```

You'll basically name the inputs, hold down a button, rinse and repeat.  Just be sure to replace "eventx" with what you had from the previous step.  "file" can be whatever you want to name the output.  Once complete and to your liking copy that over as your lircd.conf:
```
sudo cp file /etc/lircd.conf
```

You'll also want to update hardware.conf under "Device" with your /dev/event/inputx:
```
sudo nano /etc/lirc/hardware.conf
```

Not that mine has gotten very far, but that should save you some research (if you haven't already).  Maybe help someone else.

---

### Post by sgeoxd on 2009-04-10
> **sgeoxd said:**
> Been fighting a similiar issue myself on a card with the same chipset (Pinnacle 800i).  I'm finding it to be finnicky with what IR codes it will receive, still trying to lock down a good config for my Harmony 620.  So if anyone has a better response I would be interested.

I had to install LIRC via the normal repositories, then compile LIRC. So you may want to try:
```
sudo apt-get install lirc build-essential dialog
wget http://prdownloads.sourceforge.net/lirc/lirc-0.8.4a.tar.gz
tar -xvf lirc*
cd lirc*
sudo ./setup.sh

```

In the options, under "Driver configuration" go to "Other" then "Linux input layer".  Ok a few times, then select "Save configuration and run configure" from the main menu.  Once it is finished the usual:
```
make
sudo make install
```

Then you'll need to find out which event the IR is set to, look for the CX88 chipset and eventx:
```
cat /proc/bus/input/devices
```

Then if you have a remote that is similiar enough you can record a lircd.conf file.  Just follow the prompts after:
```
sudo irrecord -n -H /dev/input/eventx file
```

You'll basically name the inputs, hold down a button, rinse and repeat.  Just be sure to replace "eventx" with what you had from the previous step.  "file" can be whatever you want to name the output.  Once complete and to your liking copy that over as your lircd.conf:
```
sudo cp file /etc/lircd.conf
```

You'll also want to update hardware.conf under "Device" with your /dev/event/inputx:
```
sudo nano /etc/lirc/hardware.conf
```

Not that mine has gotten very far, but that should save you some research (if you haven't already).  Maybe help someone else.

Sorry, messed that up.  Use this instead:
```
sudo irrecord -d /dev/input/eventx file
```

---

### Post by morgan88 on 2009-04-13
think my problem may be because of hardware problems. installed windows xp as dual boot, but the remote wont work there either

---

### Post by Johnius on 2009-06-01
So where do you go from there?  I mapped all of my buttons, but they still don't do anything and gnome-LIRC still says there's no device.

---

