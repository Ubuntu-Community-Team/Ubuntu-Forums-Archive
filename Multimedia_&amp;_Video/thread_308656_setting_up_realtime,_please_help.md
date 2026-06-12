---
title: "setting up realtime, please help"
date: 2006-11-28
forum: Multimedia &amp; Video
---

### Post by falkenberg_cph on 2006-11-28
Hi
I had some problems setting up realtime.
1. The [howto](https://help.ubuntu.com/community/HowToVanillaKernelWithRealtimePreemption) says i shouldnt be using 2.6.16.x, i guess that goes for 2.6.18.x as well.
But on kernel.org, there is only a 2.6.18.3, is this ok to use? Where are the older editions?

2. I tried going with the 2.6.18.3 and i soon had problems:
 > mv linux linux.old
 ln -s linux-2.6.16-rt26/ linux
No folder called linux.old, so i created one.
next. no folder called linux?
What am i doing wrong?

Hope you can help
/Carsten

---

### Post by falkenberg_cph on 2006-11-28
Doh. problem no. 1 is solved. Of cause i didnt have to find it. I only had to write:
> wget [http://kernel.org/pub/linux/kernel/v2.6/](http://kernel.org/pub/linux/kernel/v2.6/)**linux-2.6.18.tar.bz2**

---

### Post by falkenberg_cph on 2006-11-28
Ok. here is my problem:

cd linux/

No such folder?

---

### Post by falkenberg_cph on 2006-11-28
skipped the linux.old part. created a linux folder and did the linking.

Now this comes up:
> 
The next patch would delete the file Documentation/hrtimers.txt,
which does not exist!  Assume -R? [n] y
The text leading up to this was:
--------------------------
|Index: linux/Documentation/kernel-parameters.txt
|===================================================================
|--- linux.orig/Documentation/kernel-parameters.txt
|+++ linux/Documentation/kernel-parameters.txt
--------------------------
File to patch: linux-2.6.18
linux-2.6.18: No such file or directory
Skip this patch? [y] n
File to patch: linux-2.6.18-rt7
linux-2.6.18-rt7: No such file or directory
Skip this patch? [y] n
File to patch: 


What is this, its not part of the howto :confused: :-?

---

### Post by falkenberg_cph on 2006-11-29
Please anyone. I spend the whole evening yesterday looking for an answer.
Is it because 2.6.18 is no good for realtime, or what?

/Carsten

---

### Post by luneo on 2006-11-29
I have compiled a realtime linux kernel... just go to [http://luneo.zendurl.com](http://luneo.zendurl.com) ... and download it...
it is based on the ubuntu generic kernel configuration.... plus realtime...

---

### Post by falkenberg_cph on 2006-11-30
Why is that link not a sticky? it was so easy.

But. I do have some questions:
1. I lost my wlan. it says: SIOCGIFFLAGS-error: No such device.
What can i do about that?

2. How can i make sure i really have realtime. Because Frankly theres no real difference from now and before.
Using ZynAddSubFX for testing my Lexicon Omega. Using the default instrument, i can play ok with these settings:
Frames: 64
Sampple Rate: 48000
Periods: 4
Port: 128
Timeout: 5000
Input: 4
Output: 2

If however, i try using the plucked wah instrument. I get loads of Xruns.
My Latency is 5.33, and when i see the result others are getting, i think something must be wrong with my setup.

But thanks for the link
/Carsten

[EDIT]: tried some different stuff:
1. uname -r tells me the kernel is correct 2.6.18-rt7
2. lspci show my wireless card (Broadcom BCM4306 ... im pretty sure i used to have 4318 )
3. sudo modprobe ndiswrapper:  gives me; FATAL: Module ndiswrapper not found.
4. modinfo ndiswrapper: gives me; modinfo: could not find module ndiswrapper
5. tried reinstalling all 4 ndiswrapper packages, same result.

---

### Post by luneo on 2006-11-30
The thing is that ndiswrapper was compiled for the ubuntu kernel... I try to compile one for my kernel... and for the Xruns... you have to make other changes... not just the kernel... you have to set some pam permissons... I will make a post on my site teaching it...

---

### Post by falkenberg_cph on 2006-12-01
Great thanks. Cant wait :) 

/Carsten

---

