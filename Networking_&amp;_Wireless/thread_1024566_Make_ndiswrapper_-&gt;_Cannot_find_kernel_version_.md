---
title: "Make ndiswrapper -&gt; Cannot find kernel version in"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by Nicsoft on 2008-12-29
Hello,

I am new to Linux (so please, be humble...:D) and I am trying to get my wireless card to work (WMP54G, Ralink rt61 chipset) using ndiswrapper. 

When I try to make ndiswrapper i get 

```
sudo make
make -C driver
make[1]: Entering directory `/home/niklas/Desktop/ndiswrapper-1.53/driver'
Makefile:34: *** Cannot find kernel version in /lib/modules/2.6.27-7-server/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/niklas/Desktop/ndiswrapper-1.53/driver'
make: *** [all] Error 2
```

The headers are installed and the source to, I think. Perhaps I don't get the links correct configured? I created the link in this way:

```
sudo ln -s /usr/src/linux-source-2.6.27 /lib/modules/2.6.27-7-server/build
``` and when that is done I have the following link in /lib/modules/2.6.27-7-server/build: linux-source-2.6.27. Or to make it more clear:

```
$ pwd
lib/modules/2.6.27-7-server/build

$ ls -l
lrwxrwxrwx 1 root root 28 2008-12-29 11:12 linux-source-2.6.27 -> /usr/src/linux-source-2.6.27
```

Is this correct? How come the kernel version isn't found there? I can find it in /usr/src/linux-source-2.6.27

```
$ pwd
/usr/src/linux-source-2.6.27

$ ls
//among other things
kernel-version
```


Any ideas?

Thank you in advance!

Regards,
Niklas

---

### Post by cdtech on 2008-12-29
Why not install it through the "Synaptic Package Manager"?

---

### Post by kevdog on 2008-12-29
You don't need to make any symbolic links

sudo aptitude install linux-headers-`uname -r` build-essential

---

### Post by Nicsoft on 2008-12-29
Hello, 

Thanks for the quick answers. 

I think I have done both of your suggestions (probably more than once...). 

In Synaptic Package Manager, the ndiswrapper-utils-1.9 and ndiswrapper-common is marked as already installed. 

The actual reason why I want to do this is because when I am trying to do 
```
sudo modprobe ndiswrapper
``` I get 
 ```
FATAL: Could not open '/lib/modules/2.6.27-7-server/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory
```
I found in a forum that I have to compile ndiswrapper myself in order to fix this. 

When i do this: 

```
sudo aptitude install linux-headers-`uname -r` build-essential
```

I get this: 

```

[sudo] password for niklas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 39 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

I.e. It's already installed if I am not wrong. 

But it's not the header files that is the problem now, is it? The complaints are for the kernel version and isn't that positioned with the source files?

Should I remove the link?

Regards,
Niklas

---

### Post by kevdog on 2008-12-29
Not to change the subject, but I thought there were native rt61 drivers already included in the kernel making the ndiswrapper process obsolete.

---

### Post by Nicsoft on 2008-12-29
I think there is. But it didn't work and during my quest when I have tried getting it to work. I gave up the native one and started on the ndiswrapper which seemed to be more successfull and more commonly used when searching the forums. 

Perhaps I am focusing on the wrong problem here? Perhpas I should focus on the native one? 

Just a quick brief, here is where I stopped (since it didn't work I was trying to install the native one from scratch): 

```
$ pwd
/opt/2008_0723_RT61_Linux_STA_v1.1.2.2/Module


$ sudo make
[sudo] password for niklas: 
make -C /usr/src/linux-headers-2.6.27-7-server SUBDIR=/opt/2008_0723_RT61_Linux_STA_v1.1.2.2/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-server'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-server'
make: *** [all] Error 2
```

I was thinking like you, "This is going to be no problem, it will work out of the box..." Three days later...

Or should I look somewhere else. Sorry, but I am totally lost and will be most happy for any guidance! And I may as well have destroyed the installation because ifconfig doesn't show wlan0 anymore I just noticed. 

Thanks again!

/Niklas

---

### Post by kevdog on 2008-12-29
Is that a USB device?  If not, serial monkey makes a good set of rt61 drivers.

---

### Post by Nicsoft on 2008-12-29
Hello again,

This is what I did. I re-installed Ubuntu 8.10. Mainly because I wanted to start from a clean installation but also because I think I did install the acutal card after I installed Ubuntu before. Just to make sure I didn't do exactly in the same way again I installed the desktop version instead of the server version. 

I used the Network Manager Applet in the top-left to configure my network and unplugged the fixed cable. Voiala, not it works. 

So, I actually have no idea what all problems was, but most likely I messed up to much and I didn't use the NM Applet before things were already destroyed. 

Thanks for your time anyway. :D

Best Regards,
Niklas

---

