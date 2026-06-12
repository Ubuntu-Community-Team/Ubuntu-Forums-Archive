---
title: "Nvidia Drivers..."
date: 2010-09-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Orpheon on 2010-09-12
I know there are about 500 different theads and pages about this, but not a single one can help me. In Lucid I tried several games, most of them running ok to laggy. I blamed this on wine, because my computer had no problems with them on windows and because the nvidia drivers were updated and running. Now however, not even starcraft 1 will run without a 2-second lag in singleplayer, and the other games have worsened. Wine says they are not to blame, and nvidia has some strange outputs. The 'Additional Drivers' in the menu says that nvidia-current is 'activated and currently in use'. But the 'Nvidia X Server Settings' always opens a window telling me that I do not appear to be using the Nvidia x driver. It tells me to run 'nvidia-xconfig' as root in terminal and restart the x server. I do that: bam, it goes xterm mode, flashes a bit, and shows all the other symptoms of a corrupt driver. I then always run these commands I have received: ldconfig, update-initramfs -u, and rename xorg.conf to xorg.conf.backup. Then startx works, and I'm back in, back at square one. Compiz, which worked flawlessly with the exeption of atlantis in Lucid, does not work either because if I try to enable desktop effects, everything flashes a few times, and a small window appears: 'Desktop effects could not be enabled'. Can someone help me?
ps: I have a Geforce 6200 card with 256mb. If you need more information, ask me. Sorry if this has already been handled.

---

### Post by ronacc on 2010-09-12
there was a major upgrade to the xserver in maverick and not everything is working  quite as it should yet , not just with Nvidia  most  of the cards have some kind of problems , right now the repo nvidia driver installs but don't work for me and the latest beta from nvidia has to be installed twice to work , first time it installs but wont start 2nd time it starts ok but disappears on reboot nad again has to be installed twice . best advice is keep updating and trying .:p

---

### Post by mc4man on 2010-09-12
> The 'Additional Drivers' in the menu says that nvidia-current is 'activated and currently in use'

If "square one" shows that then remove nvidia-current (in Additional Drivers), reboot and try Additional Drivers again (install/activate

> I then always run these commands I have received: ldconfig, update-initramfs -u, and rename xorg.conf to xorg.conf.backup


Well that is part of a way to return to nouveau though they should be preceded by this - picking the mesa option
sudo update-alternatives --config gl_conf

---

