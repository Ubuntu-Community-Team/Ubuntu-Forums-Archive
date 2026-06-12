---
title: "Compiz and Drivers"
date: 2009-06-09
forum: Multimedia Software
---

### Post by a-hamster on 2009-06-09
I have Compiz (desktop effects) set to run as a start-up program, but I disabled the propitiatory Nvidia driver. So when Compiz tries to render the screen using openGL it can't and I'm stuck with a white screen and a mouse cursor. I can click on controls on the screen, I just can't see them. So what I'm asking for is either:

A. A method to install the Nvidia driver through the command line

B. A way to disable start-up programs (fail-safe didn't work)

C. The keystrokes needed to enable the driver after clicking on the applications menu in the upper right hand corner of 9.04.

Any help would be greatly appreciated!

---

### Post by AoSteve on 2009-06-09
Ok to get the nvidia driver, I just used envy, and it's the easiest command line method I've found.

sudo apt-get remove envy   (to remove it if you have it)

sudo apt-get install envyng-core

sudo envyng -t     (this will start the envyng program in the terminal so you can uninstall and reinstall the drivers without a GUI)   

Once you download the drivers, it should work correctly for you bud.   I hope this helps out!

I must give thanks to a friend who pointed me in this direction.   I'm still stuck without my 1680x1050 resolution, but compiz is working LOL!

---

### Post by a-hamster on 2009-06-09
Thanks a ton! Envy worked perfectly and now I'm back in business.

---

### Post by AoSteve on 2009-06-09
Good to hear buddy!  :)   Glad I was able to help you out!   Now if someone could just help me LOL

---

