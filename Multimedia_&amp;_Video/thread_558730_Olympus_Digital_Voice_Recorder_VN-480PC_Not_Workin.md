---
title: "Olympus Digital Voice Recorder VN-480PC Not Working"
date: 2007-09-24
forum: Multimedia &amp; Video
---

### Post by onlineapps on 2007-09-24
Any idea on how to use my Olympus Digital Voice Recorder VN-480PC with Kubuntu Feisty?  It's a USB recorder that works fine on Windows, but not on Linux.

---

### Post by sammermpc on 2007-09-25
I've got an Olympus VN-960PC.  I've been searching around, it seems that Olympus provides no support, and I have yet to find anyone who has managed it:

What recourse do we have with an unsupported device?  

As astonishing as it is, I'm so used to everything working so well with ubuntu, I entirely forgot that linux is traditionally plagues with this sort of problem.  Is there a way to make/find a custom module to grab the files off the player?  Unfortunately, it doesn't mount like a flash drive, or anything like that.

---

### Post by sammermpc on 2007-11-13
I guess, none recourse whatsoever then.  Any thoughts?

---

### Post by detroit/zero on 2007-12-13
I just got an Olympus VN-3100PC recorder, and I have the same problem. Neither my Feisty machine nor my Gutsy machine will detect and mount the recorder when connected on the USB port.

Anybody else have any ideas? I'd hate to have to deal with Vista or XP for a simple task like importing audio files from a recorder.

---

### Post by emanuelgreisen on 2008-01-09
I found this one, and it worked (you have to run the little app as root to read the wav files....)

[http://www.qbik.ch/usb/devices/showdr.php?id=286](http://www.qbik.ch/usb/devices/showdr.php?id=286)

---

### Post by aonegodman on 2008-04-25
> **emanuelgreisen said:**
> I found this one, and it worked (you have to run the little app as root to read the wav files....)



OK, I D/L'd the driver and installed ok. My VN-960PC is listed when I run my "USB Devices" as USB(3). Now my question is please explain your last comment -

(you have to run the little app as root to read the wave files . . .')   what is command structure???

How do I get files off of VC?   Normally under Windows they d'l to a folder and I use Audacity to then grab the wav files and edit to MP3's.

Thanks!  :)

---

### Post by aonegodman on 2008-04-25
Alright I've figured out the basic command line structure EXCEPT how to designate the <folder> option?

I've tried the following to no effect:

sudo odvr -d /home/username/audio
sudo odvr -d ./home/username/audio
sudo odvr -d /username/audio

and so forth . . .   ](*,)   please help    Thanks.


For other readers:   In Terminal enter
```


sudo odvr -h

```


This will give the command structure to use the prog.

---

