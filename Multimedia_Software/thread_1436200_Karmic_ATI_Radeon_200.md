---
title: "Karmic: ATI Radeon 200"
date: 2010-03-22
forum: Multimedia Software
---

### Post by Kheops_74 on 2010-03-22
I install Ubuntu 9.10 on a computer with a ATI Radeon 200 video card. Sometime the computer freeze. I must reboot using the reset button. This happens a lot while using Google Chrome or FireFox. 

I'm pretty sure it came from the graphic card driver. Any comments or how-to to get this video card work.

Thanks

K

---

### Post by Kheops_74 on 2010-03-22
By the way, currently i use the ATI 8.660-0ubuntu4 driver instaled by EnvyNG.

---

### Post by Yellow Pasque on 2010-03-22
You can't use the proprietary driver with this card. The last Catalyst driver that supported it was Catalyst/fglrx 9-3 (and that version won't run on anything later than Ubuntu 8.10/Intrepid).

Follow this to reset your video driver back to stock configuration: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

You may also try an updated video driver by using the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Kheops_74 on 2010-03-22
I did this:
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg

And add the PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) to synaptics.

The computer freeze after the logon screen. I can only connect using a gnome (safe mode).

Any other idea? Maybe i had to execute other command after adding the ppa.

Thanks

---

### Post by Yellow Pasque on 2010-03-22
I don't want to alter your system more than you are comfortable with. If you want to go back to original video configuration, use this command and then restart your system:
```
sudo apt-get install ppa-purge xorg-edgers
```

If you want to continue troubleshooting, it is possible that the problem is caused by the mode-setting part of the video driver, which is now in the kernel, so you can try the latest stable kernel (if you are using 64-bit ubuntu, you need to change 'i386' to 'amd64' in the wget command):
```
cd ~/
mkdir kerneldebs
cd kerneldebs/
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633-generic_2.6.33-020633_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633_2.6.33-020633_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb
sudo dpkg -i linux*
```
You can now reboot your system, and it should boot into the new kernel. Check if the issue persists. If it does, then the freezing is probably caused by something else. I would recommend you boot into memtest from the grub menu (hold down Shift key when you start your system) and let it run through at least one pass.

---

### Post by Kheops_74 on 2010-03-23
I use 
Linux 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

You think there is a difference between this kernel and the one you are proposing 2.6.33 ?


Must i use your command without modifying them ?

Thank

---

### Post by Kheops_74 on 2010-04-30
With Lucid Lynx, no freeze but i don't have a lot of color (256 i think). Where you can tell Ubuntu to use more than 256 colors?

K

---

### Post by Yellow Pasque on 2010-04-30
Can you post the /var/log/Xorg.0.log ?

---

### Post by Elrond_Smith on 2010-05-07
I have the same problem on the same GPU. But I think problem not in video drivers. On my laptop freezing become after kernel update on ubuntu 9.10 from 20 to 21.
On 21 kernel system freeze all the way. then I boot it with 20 kernel system works fine.
On 10.04 in half times system starts normal, half freeze. Some times system freeze after some time of work. And it looks like slows only X.Org because music plays normal and normally[COLOR=#000000] responds on media buttons.
[/COLOR]

---

### Post by Kheops_74 on 2010-05-07
If you're right. Who will correct that in the kernel???

---

### Post by Elrond_Smith on 2010-05-08
may be we should recompile kernel manually.

---

