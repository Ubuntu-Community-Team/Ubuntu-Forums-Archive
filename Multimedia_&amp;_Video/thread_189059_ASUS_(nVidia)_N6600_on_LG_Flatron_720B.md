---
title: "ASUS (nVidia) N6600 on LG Flatron 720B"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by predrag_ns on 2006-06-04
Hi to you all. 

I just trasfered from WinXP to Ubuntu - and I have one problem. 

When I walk through menus and/or moving windows arround desktop - everything looks (drawing of windows) slow. When something needs to fade (e.g. on turning off) it fades pretty slow. 

So, my question is (i think so) - Where can I find Ubuntu drivers for NVIDIA N6600? (I already installed **nvidia-glx**)

Thanks!

Kind regards, 
Predrag

---

### Post by johnc4510 on 2006-06-04
You installed the nvidia-glx drivers, but did you enable them?
sudo nvidia-glx-config enable
Open a terminal:Applications>Accessories>Terminal   and copy and paste the above line into it and then hit enter. To close the terminal type in exit and hit enter.

---

### Post by predrag_ns on 2006-06-05
[QUOTE=johnc4510]You installed the nvidia-glx drivers, but did you enable them?
sudo nvidia-glx-config enable
Open a terminal:Applications>Accessories>Terminal   and copy and paste the above line into it and then hit enter. To close the terminal type in exit and hit enter.[/QUOTE]

Thank you John - it worked! I needed also (before or after that) to manually edit xorg.conf Drivers section from *nv* to *nvidia*

My glxgears work fluently now :-D 

Thanks again, 
Predrag

---

