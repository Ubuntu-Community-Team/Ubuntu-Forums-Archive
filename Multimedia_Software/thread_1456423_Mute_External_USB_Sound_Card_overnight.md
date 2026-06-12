---
title: "Mute External USB Sound Card overnight"
date: 2010-04-17
forum: Multimedia Software
---

### Post by klorenzo on 2010-04-17
Hi, I have an external USB Sound Card (Audiophile Fubar II DAC) that worked flawlessy up to one or two months ago when suddenly it stopped to make any sound.
The card, speakers, etc. are working, I tried it from another OS running on the very same PC.

The card is detected, but it's dumb

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCM2702 [Burr-Brown Japan PCM2702], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc400000 irq 22
 1 [PCM2702        ]: USB-Audio - Burr-Brown Japan PCM2702
                      Burr-Brown Japan Burr-Brown Japan PCM2702 at usb-0000:00:1d.7-2.1, full speed
 3 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xcfeec000 irq 17
 4 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:1d.7-2.3.3, full speed

(the card is the "Burr-Brown Japan PCM2702")

$ uname -a; cat /etc/issue
Linux sentiero 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
Ubuntu 9.10 \n \l


The card appears under System->Preferences->Sound->Hardware but there are two unusual things (if I remember correctly). 
1. The green sound card icon on the left is not shown, it's not gray, there is nothing (but  the USB Headset, that works well, doesn't have the icon either so maybe it'ok). 
2. From the Profiles dropdown I can only choose from four options (off, analog mono, analog stereo and digital duplex). Before there were more (digital output only, etc.).

I checked the levels several times. Another external USB card (SB Xi-Fi 5.1) works well.

From a couple of posts found on the net I suspect it is related to some kernel upgrade.

Any ideas? 

Thanks, bye

---

### Post by lidex on 2010-04-18
You're using two soundcards at once? Have you tried disabling onboard audio in bios?

---

### Post by klorenzo on 2010-04-19
> **lidex said:**
> You're using two soundcards at once? Have you tried disabling onboard audio in bios?

Hi lidex, thanks for the reply.

Up to one month ago I used to run the internal card and two external USB DAC without any problem :(

Anyway this is a good idea that I missed, I'll try it this evening.

---

