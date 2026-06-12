---
title: "Source code for CB21AG Wireless Card... Help Needed!!"
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by sunandi on 2011-07-03
Two Questions:

[B]A:
[/B]Can you tell me which code belongs to CB21AG code?
In the directory debian/debian/drivers/net/wireless/ath/ath5k/ I can see two modules written 
1. pci.c and 
2. ahb.c

Not sure which one to look for!!

[B]B:
[/B]If I want to build ath5k.ko module by making some changes then how to build it?
If I go to directory
debian/debian/drivers/net/wireless/ath/ath5k/ and give make then it doesnt goes through :-(
[B]sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/source/debian/debian/drivers/net/wireless/ath/ath5k$ make
make: *** No targets.  Stop.
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/source/debian/debian/drivers/net/wireless/ath/ath5k[/B]

Need help in this too!!!

---

### Post by chili555 on 2011-07-03
In order to check, I'll have to look at it. Where did you download this little gem? May I have a link?> which code belongs to CB21AG code?What is CB21AG? Your wireless card? Pardon my misunderstanding, please.

---

### Post by sunandi on 2011-07-03
Hi Chilli,
I am talking about the wireless Card AIR-CB21AG-A-K9 802.11a/b/g Cardbus Adapter.

I am searching for the driver code of this card,
It is one of the precompiled and preloaded module named ath5k.ko.

My intention is to make some changes and playaround with this peice of code :D

---

### Post by chili555 on 2011-07-03
> My intention is to make some changes and playaround with this peice of codeAwesome, man! I applaud you. However, as far as I know, unless you want to recompile the entire kernel, a daunting and lengthy task, it is impossible to compile ath5k or any other module already compiled and built in to the running kernel. It would be much easier to download the compat-wireless package, make a few changes in the not yet compiled code and then compile and install it.

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)> sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/source/debian/debian/drivers/net/wireless/ath/ath5k$ make
make: *** No targets. Stop.There is no Makefile there, so, it doesn't 'make.' There is one here: /usr/src/linux-headers-2.6.38-8/drivers/net/wireless/ath/ath5k/[COLOR="Red"]Makefile[/COLOR]; however, I am not sure you can rebuild a module already compiled on a running kernel.

---

### Post by sunandi on 2011-07-03
Hi Chili,
Thanks a lot for such a warm applause :-) and thanks a lot for the link, I am going through it .....
1. I we can rmmod a driver, the way you told me to unload the module for intel driver
sudo rmmod -f <wrieless_driver>
I thought it should be possible the otherway too!. 

2. There is a Make file in the directory "debian/debian/drivers/net/wireless/ath/ath5k"
I am pasting the content here

```
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/source/debian/debian/drivers/net/wireless/ath/ath5k$ ll Makefile 
-rw-r--r-- 1 sudipto sudipto 512 2011-07-02 15:24 Makefile
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/source/debian/debian/drivers/net/wireless/ath/ath5k$ cat Makefile 
ath5k-y                += caps.o
ath5k-y                += initvals.o
ath5k-y                += eeprom.o
ath5k-y                += gpio.o
ath5k-y                += desc.o
ath5k-y                += dma.o
ath5k-y                += qcu.o
ath5k-y                += pcu.o
ath5k-y                += phy.o
ath5k-y                += reset.o
ath5k-y                += attach.o
ath5k-y                += base.o
ath5k-y                += led.o
ath5k-y                += rfkill.o
ath5k-y                += ani.o
ath5k-y                += sysfs.o
ath5k-y                += mac80211-ops.o
ath5k-$(CONFIG_ATH5K_DEBUG)    += debug.o
ath5k-$(CONFIG_ATH5K_AHB)    += ahb.o
ath5k-$(CONFIG_ATH5K_PCI)    += pci.o
obj-$(CONFIG_ATH5K)        += ath5k.o

```I really doubt that we CANNOT build our own ath5k.ko and load it to the kernel.
Its just another module ..... Pardon me if I am not correct and talking too lame, I am a newbie!!!

---

### Post by chili555 on 2011-07-03
> I really doubt that we CANNOT build our own ath5k.ko and load it to the kernel.I think you are absolutely correct, we can. I just don't know about rebuilding one that's already built and compiled into the kernel. Read carefully, I didn't say 'can't," I said "I don't know." I think you have two alternatives: find someone who does know or try it and see if it works! If it does, I will bow to your skill and fall off my chair in shock.

The advantage of the compat-wireless package is that it has not yet been compiled into the kernel; we know we can read the source code and we know we can perfectly compile it, install it and use it.

---

### Post by sunandi on 2011-07-03
Hi Chili,
I am trying to install and build compat wireless package, this looks more intresting for now :-)
Lets see how far I can go with this. Rightnow resolving few dependencies.

Thanks again for the link.
Will definitely  need your help in this, will keep bugging you :D

---

### Post by chili555 on 2011-07-03
Your dependencies will be resolved if you install build-essential and linux-headers-generic. Have you already made your modifications? They must be done* before* you compile.

---

