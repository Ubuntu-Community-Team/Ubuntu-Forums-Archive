---
title: "HVR1950/mythtv/pvrusb2"
date: 2009-01-19
forum: Multimedia Software
---

### Post by cunningm@cwtg.com on 2009-01-19
i've been trying to get my hauppauge HVR1950/mythtv to work in intrepid. i also have tried xawtv with no luck(blank screen & hangs). it looks like intrepid is finding my hardware, but something is missing. i'm trying to use the pvrusb2 support built into the kernel. when i boot up i see the light on the unit flash briefly - it stays on all the time in XP(i am dual booting). i extracted the firmware(file list below) from the distribution cd with mike isley's perl script. when i run mythtv-setup & choose 'capture card' i get:
card type: MPEG2 encoder card(PVR-x50, PVR-500)
video device: /dev/video0
Probed info: failed to open /dev/video0

am i close here? can someone give me a clue where to look next? i'm trying to get away from microslop but i want to use my hardware in linux & i have reading all over the web & trying lots of stuff & so far i feel like am so close but so far away. thanks to all.
mikec


mdc@eppes-ubu1:~$ ls -lt /lib/firmware/v4l*|pg                                                                                           
-rw-r--r-- 1 root root 376836 2008-12-19 12:34 /lib/firmware/v4l-cx2341x-enc.fw
-rw-r--r-- 1 root root  16382 2008-12-19 12:34 /lib/firmware/v4l-cx25840.fw
-rw-r--r-- 1 root root   8192 2008-12-19 12:34 /lib/firmware/v4l-pvrusb2-73xxx-01.fw
-rw-r--r-- 1 root root 141200 2008-10-27 01:33 /lib/firmware/v4l-cx23418-apu.fw
-rw-r--r-- 1 root root 158332 2008-10-27 01:33 /lib/firmware/v4l-cx23418-cpu.fw
-rw-r--r-- 1 root root  16382 2008-10-27 01:33 /lib/firmware/v4l-cx23418-dig.fw
-rw-r--r-- 1 root root 262144 2008-10-27 01:33 /lib/firmware/v4l-cx2341x-dec.fw
-rw-r--r-- 1 root root 155648 2008-10-27 01:33 /lib/firmware/v4l-cx2341x-init.mpg
-rw-r--r-- 1 root root   8192 2008-10-27 01:33 /lib/firmware/v4l-pvrusb2-24xxx-01.fw
-rw-r--r-- 1 root root   8192 2008-10-27 01:33 /lib/firmware/v4l-pvrusb2-29xxx-01.fw


mdc@eppes-ubu1:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 2040:7501 Hauppauge 
Bus 001 Device 005: ID 0409:013e NEC Corp. 
Bus 001 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

mdc@eppes-ubu1:~$ lsmod|grep pvrusb
pvrusb2               149848  0 
dvb_core               92416  1 pvrusb2
cx2341x                20996  1 pvrusb2
v4l2_common            21120  4 tuner,cx25840,pvrusb2,cx2341x
videodev               40960  2 tuner,pvrusb2
v4l1_compat            22404  2 pvrusb2,videodev
tveeprom               20228  1 pvrusb2
i2c_core               31892  8 s5h1411,tda18271,tda8290,tuner,cx25840,pvrusb2,v4l2_common,tveeprom
usbcore               148848  5 pvrusb2,usbhid,uhci_hcd,ehci_hcd

mdc@eppes-ubu1:~$ ls -l /dev/video*
crw-rw---- 1 root video 81, 0 2009-01-19 07:03 /dev/video0
mdc@eppes-ubu1:~$ 


entries from dmesg

[   13.635898] pvrusb2: V4L in-tree version:Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
[   13.635901] pvrusb2: Debug mask is 31 (0x1f)
[   13.672602] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   14.016814] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.636256] firmware: requesting v4l-pvrusb2-73xxx-01.fw
[   15.663274] pvrusb2: Device microcontroller firmware (re)loaded; it should now reset and reconnect.
[   15.697150] usb 1-1: USB disconnect, address 2
[   15.699367] pvrusb2: Device being rendered inoperable
[   17.448018] usb 1-1: new high speed USB device using ehci_hcd and address 6
[   17.591505] usb 1-1: configuration #1 chosen from 1 choice
[   17.690933] cx25840' 0-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[   17.909163] tuner' 0-0042: chip found @ 0x84 (pvrusb2_a)
[   17.935836] tveeprom 0-00a2: Hauppauge model 75111, rev C3E9, serial# 5127259
[   17.935841] tveeprom 0-00a2: MAC address is 00-0D-FE-4E-3C-5B
[   17.935845] tveeprom 0-00a2: tuner model is Philips 18271_8295 (idx 149, type 54)
[   17.935848] tveeprom 0-00a2: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   17.935851] tveeprom 0-00a2: audio processor is CX25843 (idx 37)
[   17.935854] tveeprom 0-00a2: decoder processor is CX25843 (idx 30)
[   17.935857] tveeprom 0-00a2: has radio, has IR receiver, has IR transmitter
[   17.935863] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB
[   17.935868] pvrusb2: Mapping standards mask=0x300b700 (PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB)
[   17.935872] pvrusb2: Setting up 6 unique standard(s)
[   17.935876] pvrusb2: Set up standard idx=0 name=PAL-M
[   17.935879] pvrusb2: Set up standard idx=1 name=PAL-N
[   17.935882] pvrusb2: Set up standard idx=2 name=PAL-Nc
[   17.935884] pvrusb2: Set up standard idx=3 name=NTSC-M
[   17.935887] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[   17.935890] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[   17.935894] pvrusb2: Initial video standard (determined by device type): NTSC-M
[   17.935904] pvrusb2: Device initialization completed successfully.
[   17.936100] pvrusb2: registered device video0 [mpeg]
[   17.936105] DVB: registering new adapter (pvrusb2-dvb)
[   17.950241] firmware: requesting v4l-cx25840.fw
[   18.347003] type=1505 audit(1232366616.218:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3933
[   18.536286] type=1505 audit(1232366616.410:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3938
[   18.536492] type=1505 audit(1232366616.410:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3938
[   18.586459] type=1505 audit(1232366616.458:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=3942
[   18.755556] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.457932] ACPI: WMI: Mapper loaded
[   20.428863] cx25840' 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   20.644732] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   20.661736] tda829x 0-0042: setting tuner address to 60
[   20.748633] tda18271 0-0060: creating new instance
[   20.784619] TDA18271HD/C1 detected @ 0-0060
[   21.050300] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   21.050308] apm: overridden by ACPI.
[   25.478386] cx25840' 0-0044: Video signal:              not present
[   25.478395] cx25840' 0-0044: Detected format:           NTSC-M
[   25.478399] cx25840' 0-0044: Specified standard:        NTSC-M
[   25.478401] cx25840' 0-0044: Specified video input:     Composite 7
[   25.478404] cx25840' 0-0044: Specified audioclock freq: 48000 Hz
[   25.499257] cx25840' 0-0044: Detected audio mode:       mono
[   25.499266] cx25840' 0-0044: Detected audio standard:   BTSC
[   25.499269] cx25840' 0-0044: Audio muted:               no
[   25.499272] cx25840' 0-0044: Audio microcontroller:     running
[   25.499274] cx25840' 0-0044: Configured audio standard: automatic detection
[   25.499277] cx25840' 0-0044: Configured audio system:   BTSC
[   25.499280] cx25840' 0-0044: Specified audio input:     Tuner (In8)
[   25.499283] cx25840' 0-0044: Preferred audio mode:      stereo
[   25.567560] cx25840' 0-0044: 0x0000 is not a valid video input!
[   28.019471] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   28.030145] tda829x 0-0042: type set to tda8295
[   28.068705] tda18271 0-0060: attaching existing instance
[   32.942450] firmware: requesting v4l-cx25840.fw
[   35.300749] cx25840' 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   37.596608] firmware: requesting v4l-cx2341x-enc.fw

mdc@eppes-ubu1:~$ ls -l /proc/bus/usb
total 0
mdc@eppes-ubu1:~$

---

### Post by saedelaere on 2009-01-19
[Here]("http://ubuntuforums.org/showthread.php?t=763698") is an alternative to mythtv that could work with your device. 

Does this command produce a readable mpeg file?

```
cat /dev/video0 > test.mpeg
```

The file should appear in your users home directory.

---

### Post by Dramaman on 2009-02-12
I just received my Win-TV HVR 1950 last night and had the same sort of issue getting it to work on Intrepid.  After providing the firmware and plugging in the device, all the modules seemed to load okay, but I wasn't sure how to proceed next.  My attempts to work with a normal TV application (tvtime) or mplayer or xine produced nothing viewable.  It turns out that these were trying to read /dev/video0 as if the HVR 1950 was a regular analog device.  Actually there should be a way to view an analog signal from the HVR 1950, but I haven't figured that out.  Read on, however, for the basics on finding and viewing digital signals.

The digital tv functionality of the HVR makes it a DVB (Digital Video Broadcasting) device. With the stock Ubuntu kernel and extracted firmware, when the HVR is plugged into your USB port, /dev/dvb/adapter0/dvr0 should be created.  Check to see if it exists.  If it doesn't exist that you may have a driver problem.  Check online sites regarding the pvrusb2 driver that supports the device.

Assuming that dvr0 exists, you need to scan the HVR 1950 to find viewable channels.  This is done using a program called 'scan' which is in the dvb-utils ubuntu package.

The command is: 

[INDENT]***scan [/path_to_the_initial_scan_file] > channels.conf***[/INDENT]

The initial scan file can be found in a subdirectory of /usr/share/docs/dvb-utils/. There are different scan files for different geographic locations.  Choose one that fits your area.  If there is not an exact match, then there should be general one that you can use.  There wasn't one for me, so I used us-ATSC-center-frequencies-8VSB, which is a general scan file for scanning digital channels via antenna in the USA.  For a general USA cable scan you would probably use us-Cable-Standard-center-frequencies-QAM256.  More (not Ubuntu specific) info about using scan can be found at [[COLOR="Blue"]http://www.linuxtv.org/wiki/index.php/Scan[/COLOR]]("http://www.linuxtv.org/wiki/index.php/Scan").

It will take a while to run the scan. You should end up with a file, channels.conf, that will contain the viewable digital channels that were found.

The channels.conf file can be used with other apps (azap, czap, tzap, among others) included in dvb-utils.  I won't go into detail here. You can find more at [[COLOR="Blue"]http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device[/COLOR]]("http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device").

If you use mplayer, mplayer can display the digital channels using the channels.conf file.  Copy channels.conf to ~/.mplayer/.  Run mplayer by typing:

[INDENT]***mplayer://dvb***[/INDENT]

Mplayer should start up a window displaying the first channel found in channels.conf.  The 'h' and 'k' keys tell mplayer to change to the next channel up or down.

That is about all I've done so far. I haven't yet gotten lirc to recognize the remote that came with the HVR 1950, nor figured out how to view analog signals.

Hope that helps.

---

### Post by Mythgruntled on 2009-02-14
cunningm, this post by Dono should answer your query about how to successfully add the Hauppauge USB card:
_[COLOR=#810081][http://ubuntuforums.org/showthread.php?p=6732655#post6732655](http://ubuntuforums.org/showthread.php?p=6732655#post6732655)[/COLOR]_[]("http://ubuntuforums.org/showthread.php?p=6732933")

---

