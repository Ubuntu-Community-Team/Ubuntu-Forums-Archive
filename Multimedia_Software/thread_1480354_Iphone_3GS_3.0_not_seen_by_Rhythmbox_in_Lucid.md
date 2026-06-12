---
title: "Iphone 3GS 3.0 not seen by Rhythmbox in Lucid"
date: 2010-05-11
forum: Multimedia Software
---

### Post by mhedges48 on 2010-05-11
Hello, I recently upgrading to Lucid in order to get IPhone compatbility (I have the 3GS running 3.0 software). However, my IPhone does not appear in Rhythmbox. Per other threads, I have restarted various times, tried different USB ports, started one and then the other and vice versa, etc., all to no avail. I have removed and reinstalled Rhythmbox, no changes.

There is no IPhone icon in the side pane or other way to access the IPhone in Rhythmbox. Rhythmbox does detect it (but only when the Portable Players: MTP plugin is selected, when this is deselected it doesn't detect it at all). I say it detects it because when I choose "File: Scan Removable Media" the IPhone beeps. The below is the error from terminal:

¨¨¨¨¨¨
user:~$ rhythmbox
Device 0 (VID=05ac and PID=1294) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=05ac and PID=1294) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=05ac and PID=1294) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=05ac and PID=1294) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=05ac and PID=1294) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=05ac and PID=1294) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=05ac and PID=1294) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
LIBMTP PANIC: could not inspect object property descriptions!
LIBMTP PANIC: could not inspect object property descriptions!
LIBMTP PANIC: could not inspect object property descriptions!
¨¨¨¨¨¨

Any ideas on how to fix are greatly appreciated!

thanks

---

### Post by ajayrockrock on 2010-05-13
There's already a bug in libmtp sourceforge bug tracker, and it's also on launchpad for ubuntu:

[https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/546714](https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/546714)

So hopefully it gets fixed as I'd like to be able to sync my iphone too.

---

### Post by mhedges48 on 2010-05-13
thanks ajrockrock.

Out of curiosity, where are you using your IPhone? I am currently in Argentina and have it jailbroken to be able to access the provider here. Wondering if that has anything to do with the problem or not.

---

### Post by ajayrockrock on 2010-05-21
I'm in the US on AT&T and I haven't jail broken my phone.

I did manage to get gtkpod to see my iphone, but rhythm box is still busted.

---

### Post by ajayrockrock on 2010-06-09
I was able to get mine to connect by disabling the "Portable Players - MTP" plugin in rhythmbox.

---

### Post by Jake007g on 2010-06-09
Try using gtkPod, it's what I use on my 3g (3.1.3 Jailbroke)

Rhythmbox seems to take a long time to sync compared to gtkPod.

---

### Post by mhedges48 on 2010-06-12
Thank you all. I have tried disabling MTP and also gtkipod. However, neither works.  Rhythmbox still does not see the IPhone, nor does gtkipod. I wonder if my Iphone is not being mounted correctly. It mounts in Nautilus but as a gphoto2 filesystem (can view pictures with with F-Spot)... I wonder if this is interfering with it mounting correctly for Rhythmbox and gtkipod? 

many thanks

---

### Post by Jake007g on 2010-06-14
> **mhedges48 said:**
> Thank you all. I have tried disabling MTP and also gtkipod. However, neither works.  Rhythmbox still does not see the IPhone, nor does gtkipod. I wonder if my Iphone is not being mounted correctly. It mounts in Nautilus but as a gphoto2 filesystem (can view pictures with with F-Spot)... I wonder if this is interfering with it mounting correctly for Rhythmbox and gtkipod? 

many thanks

Make sure you have the correct libraries installed:

> sudo apt-get install libimobiledevice0 libimobiledevice-utils

---

### Post by mhedges48 on 2010-06-14
Jake007,

Many thanks for your help.  I have those libraries installed so that is not it. I do not get any terminal errors when I run rhythmbox.

I am attaching a screenshot that shows you what Rhythmbox looks like and also gtkpod. Nothing happens when I scan removable media in rhythmbox or try and load ipods in gtkpod.  You can see that Ubuntu is mounting the IPhone though (as a filesystem type gphoto2).

Can you see how your IPhone is mounted?


thanks again!

---

### Post by mondomunchies on 2010-06-19
I may be completely wrong here but when you plug your iphone into your computer you have to unlock it before it is recognized.  I'm sure that's not the issue but ... just in case.

---

### Post by mhedges48 on 2010-06-22
Thank you, but not that.

I think it has something to do with how it is mounted. It only wants to mount as a camera, just showing the IPhone pictures folders...

---

### Post by VinoFuriaRoja on 2010-06-27
Not to hijack your thread or anything, but I am having the same issue with my new Iphone 3GS with the new iOS4 update.  Rhythmbox WILL NOT recognize my iphone whatsoever, but it does recognize my old iphone.  Any help?

---

### Post by bdfam0916 on 2010-07-03
Same problem here. If I plug in my daughter's 3G phone there is no problem. The "iPod Detected" window pops up and I can choose her model, enter a name, and it initializes. With my 3GS, I still get the "iPod Detected" window, by the drop down window to choose the model is grayed out.

---

### Post by danleong on 2010-07-17
Found this thread while having same problem with iPhone 3GS on Fedora 13 (I'm also an occasional Ubuntu user:)

Solution that work for me - upgrade GVFS to 1.6.2

[U]Problem in detail
[/U]iPhone appears in Nautilus and all files visible. Shotwell allows me to copy images from camera for example. But after opening Rhythmbox there's no iPhone device. This worked in Fedora 12

_Solution in detail_
I got frustrated and updated everything I could think of, and then rebooted after each update. Here's my versions that now work:

kernel.x86_64            2.6.33.5-112.fc13
rhythmbox.x86_64     0.12.8-4.fc13
usbmuxd.x86_64        1.0.4-2.fc13
libimobiledevice.x86_64  1.0.2-1.fc13
gvfs.x86_64               1.6.2-1.fc13

Good luck - hope this helps somebody else!

---

### Post by Joan A. on 2010-07-19
> **Jake007g said:**
> Make sure you have the correct libraries installed:

Is it completely necessary to have installed **libimobiledevice-utils**? I hasn't it installed, maybe I deleted this package with deborphan. :-s

---

### Post by Joan A. on 2010-07-19
> **danleong said:**
> Found this thread while having same problem with iPhone 3GS on Fedora 13 (I'm also an occasional Ubuntu user:)

Solution that work for me - upgrade GVFS to 1.6.2

[U]Problem in detail
[/U]iPhone appears in Nautilus and all files visible. Shotwell allows me to copy images from camera for example. But after opening Rhythmbox there's no iPhone device. This worked in Fedora 12

_Solution in detail_
I got frustrated and updated everything I could think of, and then rebooted after each update. Here's my versions that now work:

kernel.x86_64            2.6.33.5-112.fc13
rhythmbox.x86_64     0.12.8-4.fc13
usbmuxd.x86_64        1.0.4-2.fc13
libimobiledevice.x86_64  1.0.2-1.fc13
gvfs.x86_64               1.6.2-1.fc13

Good luck - hope this helps somebody else!

I tried to update the **gvfs** package in my Ubuntu. Unfortunately, it was impossible, as when I try to open the downloaded package it closes quickly without giving me the oportunity to install it. Why it happens? :(

---

### Post by pbateman on 2010-07-25
I was having the same problem, tried just about all that was mentioned here but no luck. 
Funny thing is, i tried a different USB port on the laptop and lo and behold it mounted it properly and i can now see it in rhythmbox...
Just something to think about...

---

### Post by Joan A. on 2010-08-20
The best option to solve it is either to format or to reinstall Ubuntu 10.04. I did it on my laptop and now Iphone (3G) and Rhythmbox are working perfectly.

---

### Post by jdorenbush on 2010-09-10
I think I'm having the same problem.

Ubuntu (Lucid, 10.04) recognizes my iPhone and mounts it. I'm able to browse my iPhone with nautilus as well. BUT I can't see my iPhone inside of Rhythmbox.

---

### Post by Alecatta on 2010-09-14
> **jdorenbush said:**
> I think I'm having the same problem.

Ubuntu (Lucid, 10.04) recognizes my iPhone and mounts it. I'm able to browse my iPhone with nautilus as well. BUT I can't see my iPhone inside of Rhythmbox.

Hi to everybody.
I'm running UBUNTU 10.04 Lucid.

I have just bought a brand new IPOD TOUCH 4G 32G, and it can be seen only as a picture file under f-spot.
No way to see it in Rhythmbox, even in a Live-versione running from CD, that is supposed to be fresh and not messed up by me!
:???:
HELP!!!

---

### Post by Claire Voyant on 2012-11-26
> **pbateman said:**
> I was having the same problem, tried just about all that was mentioned here but no luck. 
Funny thing is, i tried a different USB port on the laptop and lo and behold it mounted it properly and i can now see it in rhythmbox...
Just something to think about...

My iPhone 4s wasn't visible in Rhythmbox but after seeing the quote I switched USB port and the iPhone was visible. Not sure why this works but it has for at least 2 of us.
Ubuntu 12.10

---

### Post by wildmanne39 on 2012-11-26
Old thread closed.

---

