---
title: "Installing Creative Xi-Fi driver (64-bit)"
date: 2010-10-14
forum: Multimedia Software
---

### Post by raoul_1101 on 2010-10-14
Hello all,

I'm very new to Ubuntu (or any flavour of Linux) and recently installed in on my computer. All seems to be working nicely except for sound. I have a Creative Xi-Fi sound card. There is a driver installed currently, but unless my sound is at 100%, everything sounds distorted. My first inclination, as a Windows user, would be to update the driver.
So, I downloaded the driver from their site in the form of a .tar.gz.
I followed the guide here:
[http://ubuntuforums.org/showthread.php?t=870001&highlight=creative+driver](http://ubuntuforums.org/showthread.php?t=870001&highlight=creative+driver)
But, as soon as I get to the step where I actually compile it (make), I get errors.

```
user@user-XFX-Nforce-680i-LT:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make
make -C /lib/modules/2.6.35-22-generic/build M=/home/user/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/user/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/user/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14: fatal error: sound/driver.h: No such file or directory
compilation terminated.
make[2]: *** [/home/user/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/user/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [all] Error 2

```Note: This is 64-but 10.10 Ubuntu.

 If someone could help me get through this is would be greatly appreciated :).
Raoul

---

### Post by Raff1 on 2010-10-20
This is exactly the same problem that I got! ^^

I only got this little line (the middle one) extra:
```

make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  **LD      /home/user/XFi_Drivers_Linux/built-in.o**
  CC [M]  /home/user/XFi_Drivers_Linux/xfi.o

```I really hope we can get some helpful input here. Last time I did this was on 9.04, but now I have moved on to 10.10.

---

### Post by Raff1 on 2010-10-23
I tried to look a bit more into the details here. It cant find the **driver.h** in the **sound/** folder. From the output I deduced that it is actually looking in the folder **/usr/src/linux-headers-2.6.35-22-generic/sound**:

```

user@Computer:/usr/src/linux-headers-2.6.35-22-generic/sound$ ls
aoa  atmel  drivers  isa      Makefile  oss     pci     ppc  soc    spi    usb
arm  core   i2c      Kconfig  mips      parisc  pcmcia  sh   sparc  synth


```However, there is no driver.h there. There is however a folder called **drivers** there:
```

user@Computer:/usr/src/linux-headers-2.6.35-22-generic/sound/drivers$ ls
Kconfig  Makefile  mpu401  opl3  opl4  pcsp  vx

```I really have no idea about the stuff in either folder. It seems likely however, that we need to edit some lines in the driver sources or the MakeFile. I hope I am wrong.

It would have been really nice if someone with some insight into what this driver.h is about and where it has gone would share their wisdom! ^^ It worked on 9.04 but fails in 10.10.

Edit: I am on 32 bit BTW. So it seems its similar on both 32 and 64 bit versions.

---

### Post by Raff1 on 2010-10-23
When enabling my proprietary video card drivers (**Administration > Additional Drivers**) I noticed that **X-FI driver version 1.00** was listed there as "This driver is *activated* but *currently not in use*" and "Tested by Ubuntu developers".

Seems my sound card has been recognized and drivers has been provided! Thats nice, but how do I enable them? :P

---

### Post by Raff1 on 2010-10-24
I tried following this guide: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

> **[SIZE=1]Manually starting the Audio driver[/SIZE]**

 Open a terminal and type sudo modprobe snd-[NAME OF YOUR SOUNDCARD'S DRIVER]. For example, my driver is a via82xx so I would type,```
 sudo modprobe snd-via82xx
``` I need to find out what my sound drivers name is.

sudo aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  ...

```Maybe my drivers nane is "ctxfi"? I try:
```
sudo modprobe snd-ctxfi
```but still no results.

I did not find any useful information regarding my drivers name here either: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

The drivers for my soundcard definately worked in ubuntu 9.04.

---

### Post by Raff1 on 2010-11-02
I failed to get any further with this, but managed to activate my old sound card instead which is also connected to my MoBo. Any insight into this would still be helpful though. I got sound, but my original problem is not solved, only bypassed.

---

