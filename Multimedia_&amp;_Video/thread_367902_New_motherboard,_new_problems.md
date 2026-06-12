---
title: "New motherboard, new problems"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by Rhapsody on 2007-02-22
I've recently gotten a new PC, with integrated graphics and sound. Despite being cheap, it's better than my old PC, however Kubuntu seems to be having difficulty getting everything out of it.

The motherboard is an "ASRock K8NF6G-VSTA" with "Integrated NVIDIA GeForce6-class graphics DX9.0 VGA" for the graphics and "Realtek ALC861VD/ALC883 7.1 channel audio CODEC with High Definition audio" for the sound.

The first problem was with my refresh rate (Kubuntu wouldn't let me set it higher than 60Hz in any resolution, despite my monitor supporting much higher) but I fixed that by editing xorg.conf and forcing it to let me user higher refresh rates.

The second problem is that I can't seem to get hardware acceleration. I tried installing the [NVIDIA drivers](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) (like I successfully did with the GeForce4 MX in my old PC) but that just killed X.org, forcing me to restore xorg.conf to get the GUI back.

Finally, Kubuntu completely fails to detect my sound hardware. KMix says "Mixer cannot be found" and alsamixer says "alsamixer: function snd_ctl_open failed for default: No such device". It's like there's nothing there. A desktop CD of the same version of Kubuntu I'm using now (Edgy Eft) does exactly the same.

Additionally, Add/Remove Programs won't let me install MPlayer Movie Player or Xine extra plugins. They're also not listed in Adept. I was able to do that with the same version of Kubuntu on my old PC, so I'm assuming this has something to do with one of the problems listed above. I'd like to install both if at all possible, as I typically make fairly heavy use of them.

I'm sure this PC can be productive and enjoyable, but it's difficult without it detecting my hardware properly.

---

### Post by Chunghau on 2007-03-17
I had the same problems as well when I swapped out the K8NF4G-SATA2 to the K8NF6G-VSTA.  Feisty Fawin 7.04 Herd 5 has been running ok so far, though.  Video, network, and sound are working fine.  Sound is kinda broken again but I hope to figure out soon why.

---

### Post by AnRa on 2007-03-17
To get the sound working you have to download [this file]("ftp://202.65.194.211/pc/audio/realtek-linux-audiopack-4.05f.tar.bz2") (from the Realtek website) and install it.

For the hardware acceleration, I got it working with this Beryl installation script:

```

#!/bin/bash
if [ `whoami` != "root" ]; then
 echo "You must run this script as root.";
else
 cp /etc/apt/sources.list /etc/apt/sources.list.backup.beryl-script
 cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.beryl-script
 echo "deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable" >> /etc/apt/sources.list
 wget http://nvidia.limitless.lupine.me.uk/ubuntu/root@lupine.me.uk.gpg -O- | apt-key add -
 aptitude -y update && aptitude -y install linux-restricted-modules-$(uname -r) nvidia-glx
 nvidia-xconfig --add-argb-glx-visuals
 echo "deb http://ubuntu.beryl-project.org/ edgy main" >> /etc/apt/sources.list
 wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | apt-key add -
 aptitude -y update && aptitude -y dist-upgrade
 aptitude -y install beryl emerald emerald-themes aquamarine
 ln -s /usr/bin/beryl-manager ~/.kde/Autostart/beryl-manager
 echo -e "\n\nBeryl is now installed; please reboot.\n\nBackups of /etc/apt/sources.list and /etc/X11/xorg.conf were made:\n   $
fi;

```

Good luck! ;)

---

