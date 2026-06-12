---
title: "Cannot get sound on my Hp DVX6"
date: 2009-09-17
forum: Multimedia Software
---

### Post by A.Baeten on 2009-09-17
I am running ubuntu Jaunty 64-bit on an HP DVX6 product number FV167AV and cannot get ANY sound.
I Am new to ubuntu, but my friend is not. He and I have tried every command listed on the forums on terminal with no help. i have been searching for a solution for a solid 2 weeks. any help would be greatly appreciated. 
      Thank You.

---

### Post by A.Baeten on 2009-09-20
Anyone? i really need the help.

---

### Post by majiciannz on 2009-09-20
> **A.Baeten said:**
> I am running ubuntu Jaunty 64-bit on an HP DVX6 product number FV167AV and cannot get ANY sound.
I Am new to ubuntu, but my friend is not. He and I have tried every command listed on the forums on terminal with no help. i have been searching for a solution for a solid 2 weeks. any help would be greatly appreciated. 
      Thank You.
I have an HP dv5 and I'm running ubuntu 9.04. I also had sound problems....
The pc speakers wouldn't work but the headphones would.

I did the following and it works for me.........

Try inserting the following in /etc/modprobe.d/alsa-base.conf:

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel


Hope this helps.

---

### Post by A.Baeten on 2009-09-23
sorry but im in terminal and when i type in /etc/modprobe.d/alsa-base.conf, it says permission denied, how do i get there?

---

### Post by majiciannz on 2009-09-23
> **A.Baeten said:**
> sorry but im in terminal and when i type in /etc/modprobe.d/alsa-base.conf, it says permission denied, how do i get there?
You must have root permission to change system files.
Adding sudo or gksudo will temporaraly give you that.

gksudo gedit /etc/modprobe.d/alsa-base.conf

When alsa-base.conf is open, copy and paste the following onto the page at the end of the text.
Save and close.
Reboot.

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel

Should now have sound.

---

