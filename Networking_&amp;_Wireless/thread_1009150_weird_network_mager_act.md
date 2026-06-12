---
title: "weird network mager act"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by omi6541 on 2008-12-12
Hi!

I've got a Dell Studio 15 which has Broadcom 4310 wireless card.
I recently installed Ubuntu 8.10 on it and facing problems with setting up wireless.

well, I searched a few times. used ndiswrapper n stuff already but this thing is little different. 
I mean when I use Ubuntu for the very first time after clean installation, wireless works fine. i mean when I get to desktop, It already shows wireless networks available and connects to any of them, internet works fine.. but dunno what the heck happens when I reboot. It simply stops. After reboot lspci shows its 4312 when its actually 4310.

I tried enabling restricted drivers and nothing helped.
Then I used ndiswrapper. went through whole process and installed the driver. again it started working. but only 1 time.
on next reboot there was no network manager icon in system tray. It simply doesn't load ! If I see processes, it shows it as sleeping.

next- when I enable restricted drivers once again, network manager shows up instantly but wireless is disabled.If I restart when restricted drivers are enabled and network manager is shown, it again doesn't load on next reboot. again If I disable them, it shows up instantly. 

I mean.. huh ? 

any solution over this ? I really don't want to re-install it one more time. Every other thing has been setup and its working absolutely fine.. dunno whats wrong with network :(

help ! please.. 

Thanks

---

### Post by iponeverything on 2008-12-12
word on the street is that this might work:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Don't forget to grab the readme.

---

### Post by Ayuthia on 2008-12-12
And here is the link to the patch that makes it compile in 8.10:
[http://jaux.net/2008/10/14/patch-to-broadcom-80211-linux-sta-driver-for-kernel-2627/](http://jaux.net/2008/10/14/patch-to-broadcom-80211-linux-sta-driver-for-kernel-2627/)

It will cause ssh and some secure remote connections to not work (such as connecting to mysql from the network to use mythtv).  I think that the patches that were applied in Ubuntu fixed these issues, but it broke a portion of the 4312 cards.

By the way, your card is actually a 4312 card not a 4310 card.  It was initially listed incorrectly because it really does not have anything to do with USB.  That is why the name was corrected.  If you type lspci -nn, you will see that it will always be 14e4:4315.

---

### Post by omi6541 on 2008-12-12
umm.. I'm little confused here..
that patch thigi... what am I supposed to do ?
copy all text into a file and save it. then use
```
sudo patch -p1 -E filename
```

nah ? [i'm in the same directory as patch file]

after hitting ^ command cursor moves to new line on terminal and keeps blinking. is this normal ?

(and it showing 14e4:4315 .. didnt know that. Thanks. Now I has problems with 4312)

---

### Post by Ayuthia on 2008-12-12
You need to be in the directory where the wl source code is located.  You save the patch file in there.  Since you are now in that directory (It should have Makefile in there), you will need to do the following:
```
patch -p1 -E < path_to_patch/hybrid_wl_5.10.27.6_patch-2.6.27
```
From there you can run the commands to build the file.

---

### Post by omi6541 on 2008-12-13
I tried that and getting errors-

patching file src/wl/sys/wl_iw.c
Hunk #1 FAILED at 931
Hunk #2 FAILED at 944
Hunk #3 FAILED at 952
Hunk #4 FAILED at 970
Hunk #5 FAILED at 978
Hunk #6 FAILED at 989
Hunk #7 FAILED at 1003
Hunk #8 FAILED at 1012
8 out of 8 hunks FAILED -- saving rejects to file src/wl/sys/wl_iw.c.rej

---

### Post by iponeverything on 2008-12-13
grab the already patched source from:

[http://www.cenolan.com/fedora9/broadcom-patched-x86_32-5.10.27.6.tar.gz](http://www.cenolan.com/fedora9/broadcom-patched-x86_32-5.10.27.6.tar.gz)

then follow the instructions from the readme on the broadcom page.

Follow-up with success or failure for the benefit of future generations.
;)

---

### Post by Ayuthia on 2008-12-13
I just noticed a couple of things.  The fedora patched code does not compile in Ubuntu.  The other thing is that Broadcom created another release of their drivers which does not compile in 2.6.27 either. 

I am looking to see what can be done.

---

### Post by omi6541 on 2008-12-13
@iponeverything, I tried that and it finished without any error, followed broadcom readme, again, its not working.

@Ayuthia, 
okay, I'll wait :)

---

### Post by Ayuthia on 2008-12-13
Here is a patch that I created (so it is not official), but it is based on the same patch that was made for the original source.  The patch compiled and worked on my 4311 card.  I have not tested the new changes on the Broadcom version so I am not for sure what changes they have made.

Attached is the patch.  You will need to download the source from:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
Extract the download like the instructions say in the Broadcom site.  Do not compile it yet.

Download the attached patch from this post and place it in the directory where you extracted the Broadcom source (it will be in the same directory as the Makefile).  Extract the hybrid_wl-5.10.27.11_patch-2.6.27.tar.gz:
```
tar -xvvf hybrid_wl-5.10.27.11_patch-2.6.27.tar.gz
```Then apply the patch:
```
patch -p1 -E < hybrid_wl-5.10.27.11_patch-2.6.27
```

Finally compile as normal:
```
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`
```
Just replace <2.6.xx.xx> with the current kernel version (uname -r from the terminal).

Hope this helps.  As I said, this is not the official patch, but one that I created so it has only been tested by me, but it is similar to the patch from before.  If you are not comfortable, you can wait a few days until a patch comes out for this kernel.

---

### Post by omi6541 on 2008-12-13
umm... I'm a sane guy over internet but ... excuse me for this perticular post please..

Ayuthia, YOU ROCK !!!!!!!!!!!!!! THANKS ALOT FOR HELP :D

HOLY COW ! HOLY JESUS !! HOLY GOD !!! I'M ON WIRELESS RIGHT NOW :D :guitar:


Thanks alot Ayuthia :) hey iuponeverything, thanks :)

cya !

---

### Post by jron on 2008-12-14
I'm working on this too. I'll post my results shortly (I hope!).

results:
[http://ubuntuforums.org/showthread.php?t=1010751](http://ubuntuforums.org/showthread.php?t=1010751)

---

### Post by cenwesi on 2008-12-16
when i try to apply this patch, it is asking for "File to patch"
Can you please tell me how to apply this patch correctly??

> **Ayuthia said:**
> Here is a patch that I created (so it is not official), but it is based on the same patch that was made for the original source.  The patch compiled and worked on my 4311 card.  I have not tested the new changes on the Broadcom version so I am not for sure what changes they have made.

Attached is the patch.  You will need to download the source from:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
Extract the download like the instructions say in the Broadcom site.  Do not compile it yet.

Download the attached patch from this post and place it in the directory where you extracted the Broadcom source (it will be in the same directory as the Makefile).  Extract the hybrid_wl-5.10.27.11_patch-2.6.27.tar.gz:
```
tar -xvvf hybrid_wl-5.10.27.11_patch-2.6.27.tar.gz
```Then apply the patch:
```
patch -p1 -E < hybrid_wl-5.10.27.11_patch-2.6.27
```

Finally compile as normal:
```
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`
```
Just replace <2.6.xx.xx> with the current kernel version (uname -r from the terminal).

Hope this helps.  As I said, this is not the official patch, but one that I created so it has only been tested by me, but it is similar to the patch from before.  If you are not comfortable, you can wait a few days until a patch comes out for this kernel.

---

### Post by Ayuthia on 2008-12-17
> **cenwesi said:**
> when i try to apply this patch, it is asking for "File to patch"
Can you please tell me how to apply this patch correctly??

It appears that you are not in the correct directory.  I am not for sure about where you placed the Broadcom source code so we will start from the beginning.  Let's  say that you have the hybrid_wl-5.10.27.11_patch-2.6.27.tar.gz file and the hybrid-portsrc-*_5_10_27_11.tar.gz on the Desktop.  You will then need to do the following:

**Step 1: Make a directory to patch and compile the source**
```
cd ~/Desktop
mkdir hybrid
```

**Step 2: Copy the two files (source and patch) into the new directory**
```
cp hybrid-portsrc-*_5_10_27_11.tar.gz hybrid
cp hybrid_wl-5.10.21.11_patch-2.6.27.tar.gz hybrid
```

**Step 3: Go into the new directory and extract the files**
```
cd hybrid
tar -xzf hybrid-portsrc-*_5_10_27_11.tar.gz
tar -xvvf hybrid_wl-5.10.21.11_patch-2.6.27.tar.gz
```

**Step 4: Patch the source**
```
patch -p1 -E < hybrid_wl-5.10.27.11_patch-2.6.27
```

**Step 5: Clean up the source in case there has been prior compiles**
```
make -C /lib/modules/`uname -r`/build M=`pwd` clean
```

**Step 6: Compile the source**
```
make -C /lib/modules/`uname -r`/build M=`pwd`
```

**Step 7: Verify that the wl.ko was created**
```
ls
```
If you see a wl.ko file at the end of all these commands, the module is compiled.  Hope that helps.

---

### Post by cenwesi on 2008-12-29
worked like a charm... just make sure you use the patch on this thread.

ps: i am running kernel 2.6.27.9

---

