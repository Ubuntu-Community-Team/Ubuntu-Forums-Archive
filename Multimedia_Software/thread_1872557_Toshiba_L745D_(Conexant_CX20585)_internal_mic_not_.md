---
title: "Toshiba L745D (Conexant CX20585) internal mic not working"
date: 2011-10-30
forum: Multimedia Software
---

### Post by hotweiss on 2011-10-30
I have a Toshiba L745D (AMD A6-3400M). I cannot get my internal mic to work.

My sound card: Conexant CX20585

I've tried this:

echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf

echo "options snd-hda-intel model=ideapad" | sudo tee -a /etc/modprobe.d/alsa-base.conf

echo "options snd-hda-intel model=asus" | sudo tee -a /etc/modprobe.d/alsa-base.conf

...but that didn't work either. Apparently that works for different notebook models with the same sound card. I also tried muting the right mic channel; that also worked for someone on a different model.

Here is my ALSA information:

[http://www.alsa-project.org/db/?f=6b57a7faecf5525ccb5212a6f60ee9d1bc792838](http://www.alsa-project.org/db/?f=6b57a7faecf5525ccb5212a6f60ee9d1bc792838)

Launchpad bug report:

[https://bugs.launchpad.net/alsa-driver/+bug/882427](https://bugs.launchpad.net/alsa-driver/+bug/882427)

Any solutions out there?

---

### Post by hotweiss on 2011-11-02
The internal microphone will not work if you have Fast Boot enabled in the BIOS.  If you install Ubuntu with Fast Boot enabled, you will have to reinstall it with Normal Boot enabled to get your microphone working.

---

