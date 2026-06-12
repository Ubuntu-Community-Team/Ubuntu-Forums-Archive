---
title: "Latest Nvidia Drivers with Nvdia GTX 570 on 12.10 - Not working!"
date: 2012-11-05
forum: Multimedia Software
---

### Post by Sparkarof on 2012-11-05
I am using Ubuntu 12.10. Nvidia GTX 570 card. Intel core i7 CPU.

Now running Nouveou. Tried everything installing the latest drivers: Stable, beta, from the additional software dialogue (WITH NO SUCCESS) and also from x-swat.

Also tried this guide/script [http://ubuntuxtreme.com/howto/nvidia-drivers-installer-script/]("http://ubuntuxtreme.com/howto/nvidia-drivers-installer-script/")(which also just uses x-swat)

Every time, and I mean every time - It installs and then reboots and the driver is not active (also stated when I run nvidia-settings; this then tells me to run nvidia-xcofig and reboot, but this doesn't help either). I have awefully low resolution as as stated, running nvidia-xconfig doesn't help. Sometimes I even don't have window borders... I am pulling out my hair!

I have to do this in between each failed attempt to just get the nouveou drivers working again: 
```
sudo rm /etc/X11/xorg.conf
sudo dpkg-reconfigure xserver-xorg
```

Please assist.

---

### Post by stinkeye on 2012-11-05
This worked for me....
```
sudo apt-get purge nvidia*
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current nvidia-settings
```

There's some bug with linux-headers...
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=12304169&postcount=3[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12304169&postcount=3")

---

### Post by Sparkarof on 2012-11-05
It worked! thank you **stinkeye**!

Really appreciate the quick and awesome response! :KS

---

### Post by Wickedares on 2013-01-11
This also worked for me! thank you!

---

