---
title: "gtkpod blank and ipod not working on any music player"
date: 2012-02-01
forum: Multimedia Software
---

### Post by supermeow on 2012-02-01
hi, common problem, but a hard one to solve: ipod doesn't work. i have tried everything and anything... 

the ipod appears on my screen (actually on my left dock as: "ipod" and "documents on ipod" - both have an ipod icon, so i assume the system reads them correctly)  

However, there is just now way to put music or read music or sync it with any of these programs:

**BANSHEE**: only reads the documents in my ipod, can't seem to load the ipod, let alone transfer any music or sync. **no error message**.

**CLEMENTINE**: reads the ipod but doesn't transfer any music), **error message: Unsupported checksum type**

**AMAROK**: (doesn't read it at all)

**GTKPOD**: a complete failure..doesn't even open, it starts opening the program, asks me to select the ipod (model xc540 in my case) then it goes blank and stays like that. 
[B]error message 1: Import Repository Errors. Errors created during repository import
error message 2: Newly mounted iPod at '/home/supermiao/.gvfs/MeowPod Touch' appears to be already loaded![/B]

**RHYTHMBOX:** doesn't transfer any music on the device. no error message. it starts syncing the ipod and it stays like that forever. the cpu/fan starts going crazy if i unplug the ipd, no music on it.


This is what I am using:
ipod touch 4g, with newly installed 5.0.1 OS (unjailbroken yet)
ubuntu 11.10 - 64bit
kernel 3.0.15
libimobiledevice 2 and all related libraries (just updated)
updated ifuse
all plugins for music players are updated and active.

i installed and update any possible library related to ipod touch, read all the advice i could handle... but nothing works.

tricks like
"idevicepair unpair && idevicepair pair"

do not work as well

i am really lost. 
any suggestion?


thx a million

---

### Post by wolfen69 on 2012-02-01
> **supermeow said:**
> 
This is what I am using:
ipod touch 4g, with **newly installed 5.0.1 OS** (unjailbroken yet)

That is probably the problem right there. Apple goes out of their way to make it difficult for linux users. The linux devs need time to catch up to the latest releases of iOS. There's really nothing you can do about it. 

Apple will not support linux in any way, it's up to the linux community to figure it out.

The only other thing I can suggest, is to install windows in virtualbox.

---

