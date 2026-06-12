---
title: "Codecs"
date: 2008-06-14
forum: Multimedia Software
---

### Post by sayian_z on 2008-06-14
I used in windows K-Lite and CCCP codecs but I don't know what to use in ubuntu
I installed VLC but not all video types work with it :confused:

---

### Post by cariboo on 2008-06-15
Make sure you have all the sources checked in System-->Administrtion-->Software Sources except for the cd-rom. Then go to System-->Administration-->Synaptic Package Manager and search for ubuntu-restricted-extras mark it for installation and click apply. This will install most of the codecs you need to play audio and video files

---

### Post by Pjotr123 on 2008-06-15
Here's a complete how-to for full multimedia support:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by cozmicharlie on 2008-06-15
In addition to the great links Pjotr123 provided I would recommend this [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683).

Also, to add to cariboo907 recommendation, be sure to add the Medibuntu repository to your source list.  The post above shows you how.  

Enjoy

---

### Post by Joeb454 on 2008-06-15
You could try ```
sudo apt-get install libxine1-all-plugins
``` From a terminal :)

---

