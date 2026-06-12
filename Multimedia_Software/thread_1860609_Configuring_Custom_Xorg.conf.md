---
title: "Configuring Custom Xorg.conf"
date: 2011-10-14
forum: Multimedia Software
---

### Post by 01001101 on 2011-10-14
I've just upgraded from Maverick Meerkat to the new Ubutnu 10.10, and I have two monitors that are tied into an Nvidia Fx 580 workstation card. After doing a bit of research, I've found that the new version of xorg attempts to automatically analyze your hardware so that you don't have to play around with Xorg.conf. My problem is that it got it wrong. It utilizes the board graphics on my computer rather than the graphics card. In the past, for some reason, my graphics card never fully agreed with my motherboard (I had to overhaul BIOS to even get it to boot with the graphics card). But, xorg was able to pick the propper graphics drivers (nvidia rather than ati), but still uses the board (because I'm getting input from VGA rather than DVI)

If I remember correctly in past versions there was a program in the administration menu that allowed you to configure your xorg.conf file in a nice graphic interface that would allow me to see what side of the screen my second monitor would be placed, then I would just generate the code and use that. I know that if I make my own Xorg.conf file, the computer will automatically use that one. I'm able to create code that says what monitors I have and what side to place the screen, but I don't know the code for telling xorg that I want it to run the graphics chip that's in the pci express slot, not the one on the board. Or is there an easier solution.

Thanks for your help.

---

### Post by collisionystm on 2011-10-14
gnome-randr-applet
arandr
grandr
lxrandr
xrandr

---

### Post by BicyclerBoy on 2011-10-14
If you are using the nVidia proprietary driver then use:
nvidia-settings
..
Don't use the gnome display prefs..

---

