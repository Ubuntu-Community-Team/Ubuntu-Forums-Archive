---
title: "How are ATI Drivers these days?"
date: 2009-06-20
forum: Multimedia Software
---

### Post by DeathOnJuice on 2009-06-20
I'm thinking about getting a new computer once another wave of hardware comes out. I've heard that ATI has made some big gains on NVidia. But, I also know that they used to have big driver incompatibilities with Linux. How is this the situation now? Would I be safe with ATI?

---

### Post by Arup on 2009-06-20
Improving but still long way to go when compared to nvidia, nothing like vdpau on anvil for ATI yet.

---

### Post by Melcar on 2009-06-20
- Current drivers have problems with composition (Compiz, Kwin, Metacity, etc.) and xserver 1.6 (basically all current distros like Jaunty).  Most common issues are slow window transformation (resizing, maximizing, etc.) and problematic accelerated video playback (Xv, opengl)

- Tearing with video playback.  This is noticeable even with the open source drivers, so I don't buy that it's a fglrx only bug. 

- Problematic WINE support.  It got a bit worse after the latest WINE release due to certain changes in WINE's code.

Other than those big 3 issues, the driver works fine for normal desktop use.

---

### Post by headsmash on 2009-06-20
I was unable to get multiple ATI cards to work in Ubuntu or Fedora. Nvidia for the most part was not difficult.

---

