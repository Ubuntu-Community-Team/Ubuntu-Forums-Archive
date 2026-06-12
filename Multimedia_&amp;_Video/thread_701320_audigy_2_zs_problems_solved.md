---
title: "audigy 2 zs problems solved"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by klemens on 2008-02-19
i really had a pain to configure my audigy 2 using the module snd_emu10k1

sometimes it worked, sometimes it didn't, sometimes the sound was really bad, the funny thing is you never what you are gonna get @ reboot.
flash didn't work etc.... 
If you have same probs, you should try this it worked for me:

cat /proc/asound/modules
sudo  /etc/modprobe.d/alsa-base

@ the end of the document add
options snd_emu10k1 index=0
options snd_.... (whatever other soundcard should be loaded) index=1
options snd_...            index=3

Now in system > preferences > sound choose OSS - Open Sound System everywhere!
Reboot.

Now i can play multiple channels, flash also works and no scratching anymore.

got the info from [Ubuntu documentation]("https://help.ubuntu.com/community/SoundTroubleshooting")

Hope it will help someone.

---

### Post by Magatsu Taito on 2008-02-21
Can someone please clarify what this mean?

options snd_.... (whatever other soundcard should be loaded) index=1
options snd_... index=3

especially those dots? Whatever other soundcard should be loaded? If I don't have another soundcard, what should I put there then? And about that index=3, what more is needed, since youy used dots?

---

