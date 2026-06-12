---
title: "K9Copy Crashing"
date: 2009-12-21
forum: Multimedia Software
---

### Post by dewmanstl on 2009-12-21
Hello, 
I am trying to use k9copy but the for some reason when I use the k9copy assistant it crashes out. I created a bug report but (been a few days and no response yet) so I thought I would ask here. the bug report is here.

```
https://bugs.launchpad.net/bugs/498519
```Has anyone see this before? Or point me in the right direction?

When I use the application without the assistant, it works fine. It just crashes with the assistant.

---

### Post by saechen on 2009-12-21
Funny I get the exact opposite. Can use the assistant, but when use the main it crashes. Either way... BUMP :-)

---

### Post by saechen on 2009-12-21
The program will start fine, but when I try and open the DVD it errors:

Application: k9copy (k9copy), signal: Segmentation fault
[Current thread is 1 (Thread 0xb784b700 (LWP 2009))]

Thread 2 (Thread 0xb61fcb70 (LWP 2012)):
#0  0x00223422 in __kernel_vsyscall ()
#1  0x01ba1981 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0x019c6af5 in ?? () from /usr/lib/libQtCore.so.4
#3  0x018f7e32 in ?? () from /usr/lib/libQtCore.so.4
#4  0x0034f80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0x01ba87ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb784b700 (LWP 2009)):
[KCrash Handler]
#6  0x00000000 in ?? ()
#7  0x08068d2b in _start ()

---

### Post by saechen on 2009-12-21
Only seems to happen when I used encrypted DVDs. A previously made open backup has no problem. So would this point to something in one of the multimedia drivers? 

Dewmanstl do you see the same behaviour?

---

### Post by saechen on 2009-12-21
Just got it to work by installing every DVD backup program I could find (DeVeDe, dvdRip, Dvd95) and then reinstalling libdvdcss with these instructions: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs).  It will now open a encrypted DVD next will be to see if can make a backup.

---

### Post by dewmanstl on 2009-12-21
You know, there was a couple of times when it did work correctly. It seemed to be when I did a power down of the box....Not sure if that would cause any thing strange or not. I found a post somewhere to rename my kde folder and try it again(so kde could rebuild it,not, that didnt seem to work. 

Strange, I just inserted a un-encrypted dvd and it got past the point of where it crashed. I will make a note of this in the bug report right now.

---

### Post by dewmanstl on 2009-12-21
ok that is just strange. I un-installed libdvdcss and reinstalled it along side with k9copy and it got past the point of crashing.

---

### Post by saechen on 2009-12-21
Successfully made a backup!

---

