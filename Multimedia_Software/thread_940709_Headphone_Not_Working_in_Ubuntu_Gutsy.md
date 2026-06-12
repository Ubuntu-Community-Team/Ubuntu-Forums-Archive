---
title: "Headphone Not Working in Ubuntu Gutsy"
date: 2008-10-07
forum: Multimedia Software
---

### Post by thewebpromoter on 2008-10-07
I have a headphone that do not work lately, but when I searched for Ubuntu Tweaks, Tips and Howto, I found this codes in this Community, much thanks goes to [hyperandy and his thread]("http://ubuntuforums.org/showthread.php?t=707231").  

The codes runs this way:


wget [ftp://ftp.alsa-project.org/pub/drive...1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.16.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/a...1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/a...1.0.16.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils...1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/utils...1.0.16.tar.bz2)

Extracting them and removing tarballs:
Code:

tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2

Making the directory for compiling the source:
Code:

sudo mkdir -p /usr/src/alsa
sudo mv alsa-* /usr/src/alsa

Compiling and installing alsa-driver
Code:

cd /usr/src/alsa/alsa-driver*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

Compiling and installing alsa-libs
Code:

cd /usr/src/alsa/alsa-lib*
sudo ./configure
sudo make
sudo make install

Compiling and installing alsa-utils
Code:

cd /usr/src/alsa/alsa-utils*
sudo ./configure
sudo make
sudo make install

*** I dont need to do the codes below, since it functions anyway, plus I got some error when I do them, but I am posting it here, you might be needing them.

After doing the codes above, do the following instructions:

Reboot the machine and run more these comands:
Code:

sudo cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
sudo cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
sudo depmod -a

Reboot once more. And the next time will have sound working, no extra tweaks needed, like adding some line to /etc/modprobe.d/alsa-base. The steps above must solve the problem with sound and mic. The mic will work after enabling all boxes in the Gnome mixer applet. Change the input source to "front mic" or "mic" depending on which microphone you are gonna use. That's it.

Once again, thanks to **hyperandy**, Long Live Ubuntu Users!

---

