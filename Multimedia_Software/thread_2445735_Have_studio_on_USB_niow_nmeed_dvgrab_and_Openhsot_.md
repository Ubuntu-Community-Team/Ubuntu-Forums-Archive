---
title: "Have studio on USB niow nmeed dvgrab and Openhsot but how to load ?"
date: 2020-06-18
forum: Multimedia Software
---

### Post by ozstar on 2020-06-18
Hi,

I have Studio on a USB and it has booted and looks great.

I now need to get dvgrab and Openshot loaded on to the stick.

How do I do that please.

Thanks

oz

---

### Post by CelticWarrior on 2020-06-19
If it's a live session anything you install won't survive a reboot.
If it's a normal installation then any software is installed in the exact same way as in a system running from the internal drive.

---

### Post by sudodus on 2020-06-19
There is an alternative between those described by CelticWarrior, a **persistent live** drive, which is easier to install than a fully installed system and more portable between computers. However **an installed system in a fast USB drive** is more stable and easy to manage, once it is installed.

If you want to test a persistent live drive, I suggest that you use [mkusb](https://help.ubuntu.com/community/mkusb) to create it.

---

### Post by ozstar on 2020-06-19
Thanks.  I have a 32Gb USB and it is fine now with Openshot working.

Only thing now is I can't get dvgrab to find the camera. It gives me that error and I am not sure where to go now. I have a TI 1394 card in and connect with a good dv cable to the cam. Tried both cams as a matter of fact, A Sony and a Panasonic.
How can I see if the 1394 is in fact showing?  In MS it is in Device Manager.

---

### Post by ozstar on 2020-06-20
Not sure why, but after a few cold boots, dvgrab now works.. or did.  Now I get this message..

u```
buntu-studio@ubuntu-studio:~$ dvgrab
Found AV/C device with GUID 0x0080458011443010
libiec61883 error: Failed to get channels available.
Waiting for DV...
Capture Started
>>> Error writing frame!
"dvgrab-008.dv":     0.00 MiB 0 frames timecode 00:00:15.24 date 2005.05.04 19:51:08
Capture Stopped
terminate  called after throwing an instance of  'std::__cxx11::basic_string<char, std::char_traits<char>,  std::allocator<char> >'
Aborted (core dumped)
```
 
It then goes back to the terminal $

Any ideas please ?

---

### Post by sudodus on 2020-06-20
Several years ago I borrowed a camcorder using dv, and I had big problems. Finally I had it working long enough to get the footage into the computer in a way, that could be processed further. I never learned how to grab dv. Instead I bought an own camera. that produced files on memory cards, and those files are much easier to manage.

I think the support for dv in linux was flaky, and it might still be flaky. It is probably better in MacOS, at least in older versions. I'm sorry, but I am not the right person to help you with dvgrab.

Maybe the best option is to borrow some equipment made by Apple for this task.

---

### Post by ozstar on 2020-06-20
Many thanks for your help, I have been on computers since mainframes in the mid 70's and every now and then due to the growth of technology, it drives me to distraction ! &#55358;&#56631;*&#9794;&#65039;

This is yet another time. Capture worked with XP and I think with 7 but 10 seems to have put a stake into the heart of easy capturing. I hoped that Linux would be fine but it seems there are still problems to face. I like the Studio package, it is really well set out and Openshot looks good too. I have 2 DV cams, a Sony and a Panasonic and it seems so random that it picks them up.  I mostly get a Can't see camera errors.  I would like to know what that message actually means and what I have to do to fix it. Thanks again.

---

