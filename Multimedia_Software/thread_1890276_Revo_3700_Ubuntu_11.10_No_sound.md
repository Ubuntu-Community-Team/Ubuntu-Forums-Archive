---
title: "Revo 3700 Ubuntu 11.10 No sound"
date: 2011-12-03
forum: Multimedia Software
---

### Post by spwilkinson on 2011-12-03
Hi all,

I realise there are numerous threads regarding sound over HDMI on a Revo machine, but I've been through just about all of them and can't get mine to work properly.

I have Ubuntu 11.10 running on a revo 3700.  I have installed the Nvidia drivers.

My current status is that no sound comes from banshee, xbmc and a couple of other applications. 

I've been trying to get this working over the past few days and I did manage to get sound coming from vlc if I set the audio profile to use ALSA and HDA Nvidia (hw 1,7).
I have also always managed to get audio when running this command

```
aplay -D plughw:1,7 /usr/share/sounds/alsa/Front_Center.wav
```however, now I receive this error message:


```
aplay: main:660: audio open error: Device or resource busy
```

VLC now won't work when using HDA Nvidia (hw 1,7)

My /etc/asound.conf :



```
cat /etc/asound.conf 
pcm.!default {
     type plug slave.pcm {
           type hw card 1 device 7
     }
}

```Annoyingly, sound is still coming out of youtube, so something is working somehow!!!

Not sure whether this is related, but for some reason, I now can't open alsamixer from the command line
```

alsamixer 
cannot open mixer: Invalid argument
```I can, however open gnome-alsamixer.

Any help would be very much appreciated

---

### Post by spwilkinson on 2011-12-04
For reference, I now have sound working by using the recommended Nvidia driver.  Not sure how/why I was using the other driver but changing it seems to have got most things working.

Strangely, you tube videos now don't have any sound, so I'm leaving this thread open in the hope of getting assistance with that.

Any thoughts?

---

### Post by BicyclerBoy on 2011-12-04
For browser sound you typically need pulse audio set to use the HDMI audio device.
Your asound.conf is overriding the default alsa definition. This is alsa only. If you set pulse to use this device it could have worked..

But the latest pulse audio has made this much easier because it detects & enumerates all the HDMI (sub)devices..
Run:
pavucontrol

& set the default audio device to be the correct HDMI output.

test alsa hw device:
speaker-test -c 2 -r 48000 -D hw:1,7

In **previous** pulse you had to have an entry /etc/pulse/default.pa:
load-module module-alsa-sink device=hw:1,7
Not anymore..

So should check if you have this old entry & comment it out..

XBMC (& VLC) should output direct to alsa device if you want all HDA audio support. Pulse audio does **now** support AC3/DTS digital pass-thru'. This support may not have surfaced in 11.10 yet..
vlc --aout alsa --alsa-audio-device iec958
aplay -L shows what iec958 alias is pointing at..

---

### Post by MoreOrLess on 2011-12-04
If you only want sound from HDMI, it may be easier to turn off the onboard audio in the BIOS and remove the custom asound.conf

---

