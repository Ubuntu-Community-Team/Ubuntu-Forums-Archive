---
title: "Need help with Yamaha MW10 USB mixing studio."
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by Smu on 2007-03-09
I've got problems getting my Yamaha MW10 USB mixer working on kubuntu. I get no signal in or out from the device. I've tried configuring Kmix and Alsamixer, but it doesn't seem to work. I'm quite new to linux and ubuntu, so it might be that I'm doing something wrong. 

I've checked out the Alsa supported hardware list, and the MW10 isn't listed. Though according to this post ([http://ubuntuforums.org/showthread.php?p=925652](http://ubuntuforums.org/showthread.php?p=925652)) he got the mixer working on ubuntu with just Kmix. 

This is what I get when i run aplay -l in konsole:
[INDENT]
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1[/INDENT]

So it seems that the system recognizes the mixer....

Anyone has an idea why it isn't working? Help, please!?

---

### Post by u4david on 2008-01-26
i'm interested of more info?
I have marshal 2001 mic it need 48v phantom.
Laptop si IBM T60 
I lik to use ubuntu studio for recording acustical stuff.

how is your recording going in terms of noise quality....
how meny tracks can you get with thisset up to record @ ones?

Any coment about your experinec is aprishiated

u4davidatgmaildotcom is my email.

---

### Post by eye208 on 2008-01-26
> **Smu said:**
> card 2: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
It seems your device was recognized as a standard USB audio device. Now you have to tell your applications to use it instead of the built-in sound card. The proper way to do this depends on the application.

If the application can be configured to use a particular ALSA device, tell it to use "hw:2,0" (card 2, device 0). However some applications will always use the "default" ALSA device.

You can set hw:2,0 as the default device by creating a file ".asoundrc" in your home folder. The [ALSA wiki](http://alsa.opensrc.org/.asoundrc) explains how to do this.

---

