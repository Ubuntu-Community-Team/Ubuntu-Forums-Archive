---
title: "Currently Update breaks my ATI X1300"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by bluntu on 2006-08-20
::::::::::::Nevermind, Just restarted my comp and everything is back to normal::::

---

### Post by bluntu on 2006-09-19
Just updated and this time it's for real.

I'm using ATI X1300 and when I first installed Ubuntu with it it worked fine (no 3d acceleration and no driver installation). Right after the kernel/linux-image update I now get [www.mesa3d.org](www.mesa3d.org) thing.

Is there anyway I can restore my ati without much work? I'm starting to fear the update icon! (the red/orange update icon...)

---

### Post by FyreBrand on 2006-09-19
If you used the proprietary driver you have to recompile it everytime there is a kernel update.  So check out this thread in the sticky section: Fitzman49's [HowTo: Fglrx 8.26.18 Driver Installation]("http://www.ubuntuforums.org/showthread.php?t=204910").  It is very thorough just read it carefully.  It's not a lot of work but you do have to pay close attention to some small details like making sure you have the proper repositories enabled.

Good luck.

---

### Post by bluntu on 2006-09-19
Thank you very much! I almost had a heart-attack. Before I did this I backuped everything in case it's deja-vu all over. Anyway here's what I did in case someone is also going through this.

I followed fitzman49's instructions (from start to finish) but it didnt' work... so I blacked out "fglrx" in /etc/default/linux-restricted-modules-common  and did this:

```

sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo shutdown -r now

http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually

```

---

