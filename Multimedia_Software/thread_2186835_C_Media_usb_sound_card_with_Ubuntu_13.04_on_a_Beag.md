---
title: "C Media usb sound card with Ubuntu 13.04 on a Beaglebone Black"
date: 2013-11-09
forum: Multimedia Software
---

### Post by oene.bakker on 2013-11-09
Hello,


I plugged in a C-Media sound card in a BeagleBone Black booted with Ubuntu 13.04.
The green led on the C-Media is burning and everything looks fine.
But there is no sound :(


I also changed alsa-base.conf but the C-Media card didn't become the default sound card.


I did the following steps:


=================================================================================
Step 1:
ubuntu@arm:~$ sudo apt-get install alsa-base alsa-utils alsa-oss
Reading package lists... Done
Building dependency tree
Reading state information... Done
alsa-base is already the newest version.
alsa-utils is already the newest version.
The following NEW packages will be installed:
  alsa-oss
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 0 B/28.0 kB of archives.
After this operation, 112 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously unselected package alsa-oss.
(Reading database ... 23566 files and directories currently installed.)
Unpacking alsa-oss (from .../alsa-oss_1.0.25-1_armhf.deb) ...
Setting up alsa-oss (1.0.25-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ubuntu@arm:~$


=================================================================================
Step 2:
ubuntu@arm:~/media$ sudo nano /etc/modprobe.d/alsa-base.conf


...
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
# Set sound cards
options snd cards-limit=2
alias snd-card-0 snd-black
alias snd-card-1 snd-cmedia
options snd slots=snd-cmedia,snd-black


=================================================================================
Step 3: reboot


=================================================================================
Step 4:
ubuntu@arm:~$ alsamixer


lqqqqqqqqqqqqqqqqqqqqqqqqqqqqq AlsaMixer v1.0.25 qqqqqqqqqqqqqqqqqqqqqqqqqqqqqqk
x Card: TI BeagleBone Black                            F1:  Help               x
x Chip:                                                F2:  System information x
x View: F3: Playback  F4: Capture  F5: All             F6:  Select sound card  x
x Item:                                                Esc: Exit               x
x                                                                              x
x                                                                              x
x                                                                              x
x                This sound device does not have any controls.                 x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
mqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqj


The C-Media card did not become the default...


F6


lqqqqqqqqqqqqqqqqqqqqqqqqqqqqq AlsaMixer v1.0.25 qqqqqqqqqqqqqqqqqqqqqqqqqqqqqqk
x Card: TI BeagleBone Black                            F1:  Help               x
x Chip:                                                F2:  System information x
x View: F3: Playback  F4: Capture  F5: All             F6:  Select sound card  x
x Item:                                                Esc: Exit               x
x                                                                              x
x                                                                              x
x                                                                              x
x                This sound device does not have any controls.                 x
x                        lqqqqqqqq Sound Card qqqqqqqqk                        x
x                        x-  (default)                x                        x
x                        x0  TI BeagleBone Black      x                        x
x                        x1  C-Media USB Headphone Setx                        x
x                        x   enter device name...     x                        x
x                        mqqqqqqqqqqqqqqqqqqqqqqqqqqqqj                        x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
x                                                                              x
mqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqj


Optie 1


lqqqqqqqqqqqqqqqqqqqqqqqqqqqqq AlsaMixer v1.0.25 qqqqqqqqqqqqqqqqqqqqqqqqqqqqqqk
x Card: C-Media USB Headphone Set                      F1:  Help               x
x Chip: USB Mixer                                      F2:  System information x
x View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  x
x Item: Headphone [dB gain: -1.56, -1.56]              Esc: Exit               x
x                                                                              x
x                  lqqk               lqqk                                     x
x                  x  x               x  x                                     x
x                  xaax               x  x                                     x
x                  xaax               x  x                                     x
x                  xaax               x  x                                     x
x                  xaax               x  x                                     x
x                  xaax               xaax                                     x
x                  xaax               xaax                                     x
x                  xaax               xaax                                     x
x                  xaax               xaax                                     x
x                  xaax               xaax                                     x
x                  xaax               xaax                                     x
x                  tqqu               tqqu               lqqk                  x
x                  xMMx               xMMx               xOOx                  x
x                  mqqj               mqqj               mqqj                  x
x                 92<>92               52                                      x
x          <    Headphone     >       Mic         Auto Gain Control            x
mqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqj




=================================================================================
Step 3:
ubuntu@arm:~/media$ aplay chord.wav                                             
Playing WAVE 'chord.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
ubuntu@arm:~/media$


Result: no sound


=================================================================================
Step 4:
ubuntu@arm:~/media$ lsusb
Bus 001 Device 002: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@arm:~/media$


=================================================================================
Step 5: 
ubuntu@arm:~/media$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Black [TI BeagleBone Black], device 0: HDMI nxp-hdmi-hifi-0 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Set [C-Media USB Headphone Set], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ubuntu@arm:~/media$


=================================================================================
Step 6:
ubuntu@arm:~/media$ aplay -D hw:1,0 chord.wav
Playing WAVE 'chord.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
ubuntu@arm:~/media$


Result: no sound


=================================================================================


Please help, thnx!

---

### Post by temujin92 on 2014-04-18
[http://ubuntuforums.org/showthread.php?t=1184923](http://ubuntuforums.org/showthread.php?t=1184923) implies that the [COLOR=#000000]snd-usb-audio line in your [/COLOR][COLOR=#000000]/etc/modprobe.d/alsa-base.conf might be the culprit.[/COLOR]

---

