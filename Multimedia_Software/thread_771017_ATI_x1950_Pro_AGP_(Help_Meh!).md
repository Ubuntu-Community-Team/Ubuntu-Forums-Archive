---
title: "ATI x1950 Pro AGP (Help Meh!)"
date: 2008-04-27
forum: Multimedia Software
---

### Post by Johnnyftw on 2008-04-27
How do I install my videocard? I'm new to Linux and Every time I try my screen goes black and I have no video.. Ubuntu does load up but I just no video, I'm running 8.0.4.. Need help :(

---

### Post by xMachina on 2008-05-13
Hi Johnny, I finally got this card going properly in Linux after owning it for 6 months+ ... some guy called Alastair over at the ATI bugzilla has figured out how to get it going! By:

1) Follow the manual install option for the Proprietary ATI drivers at [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually)

EXCEPT before rebooting, you also need to make sure the AGP memory listing matches up at 3 places, to avoid the "ATI black screen of death":

2) Look up exactly how much video RAM your card has, eg from the box, receipt, or the ATI control centre in windows (it will either be 256MB or 512MB). For the instructions below I'll go with 512, but substitute as appropriate.
3) edit your /etc/X11/xorg.conf, and add the following line at the end of the fglrx device section:
>  Option      "MaxGARTSize"       "512"
4) edit your grub boot instructions for your kernel in the /boot/grub/menu.lst file, adding vmem=512 to your kernel boot line for your main kernel, e.g.:  
> 
title           Ubuntu 8.04, kernel 2.6.24-16-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-16-386 root=UUID=64fa7a1b-a8d7-45fb-a891-a81f3977bc13 ro quiet splash **vmem=512**
initrd          /boot/initrd.img-2.6.24-16-386

5) Ok, now reboot, but ENTER YOUR BIOS and look for the setting related to AGP memory, for me it was in the "Advanced Chipset Features" section. Change it to the same value as the others, eg 512MB.

...and that worked for me, ~1600 FPS in fg_glxgears ;) Haven't tried Compiz etc yet

---

