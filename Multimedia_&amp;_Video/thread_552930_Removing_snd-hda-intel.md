---
title: "Removing snd-hda-intel"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by j0lliyo on 2007-09-17
i'm trying to remove the snd-hda-intel module, and do:
**sudo modprobe -r snd-hda-intel**

this returns:
*FATAL: Module snd_hda_intel is in use.*

I'm guessing this means snd-hda.intel is in use by the system, so i can't remove it.
So i'm wondering how to shut down everything that's using the module, or booting without loading that module, so i can remove it.

thanks in advance

---

### Post by Lord Illidan on 2007-09-17
Since snd-hda-intel is in the kernel, removing the module will probably entail recompiling the kernel, not a very hard task to do for an advanced user. Why were you intending to remove the module?

---

### Post by j0lliyo on 2007-09-17
i need to remove them to install the via drivers, following the via howto by via themselves at:
[http://www.viaarena.com/Driver/via_ubuntu_7.04_linux_hd_audio_ig_ver0.8.tar.gz]("http://www.viaarena.com/Driver/via_ubuntu_7.04_linux_hd_audio_ig_ver0.8.tar.gz")

the guide there tells me to remove the snd-hda-intel mod that ships with ubuntu

---

### Post by Lord Illidan on 2007-09-17
Make sure that all audio programs have been unloaded. Run 
```
killall esd 
``` before running that command.

---

### Post by j0lliyo on 2007-09-17
thanks. found out that just blacklisting the module in /etc/modprobe.d/blacklist worked also

---

