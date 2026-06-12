---
title: "No Sound Acer laptop"
date: 2006-01-15
forum: Multimedia &amp; Video
---

### Post by okie50 on 2006-01-15
Hi
Installed Breezy, video,mouse, and wireless work great.
But no sound. Any help would be appreciated.
Laptop is Acer Travelmate 723TX.
Souncard is identified as Neomagic Magicwave 3d ( NMX2200) by Ubuntu.
Thanks
Bill

---

### Post by FarEast on 2006-01-17
Hi,

Please refer to the infomation below and search for success stories with google.

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Neomagic#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Neomagic#matrix)

Then describe the options in **/etc/modprobe.d/sound** , execute 'sudo update-modules' and 'modprobe snd-nm256'.

I hope you can configure your sound card properly;) .

---

