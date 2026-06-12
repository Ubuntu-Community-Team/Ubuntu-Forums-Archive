---
title: "how do i configure 6.1 surround on hardy?"
date: 2008-05-06
forum: Multimedia Software
---

### Post by archy87 on 2008-05-06
i've got audigy2 + 6.1 creative surround, everything worked fine on gutsy
and now when i installed hardy i cant find a way to make it work...

if someone can help me out.. thanks..

---

### Post by archy87 on 2008-05-06
anyone?? im realy stuck with this...

---

### Post by jamesford on 2008-05-06
i *think* what u need is:
sudo gedit /etc/pulse/daemon.conf
find the line "; default-sample-channels = 2"
change from 2 to 7 and remove the ;
reboot

---

### Post by archy87 on 2008-05-07
> **jamesford said:**
> i *think* what u need is:
sudo gedit /etc/pulse/daemon.conf
find the line "; default-sample-channels = 2"
change from 2 to 7 and remove the ;
reboot

it's doesn't help.
plz anyone else?

---

### Post by Master_Rex on 2008-05-28
well although I'm new to linux world, I have SB audigy 2ZS platinum pro, and a 5.1 speaker system by Logitech. I have surround sound only if I choose alsa. Pulse audio doesn't seem to be working with my current configuration (it might be the fault of pulseaudio itself i dunno). In vlc, i also choose alsa and everything works fine. Even mp3s upmix in 5.1 sound. So I guess this might work for you![http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

