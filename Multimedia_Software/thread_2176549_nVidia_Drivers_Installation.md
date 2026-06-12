---
title: "nVidia Drivers Installation"
date: 2013-09-24
forum: Multimedia Software
---

### Post by danny7 on 2013-09-24
New to Ubuntu and I'm having some issue installing drivers for a 765m chip. Here's the message I'm getting, hopefully you guys can guide me in the right direction. 


[IMG]http://i.imgur.com/XpKB5qL.png[/IMG]

---

### Post by Yellow Pasque on 2013-09-25
Welcome to Ubuntu. 
Step 1 - stop trying to install drivers the Windows way..

What version of Ubuntu are you running? Ubuntu 13.10 and 12.04 already have nvidia-319.32 driver packaged in the main repo. For 12.10 or 13.04, you can get it here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by danny7 on 2013-09-25
Well thank, seems I have much to learn, However it doesn't appear like Ubuntu has recognized the chip under system details, it only lists Intel integrated graphics.

---

### Post by Yellow Pasque on 2013-09-25
Oh, so this is an Optimus system? (I should have guessed from the 765**m**).. :\

1. Remove any nvidia drivers you installed
2. Make sure your BIOS is set to Optimus mode if it has a switch to select what graphics modes are active
3. Make sure that the lspci command shows both cards
4. [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

