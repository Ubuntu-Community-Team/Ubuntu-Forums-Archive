---
title: "On Board Sound not working"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by Mohamed Fahim on 2008-02-03
I am using gigabyte motherboard which comes with realtek audio on board i installed Ubuntu 7.10 on my machine which is already running windows xp professional there are 2 problems which i cant solve they are
   1. I cannot hear any sound i tried all the ways but ubuntu shows realtek 833
   2. I cannot find my video card driver which comes with Intel board Intel Chipset 965 

Thanks in advance

:confused:

---

### Post by Mze on 2008-02-03
Check this [thread]("http://ubuntuforums.org/showthread.php?t=685619") out.

See if any of the suggestions there might help.

---

### Post by ngacleetus on 2008-02-03
I have a Gigabyte board as well.  I have found this solution to be helpful.  The problem that I now have, is that if i am not playing music, I have feedback in the speakers.  Currently trying find the solution to that problem.  I'm re-installing the drivers directly from Gigabyte and hopefully that works.  After the reboot make sure to un-mute the sound from the system tray on the bottom right.  By default it automatically mutes.  Hope that helps.

sudo apt-get install alsa-source
cd && mkdir alsa-patched && cd alsa-patched
tar -jxvf /usr/src/alsa-driver.tar.bz2
cd modules/alsa-driver/
wget -O alsa-kernel/pci/hda/patch_analog.c [http://launchpadlibrarian.net/9021234/patch_analog.c](http://launchpadlibrarian.net/9021234/patch_analog.c)
./configure --with-cards=hda-intel && make
sudo make install
sudo cp ./modules/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel/
sudo depmod -a
sudo shutdown -r now

---

