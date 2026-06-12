---
title: "Sound worked just once!"
date: 2011-07-15
forum: Multimedia Software
---

### Post by cheezNjam on 2011-07-15
Hi,

I've been using ubuntu 9.10 for over a year and wasn't happy with the sound and I thought it'd be fixed in 11.04 but that wasn't the case.
I've got a new laptop msi fx400. I installed ubuntu 11.04 but the sound didn't work so I followed this guide:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
and added the line
options snd-hda-intel model=basic
to
/etc/modprobe.d/alsa-base.conf
then I executed the reloading command but no sound. Then, when I rebooted the sound worked! and I could go to youtube and view and listen to some videos.
The problem was when I booted the next time, NO sound! rebooted x times but nothing!
What can I do to solve this issue?

Some more info:
When I talk into the built in mic I can see the "Input level" indicator at "Sound Preferences" move
I used headphones but nothing changed
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by masny on 2011-07-16
I had the same problem. If your card is ALC269vb, you need to add the following line on the end of the file 

options snd-hda-intel model=ALC260

(model=basic was just an example)

If it does not help go to system > preferences > sound. In hardware tab change HDMI to analog device (if you have both)
This worked form me

---

### Post by cheezNjam on 2011-07-16
Thanks masny.

They didn't work.

Also, the "basic" option is not an example it's one of the possible parameters I found for ALC269 in HD-Audio-Models.txt.gz.

Thnx

---

### Post by cheezNjam on 2011-07-16
It worked after the second reboot! Why not after the first one, I don't know. Probably I changed the connector option to "Analog Speakers". I don't know if I did. But it works now and thats enough :)

Thanks masny again

P.S I'm not gonna change it to Solved till I find everything OK.

---

