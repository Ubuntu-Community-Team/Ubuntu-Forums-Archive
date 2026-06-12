---
title: "usplash, initrd.img and BIOS splash."
date: 2009-03-31
forum: Multimedia Software
---

### Post by kagashe on 2009-03-31
I use HP/COMPAQ 2500 Series Laptop (whose display is broken) as a Desktop using VGA monitor. It has ATI RADEON IGP 345M card.

I have Ubuntu Hardy Heron Cli+LXDE. Initially I did not have usplash. Subsequently I installed ubuntu-usplash-theme.

When you install usplash it updates /boot/initrd.img

I also have other Linux Distributions on the hard drive and some of them also have usplash themes.

Ubuntu Hardy LXDE is the default installation.

When I started one fine morning the secondary monitor did not display the BIOS splash and remained on standby till GDM Login Screen appeared. After googling I discovered that it is some thing related to usplash. That time the Ubuntu installation did not have any usplash. That is when I installed ubuntu-usplash-theme and I could see the BIOS splash, Grub screen and Ubuntu splash during the boot process.

This problem has repeated once again and I had to remove ubuntu-usplash-theme and the BIOS splash and the boot time text appeared once again. I have re-installed ubuntu-usplash-theme once again and it is working fine.

I don't know the cause of the problem (it may be Ubuntu or other Linux Distribution) but I know the solution. I re-install Ubuntu splash which re-writes initrd.img.

I can understand the monitor not showing the Grub splash or Ubuntu splash but don't understand why it does not show BIOS splash.

Can the settings in initrd.img affect BIOS splash?

kagashe

---

