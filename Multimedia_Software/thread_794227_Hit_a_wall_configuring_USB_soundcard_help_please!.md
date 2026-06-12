---
title: "Hit a wall configuring USB soundcard help please!"
date: 2008-05-14
forum: Multimedia Software
---

### Post by tabithaboof on 2008-05-14
I have managed to get a fair way configuring my USB card but I am now completely stuck and would love some help. Basically, my soundcard is detected and I can select my card in Audacity and everything works fine. Every other application I use (Amarok and Firefox crash when I try and play sound, VLC player doesnt produce sound, Audacious plays 2 seconds of sound and stops) have major audio problems. Also changing anything in "System Settings -> Sound System ->Hardware" causes the system settings application to hang 90 percent of the time. I dont really have any idea how to begin trouble shooting this. 

From "less /proc/asound/modules" I get

```
1 snd_usb_audio
```

and from "cat /proc/asound/cards" I get

```
cat /proc/asound/cards
```

"aplay -l" gives me

```
**** List of PLAYBACK Hardware Devices ****
card 1: UA25 [UA-25], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

All of which seems like good news. But the above problems continued

I followed the advice in this post 

[http://ubuntuforums.org/showthread.php?t=402293](http://ubuntuforums.org/showthread.php?t=402293)

did the following 

```
udo kate /etc/modprobe.d/blacklist

and then added this line at the end

blacklist snd_intel8x0
```

and 

```
I also added these lines to the /etc/modprobe.d/alsa-base file.

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd_usb_audio
#install sound-slot-1 /sbin/modprobe snd_intel8x0

And commented this
#options snd-usb-audio index=1
#options snd-usb-usx2y index=-2
```

yet still I have the same problems, I would LOVE any help as this has me totally confused. I dont know if it makes any difference but my sound card is an Edirol UA-25 which is apparently supported by alsa fully

---

### Post by tabithaboof on 2008-05-14
I wouldnt usually bump a topic but this is a real sticking point for me. Any help at all would be much appreciated.

---

### Post by hogiewan on 2008-05-29
have you disabled your onboard sound in the BIOS?

---

