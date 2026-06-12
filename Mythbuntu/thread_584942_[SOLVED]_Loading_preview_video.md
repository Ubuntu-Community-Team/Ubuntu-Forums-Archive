---
title: "[SOLVED] Loading preview video"
date: 2007-10-21
forum: Mythbuntu
---

### Post by axelsvag on 2007-10-21
I think mythbuntu is a fantastic project. But it still need some tweaking, at least at my machine. After the xmltv and remote problem I came to the next level of problem "nice to work" instead of "need to work". When I choose "watch TV" and choose programguide the "loading preview video" is misaligned and distorted. Instead of beeing in the right upper corner the video stream is positioned at the upper left corner above the text. And the video stream is distorted so it´can´t be watched. I rember I have had exactly the same problem a year ago but then I changed from ATI card to NVIDIA 7600GS. That time everything worked perfectly but now the error is back. Is it just on my machine or does anyone else recognize this problem.?? I presume it has something to do with the videodriver.

---

### Post by superm1 on 2007-10-21
This is characteristic of the open source 'nv' driver.  Open up mythbuntu-control-centre, and activate the restricted driver for the nvidia card.

---

### Post by axelsvag on 2007-10-21
I have tried that but it seems like even if MCC says that the restriced driver is installed and activated the problem is the same. But I doubt that the driver is loaded as you suggest. Maybe has the the new driver together with the tvout, problem to work together. Maybe this is a longshot, but when I try to make nvidia-settings to work the remote control stops to work as I mentioned in another thread. Can it be that I have to change to a LCD tv to be able to get this to work?

---

### Post by superm1 on 2007-10-21
Well nvidia-settings will tell you for sure whether the nvidia driver is loaded or a different one.

---

### Post by axelsvag on 2007-10-21
But shouldn´t I be able to access the nvidia-settings if the driver is installed correctly? Now I just get a message that says something like I need to start nvidia xserver.

---

### Post by superm1 on 2007-10-21
> **axelsvag said:**
> But shouldn´t I be able to access the nvidia-settings if the driver is installed correctly? Now I just get a message that says something like I need to start nvidia xserver.
On that same page, choose the display config gtk option.  You can make sure on the second tab that the nvidia driver is loaded there.

---

### Post by axelsvag on 2007-10-21
OK, I will try that. I think I have installed and activated the nvidia-glx-new When I go through the startprocess I always get the message that the computer use low resolution due to the fact the either the monitor or the hardware can´t do anything else.  It is a little bit odd because everything worked well in feisty with mythtv.

---

### Post by axelsvag on 2007-10-24
Now I have tried to install and uninstalled enabled/disabled the nvidia driver. And I have not once been able get it fully installed. If I get close to install enable The remote is disbled or get just lines on the screen. In feisty all this worked perfectly. Can my problem have something to do with AMD 64 problems or is it a long shot? I will try to install the final release in the weeken, maybe that will solve my problem.

---

### Post by superm1 on 2007-10-24
I didn't realize you weren't on the final release.  Please do experiment from that.  There have been a lot of bug fixes (including in the installer related to driver installation).

---

### Post by axelsvag on 2007-10-25
Thank you for all help. As I said I will try to make a fresh install with the final release this weekend. I will report if that fix my troubles.

---

### Post by axelsvag on 2007-10-25
I would like to make one last observation before I will a fresh install. If I look inte etc/X11 directory I see that it is not the xorg.conf that is the last but a file called failsafe.conf and when I look in that file I can see that a lot of the compoenets that is usually in the xorg.conf file is missing. Like the right keyboard layout, the svideo and the h and v sync that is suitable for the crt monitor. So I think something load a different xorg.conf into the system and make it instable.

---

### Post by axelsvag on 2007-10-26
The last chapter. After making a fresh install with FR everything works perfectly according to the load preview video. So there seems to be a lot of bugfixes between RC to FR. Thank you everyone who have worked so hard with this magnificent software.

---

