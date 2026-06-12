---
title: "No sound in 8.04"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by dmrlook on 2008-04-17
Hello - Hopefully someone here can help me.  I have ubuntu (KDE desktop environment) installed, version 8.04.  Just recently I lost all sound, and can't figure out why.  I no longer have a /dev/snd directory, and imagine this is the cause.  I can not run alsamixer. as when I do, I get the message:

alsamixer: function snd_ctl_open failed for default: No such file or directory

I imagine it is becayse /dev/mixer  also does not exist.

Anyone know what is going wrong.  I have reinstalled all alsa components with no luck.  I am up-to-date on all releases.

Any thoughts?

---

### Post by dmrlook on 2008-04-20
OK - I have some more info,  If I run command:
sudo modprobe snd 

then /dev/snd and some subdirectories appears.  Then, I need to run:
sudo modprobe snd_hda_intel

and my sound comes back.  I still can't run alsamixer, but I'm sure I will be able to once I figure out what commands to run to get my /dev/mixer directory back.

Anyone know why this is not ahppening by default?

Thanks,
Rob

---

