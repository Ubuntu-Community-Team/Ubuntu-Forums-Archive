---
title: "LinkSys PCMCIA Card - Can'tget Wifi, at a loss!"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by Fujiwara86 on 2011-02-12
Hello there,

First up, before anyone suggests running search etc, I have already been through multiple tutorials and the troubleshooting guide sticky'd on this thread to no avail.

I'm running 32 bit Ubuntu 10.10 on an IBM Thinkpad R32. It has a Pentium 4 Processor and 512mb RAM. The PCMCIA wifi card I have is a Linksys WPC54G Version 3.2. The card has power but no network.

I should also specify that I am a complete Linux noob...and some of my trouble comes from working through the tutorials then reaching a step that doesn't work for me - and that leaves me nowhere to go. 

So, I started by installing Ndiswrapper via the Ubuntu Software Centre, then downloading the most recent Windows driver for my wifi card. The driver seemed to install ok. But running the command:

sudo modprobe ndiswrapper
returned nothing. I therefore worked through the troubleshooting section stickied on this section of the forum. I ended up at Step 4 where it showed that the network was unclaimed.

I carried on and got no response from:

lsmod | grep ndis 
or from
sudo modprobe ndiswrapper again.

Moving onto step 5, I ran:

dmesg | grep -e ndis -e wlan
This returned 2 lines only, no errors:

[  507.517874] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  508.060642] usbcore: registered new interface driver ndiswrapper

Not knowing where to go from here, I unsintalled Ndiswrapper and tried reinstalling again from source as per step 7. Ndiswrapper was removed successfully. However I cannot get the new package to install. In fact I can't get anything to install from terminal. I always get a series of errors. In the case of ndiswrapper, I get the following output from *make install:*

make -C driver install
make[1]: Entering directory `/home/lewis/Downloads/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.35-25-generic M=/home/lewis/Downloads/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/lewis/Downloads/ndiswrapper-1.56/driver/wrapndis.o
/home/lewis/Downloads/ndiswrapper-1.56/driver/wrapndis.c: In function ‘set_multicast_list’:
/home/lewis/Downloads/ndiswrapper-1.56/driver/wrapndis.c:953: error: ‘struct net_device’ has no member named ‘mc_count’
/home/lewis/Downloads/ndiswrapper-1.56/driver/wrapndis.c:956: error: ‘struct net_device’ has no member named ‘mc_count’
/home/lewis/Downloads/ndiswrapper-1.56/driver/wrapndis.c:960: error: ‘struct net_device’ has no member named ‘mc_count’
/home/lewis/Downloads/ndiswrapper-1.56/driver/wrapndis.c:960: warning: type defaults to ‘int’ in declaration of ‘_min2’
/home/lewis/Downloads/ndiswrapper-1.56/driver/wrapndis.c:960: error: ‘struct net_device’ has no member named ‘mc_count’
/home/lewis/Downloads/ndiswrapper-1.56/driver/wrapndis.c:967: error: ‘struct net_device’ has no member named ‘mc_list’
/home/lewis/Downloads/ndiswrapper-1.56/driver/wrapndis.c:968: error: dereferencing pointer to incomplete type
/home/lewis/Downloads/ndiswrapper-1.56/driver/wrapndis.c:969: error: dereferencing pointer to incomplete type
/home/lewis/Downloads/ndiswrapper-1.56/driver/wrapndis.c:971: error: dereferencing pointer to incomplete type
make[3]: *** [/home/lewis/Downloads/ndiswrapper-1.56/driver/wrapndis.o] Error 1
make[2]: *** [_module_/home/lewis/Downloads/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/lewis/Downloads/ndiswrapper-1.56/driver'
make: *** [install] Error 2

I have no idea where to go from here I'm afraid! I think it was somewhere close before I removed Ndiswrapper and tried again to install from source - but as I say I think this problem runs a bit deeper as I can't get anything to make from source. 

Please help!! :confused:

Thanks.

---

### Post by PRC09 on 2011-02-12
I have the same card and I believe if you had gone to System > Administration > Additional Drivers the driver should have been there to activate.....

---

### Post by PRC09 on 2011-02-12
Edit:   My card is version 1.2 so not sure if it will make a difference......

---

### Post by Fujiwara86 on 2011-02-13
Thanks for your response PRC09. That does make sense! I will try that once I get Ndiswrapper installed again...but can anyone shed any light on my installation problems using the terminal?

Cheers!

---

### Post by dmizer on 2011-02-13
We need to know the chipset of your card. Please post the output of:
```
lshw -C network
```

---

### Post by Fujiwara86 on 2011-02-13
Output as requested is:

 *-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=0
       resources: memory:d4000000-d4001fff

---

### Post by dmizer on 2011-02-13
This is your chipset: BCM4318

There is a sticky at the top of this forum for how to make your card work. Here is a direct link: [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

Before you look at that link, you should uninstall ndiswrapper.

---

### Post by Fujiwara86 on 2011-02-15
Thanks again for your responses. I uninstalled Ndiswrapper and followed the solution in the sticky as suggested. However I get the following error on package installation:

E: firmware-b43-lpphy-installer: subprocess installed post-installation script returned error exit status 1

Wireless still isn't working and response to lshw -C Network hasn't changed.

Still stuck for ideas I'm afraid!

---

### Post by dmizer on 2011-02-15
Connect to the internet via a wired LAN, and try this:

```
sudo apt-get install b43-fwcutter
```

---

### Post by Fujiwara86 on 2011-02-15
b43-cutter was already installed.

I also tried removing all the b43 stuff and installing the Broadcom STA driver. But when I goto System > Administration > Additional Drivers, the list is empty. Still no change to lshw -C Network output.

---

### Post by dmizer on 2011-02-15
Ok, try uninstalling b43-fwcutter then try installing firmware-b43-lpphy-installer

---

### Post by Fujiwara86 on 2011-02-15
> **dmizer said:**
> Ok, try uninstalling b43-fwcutter then try installing firmware-b43-lpphy-installer


Ok I get the same error as above. It seems Package Manager won't let me install firmware-b43-lpphy-installer without also installing b43-fwcutter.

---

### Post by dmizer on 2011-02-15
Interesting.

I've been reading a lot about your card. Try this (start at step 5): [http://ubuntuforums.org/showpost.php?p=10395026&postcount=89](http://ubuntuforums.org/showpost.php?p=10395026&postcount=89)

---

### Post by billplowman on 2011-02-15
Having the same problem with a Dell laptop. Once I installed NDISWRAPPERS, I had no problem getting the Linksys card to work in a Panasonic laptop. But, once I moved it to the Dell, I'm getting the same symptoms as you. I'll keep following your thread and let you know if I figure anything out.

---

### Post by Fujiwara86 on 2011-02-15
Thanks for your continued input folks, I don't mean to be a pain in the ***.

I checked out that forum link but I don't understand the meaning of pool/main/b/b43-fwcutter - it's definitely not a location I can find  on my computer!

---

### Post by bkratz on 2011-02-15
I believe that location is actually on the installation disk.

---

### Post by Fujiwara86 on 2011-02-15
> **bkratz said:**
> I believe that location is actually on the installation disk.

Gotcha, thanks!

Ok, followed instructions for Step 5 as suggested. Trying to install from disc, b43-fwcutter popped up as already installed. So I downloaded the links and ran the commands, this extracted a load of stuff with no errors. But still no wifi, still an unclaimed network and still nothing appearing in "additional drivers". Tried restarting, but again no change.

---

### Post by billplowman on 2011-02-16
THIS WORKED! (for me at least)
 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
 
The instructions begin about halfway down the page under "Installing b43 drivers"
 
I followed these exactly as they are written and SUCCESS!
 
Good luck!

---

### Post by Fujiwara86 on 2011-02-19
Thanks for all your help folks, finally got this sussed.

Last resort - reinstalled Ubuntu from scratch, but this time with the card plugged in first. Drivers appeared in the "additional drivers" window right away, enabled and wireless now working! Yes!:D

---

