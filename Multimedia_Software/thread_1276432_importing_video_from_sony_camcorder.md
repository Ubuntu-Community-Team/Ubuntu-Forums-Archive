---
title: "importing video from sony camcorder"
date: 2009-09-27
forum: Multimedia Software
---

### Post by LowFidelity on 2009-09-27
hi, I've been looking around for a very, very long time to see how I can import video from my sony dcr-trv320 camcorder through firewire/raw1394. I have yielded no successful results.

I'm running ubuntu studio, and I've enabled raw1394 access. My camcorder is on and it says it's connected (DV in). however, when I opened up kino and tried capturing it said that I couldn't.

So I enabled raw1394 on my account through chmod and tried again. This time it says "no av/c compliant cam connected or not switched on?" ignoring that warning I tried clicking capture and pressed the play button on my camcorder, but to no avail. Nothing happened.

I've tried dvgrab and get "Error: no camera exists".

I also tried enabling dv1394, ohci1394, and video1394 but nothing has worked.

I've tried running kino as root, too, but that didn't make a difference.

I've also tried transferring through cinelerra, but that didn't make a difference either.

The cable has been tested on another computer and is working. The two ieee 1394 ports are built into the motherboard, which is brand new.

please help. I have been trying to solve this problem by looking at countless other threads for almost a year now, and none of their solutions have helped me.

---

### Post by LowFidelity on 2009-09-28
bump? I still haven't found any solution.

---

### Post by bumanie on 2009-09-28
Follow [this]("http://ubuntuforums.org/showthread.php?t=966472&highlight=bumanie"). It will work as root. I changed ownership and as far as I can tell, without having tried more than a few seconds of capture, it seems to work without root privileges following the ownership change.

---

### Post by LowFidelity on 2009-09-29
> **bumanie said:**
> Follow [this]("http://ubuntuforums.org/showthread.php?t=966472&highlight=bumanie"). It will work as root. I changed ownership and as far as I can tell, without having tried more than a few seconds of capture, it seems to work without root privileges following the ownership change.

This isn't my problem. I've already enabled access to raw1394 for myself, both through studio and chmod. 

"no av/c compliant cam connected or not switched on?"

I receive this error message regardless of whether I run kino as root or as a user.

---

### Post by LowFidelity on 2009-10-01
Hi. I still haven't found any solution yet.

---

### Post by lisati on 2009-10-01
Does [this]("http://ubuntuforums.org/showpost.php?p=7983141&postcount=6") help? (Note: it's "sudo", not "studio")

---

### Post by LowFidelity on 2009-10-01
> **lisati said:**
> Does [this]("http://ubuntuforums.org/showpost.php?p=7983141&postcount=6") help? (Note: it's "sudo", not "studio")

no, I meant "studio, as in I have installed on my computer "ubuntu studio".

All those packages are already and have been installed on my computer. That didn't help me...

---

### Post by LowFidelity on 2009-10-04
hello, still no solution has been found

---

### Post by LowFidelity on 2009-10-07
Still looking, thanks

---

### Post by LowFidelity on 2009-10-11
Bump!!! I need help!! Please!!

---

### Post by LowFidelity on 2009-10-13
still looking

---

### Post by LowFidelity on 2009-10-13
I posted this thread two weeks ago, still no solution

---

### Post by LowFidelity on 2009-10-25
no luck yet

---

### Post by LowFidelity on 2009-10-26
hopefully I'll have more luck in three days... heh...

---

### Post by tomdkat on 2009-11-20
I've been playing with a JVC MiniDV camcorder and Ubuntu 9.10 (64-bit) today and I had problems, which were mainly permissions related.

In your case, I would try this:  Reboot the system WITHOUT the camcorder connected.  Then, open a terminal window and issue the "dmesg | grep 1394" command and see what kind of output you get.  Then, connect the camcorder and turn it on and re-issue the "dmesg | grep 1394" command and see if you get any new output.

The idea being to use the "dmesg" output to see if the udev is detecting the camcorder and loading the IEEE1394 support modules appropriately.

Peace...

---

