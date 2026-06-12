---
title: "M-Audio Audiophile Firewire External problems . . ."
date: 2010-10-04
forum: Multimedia Software
---

### Post by fatwilly6 on 2010-10-04
I am running Maverick Meercat 10.10 with full Ubuntu Studio package.
I am added as an audio & video user.
I have run sudo modprobe raw1394
I am struggling to perform the firmware upgrade required to get my M-Audio FW Audiophile box to work. I have got Wine running + ffado but when I try and update the firmware I get errors.

1st problem (may be all of the problem) is when I run ffado-bridgeco-downloader

dmt@dmt-desktop: ffado-bridgeco-downloader
BridgeCo BeBoB platform firmware downloader
Part of the FFADO project -- [www.ffado.org]("http://www.ffado.org")
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

Node id        GUID                  Vendor - Model
0              0x000d6c0310ed4910    'M-AUDIO' - 'FW Audiophile Bootloader '
00459055666: Error (configrom.cpp)[ 150] initialize: Could not parse config rom of node 1 on port 0
no message buffer overruns

in other posts I have seen there is another device recognised at node id 1 - so I am wondering what I am doing wrong or if the box is ok. It runs fine with $windows.

I then tried to update the firmware anyway but got checksum/CRC errors . . .

dmt@dmt-desktop:~$ ffado-bridgeco-downloader 0x000d6c0310ed4910 firmware /home/dmt/fwap.bcd -m 0x001807198000LL
-----------------------------------------------
BridgeCo BeBoB platform firmware downloader
Part of the FFADO project -- [www.ffado.org]("http://www.ffado.org")
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

YOU HAVE SPECIFIED THE CORRECT MAGIC NUMBER.
HENCE YOU ACCEPT THE RISKS INVOLVED.
05248277654: Warning (ieee1394service.cpp)[ 375] initialize: Could not set SPLIT_TIMEOUT to min requested (1000000)
05248277704: Warning (ieee1394service.cpp)[ 379] initialize: Set SPLIT_TIMEOUT to min requested (1000000) did not succeed
05248358186: Error (configrom.cpp)[ 150] initialize: Could not parse config rom of node 1 on port 0
05248500201:  (configrom.cpp)[ 583] printConfigRom: Config ROM
05248500247:  (configrom.cpp)[ 584] printConfigRom:     Current Node Id:    0
05248500260:  (configrom.cpp)[ 585] printConfigRom:     GUID:            0x000D6C0310ED4910
05248500278:  (configrom.cpp)[ 586] printConfigRom:     Vendor Name:        M-AUDIO
05248500292:  (configrom.cpp)[ 587] printConfigRom:     Model Name:        FW Audiophile Bootloader 
05248500309:  (configrom.cpp)[ 588] printConfigRom:     Node Vendor ID:        0x000d6c
05248500321:  (configrom.cpp)[ 589] printConfigRom:     Model Id:        0x00010060
05248500337:  (configrom.cpp)[ 590] printConfigRom:     Unit Specifier ID:    0x00a02d
05248500348:  (configrom.cpp)[ 591] printConfigRom:     Unit version:        0x00014001
05248500364:  (configrom.cpp)[ 592] printConfigRom:     ISO resource manager:    0
05248500376:  (configrom.cpp)[ 593] printConfigRom:     Cycle master capable:    0
05248500391:  (configrom.cpp)[ 594] printConfigRom:     Bus manager capable:    0
05248500404:  (configrom.cpp)[ 595] printConfigRom:     Cycle clock accuracy:    100
05248500420:  (configrom.cpp)[ 596] printConfigRom:     Max rec:        8 (max asy payload: 512 bytes)
Info Registers
    Manufactors Id:        bridgeCo
    Protocol Version:    0x00000001
    Bootloader Version:    0x00002803
    GUID:            0x000d6c0300ed4910
    Hardware Model ID:    0x0000000d
    Hardware Revision:    0x00000001
    Software Date:        04.05.2007, 10:22:12
    Software Id:        0x00010060
    Software Version:    0x00ffffff
    Base Address:        0x20080000
    Max. Image Len:        0x00180000
    Bootloader Date:    06.10.2003, 10:00:41
    Debugger Id:        0x00000000
    Debugger Version:    0x00000000
parse BCD file
05248572830: Error (bebob_dl_bcd.cpp)[ 358] checkHeaderCRC: checkHeaderCRC: CRC check failed, 0xe3c4bb1e expected, 0x42f50400 calculated
05248572865: Error (bebob_dl_bcd.cpp)[ 180] parse: parse: Header CRC check failed
05248572876: Error (bebob_dl_mgr.cpp)[ 249] downloadFirmware: downloadFirmware: BCD parsing failed
Failed to download firmware
no message buffer overruns

also I can't seem to get the envy24 programme to run at all . . .

any ideas anyone - thanks . . .

---

### Post by fatwilly6 on 2010-10-05
> **fatwilly6 said:**
> 
parse BCD file
05248572830: Error (bebob_dl_bcd.cpp)[ 358] checkHeaderCRC: checkHeaderCRC: CRC check failed, 0xe3c4bb1e expected, 0x42f50400 calculated
05248572865: Error (bebob_dl_bcd.cpp)[ 180] parse: parse: Header CRC check failed
05248572876: Error (bebob_dl_mgr.cpp)[ 249] downloadFirmware: downloadFirmware: BCD parsing failed
Failed to download firmware
no message buffer overruns


have spent several hours on a variety of fora trying to find out more about this particular error - no joy :confused: so any ideas or help will be appreciated . . .

---

### Post by fatwilly6 on 2010-10-09
> **fatwilly6 said:**
> 
Node id        GUID                  Vendor - Model
0              0x000d6c0310ed4910    'M-AUDIO' - 'FW Audiophile Bootloader '
00459055666: Error (configrom.cpp)[ 150] initialize: Could not parse config rom of node 1 on port 0
no message buffer overruns

at least this solved by running modprobe ohci1394 - now get

Node id        GUID                  Vendor - Model
0              0x000d6c0310ed4910    'M-AUDIO' - 'FW Audiophile Bootloader '
1              0x00e01800004cb424    'Linux - ohci1394 ' - ''
no message buffer overruns

however still getting the CRC parse error

parse BCD file
11235262476: Error (bebob_dl_bcd.cpp)[ 358] checkHeaderCRC: checkHeaderCRC: CRC check failed, 0xe3c4bb1e expected, 0x42f50400 calculated
11235262507: Error (bebob_dl_bcd.cpp)[ 180] parse: parse: Header CRC check failed
11235262522: Error (bebob_dl_mgr.cpp)[ 249] downloadFirmware: downloadFirmware: BCD parsing failed
Failed to download firmware


 and unable to run jack as have disabled on board audio & trying to use Toneport USB Audio
p, li { white-space: pre-wrap; } Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|hwmon|hwmeter|-|32bit
 Using ALSA driver line6usb running on card 0 - Line6 TonePort UX2 at USB 3-1:1.0
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 16bit little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 16bit little-endian
 ALSA: use 3 periods for playback
 [COLOR=#FF0000]20:56:57.799 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Driver is not running
 Cannot create new client
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 [COLOR=#FF0000]20:57:08.909 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Driver is not running
 Cannot create new client
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 [COLOR=#FF0000]20:57:24.011 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Driver is not running
 Cannot create new client
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 ALSA: poll time out, polled for 34828025 usecs
 JackAudioDriver::ProcessAsync: read error, skip cycle
 ALSA: poll time out, polled for 34828014 usecs
 JackAudioDriver::ProcessAsync: read error, skip cycle
 ALSA: poll time out, polled for 34828014 usecs
 JackAudioDriver::ProcessAsync: read error, skip cycle
 ALSA: poll time out, polled for 34828015 usecs
 JackAudioDriver::ProcessAsync: read error, skip cycle
 ALSA: poll time out, polled for 34828016 usecs
 JackAudioDriver::ProcessAsync: read error, skip cycle

all very frustrating . . . sigh . . .

---

### Post by cchhrriiss121212 on 2010-10-09
The audiophile firewire is not reported as working with ffado, and the best results I can see on the website are hit and miss functionality. Unless you enjoy this kind of tinkering, I would not advise you spend any more time on this issue.

The USB with jack:
Have you set up jack with real time privileges?:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

USB sound devices can also get interrupted by other peripherals that share the same bus, try unplugging any extra things.

---

### Post by fatwilly6 on 2010-10-10
thanks for the reply - I am running Meerkat and there don't seem to be rt kernels 

dmt@dmt-desktop:~$ sudo apt-get install linux-rt linux-headers-rt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-rt
E: Unable to locate package linux-headers-rt

. . . but Jack has an RT flag in the main window and a checkbox in the setup page. It does seem to start now but only if the (disabled in BIOS) Via Audio chip is selected! I have a USB HDD which has been removed now. Will post progress later but sun out & grass needs cutting . . .

---

### Post by cchhrriiss121212 on 2010-10-10
Realtime mode with jack does not require an rt kernel, but it will help you with latency compared to the generic. Just search for rt in synaptic and it should be there somewhere.

---

### Post by fatwilly6 on 2010-10-14
Still no joy with this . . I have loaded (I think) rt kernesl via synaptic but don't seem to have an rt option when booting via grub main screen - any way to check if I have installed them?On a +ve note I did get my Creative card installed + have got a Focusrite Sapphire LE Firewire card for a very good price from eBay!

---

### Post by cchhrriiss121212 on 2010-10-14
When you installed the kernel did you install the header packages as well? You can organise your GRUB menu with startupmanager which is in the repos.

---

### Post by fatwilly6 on 2010-10-14
thanks again - I think I have installed headers too but threads in Ubuntu studio forum seem to suggest there are no rt kernels for 10.10. Is there a low latency kernel as well??
 
Other threads there seem to suggest my problems with jack (above) are due to not [killing pulseaudio]("http://ubuntuforums.org/showthread.php?t=1591788") so will be trying that later

---

### Post by cchhrriiss121212 on 2010-10-14
Thats right about the lack of kernels in 10.10, you can still install them but they are not in the official repository, get the lowlatency or rt from [this guy]("https://launchpad.net/%7Eabogani/+archive/ppa"). This is a PPA, which means a personal package archive, and it adds an extra quantity of software (like kernels or apps) available for you to install using your package manager.

---

