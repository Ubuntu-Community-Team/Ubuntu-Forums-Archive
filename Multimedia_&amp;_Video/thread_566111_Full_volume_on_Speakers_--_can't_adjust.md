---
title: "Full volume on Speakers -- can't adjust"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by doagie on 2007-10-03
Hi all,

I just bought Altec Lansing FX5051 Speakers (6.1 USB audio speakers), and plugged them into my laptop. The speaker light turns on and I've tested them with a portable mp3 player and they work. 

However, under System --> Preferences --> Sound --> Sound Events --> Sound playback, I try  "USB Audio" and click "Test", but the speakers play an unbearable 100% volume and will not adjust, no matter if I change them through the physical speakers. There is no ALSA mixer option on my computer to change the volume, so I am really stuck (and it's painful to test anything!). I would greatly appreciate any help.

Thanks again,
D

---

### Post by weed-n-linux on 2007-10-03
first off if alsa is not there then try kmix (put kmix in a command line) .i had the same problem in mandriva but i choosed the coward way and switched to ubuntu ,the best thing that ever happen to me .so if you're not on ubuntu then try to switch , are you computer's original speakers working fine ?

---

### Post by doagie on 2007-10-03
Sorry, I need to be more clear. I am using Ubuntu 7.04 and I do have ALSA working, it's just that in Volume Control Preferences there is no way to adjust the sound of the ALSA Default Mixer Track for the speakers, only for the integrated HDA Intel sound card. Any thoughts?

---

### Post by hofsmo on 2007-10-26
I have the same problem with my logitech V20 usb speakers. The weird thing is that the speakers work perfectly in puppy 3.0 which is only 99M, however if it works in puppy it should be possible to fix it for ubuntu too.

---

### Post by atrus on 2008-04-20
Just filed this one:

[https://bugs.launchpad.net/alsa-driver/+bug/219990](https://bugs.launchpad.net/alsa-driver/+bug/219990)

---

### Post by itsme_n8 on 2008-05-16
artus, your link no longer links to a bug... was this resolved?  I would love to get my Logitech V20 USB Speakers working (properly... full volume isn't what I'd call proper)

Nate

---

### Post by atrus on 2008-05-16
> **itsme_n8 said:**
> artus, your link no longer links to a bug... was this resolved? 

Nope, looks like I might have pasted it wrong. Corrected that now.

[https://bugs.launchpad.net/alsa-driver/+bug/219990](https://bugs.launchpad.net/alsa-driver/+bug/219990)

---

