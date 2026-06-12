---
title: "mpg123 hangs after a few seconds playing"
date: 2010-07-24
forum: Multimedia Software
---

### Post by Maisondouf on 2010-07-24
I try to play some music with my PlugComputer and I use an USB audio key.

I have succefully installed linux-sound-base, alsa and mpg123.

When I run mpg123 the sound loud during 5 seconds and stop.

After the device is locked and nothing can be played without rebooting.

> root@Sheeva:/media/usb2/public/Music/Melange# mpg123 -a default:1 d.mp3 
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layers 1, 2 and 3
    version 1.12.1; written and copyright by Michael Hipp and others
    free software (LGPL/GPL) without any warranty but with best wishes

Playing MPEG stream 1 of 1: d.mp3 ...
Title:   Mercy                           Artist: Duffy
Comment:                                 Album:  Rockferry
Year:    2008                            Genre:  Pop
MPEG 1.0 layer III, 192 kbit/s, 44100 Hz stereo
^C
[1:16] Decoding of d.mp3 finished.
root@Sheeva:/media/usb2/public/Music/Melange# mpg123 -a default:1 d.mp3 
[jack.c:250] error: Failed to open jack client: 0x1
[pulse.c:84] error: Failed to open pulse audio output: Connection refused
[audio.c:625] error: failed to open audio device
[audio.c:180] error: Unable to find a working output module in this list: alsa,oss,esd,jack,pulse,nas,arts
[audio.c:527] error: Failed to open audio output module
[mpg123.c:847] error: Failed to initialize output, goodbye.
Usage:program_name [address][:port]root@Sheeva:/media/usb2/public/Music/Melange# The USB card is well detected:
> root@Sheeva:/media/usb2/public/Music/Melange# amixer -c 1
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 19
  Mono:
  Front Left: Playback 16 [84%] [0.00dB] [on]
  Front Right: Playback 16 [84%] [0.00dB] [on]
root@Sheeva:/media/usb2/public/Music/Melange# aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Phone
    USB Phone, USB Audio
    Default Audio Device
front:CARD=Phone,DEV=0
    USB Phone, USB Audio
    Front speakers
surround40:CARD=Phone,DEV=0
    USB Phone, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Phone,DEV=0
    USB Phone, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Phone,DEV=0
    USB Phone, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Phone,DEV=0
    USB Phone, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Phone,DEV=0
    USB Phone, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Phone,DEV=0
    USB Phone, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
root@Sheeva:/media/usb2/public/Music/Melange# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: Phone [USB Phone], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@Sheeva:/media/usb2/public/Music/Melange#

Somebody have already seen that ?

---

### Post by gordintoronto on 2010-07-24
What is a PlugComputer? Why don't you use one of the normal music players which is included in Ubuntu? What version of Ubuntu are you using? What brand and model is the USB audio card?

---

### Post by Maisondouf on 2010-07-24
PlugComputers are very small computers without any keyboard and video ouput which are only controled via ssh.

See here : [http://www.newit.co.uk/shop/products.php?cat=5](http://www.newit.co.uk/shop/products.php?cat=5)

Principal use of these cpu is small home server (Apache, samba, streaming, ...)

On the SheevaPlug, the standart OS is Ubuntu 9.04 in armv5 architecture.


My usb audio key is a generic no brand model, "lsusb" says : ID 04f3:0a01 Elan Microelectronics Corp. 

Ubuntu recognize it as "USB Phone" (like small USB phone for Skype)

---

### Post by gordintoronto on 2010-07-24
That's cool! Sorry, I haven't got a clue what you should do to fix your problem.

---

