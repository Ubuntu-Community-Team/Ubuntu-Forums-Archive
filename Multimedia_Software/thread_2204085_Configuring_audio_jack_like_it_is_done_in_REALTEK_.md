---
title: "Configuring audio jack like it is done in REALTEK audio manager under windows"
date: 2014-02-06
forum: Multimedia Software
---

### Post by SOULTE on 2014-02-06
Hello all;

I use the "line in" jack on my m.b equipped with a realtek audio chipset as an output for my headphones, by configuring it in REALTEK audio manager under Windows. I was just wondering whether it would be possible to do it in Ubuntu (somewhere in alsamixer maybe). Any suggestions?

---

### Post by Yellow Pasque on 2014-02-07
If using Ubuntu 13.10 or later:
```
sudo apt-get install alsa-tools-gui
hdajackretask
```

Otherwise:
```
sudo apt-add-repository ppa:diwic/hda
sudo apt-get update
sudo apt-get install hda-jack-retask
hda-jack-retask
```

---

