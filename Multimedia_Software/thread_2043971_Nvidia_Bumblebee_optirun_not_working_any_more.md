---
title: "Nvidia Bumblebee optirun not working any more"
date: 2012-08-17
forum: Multimedia Software
---

### Post by Marric on 2012-08-17
If bumblebee was working fine up to now and you get this error message when running optirun```

[ERROR]Cannot access secondary GPU - error: Could not load GPU driver
[ERROR]Aborting because fallback start is disabled.
```then edit the bumblebee configuration file
```
sudo gedit /etc/bumblebee/bumblebee.conf
```change 

Driver= 
   to    
Driver=nvidia

and

KernelDriver=nvidia-current 
to    
KernelDriver=nvidia

---

### Post by metalf8801 on 2012-08-20
This didn't work for me until after I rebooted... I know that might be an obvious step for most people but I didn't think of it right away

---

### Post by Marric on 2012-08-20
you can restart the bumblebee daemon in order to assume the changes
```
sudo restart bumblebeed
```

---

### Post by obviator on 2012-08-23
Awesome - this worked great for me on Ubuntu 12.04. I've got an Asus laptop with optimus, which randomly stopped working after I upgraded the Nvidia drivers. This helped me get up & running again. Thanks!

---

### Post by jmath on 2012-10-13
> **Marric said:**
> you can restart the bumblebee daemon in order to assume the changes
```
sudo restart bumblebeed
```

I have tried this but I've got the following error:

restart: Unknown instance:

Any clue?

---

### Post by Holmen on 2012-10-20
Thank you! This drived me crazy.

Works in Ubuntu 12.10.

---

### Post by herczigem on 2012-10-29
> **Marric said:**
> If bumblebee was working fine up to now and you get this error message when running optirun```

[ERROR]Cannot access secondary GPU - error: Could not load GPU driver
[ERROR]Aborting because fallback start is disabled.
```then edit the bumblebee configuration file
```
sudo gedit /etc/bumblebee/bumblebee.conf
```change 

Driver= 
   to    
Driver=nvidia

and

KernelDriver=nvidia-current 
to    
KernelDriver=nvidia

Hello! I modify same the bumblebbe.conf file, and restart the system, but it doesn't work.

This message give me the system:
[   96.155131] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[   96.155208] [ERROR]Could not connect to bumblebee daemon - is it running?

---

### Post by Tieuc on 2012-12-25
Hi everybody!

I came back in the LInux World yesterday  with Ubuntu, I installed Bumblebee right after and I had the same message than Marric, then I changed the "driver=" and the "KernelDriver=", but know I've got the same problem than herczigem!
Do you have a solution?


Just for information I installed the 12.10 version, and a couple of months ago, with the same laptop, but with the 12.04 everthing was fine.
Thanks

Matthieu

12/25: I installed all the last update! And evrything is fine! So my problem is solved! Merry Christmas!

---

### Post by SabriCan on 2013-02-05
> **Tieuc said:**
> Hi everybody!

I came back in the LInux World yesterday  with Ubuntu, I installed Bumblebee right after and I had the same message than Marric, then I changed the "driver=" and the "KernelDriver=", but know I've got the same problem than herczigem!
Do you have a solution?


Just for information I installed the 12.10 version, and a couple of months ago, with the same laptop, but with the 12.04 everthing was fine.
Thanks

Matthieu

12/25: I installed all the last update! And evrything is fine! So my problem is solved! Merry Christmas!

I did the same with Tieuc including last updates. But I still have the same problem than herczigem.
```
[ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[ERROR]Could not connect to bumblebee daemon - is it running?

```

And sudo restart bumblebeed doesn't work for me. I got:
```
restart: Unknown instance: 
```

I changed "KernelDriver=nvidia-current" to "KernelDriver=nvidia" but I found nvidia-current package when I searched in synaptic package manager. I'm not sure what driver I'm using. I run this lastly: ```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates 
```

EDIT: I installed  Ubuntu 12.10 and bumblebee works fine now. Thanks..

---

### Post by metalf8801 on 2013-02-28
Today I'm running Ubuntu Studio 12.04 with the 3.2.0-38-lowlatency-pae kernel and I wasn't able to run anything using optirun without getting an error message that included but was not limited to the following: Could not connect to bumblebee daemon 
I was able to resolve this by going back into /etc/bumblebee/bumblebee.conf and changing 

KernelDriver=nvidia 
back to what it was originally 
KernelDriver=nvidia-current 

and then restarting my laptop 

Also I did NOT change left Driver=nvidia back to Drive=

---

### Post by tilosag on 2013-12-14
> **metalf8801 said:**
> Today I'm running Ubuntu Studio 12.04 with the 3.2.0-38-lowlatency-pae kernel and I wasn't able to run anything using optirun without getting an error message that included but was not limited to the following: Could not connect to bumblebee daemon I was able to resolve this by going back into /etc/bumblebee/bumblebee.conf and changing KernelDriver=nvidia back to what it was originally KernelDriver=nvidia-current and then restarting my laptop Also I did NOT change left Driver=nvidia back to Drive=Yes Yes Yes ! ! !That worked for me too! Running Debian Jessie. ASUS U36JCintegrated Intel graphics cardand geforce 310mUsing nvidia PROPERTIARY drivers (not noveau)!Driver=nvidiaKernelDriver=nvidia-currentMy working config:> # Configuration file for Bumblebee. Values should **not** be put between quotes## Server options. Any change made in this section will need a server restart# to take effect.[bumblebeed]# The secondary Xorg server DISPLAY numberVirtualDisplay=:8# Should the unused Xorg server be kept running? Set this to true if waiting# for X to be ready is too long and don't need power management at all.KeepUnusedXServer=false# The name of the Bumbleblee server group name (GID name)ServerGroup=bumblebee# Card power state at exit. Set to false if the card shoud be ON when Bumblebee# server exits.TurnCardOffAtExit=false# The default behavior of '-f' option on optirun. If set to "true", '-f' will# be ignored.NoEcoModeOverride=false# The Driver used by Bumblebee server. If this value is not set (or empty),# auto-detection is performed. The available drivers are nvidia and nouveau# (See also the driver-specific sections below)Driver=# Directory with a dummy config file to pass as a -configdir to secondary XXorgConfDir=/etc/bumblebee/xorg.conf.d## Client options. Will take effect on the next optirun executed.[optirun]# Acceleration/ rendering bridge, possible values are auto, virtualgl and# primus.Bridge=auto# The method used for VirtualGL to transport frames between X servers.# Possible values are proxy, jpeg, rgb, xv and yuv.VGLTransport=proxy# List of paths which are searched for the primus libGL.so.1 when using# the primus bridgePrimusLibraryPath=/usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus:/usr/lib/primus:/usr/lib32/primus# Should the program run under optirun even if Bumblebee server or nvidia card# is not available?AllowFallbackToIGC=false# Driver-specific settings are grouped under [driver-NAME]. The sections are# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-# detection resolves to NAME).# PMMethod: method to use for saving power by disabling the nvidia card, valid# values are: auto - automatically detect which PM method to use#         bbswitch - new in BB 3, recommended if available#       switcheroo - vga_switcheroo method, use at your own risk#             none - disable PM completely# [https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods##](https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods##) Section with nvidia driver specific options, only parsed if Driver=nvidia[driver-nvidia]# Module name to load, defaults to Driver if empty or unsetKernelDriver=nvidia-currentPMMethod=auto# colon-separated path to the nvidia librariesLibraryPath=/usr/lib/x86_64-linux-gnu/nvidia:/usr/lib/i386-linux-gnu/nvidia:/usr/lib/nvidia# comma-separated path of the directory containing nvidia_drv.so and the# default Xorg modules pathXorgModulePath=/usr/lib/nvidia,/usr/lib/xorg/modulesXorgConfFile=/etc/bumblebee/xorg.conf.nvidia## Section with nouveau driver specific options, only parsed if Driver=nouveau[driver-nouveau]KernelDriver=nouveauPMMethod=autoXorgConfFile=/etc/bumblebee/xorg.conf.nouveau

---

