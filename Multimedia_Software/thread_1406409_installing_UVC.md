---
title: "installing UVC"
date: 2010-02-13
forum: Multimedia Software
---

### Post by koolkid93 on 2010-02-13
I'm trying to install UVC on my computer so i can use my webcam. i have a ubuntu 9.04. i'm trying to follow the directions on the ubuntu help. i downloaded the source codes and extracted them into the hoem folder. when i try to do the second step and enter into the terminal 
sudo apt-get install linux-headers-`uname -r`

and all it says is that it cannot find the program. am i doing something
wrong? am i missing a step? is this even possible to do? i need help

---

### Post by Yellow Pasque on 2010-02-14
You should have headers already installed, but that command should work. Are you sure you typed backticks (the ~ key) and not apostrophes?

---

### Post by koolkid93 on 2010-02-14
okay so i fixed that and entered sudo apt-get install linux-headers-~uname -r~ and it came up with E: Command line option 'r' [from -r~] is not known. i am pretty clueless when it comes to programing so i don't know what to do. 

you said i should already have the header so could i just skip this step? if i can where do i go from here? i'm trying to get my webcam to work and i've tried it several times but nothing. 

sorry i'm so clueless but thank you soo much for your help!! i really appreciate it!!

---

### Post by Yellow Pasque on 2010-02-14
> sudo apt-get install linux-headers-~uname -r~
LOL, no.
Just copy and paste this:
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by koolkid93 on 2010-02-14
haha oh i got what you ment now. so that worked and i worked through all the steps of building the uvc module. on the second last step i put in the command lsusb and got

Bus 002 Device 006: ID 046d:0805 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 03f0:7e04 Hewlett-Packard Deskjet F4100 Printer series
Bus 005 Device 003: ID 413c:2105 Dell Computer Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:3012 Dell Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

so my webcam showed up on the list like it should. so i entered the last step
 
 sudo modprobe uvcvideo

and nothing happened. i assumed it worked so i tried to use my webcam on skype but it still doesn't work. any ideas?

---

