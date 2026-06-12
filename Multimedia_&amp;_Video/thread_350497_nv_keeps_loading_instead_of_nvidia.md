---
title: "nv keeps loading instead of nvidia"
date: 2007-01-31
forum: Multimedia &amp; Video
---

### Post by Ampage on 2007-01-31
Hi people. - couldnt seem 2 find anyone else with this problem.

Running kubuntu edgy 6.10 here on AMD64 (Intel Pentuim D 64bit dual core) 

Since the update, my previous official nvidia driver (8776) stopped functioning properly. X crashed whenever the 3D screensaver loaded. 

I tried upgrading to the latest nvidia drivers from nvidia.com (9746) and have encounterd another problem. - Despite xorg.conf set to load nvidia, when x stards and kdm appears, it is running the nv driver - no hardware acceleration. I can tell by the choppiness, the fonts and when i had a look in systemsettings it said it was running on the nv driver.

Tried re-installing the new driver several times, no joy.
tried 'depmod -ae' too, with no luck.

Any ideas? :confused:

---

### Post by taurus on 2007-01-31
And I assume the Driver in /etc/X11/xorg.conf right now is pointing to nv!  Maybe this guide would help with the latest driver for your nVidia card.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Ampage on 2007-02-01
You assume wrong i'm afraid :)

xorg.conf says nvidia - (not at home at the moment so i cant paste it)

I'll try using this guide to re-install.

- Also, havent tried blacklisting nv.. could give that a go.

---

### Post by Ampage on 2007-02-01
ok tried using envy to reinstall the driver but it didnt work. - its still loading nv instead of nvidia

anyone else have any ideas?

---

### Post by bgochnauer on 2007-03-09
> **Ampage said:**
> ok tried using envy to reinstall the driver but it didnt work. - its still loading nv instead of nvidia

anyone else have any ideas?

New to Kubuntu, but had the same problem, i needed the legacy driver. 
(nVidia Vanta card  aka;TNT2)
nv kept loading, fixed it by using the Synaptic package but the only way I could get it was to modify the repository list in Synaptic repositories and adding 'multiverse' to the two lines that contained 'universe' then it showed up.
As soon as I loaded it using Synaptic Package Manager and ran;
# sudo nvidia-glx-config enable
it worked.

hope that helps.

---

