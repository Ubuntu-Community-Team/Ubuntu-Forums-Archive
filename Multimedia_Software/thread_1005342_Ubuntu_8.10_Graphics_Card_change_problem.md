---
title: "Ubuntu 8.10 Graphics Card change problem"
date: 2008-12-08
forum: Multimedia Software
---

### Post by Mutahir on 2008-12-08
Hi All,

I had a Intel GMA950 graphics accelerator in my Dell Dimension 5000 PC ; I just recently changed/upgraded the graphics card to ATI Sapphire 2400HD and ubuntu won't start properly ; it gets to the screen 'check pc display settings' and thats it.

Any idea on how to get this working, I am not very experienced with linux.


Ubuntu 8.10

Thanks and Regards

---

### Post by Mutahir on 2008-12-15
Any one ? Any suggestions ?

Thanks

---

### Post by benerivo on 2008-12-15
Try Ctrl+Alt+Backspace at the screen it fails on. This should get you to a terminal screen, where you can type```
sudo dpkg-reconfigure -phigh xserver-xorg
```then use Ctrl+Alt+Del to reboot. This should get you to a working graphical environment.

You might also try the envy program to install the ATI drivers. Install it from the terminal with```
sudo apt-get install envyng-core
```and run it in the terminal with```
sudo envy -t
```

---

### Post by Mutahir on 2008-12-18
Hi Benerivo,

Thank you for your suggestion, I shall try this over the weekend and will update here.

Once again thanks and regards
Mutahir

---

