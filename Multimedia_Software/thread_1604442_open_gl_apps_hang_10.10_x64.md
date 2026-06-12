---
title: "open gl apps hang 10.10 x64"
date: 2010-10-24
forum: Multimedia Software
---

### Post by excaliber27 on 2010-10-24
Somehow and I'm not sure how. But opengl apps will completely hang Ubuntu 10.10 x64.
This is my 2nd fresh install. I'm using the latest nvidia driver for my asus gtx460 (260.19.12). Have already verified rendering is enabled, uninstalled nouveau & blacklisted, mesa glx is installed, no errors (that I can see), etc.
When I run apps, even a gl screensaver, it will hang my whole box. To the point where I can't even, ctrl + alt + F1 (or F2, F3), for cli. So no command line output. 
And I've tested this in World of Padman, Alien Arena, Call of Duty 4 (under Wine), even Amnesia: The Dark Descent. Apps will start, but any gl content will quickly hang.
This is the first time running ubuntu x64, and a new box. So any help or support here would be greatly appreciated. 

Hardware:
Processor: AMD Phenom II 965 BE 3.4
RAM: 8 GB of Corsair XMS3
HDD: 600GB WD Velociraptor HD
Graphics: ASUS ENGTX460 1GB
Motherboard: ASUS M4A87TD EVO

(Nothing is overclocked)

---

### Post by excaliber27 on 2010-10-24
Figured it out. 

Had to set CPU and PCIE Spread Spectrums both to { Disabled }.

Just a heads up for anyone who encounters this issue.

---

### Post by excaliber27 on 2011-02-22
Found a new answer to this issue. 

Install "mesa-utils" package for Ubuntu x64.

---

