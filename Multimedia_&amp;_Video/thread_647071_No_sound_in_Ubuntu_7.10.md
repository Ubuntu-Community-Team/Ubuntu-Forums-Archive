---
title: "No sound in Ubuntu 7.10"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by casdru on 2007-12-21
Hi, 

This is my first post on these forums. I've given up on trying to resolve this problem myself. 

My sound was working fine till I made an update two days ago when it suddenly disappeared giving me this error message:

> The volume control did not find any elements and/or devices to control.
This means either that you don't have the right GStreamer plugins installed,
or that you don't have a sound card configured.
You can remove the volume control from the panel by right-clicking the speaker
icon on the panel and selecting "Remove From Panel" from the menu.

I tried the solution given here: [http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/)
and it worked straight away in that I can now adjust the volume. However I still have no sound.

lspci -v|grep Audio gives

>  00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
 

so I take it, the system is finding my sound card.
I've unmuted everything in alsamixer but can't move "Caller-ID" and "Off-hook" away from 0 (my guess so far has been that this is the problem but I'm not sure and don't know how to solve it if it is).

Hope someone can help me as I've run out of ideas. Thanks!

---

### Post by balaknair on 2007-12-23
I had a few issues with my HDA card under Gutsy too. Just outlining what worked for me.
It could be that your sound card codec is just not being loaded(at least that's what I think I mean)

open a terminal and enter the following command

```
cat /proc/asound/card0/codec#* | grep Codec
```

this will tell you what codec your sound card type needs
for eg my card returned "Codec: Analog Devices AD1986A"
so the card I use is AD1986A
Next find your card configuration by checking the following link
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

(the alsa-config should also be on your system at usr/src/(your kernel version)/sound/alsa/alsa-configuration.txt)

in that page find your card model and check the details given
eg
```
AD1986A
919 6stack 6-jack, separate surrounds (default)
920 3stack 3-stack, shared surrounds
921 laptop 2-channel only (FSC V2060, Samsung M50)
922 laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
923 ultra 2-channel with EAPD (Samsung Ultra tablet PC)


```

select the description that best matches your system(eg a 5.1 surround system with 6 audio-out channels/ports would be 6stack)

then go back to the terminal and type
```
sudo nano /etc/modprobe.d/alsa-base
```

Paste this into the last line of the file
```
options snd-hda-intel model=MODEL
```
replace MODEL with your model(6stack, 3stack, laptop etc.)

reboot.

if this doesn't work you might have to consider recompiling the alsa-kernel(though if you followed the ubuntuforums guide above I guess you've already tried it.
These steps are just a part of the howto guide at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I've only mentioned the steps that worked for me with the HDA-Intel card(like yours) with Gutsy 7.04, 7.10, and with Mandriva 2008- recompiling the kernel with Gutsy led to my sound card not being detected at all and I had to purge alsa and try again, that's why I mentioned just the tips that worked for me.

Lotsa luck

---

### Post by casdru on 2007-12-23
that worked and I've got sound again. Thanks a lot!

---

