---
title: "Nvidia causes text mode garbled 8.10"
date: 2008-11-09
forum: Multimedia Software
---

### Post by KaizokuX on 2008-11-09
Hi,

After installing the nvidia-glx-177, when ever I enter console mode via ctrl+alt+f1 or logout/shutdown. I get a garbled console with random jumpy lines, this is really annoying. is there any options I can disable in xorg.conf that can fix this?

---

### Post by KaizokuX on 2008-11-10
Anyone?

---

### Post by shane19174 on 2008-11-10
The only thing I can think is that the resolution outside of X is wrong or less than optimal. You can try changing the resolution setting in startup-manager (which primarily changes the appearance of usplash, the bootup/shutdown progress bar if you've got it, but will also affect text consoles. Or you can check your grub menu.lst to see if there's a vga= entry there. You can try commenting it out to see if this makes any difference, or changing the number to correspond to a better resolution. (There are threads elsewhere that discuss the meaning of the possible number settings. Try searching for "menu.lst vga=".)

---

### Post by KaizokuX on 2008-11-10
Thanks, changing the vga fixed the problem, I looked at the list in [http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

And ended up using 352 for my 1280x800 laptop.

---

### Post by shane19174 on 2008-11-10
Hey, glad to hear that it was such an easy solution.

---

