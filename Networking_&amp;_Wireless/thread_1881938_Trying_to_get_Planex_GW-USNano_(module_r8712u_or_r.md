---
title: "Trying to get Planex GW-USNano (module r8712u or rtl819x)"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by marcelezaaa on 2011-11-16
hello, 
First of all, I am not native english speaker, and not very experienced with Linux, and also this is my first thread, so I would appreciate any guidance through it.

I am having a hard time trying to get a "Planex GW-USNano" to work on my crunchbang statler (based on Debian Squeeze). 
I tried to follow the steps on this wiki: [http://wiki.debian.org/rtl819x](http://wiki.debian.org/rtl819x) , but it didn't work out. 
and I am not sure what I am actually looking for, the r8712u or the rtl819x module. 
I not sure about which other information I should post but I will happily do it when asked!

I would really appreciate any help or advice,

Thank you very much,
Marcelo

---

### Post by chili555 on 2011-11-16
Let's be sure what we're working with first. Please open a terminal and run and post:```
lsusb
lsmod | grep -e 819 -e 8712
uname -r
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.> but it didn't work out. Please explain what you mean.

---

### Post by marcelezaaa on 2011-11-17
First of all, thank you for your time and effort to help me out!
and to clear up some things. 
I am trying to get this adapter working on my wife's laptop (which contains her and also mine important files) but I also have a pc also running CrunchBang with which I can be more experimental. 
And that machine I got the device to be recognized (but not yet working) by upgrating to squeeze-backports kernel. 

but this machine (laptop) is "normal".
and the result for the asked commands are:
```
lsusb
Bus 001 Device 003: ID 2019:ab28 PLANEX GW-USNano

```
No results for ```
lsmod | grep -e 819 -e 8712
```

and,
```
 uname -r
2.6.32-5-686

```

again, thank you very much,
Marcelo

---

### Post by chili555 on 2011-11-17
To compile the driver for the laptop will require that you download the driver file here: [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU)

Be sure you get the file called RTL8192SU-usb. Download it to your desktop. Right-click it and select Extract Here. The folder created will be called rtl8712etc. Double click it and go to the folder driver and open it and extract the file in it.

Install the kernel headers and build tools for your distribution (Debian?). In Ubuntu, the build tools are in a package called *build-essential*. Now open a terminal and do:```
cd Desktop/rtl
```Press Tab and the remainder of the file name will fill in. Press Enter. Type:```
driver/rtl
```Press Tab and the remainder of the file name will fill in. Press Enter. Now do:```
make
make install
modprobe 8712u
```Please post back if you get stuck.

---

### Post by marcelezaaa on 2011-11-17
Ok... driver downloaded (not to desktop because i dont "have" it but I suppose this will not be a problem) and extracted. 

well... it is a bit confusing now, but lets go:
inside the .zip file downloaded from "realtek" contains the folders: "document"; "driver"; "wpa_supplicant".
and files: "readme.txt" and "realeseNotes.doc"
and inside the folder "driver" contais a ".tar.gz" file with the same long name "rtl8712_8188......tar.gz" which inside contains lots of files and folders (which I belive is the important thing) 
... as I can "cd" into this .tar.gz file, I extracted it there, and tried to carry on... but the outcome for "make" was

```
beccl@hp-pavilion:~/downloads/drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401$ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.32-5-686/build M=/home/beccl/downloads/drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401  modules
make[1]: Entering directory `/lib/modules/2.6.32-5-686/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.32-5-686/build'
make: *** [modules] Error 2

```

so... is there something I am doing wrong??


thank you very much
Marcelo

---

### Post by chili555 on 2011-11-17
> so... is there something I am doing wrong??Have you installed kernel headers and build tools as I said? I'm not sure of the exact term in Debian or CrunchBang. In Ubuntu, it's```
sudo apt-get install linux-headers-generic build-essential
```

---

### Post by marcelezaaa on 2011-11-17
So, I had already build-essential and the kernel headers I installed following this little how to: [http://digitizor.com/2009/06/17/install-linux-build-and-kernel-headers-for-ubuntu-debian/](http://digitizor.com/2009/06/17/install-linux-build-and-kernel-headers-for-ubuntu-debian/) 
with the command:
```

sudo apt-get install linux-headers-$(uname -r)

```
as there is no "linux-headers-generic" on the repos for crunchbang... 

Should it be OK?
thank you very much again,
marcelo

---

### Post by chili555 on 2011-11-17
The link you gave is a good explanation of headers but I see nothing about the build tools. What does this tell us?```
sudo dpkg -s build-essential | grep Status
```

---

### Post by marcelezaaa on 2011-11-17
```
$ sudo dpkg -s build-essential | grep Status
Status: install ok installed
```

---

### Post by chili555 on 2011-11-17
Is the result the same with:```
[COLOR="Red"]sudo su[/COLOR]
make clean
make
make install
modprobe 8712u
exit
```

---

### Post by marcelezaaa on 2011-11-17
make clean
```
root@hp-pavilion:/home/beccl/downloads/drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401# make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
cd cmd ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd crypto ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd debug ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd eeprom ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8712 ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd io ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd ioctl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd mlme ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd mp ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_intf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_intf/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd pwrctrl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd recv ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd rf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd sta_mgt ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd xmit; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd efuse; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 

```

make
```
root@hp-pavilion:/home/beccl/downloads/drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401# make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.32-5-686/build M=/home/beccl/downloads/drivers/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401  modules
make[1]: Entering directory `/lib/modules/2.6.32-5-686/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.32-5-686/build'
make: *** [modules] Error 2

```

I just managed to get it working on my desktop pc, by upgrading to squeeze-backports kernel, with which the driver is supported. 
I could do the same in this machine, I suppose... but still would like to know why I can not get to compile the driver... 

thank you very much, 
marcelo

---

### Post by marcelezaaa on 2011-11-17
Hi!
It is working now, 

my problem was the same as described in this other forum: [http://crunchbanglinux.org/forums/topic/13851/solved-problem-with-make/](http://crunchbanglinux.org/forums/topic/13851/solved-problem-with-make/)
Apt-get reported my linux-headers to be installed correctly, but Synaptic said otherwise. I installed them, then needed to modify the driver Makefile to point to '/usr/src/linux-headers-2.6.32-5-686' rather than '/lib/modules/$(KVER)/build'.


but now it is working..  
thank for your time and effort to help me out!!
marcelo

---

### Post by chili555 on 2011-11-17
Excellent. Glad it's working now.

---

