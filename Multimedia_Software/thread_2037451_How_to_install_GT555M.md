---
title: "How to install GT555M?"
date: 2012-08-04
forum: Multimedia Software
---

### Post by ColdCry on 2012-08-04
Hello all. I couldnt install my NVIDIA GT555M graphic card to my laptop.  When i try sh NVIDIA.run it says "  ERROR: You appear to be running an X server; please exit X before   installing.  For further details, please see the section INSTALLING  THE NVIDIA DRIVER in the README available on the Linux driver  download page at www.nvidia.com." How can i fix it and install it? Using Lenovo Ideapad Y570 and Ubuntu 12.04. Thanks.

---

### Post by Halbblutplins on 2012-08-04
First:   Strg+Alt+F1

Second step:   login and 
```
sudo su
```Third step:  ```
initctl stop lightdm
```Last step:  type in ```
bash /home/*****/NVIDIA-Linux-*******.run

```That's all.

If you are using another distro tell it me.

---

### Post by Yellow Pasque on 2012-08-04
The Y570 is a hybrid graphics ("Optimus") system. Don't do the stuff in the post above unless your BIOS has an option to disable the integrated Intel graphics and you want to use the nvidia GPU for every task. More likely, you'll want to follow instructions for bumblebee so that you can use the Intel IGP for most tasks (and good battery life) and only use the nvidia card for demanding stuff when you're on AC (using the optirun command): [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

