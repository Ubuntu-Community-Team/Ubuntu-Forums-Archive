---
title: "Tried to remove fglrx, now stuck at a black screen on boot"
date: 2012-03-05
forum: Multimedia Software
---

### Post by osarusan on 2012-03-05
Ubuntu 11.10 x64, ATI Radeon HD 4770 + Radeon HD 4200:

I followed the instructions here:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch)

After rebooting, I only get a black screen. I have my system set to auto login, but I am not even reaching the desktop. Further, I cannot ctrl-alt-f1 to get to a terminal. Just blackness.

I also tried using the recovery mode from the grub menu. This booted to the menu, but upon loading, the menu freezes and I cannot do anything. The keyboard is unresponsive and I have to cut the power. However, it is not fully frozen, as if I plug in or unplug a USB device, text appears on the screen recognizing that a device is being plugged and unplugged...

Please help me!

---

### Post by osarusan on 2012-03-05
Ah! I figured it out. I had to manually remove xorg.conf

I was able to get away from the black screen by editing the grub menu and removing the word "splash" from the kernel line, which allowed me to use ctrl-alt-f1 to reach a terminal...

Phew!

---

