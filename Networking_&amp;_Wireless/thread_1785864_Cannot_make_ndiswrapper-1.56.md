---
title: "Cannot make ndiswrapper-1.56"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by Chasingu on 2011-06-18
Hello there. I recently installed Ubuntu 11.04 to run a Minecraft Server. Now against better judgement and seeing that it is only for 7 people, I decided to use a wireless usb card to connect to the internet. 

Well, I was told that I was going to have to install ndiswrapper. I downloaded it on my Mac and used a USB drive to transfer it to my desktop. I then double clicked and extracted. I then did this in the terminal:
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

chasetarson@chasetarson-DQ180A-ABA-S6300NX-NA410:~$ cd ~/Desktop/ndiswrapper-1.56
chasetarson@chasetarson-DQ180A-ABA-S6300NX-NA410:~/Desktop/ndiswrapper-1.56$ make
make -C driver
make[1]: Entering directory `/home/chasetarson/Desktop/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.38-8-generic M=/home/chasetarson/Desktop/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/chasetarson/Desktop/ndiswrapper-1.56/driver/loader.o
/home/chasetarson/Desktop/ndiswrapper-1.56/driver/loader.c:834:2: error: unknown field ‚Äòioctl‚Äô specified in initializer
/home/chasetarson/Desktop/ndiswrapper-1.56/driver/loader.c:834:2: warning: initialization from incompatible pointer type
make[3]: *** [/home/chasetarson/Desktop/ndiswrapper-1.56/driver/loader.o] Error 1
make[2]: *** [_module_/home/chasetarson/Desktop/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/chasetarson/Desktop/ndiswrapper-1.56/driver'
make: *** [all] Error 2
chasetarson@chasetarson-DQ180A-ABA-S6300NX-NA410:~/Desktop/ndiswrapper-1.56$ 
```I want to know what excatly I did wrong.

Here are some specs:
Recently installed 11.04 24 hours old
No updated or added packages installed.

---

### Post by ReZeeR on 2011-08-21
Yep same error, on top of that now I can't use my wireless, its like it doesn't exist

---

### Post by praseodym on 2011-08-21
Try this patched version of ndiswrapper:

[http://forum.ubuntuusers.de/post/2651205/](http://forum.ubuntuusers.de/post/2651205/)

Install the windows driver manually:

```
sudo ndiswrapper -i /path/to/driver.inf
ndiswrapper -l #check, if positive, then:
sudo modprobe -v ndiswrapper
sudo ndiswrapper -ma
```

---

