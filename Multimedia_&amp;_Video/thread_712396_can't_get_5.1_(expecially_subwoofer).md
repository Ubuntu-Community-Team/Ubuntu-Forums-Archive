---
title: "can't get 5.1 (expecially subwoofer)"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by MTiN on 2008-03-01
hey there!
I just don't know what to do to get sound out of my subwoofer!
I've got some onboard c-media 9780 chip, apla -l shows me this:
```
mtin@mtin-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

my first sound-related problem was that the keys on my keyboard and the little sound symbol in the upper right didn't change my sound volume, resolved that by setting them to change the volume of "PCM" and not "Master".

In alsamixer, Master doesnt do anything, PCM controls my left and right speakers wich really put out sound and are working fine!
If I mute/un-mute "Surround" I hear a "klick" out of my rear left and right speakers, but this entry in alsamixer hasn't got a volume control, I can just mute/unmute it....but these speakers never give out any sound! the next element in alsamixer, "Center" has got a volume control, and if I mute it my Center speaker does that klick noise, but no matter how loud I set it I hear nothing out of it...the next element is "LFE" and also has a volume control, and If I mute it I hear a pretty loud whumb out of my subwoofer...but again if I'm listening to musik or whatever the subwoofer is totally quiet...

I thought that I might need some script to just copy the left and right audio signal to the other speakers or something like that? any help would be highly appreciated!

---

### Post by MTiN on 2008-03-03
okay, found out that I have to put .asoundrc with the following content into my home diretory:
> pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

this indeed gave me perfectly fine sound out of all my 6 speakers (including subwoofer)
only problem I had was that the levels of Center and LFE in alsamixer didn't change anything, so I had to use the "hardware" controls on my speakers, not that big deal!

then some time later my ubuntu crashed (I think while doing a portscan with nmap) and now I have a terrible "tickering" noise above my music if I put this code inte .asoundrc! like 10 "bumps" per second, my music sounds totally distorted! This noise occurs only while playing some kind of audio files, if I don't play anything its quiet...

so right now I'm back to Stereo, maybe someone knows this problem and can help me?

---

