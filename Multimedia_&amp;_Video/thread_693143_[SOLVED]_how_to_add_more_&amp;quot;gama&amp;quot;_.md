---
title: "[SOLVED] how to add more &amp;quot;gama&amp;quot; to my screen on Gutsy?"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by raafaell on 2008-02-10
how to add more "gama" to my screen on Gutsy?
NVIDIA 7300 GS

thx

---

### Post by steveneddy on 2008-02-10
```
nvidia-settings
```

go to X-Server Color Correction

---

### Post by em3raldxiii on 2008-02-10
Try this:

```
sudo aptitude install nvidia-settings
```

Then either run it from your menu (applications > System Tools > nvidia-settings, or run it from console: 

 [code]gksu nvidia-settings[code]

The gksu for this type of command is the same as "sudo" only specifically for grapical apps (and therefore less likely to negatively impact your user config files).

In there are a number of things you can play around with, including xserver  color correction.

---

### Post by raafaell on 2008-02-10
> **steveneddy said:**
> ```
nvidia-settings
```

go to X-Server Color Correction

very much thx man. ;D

---

### Post by steveneddy on 2008-02-10
> **em3raldxiii said:**
> Try this:

```
sudo aptitude install nvidia-settings
```

Then either run it from your menu (applications > System Tools > nvidia-settings, or run it from console: 

 [code]gksu nvidia-settings[code]

The gksu for this type of command is the same as "sudo" only specifically for grapical apps (and therefore less likely to negatively impact your user config files).

In there are a number of things you can play around with, including xserver  color correction.

nvidia-setttings is installed by default in the new nvidia driver in Gutsy

Just hit the thanks star.

You're welcome.

---

