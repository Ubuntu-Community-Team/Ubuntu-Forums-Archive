---
title: "Sound Coming from Speaker and headphones on HP G60-549DX Laptop"
date: 2009-11-23
forum: Multimedia Software
---

### Post by Tng222 on 2009-11-23
I have Ubuntu 9.10 installed on my HP G60-549DX and I can't figure out how to make the sound only come out of the headphones and not the built-in speaker.  In previous versions of Ubuntu I could right-click on the sound in the tray and click Volume Control and mute the computer speaker and leave the headphones un-muted.  However, I have never tried the old method on this laptop because I just got it a week ago.  Now when I right-click it shows "Sound Preferences" I tried installing GNOME ALSA Mixer and I still couldn't fix it with that.

How do I get sound to come from my headphones when I plug them in and give sound back to the speakers when I unplug it. This works in Windows 7.

Thanks :-)

---

### Post by casperthedog on 2010-04-20
Did you solve this problem? I have the same problem on a Compaq nc6220. I solved it with Ubuntu 9.04 but don't remember how I did it. Now I've upgraded to 9.10 and its back.

---

### Post by lidex on 2010-04-20
Try this for me. Open alsa-base.conf for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Add this line:
```
options snd-hda-intel model=dell-vostro
```
Save. Close. Reboot. Check alsamixer.

---

