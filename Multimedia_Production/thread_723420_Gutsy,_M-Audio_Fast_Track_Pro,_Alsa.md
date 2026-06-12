---
title: "Gutsy, M-Audio Fast Track Pro, Alsa"
date: 2008-03-13
forum: Multimedia Production
---

### Post by rbragg on 2008-03-13
Hi,

Please Help, I can't seem to get my Fast Track Pro fired up.
I am using Gutsy, I have ubuntu-studio installed, and I am using a Thingpad t43.
I am trying to fire it up in jack. but I think that jack is only seeing my built in thinkpad soundcard.  The alsa mixer only has controls for the built in thinkpad soundcard.

Here are some various outputs from commands that may help.

[FONT="Courier New"]root@thor:/home/rbragg# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 008: ID 0618:0302 MacAlly 
Bus 002 Device 007: ID 0763:2012 Midiman 
Bus 002 Device 006: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

root@thor:/home/rbragg# modprobe -l |grep sound/usb
/lib/modules/2.6.22-14-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.22-14-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.22-14-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.22-14-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko

root@thor:/home/rbragg# cat /proc/asound/devices 
  2:        : timer
  3:        : sequencer
  4: [ 0- 4]: digital audio playback
  5: [ 0- 3]: digital audio capture
  6: [ 0- 2]: digital audio capture
  7: [ 0- 1]: digital audio capture
  8: [ 0- 0]: digital audio playback
  9: [ 0- 0]: digital audio capture
 10: [ 0]   : control
 11: [ 1- 0]: digital audio playback
 12: [ 1- 0]: digital audio capture
 13: [ 1]   : control[/FONT]

How can I get my Fast Track Pro running?

Thanks
rick

---

### Post by rbragg on 2008-03-13
OK,

I found out that I was using an old USB hub, once I plugged the Fast Track Pro directly into the laptop, I found it...

I now have other issues, but I will look around for solutions first.

Thanks
Rick

---

