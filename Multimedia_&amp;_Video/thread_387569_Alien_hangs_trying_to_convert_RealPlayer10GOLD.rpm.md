---
title: "Alien hangs trying to convert RealPlayer10GOLD.rpm"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by kkruecke on 2007-03-18
I installed alien using aptitude, downloaded RealPlayer10GOLD.rpm from [www.real.com](www.real.com), and then did
[HTML]alien --to-deb RealPlayer10GOLD.rpm[/HTML]
to create a .deb, so I could use dpkg to install RealPlayer. But alien never finished. I had to do CTRL+C. Anyone have any thoughts?

---

### Post by taurus on 2007-03-18
Why not download the RealPlayer10GOLD.bin and install it with

```
cd ~/Desktop
chmod 755 RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
```

---

### Post by kkruecke on 2007-03-18
Thanks for the prompt reply. My thinking was, if I installed RealPayer using

dpbk -i realplayerGOLD10.deb 

then I could use aptitude to easily uninstall it.

---

### Post by hero_zero on 2007-07-18
please help me 
i can't install 
===========



ssp@ssp-desktop:~$ alien --to-deb RealPlayer10GOLD.rpm
bash: alien: command not found
ssp@ssp-desktop:~$ cd ~/Desktop
ssp@ssp-desktop:~/Desktop$ chmod 755 RealPlayer10GOLD.bin
chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory
ssp@ssp-desktop:~/Desktop$ sudo ./RealPlayer10GOLD.bin
Password:
Sorry, try again.
Password:
sudo: ./RealPlayer10GOLD.bin: command not found
ssp@ssp-desktop:~/Desktop$ 
================

---

