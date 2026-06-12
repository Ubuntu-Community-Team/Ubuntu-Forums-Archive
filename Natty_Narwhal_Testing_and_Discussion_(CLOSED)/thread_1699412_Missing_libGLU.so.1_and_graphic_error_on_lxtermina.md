---
title: "Missing libGLU.so.1 and graphic error on lxterminal"
date: 2011-03-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Sworddragon on 2011-03-03
After upgrading to the new nvidia-current and xserver-xorg I get the message "error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory" on the game Teeworlds.

And if I'm starting lxterminal I get a black square of the same size as lxterminal on the upper left corner. It is some graphic glitch and causes often my system to freeze for some seconds - minutes.


My graphic card is a GeForce 8600 GT. Has somebody an idea how to solve the problems?

---

### Post by cariboo on 2011-03-03
If you can get to a console (Ctrl-Alt-F1-6) type:

```
sudo apt-get -f install
```

to see if any broken/missing dependencies are brought in.

If you can't get to a console, you could start in recovery mode and use the same command.

---

### Post by Sworddragon on 2011-03-03
The only broken package is keyboard-configuration (1.57ubuntu9) from the last apt-get dist-upgrade. There are no other graphic related packages.

---

### Post by cariboo on 2011-03-03
I'm using nvidia-current here, the only libglu package I have installed, is libglu1-mesa.

---

### Post by Sworddragon on 2011-03-04
I have installed this package and it worked. Now I can start Teeworlds without error message. Maybe this package was a dependency in the old version of nvidia-current but not in the new one. But the graphic error isn't solved with this. I can't even maximize lxterminal because there is a high chance for a freeze of the system.

---

### Post by dino99 on 2011-03-04
> **Sworddragon said:**
> I have installed this package and it worked. Now I can start Teeworlds without error message. Maybe this package was a dependency in the old version of nvidia-current but not in the new one. But the graphic error isn't solved with this. I can't even maximize lxterminal because there is a high chance for a freeze of the system.

use nautilus to search about that "libglu.so.1", then remove it (or remane it if you care)

---

### Post by Sworddragon on 2011-03-04
The libglu.so.1 problem is already solved or has it something to do with the freezes?

---

