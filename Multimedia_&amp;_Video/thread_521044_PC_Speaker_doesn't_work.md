---
title: "PC Speaker doesn't work"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by sovereign_soul on 2007-08-08
I can't seem to get the PC-speaker to work (It does work in windows).

$ modprobe -l pcspkr gives 
 /lib/modules/2.6.20-16-generic/kernel/drivers/input/misc/pcspkr.ko

I checked System->Preferences->Sound , system beep is also enabled. Tried beep, perl scripts, still don't hear any sound from the PC speaker. 

Any insight to the underlying cause ?? Any hints | solutions ??

---

### Post by linuxwizard on 2007-08-09
Have you checked your volume controls to make sure everything is turned up or is their something muted and needs to be unmuted.
speaker on panel > right click

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by sovereign_soul on 2007-08-09
> **linuxwizard said:**
> Have you checked your volume controls to make sure everything is turned up or is their something muted and needs to be unmuted.
speaker on panel > right click

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

yes, I am sure that nothing is mute. Infact, the other sounds/music plays nicely.. I don't have any problem with that. 

In case you're getting confused, I'd like to make it clear that the problem is regarding the PC-Speaker - the one that's responsible for system beeps and not the soundcards.

Thanks.

---

### Post by linuxwizard on 2007-08-09
No I am not confused on what you are asking. I just gave more suggestions to check. I know that my pc speaker setting was muted and volume level was turned down after install of Ubuntu.

---

### Post by sovereign_soul on 2007-08-09
thanks but any more suggestions ? ??

---

