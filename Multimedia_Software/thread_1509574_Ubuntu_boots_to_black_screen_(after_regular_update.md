---
title: "Ubuntu boots to black screen (after regular updates)"
date: 2010-06-14
forum: Multimedia Software
---

### Post by Imashinu on 2010-06-14
Yesterday I updated my Ubuntu and restarted as recommened. It booted fine, went into the boot screen and then turned black and nothing loaded on the screen. I even tried loading 2 previous kernels but it still boots into a black screen.

Anyone have any ideas? I can't even open a terminal.

---

### Post by Imashinu on 2010-06-14
FYI,
I tried CTRL-ALT-F1 and nothing appeared on the screen, its like the screen turns completely off.

---

### Post by 67GTA on 2010-06-14
At the grub menu select recovery mode. This should get you to a terminal. Then try ```
startx
``` after logging in. You can also try hitting "e" at the regular grub entry and removing "quiet splash". Then hit ctrl+x to boot. You might be able to see where it is hanging. We need some king of error message to know what is happening.

---

### Post by Imashinu on 2010-06-14
I tried using recovery mode. But it runs into the same issue, halfway through the startup scripts the screen blanks out. Ctrl-x resulted in the same issue.

To make sure it wasn't my pc, I booted a Lucid Live Disk, as well as a windows partition. I have no idea what is causing my Ubuntu install to fail like this.

---

### Post by 67GTA on 2010-06-14
The fact that it's doing this on all kernels tells me it is probably a graphics issue. Try booting the default kernel with "quiet splash" removed as posted above. Hopefully this will show where it is hanging. It could also be acpi related. Use the same method to remove quiet splash and add acpi=off.

---

### Post by Imashinu on 2010-06-14
I really appreciate the help GTA. I was able to figure out the all of the Nvidia drivers somehow got deleted during the update. I should be able to get them reinstalled no problem, I appreciate your help.

---

