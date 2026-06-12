---
title: "Driver installation"
date: 2011-10-01
forum: Networking &amp; Wireless
---

### Post by Wakemalo on 2011-10-01
Hello all, new here and come with a question that is geting me crazy :confused:. Im a noob in ubuntu but willing to learn, i´m not english so hopefully i will try make myself understable :).

Im runing ubuntu in a virtual machine that as main OS have windows Xp, the ubuntu version and headers are the follow; Ubuntu 11.04 Natty Narwhal/ headers 2.6.38-11 generic. I recently buy a wireless card and im trying to install the drivers in it because ubuntu don´t detect the card in any form (guess is because there are´t any drivers).

The wireless card is a connection N&C WNU2-ANT the chipset seems to be ralink 3070 and it comes with a instalation cd that ubuntu don´t let me execute for some reason.

My cuestion is how i should proced in order to install the driver, and if you can help me please keep in mind that im learning the ways of ubuntu :D.

Thanks in advance.

---

### Post by Wakemalo on 2011-10-01
bump.....

---

### Post by Wakemalo on 2011-10-02
tried to compile module of the driver 2009_1110_RT3070_Linux_STA_v2.1.2.0 following instructions in this lin;[http://ubuntuforums.org/showthread.php?t=1285828&page=5](http://ubuntuforums.org/showthread.php?t=1285828&page=5)

and got following log in terminal:


```
root@evo-VirtualBox:/home/evo# cd 2009_1110_RT3070_Linux_STA_v2.1.2.0
root@evo-VirtualBox:/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0# sudo make
make -C tools
make[1]: se ingresa al directorio «/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools»
gcc -g bin2h.c -o bin2h
make[1]: se sale del directorio «/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools»
/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.38-11-generic/build SUBDIRS=/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-2.6.38-11-generic»
  CC [M]  /home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.o
/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c:4002:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined
/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c:4406:1: warning: the frame size of 1576 bytes is larger than 1024 bytes
  CC [M]  /home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/action.o
  CC [M]  /home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o
/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3709:2: error: implicit declaration of function ‘init_MUTEX’
/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3710:2: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/include/rtmp.h:5704:13: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
make[2]: *** [/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-2.6.38-11-generic»
make: *** [LINUX] Error 2
root@evo-VirtualBox:/home/evo/2009_1110_RT3070_Linux_STA_v2.1.2.0# 

```

Help please  ](*,).

---

### Post by chili555 on 2011-10-02
I doubt you'll ever get that old driver, written in late 2009, to compile against a shiny new 2011 kernel. Let's see what you have. Please open a terminal and run and post with the device connected:```
lsusb
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Wakemalo on 2011-10-02
Hello chili555 did lsub first and got this:```
evo@evo-VirtualBox:~$ sudo su
[sudo] password for evo: 
root@evo-VirtualBox:/home/evo# lsusb
Bus 002 Device 002: ID 80ee:0021  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 18a5:0304 Verbatim, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@evo-VirtualBox:/home/evo# 

```later open a new terminal and hit the full code you writed and got this:
```
evo@evo-VirtualBox:~$ sudo su
[sudo] password for evo: 
root@evo-VirtualBox:/home/evo# lsusb
Bus 002 Device 002: ID 80ee:0021  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 18a5:0304 Verbatim, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@evo-VirtualBox:/home/evo# lsmod | grep rt2
 
```Was thinking ill be ignored, thanks for take the time :P.

---

### Post by chili555 on 2011-10-02
> The wireless card is a connection N&C WNU2-ANT the chipset seems to be ralink 3070Is it a USB device? Was it inserted when you ran the commands? Tell me more about the device, please.

---

### Post by Wakemalo on 2011-10-02
Yes it is a usb device, was inserted when i ran the command furthermore i have it runing both OS windows XP and Ubuntu with virtual machine both have internet acces, the device as described above is a  connection N&C WNU2-ANT.
The virtual machine conection configuration is set up as bridge connection.

---

### Post by chili555 on 2011-10-02
I think your question has more to do with a bridge connection in a virtual machine. I see nothing in your *lsusb* that is a USB wireless device. I'm very sorry, I don't know how to help.

---

### Post by Wakemalo on 2011-10-02
Well i had runing before a d-link with a rt73, had the same problem but i managed to install the drivers and a fix and was runing smooth for 3 years, but it death a week ago and had to buy a new one, problem is that im unable to install the drivers, in the install cd there is a linux firmware but is in bin format and i guess i don't have the skill to run bin files in ubuntu, but im looking rn the way to do it.

Thanks anyway.

---

### Post by chili555 on 2011-10-02
In any recent version of Ubuntu, the driver rt2870sta and needed firmware is installed by default. If it doesn't see and recognize the usb.id, it won't drive the device. > $ modinfo rt2870sta
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    [COLOR="Red"]RT2870/RT3070 Wireless Lan Linux Driver[/COLOR]
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin
srcversion:     93C0C58E1A016FE5BD4DC9F


---

### Post by Wakemalo on 2011-10-02
Yes all that information is displayed when i run the command $ modinfo rt2870sta, then i guess the problem should be in some point between the virtual machine and the ubuntu installation, i remember of the other device that when i installed the driver it start working and was reconized with the iwconfig command but i cant remember if the conection with the virtual machine was made as bridge, so at this point im lost need to do some more research about that.

---

### Post by Wakemalo on 2011-10-03
Well after some testing i managed to get the card running  but it seems slow and no working as intended, the problem was because i only install the driver in the host, once i uninstall it and install the full pack (driver+ralink utility) the device was listed by lsusb command.

I lsusb with the terminal and got this: ```
evo@evo-VirtualBox:~$ sudo su
[sudo] password for evo: 
root@evo-VirtualBox:/home/evo# lsusb
Bus 002 Device 002: ID 80ee:0021  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@evo-VirtualBox:/home/evo# 
 
```also did lsmod | grep rt2 and got this:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@evo-VirtualBox:/home/evo# lsusb
Bus 002 Device 002: ID 80ee:0021  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@evo-VirtualBox:/home/evo# lsmod | grep rt2
rt2870sta             410104  0 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
root@evo-VirtualBox:/home/evo# 
 
```Well i guess ubuntu don´t knows the device chipset for some reason, how i should fix this?

---

### Post by chili555 on 2011-10-03
> Well i guess ubuntu don´t knows the device chipset for some reason, how i should fix this?There are two drivers loaded and they conflict. Let's blacklist one:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and see if it is performing as expected.

---

### Post by Wakemalo on 2011-10-03
well i don't want to mess all the thing :) the code you writed is all followed i mean i have to write like is displayed in the post?

---

### Post by chili555 on 2011-10-03
Let me be a bit clearer. Please open a terminal and type in:```
sudo su
```Press Enter. The terminal prompt will return to a new line. Next, type in:```
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
```Press Enter. The terminal prompt will return to a new line. Then type in:```
exit
```Close the terminal and reboot. After reboot is your wireless working better?

---

### Post by Wakemalo on 2011-10-03
i write as you tell me but it send me again to the root, nothing seems to hapen  i copyed the text, and later write it myself. :(

---

### Post by chili555 on 2011-10-03
And then did you reboot? Did the wireless improve?

When you enter a command and nothing happens, that simply means, "Command executed as ordered and there are no warnings or errors to report." In this case, that's exactly what we hoped for!

---

### Post by Wakemalo on 2011-10-03
Did reboot and i don't know if it was worst before than now is so slow compared with the host connection that something have to be messing around :sad:.

---

### Post by chili555 on 2011-10-03
You might ask about virtualization in General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Sorry I can't be of more help. I'm not terribly familiar with virtualization where Windows is involved.

---

### Post by Wakemalo on 2011-10-03
Well i did some research and found a new patch from ralink seems to be really fresh the patch is called: 2011_079_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.bz2 downloaded from [http://www.ralinktech.com/en/04_support/license.php?sn=5016](http://www.ralinktech.com/en/04_support/license.php?sn=5016).

I'm quite sure that installing this patch will fix the problem, but i lack of the skills rn to compile and make it run mostly because i don't know well the commands, but i have the readme_STA_usb open and going to give a try on it.

---

### Post by chili555 on 2011-10-03
Here are some decent step-by-step instructions. You already have the driver, so you can ignore that part. See posts #2 and #4. [http://ubuntuforums.org/showthread.php?t=1800178&highlight=rt5370sta](http://ubuntuforums.org/showthread.php?t=1800178&highlight=rt5370sta)

---

### Post by Wakemalo on 2011-10-04
followed the tutorial and all went nice, not erros at all with make and make install  run fine.
Now the conection performs more fast but i can't make it  work with aircrack-ng suite.

Once i run airmon-ng in the line where the device is listed i got this: ```
root@evo-VirtualBox:/home/evo# airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
371    avahi-daemon
372    avahi-daemon
377    NetworkManager
1175    wpa_supplicant
1398    dhclient
Process with PID 1398 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan0        Unknown         usb (monitor mode enabled) 
``` now the rest of commands simply a line with device not detected.

How should i fix this? seems that the chipset is unknow for the system.

---

### Post by Wakemalo on 2011-10-04
bump...

---

### Post by donc786 on 2011-10-16
I don't think that chipset will work with the aircrack suite. I have an rt3070 and have not been able to get very far with it, the rt73 worked much better. Take a look at [this]("http://www.aircrack-ng.org/doku.php?id=compatible_cards").

---

