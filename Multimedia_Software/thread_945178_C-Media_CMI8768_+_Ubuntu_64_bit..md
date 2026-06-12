---
title: "C-Media CMI8768 + Ubuntu 64 bit."
date: 2008-10-12
forum: Multimedia Software
---

### Post by Roasted on 2008-10-12
I have a Turtle Beach Montego DDL 7.1 PCI sound card with the C-Media CMI8768 chipset. I always ran 32 bit Ubuntu because it didn't seem to work in 64 bit at all. To my surprise, after building a new computer, I booted up to the 64 bit LiveCD to give it a shot... and I heard the logon sound. Hm, great. Awesome.

So now I'm in 64 bit Ubuntu with my sound card working. Thing is, my sound controls seem to be a little qwirky. I'm unable to reboot my computer and make sure onboard sound is disabled, since I am currently rsyncing 200gb of data across 3 hard drives, but I believe it's still enabled because HDA Intel is an option in my sound device listing under sys-pref-sounds. 

The issue is this. My controls are kind of weird. When I raise/lower PCM, it changes nothing. Would this be due to onboard still being enabled? Or is there anything else I can look at for the time being till I can reboot to get into BIOS?

Any input would be appreciated. Thanks! :guitar:

---

### Post by markbuntu on 2008-10-12
No need to disable the on board, you can use them both. I have a C-Media CMI8768, not from turtle beach though and I have it working just fine along with the on-board, a usb web cam and a usb headset. I have made a little guide here for setting up multiple sound cards/devices:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

For more extensive sound troubleshooting and set up, I have another guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Oh yeah, this works for both 64 and 32 bit hardy. I run them both on the same machine.

---

### Post by Roasted on 2008-10-12
Meh, I don't need multiple sound cards. I disabled the onboard card and now everything works accordingly. 

Only thing is, and this isn't a big problem, I set F9 (lower volume) and F10 (raise volume) as hot keys, as I have done ever since I started on Ubuntu. Here, in 64 bit land with Hardy, it works fine, but visually it looks a little flaky. Take the shaded in bar for example, that signifies what volume level you're at. It moves when I change volume up/down, but sometimes it disappears till I hit the key again (further lowering/raising the volume).

It's not a big deal, but it's just one of those things I noticed and figured I'd bring it up here while I have the change.

But, yeah. Turtle Beach Montego DDL 7.1 PCI sound card C-Media CMI8768 chipset? Ubuntu Hardy 64 bit. Works fine. Just had to disable onboard sound card in BIOS and everything seemed to flow nicely.

---

### Post by markbuntu on 2008-10-14
There is a lot of that going around, flaky volume controls. It does that with my usb headset. The left channel drops to zero whenever I try to adjust the volume in any alsa mixer though it works fine in the pulseaudio volume control which is what I use anyway.

---

### Post by Roasted on 2008-10-14
Is it only common in 64 bit land?

---

### Post by markbuntu on 2008-10-15
No, My C-media card works fine on both 32 and 64 bit hardy and my usb headset is flaky on both also. I think I saw a bug report on this at pulseaudio that was also reported to alsa so the devs are aware of this issue and are hopefully working on it. 

It seems to be somewhat random, only some people are having this problem while others are not with the same hardware, weird...also difficult to track down since it does not make error reports of leave much to backtrace.

---

