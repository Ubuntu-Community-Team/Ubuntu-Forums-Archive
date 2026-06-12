---
title: "Sound too quiet, and other problems"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by aarnott on 2006-08-12
Ubuntu's sound worked from the original install.  Great work!  A few small problems though:
[LIST]
[*]the overall volume is much quieter than in Windows, even with all available volume controls set to maximum.
[*]after returning from hibernation, sound usually doesn't work until the next system restart.
[*]my USB headset gets great volume (I have to turn it down), but sometimes it'll just quit working until I replug it in, or even restart the computer.
[/LIST]

Any help on any of these problems would be great!  Below I'll include any details on my system that I think you'll find useful.  I'm not a Linux pro though, so if I don't include something useful, please ask and I'll get it to you.

cat /proc/asound/modules:
0 snd_hda_intel
1 snd_usb_audio

Ubuntu Dapper Drake 6.06 LTS
System: HP Pavilion dv5000 laptop.

Thanks again.

---

### Post by gerbman on 2006-08-13
In a terminal window, type "alsamixer" and hit enter. Make sure the Master and PCM channels are both turned up.

---

### Post by LordRaiden on 2006-08-13
Just an addition - PCM should be around the 60-80 range. Any higher and you will probably get distortion (static/buzzing).

---

### Post by aarnott on 2006-08-13
Both controls are already at 100%.

I wonder if my sound card has some hardware volume setting that Windows taps into and the default sound driver that Ubuntu uses doesn't.  Except that when I have Windows set to max and I reboot, Ubuntu is still quiet.

---

### Post by jtaylor on 2006-09-23
I am having the same problem with snd_hda_intel.  My sound is MUCH louder in windows.

Did you figure out how to fix this?

---

### Post by aarnott on 2006-09-23
No, I'm afraid I never did.  I just watch videos in Windows now.

---

### Post by naaman on 2007-01-03
Hey guys,

After an exhaustive search, I believe I have greatly improved the volume and sound quality of my HP Pavillion dv5129TX by installing the latest alsa-drivers (alsa-driver-1.0.14rc1) along with alsa-lib and alsa-utils.

I have re-written [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) to guide n00bs and l33t h4x0r5 alike on how I got it to work under the "Update to the latest version of alsa" section.

The definitive sign that the snd-hda-intel module was properly identifying my card was the change of how ALSA identified my codec:

BEFORE:
head -1 /proc/asound/card0/codec*
Codec: Generic 14f1 ID 5047

AFTER:
head -1 /proc/asound/card0/codec*
Codec: Conexant CXT5047

Thanks to Sébastien Wains - [www.wains.be](www.wains.be) - for his blogging of his solution.


Naaman.

---

### Post by Axemadman on 2007-01-05
Thank you naaman - worked a treat.  Nearly blew me off my seat when I restarted!

---

### Post by julie_miel on 2007-07-12
Hi all,
I tried gerbman's suggestion there and it works like a charm for me :guitar:

Pity though, I had to watch Taxi (French comedy) movie on the low volume. But now, we are rocking baby :)

---

### Post by jon_herr on 2007-12-28
Might be an easier way... 

Some how I've been using Gutsy for months now and only just discovered the audio problem you've been discussing.

My fix, similar to yours, is through the sound gui:

System > Preferences > Sound

Change all pulldowns (except "default mixer tracks") from 'autodetect' to 'conexant digital' 
Change / set 'default mixer tracks' to "HDA Intel (Alsa Mixer)"
<bookmark this page  : )   >
Reboot

You can verify operation by opening a console then starting "alsamixer" and changing volume  up down - asci representation of mixer settings should change along with media controls or volume control on taskbar.

Jon

---

### Post by prensing on 2008-01-31
I had a similar problem (low volume) with a VIA onboard chip. I used the alsamixer terminal app and discovered that my "VIA DXS" channel had been turned down (probably by me when I was playing with recording). I turned it up and it was fixed. 

You can do the same thing in the Gnome Mixer panel, but you need to go into Preferences to turn on all the sliders and figure out which one is low.

---

