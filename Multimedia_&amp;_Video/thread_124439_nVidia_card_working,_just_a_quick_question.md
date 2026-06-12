---
title: "nVidia card working, just a quick question"
date: 2006-02-01
forum: Multimedia &amp; Video
---

### Post by Strev_123 on 2006-02-01
I recently had trouble getting my nVidia card to work... got it working, turned out to be the PCI bus ID's in xorg.conf beng wrong. Also I had to put 'nv' under driver in the xorg.conf... I assume this is the standard ubuntu driver for nVidia cards. I have on my system the legacy drivers, which I'm told I need for my card, are there any advantages to using these drivers and what do I put inplace of 'nv' in the xorg.conf (tried to put 'nvidia' but all I got was a screen with the top half black and the bottom half white??). Any suggestions greatly appreciated.

---

### Post by super on 2006-02-01
here is the fastest way to get an nvidia card working.

first make a backup of xorg.conf:
[FONT="Courier New"]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup[/FONT]

then install nvidia drivers and enable them:
[FONT="Courier New"]sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable[/FONT]

note: i believe you need the universe repositories enabled to do this.

let me know if you need furthur help.

---

