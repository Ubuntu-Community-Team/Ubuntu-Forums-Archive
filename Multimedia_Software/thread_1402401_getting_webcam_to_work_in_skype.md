---
title: "getting webcam to work in skype"
date: 2010-02-09
forum: Multimedia Software
---

### Post by raffi_1970 on 2010-02-09
I'm a newbie to Ubuntu (9.10) and have been unable to get the webcam to work in Skype.

It works just fine in Cheese.

**lsusb yields**:

Bus 005 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 005 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 005 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 005 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2468 Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye Webcam
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**dmesg output**

[based on looking around on the forums, I figured it wouldn't hurt to add this]
  	 	 	 	 	 	  [    2.556659] usbcore: registered new interface driver hiddev 
 
  	 	 	 	 	 	  [    2.560587] usbcore: registered new interface driver usbhid 



    	 	 	 	 	 	  [   20.215176] usbcore: registered new interface driver btusb 
 
  	 	 	 	 	 	  [ 4687.774412] process `skype' is using obsolete setsockopt SO_BSDCOMPAT 
 [ 4835.589072] CE: hpet increasing min_delta_ns to 22500 nsec 
 [ 4969.226288] CE: hpet increasing min_delta_ns to 33750 nsec 
 [19757.068081] usb 3-1: new full speed USB device using uhci_hcd and address 2 
 [19757.356351] usb 3-1: configuration #1 chosen from 1 choice 
 [19757.422318] Linux video capture interface: v2.00 
 [19757.455990] gspca: main v2.6.0 registered 
 [19757.462536] gspca: probing 093a:2468 
 [19757.465124] pac207: Pixart Sensor ID 0x27 Chips ID 0x08 
 [19757.465132] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468) 
 [19757.470252] gspca: probe ok 
 [19757.470299] usbcore: registered new interface driver pac207 
 [19757.470307] pac207: registered 
 

    	 	 	 	 	 	  [    1.633062] usb 5-2: new full speed USB device using uhci_hcd and address 2 
 [    1.794838] Linux agpgart interface v0.103 
 [    1.799073] agpgart-intel 0000:00:00.0: Intel 945GM Chipset 
 [    1.799830] agpgart-intel 0000:00:00.0: detected 7932K stolen memory 
 [    1.816386] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000 
 [    1.838586] acpi device:2a: registered as cooling_device2 
 [    1.838962] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:27/input/input5 
 [    1.839030] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no) 
 [    1.839092] usb 5-2: configuration #1 chosen from 1 choice 
 [    1.839103] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434 
 [    1.839191] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2c/input/input6 
 [    1.839221] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no) 
 [    1.841740] hub 5-2:1.0: USB hub found 
 [    1.843453] hub 5-2:1.0: 3 ports detected 
 [    1.912950] [drm] Initialized drm 1.1.0 20060810 
 [    1.933226] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [    1.933237] i915 0000:00:02.0: setting latency timer to 64 
 [    1.958737] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
 [    2.032096] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0 
 [    2.032132] b44.c:v2.0 
 [    2.032172] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
 [    2.052951] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:4d:f8:6e 
 [    2.094132] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4] 
 [    2.149376] usb 5-2.1: new full speed USB device using uhci_hcd and address 3 
 [    2.294480] usb 5-2.1: configuration #1 chosen from 1 choice 
 [    2.381452] usb 5-2.2: new full speed USB device using uhci_hcd and address 4 
 [    2.437025] [drm] TV-14: set mode NTSC 480i 0 
 [    2.528473] usb 5-2.2: configuration #1 chosen from 1 choice 
 [    2.556659] usbcore: registered new interface driver hiddev 
 [    2.560208] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/input/input7 
 [    2.560512] generic-usb 0003:0A5C:4502.0001: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.3-2.2/input0 
 [    2.560587] usbcore: registered new interface driver usbhid 
 [    2.560592] usbhid: v2.6:USB HID core driver 
 [    2.564014] [drm] fb0: inteldrmfb frame buffer device 
 [    2.564026] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0 
 [    2.617377] usb 5-2.3: new full speed USB device using uhci_hcd and address 5 
 [    2.632202] [drm] LVDS-8: set mode 1280x800 17 
 [    2.764485] usb 5-2.3: configuration #1 chosen from 1 choice 
 [    2.772900] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.3/5-2.3:1.0/input/input8 
 

 

**luvcview output**

luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
ERROR: Requested frame format MJPG is not available and no fallback format was found.
 Init v4L2 failed !! exit fatal

I tried adding this line
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

and it didn't make a difference.

I'm running the beta version of Skype: 2.1.0.81

on a Dell Inspiron E1505 laptop. The audio in skype works just fine.

The video options window in skype says:
CIF Single Chip (/dev/video0)

**ls -la /dev/video0 output**

crw-rw----+ 1 root video 81, 0 2010-02-08 21:47 /dev/video0



Thanks!

---

### Post by beren.olvar on 2010-02-09
Sorry, should have read the whole post before writing... 
never mind...

---

### Post by jackcholt on 2010-02-14
I have a Microsoft LifeCam VX-1000 on Karmic (9.10) and I cannot get the camera to work in ekiga, skype, luvcview, or camstream.  

The output from luvcview is:

luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
ERROR: Requested frame format MJPG is not available and no fallback format was found.
 Init v4L2 failed !! exit fatal

ekiga puts out errors like the following:

libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9

---

### Post by no2498 on 2010-02-15
jackcholt

open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button for each 1

get a program like cheese and wxcam
if your cam uses v4l1 do not try cheese it brakes v4l1
is a lot more programs to use a webcam with like webcamstudio,guvcvew,ekiga softphone

---

### Post by raffi_1970 on 2010-02-21
running

LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype

worked!! 

thanks!

---

### Post by aircoupe on 2010-03-31
I am probably making a dumb mistake, but maybe someone could point me in the right direction...

If I type at the commandline "LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype"

It works just fine, but it I paste that commandline in a launcher, it fails...

I get a pop-up, "T**here was an error launching this applicaton**.  Detailed: Failed to execute child process "LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so" ( No Such file or directory)"

Of course the directory is valid.  What am I doing wrong?

Thanks,

Mitch

---

### Post by aircoupe on 2010-03-31
Disregard, I found other threads with same issue with resolutions....sorry

---

### Post by IanRPeachey on 2010-04-01
Hi All, 

I've struggled for a couple of days (on and off) to sort this - and finally ! ... it appears to be working.

After reading a few postings, and digging about to try and determine what libraries I have installed and what is not installed ... For my system, this appears to work....

My system is: Ubuntu 9.10 installed from the 'live' DVD - AMD64 ...and updated over night from the net (using the update manager). That's about it - I've added nothing clever, I changed nothing.

I installed skype: "skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb" from the skype web site.

I created a Launcher on my desktop, in the 'Command' field of the Launcher properties I use the following:

env LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

and that's it.

(the webcam is an old Logitec 5500 (?) I think ... er ... uvc (?) )

I hope someone finds this useful  :D

Ian

---

### Post by Peter T on 2010-04-02
Hi Ian

I have been trying to set up webcam for some weeks, have missed first few weeks of Grand Daughter, but now all OK, Your advice worked fine, thank you.
I have not tried code befor!!! 

Peter T

---

### Post by pickarooney on 2010-04-02
I've come to the conclusion that it's impossible to use both a TV tuner and a webcam on the same Ubuntu system. Can anyone prove me wrong?

---

### Post by grifonas on 2010-04-13
to [IanRPeachey]("http://newyork.ubuntuforums.org/member.php?u=1046705")

 The env LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype launcher worked perfectly for me! Cheers for that!

---

### Post by rubled on 2010-04-16
Thanks buddy it worked for me too. IM still struggling wih audio in (mic)


> **raffi_1970 said:**
> running

LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype

worked!! 

thanks!

---

### Post by walt11 on 2010-05-15
I was having the same problem with a Logitech QickCam E2500 on Ubuntu 10.04, and your solutions worked for me, too. Thanks for the help!

If I run the command shown in post #6
   LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype
from a terminal, it works, but I get an endless stream of these error messages when the video is on:

   libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
(The last 1 or 2 digits in the code vary)

That doesn't seem to be an issue, since I just had a 1/2 hour video call with someone, and it went well.

As in post #8, I created a launcher (but using the above command), and prefacing it with env. (If I don't use the env, I get the same error as in post #6.)

At this point, I'm not hearing any of the Skype sounds (including ringing for an incoming call) and don't know why. The test call, and the audio during a call are excellent. But that is minor compared to Skype now working with my webcam! Thanks again.

---

### Post by Alfredo.E on 2011-12-26
Ich habe eine Logitech Quickcam unter Ubuntu 10.4>>no, it's 10.10<< (ID 046d:08da) und kann Video in Skype zum Laufen bringen mit
                     pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.21cm; }  LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype 

in der Konsole, weiss aber nicht, wie ich Skype immer so starten kann. Könnte mir bitte jemand
helfen? Ich bin Anfänger, wie man sieht.

Sorry, here every thing is in English: how can I start video in Skype permanently? I'm a stupid  little beginner aged 64 years from Hannover, Germany. Thank You verry much!
In "Cheese" it work's fine.

---

### Post by F W Adams on 2012-06-19
Well, my only problem was having no sound input on skype with a VX-800. I tried the
"LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype"
solution but it didn't execute. I'm using ubuntu 12.04 and the reason soon became obvious. The file did not exist. The VX-800 is listed as working out of the box on 64-bit but for 32 bits ( as me ) the same files were still there in a slightly different place.

For 12.04 the correct command seems to be
"LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so /usr/bin/skype"

This didn't fix the skype sound input problem and stopped the sound output working as well. The sound on other programs was still fine. However when I came to use the computer again after switching off there was no sound in any program.

So suggest 12.04 users don't try this solution. Any help appreciated.

---

