---
title: "Wireless Adapter AE1000 Help"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by DubyaGov on 2011-01-03
Hello. I am in need of some help. I have Windows 7 and Ubuntu 10.04 (64bit) dual booted on my computer. It seems that my adapter is being detected, however, it's not connecting to anything/not working.

I have referred to other threads but to no avail. Windows and ubuntu both see the adapter but ubuntu isn't letting it...work? I need some help...

I do not have internet connection on ubuntu to download the drivers for it. I have looked at [http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558). But downloading the drivers is a problem because I don't have internet...

lsusb ---
```
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 005: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 007 Device 004: ID 046d:c221 Logitech, Inc. G15 Keyboard / Keyboard
Bus 007 Device 003: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 007 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 002 Device 002: ID 13b1:002f Linksys 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```ifconfig ---
```
eth0      Link encap:Ethernet  HWaddr 00:25:22:64:42:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)
```

---

### Post by PatchesTheCaveman on 2011-01-03
There are complete instructions on how to get this device working here:
[http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558)

While those instructions are for Fedora, they will work for Ubuntu too.  Make sure you also follow Step 4a as Ubuntu also has this newer version of the kernel.

Before you can follow those steps, you will need to install a couple packages on your system.  To do so, run this command:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Let us know if you have any trouble.

---

### Post by DubyaGov on 2011-01-08
Hey, I did the install. Whenever I try and use ```
wget -O ~/Download/RT3572_Linux_STA_v2.4.0.2.tar.bz2 'http://www.ralinktech.com/download.php?t=U0wyRnpjMlYwY3k4eU1ERXdMekE1THpFMUwyUnZkMjVzYjJGa016UXhPRFkxTnpJMk5TNWllakk5UFQweU1ERXdYekE1TVRWZlVsUXpOVGN5WDB4cGJuVjRYMU5VUVY5Mk1pNDBMakF1TWk1MFlYST1D'
```

It says 'No such file or directory.'  I am currently on an Ethernet connection until I get this wireless adapter working.

---

### Post by PatchesTheCaveman on 2011-01-08
Download it directly from Ralink's website:
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Select the driver for the RT3572 chipset.

By the way, I'm sorry I gave you the link you already had in my last post.  I don't know where my brain was that day.  :-/

---

### Post by DubyaGov on 2011-01-08
Don't worry about it. I now have the RT3572. It is is Downloads/Extract/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO    <----This is a different version than that of another thread...

Here is just some info ---

Kernal - 2.6.32-27-generic

-----

I have edited my config.mk and added the 2 'y'

Do I have to edit my linux_rt.h?

I have added my linksys device to the rtusb_dev_id.c - Do i have to use my own product hex key thing?

I have used
```
sudo make install
sudo modprobe rt3572sta
iwconfig
```And ```
make
```   <--- Everything was good.

^ No errors at all (so far)

My device is still not working... I have a couple more things I'm going to try but any extra help would be appreciated.

Thanks

!!!!EDIT!!!!!

I did have an error after changing my Linksys Hex Key to my own (my bad) And not I get this error

/home/william/Downloads/Extract/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtusb_dev_id.c:51:34: error: macro "USB_DEVICE" requires 2 arguments, but only 1 given
/home/william/Downloads/Extract/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtusb_dev_id.c:51: error: &#8216;USB_DEVICE&#8217; undeclared here (not in a function)
make[2]: *** [/home/william/Downloads/Extract/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtusb_dev_id.o] Error 1
make[1]: *** [_module_/home/william/Downloads/Extract/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-27-generic'
make: *** [LINUX] Error 2


*********Everything listed before this edit is the same. I just edited rtusb_dev_id.c**********

---

### Post by PatchesTheCaveman on 2011-01-09
I need a link to the download of the particular version you're using to look into this.

---

### Post by DubyaGov on 2011-01-09
Hello, Well I did get my Adapter to work. Im using it right now. But there seems to be a newer version of the drivers for AE1000 Link ->[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

This link is the one you told someone else on another thread to go to. I did and there seems to be a verson 5.0.0.DPO or something like that.

Thanks for your help.

---

### Post by rodrickhales on 2011-01-12
> **PatchesTheCaveman said:**
> There are complete instructions on how to get this device working here:
[http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558)

While those instructions are for Fedora, they will work for Ubuntu too.  Make sure you also follow Step 4a as Ubuntu also has this newer version of the kernel.

Before you can follow those steps, you will need to install a couple packages on your system.  To do so, run this command:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```Let us know if you have any trouble.

I wanna do this part but I have no internet with ubuntu.  How do I get this?  It says it could not find build-essentials.

---

### Post by PatchesTheCaveman on 2011-01-13
If you can't plug into a wired Ethernet connection, I'll need you to collect some information so I can point you to the appropriate packages.

Please run the following commands on a terminal:
```
gcc --version
uname -a
```
and copy/paste the results.

---

### Post by DubyaGov on 2011-01-13
Well what I had to do was go out and just get a Ethernet cable. Then just plug it into my router... It wasn't difficult, the hard part is doing it without internet...

I would recommend just getting a cable or somewhere/someone that has one.

---

