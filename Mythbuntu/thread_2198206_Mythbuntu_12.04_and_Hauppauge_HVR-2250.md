---
title: "Mythbuntu 12.04 and Hauppauge HVR-2250"
date: 2014-01-07
forum: Mythbuntu
---

### Post by barrystolar on 2014-01-07
I am not super techie but I've  been using Ubuntu for 4 years now. About 8 months ago I installed  Mythbuntu 10.?? on one of my machines. Prior to installing Mythbuntu 10.??, I  researched which tuner cards would work so I bought a Haupauge HVR-2250.  I installed it and it worked. Since then, I updated to Mythbuntu 12 and I  cannot get the HVR-2250 to work. I've scoured the internet for hours and  tried various technical procedures to get the HVR2250 to work and had  no success. my question is should I downgrade to Mythbuntu 10 or get a new Tuner  Card? If I should downgrade to Mythbuntu 10 where I can get the download  as I no longer have the ISO? If I should get a new tuner card, what is  the best dual tuner card for Mythbuntu? Any help would be appreciated.

However, if there is a simple "cut and paste code into terminal" solution to get the Haupauge HVR-2250 to work with Mythbuntu 12. I would love to see it..

Thanks in advance.

---

### Post by cedyathome on 2014-01-12
In my experience, I've had to add the 2250 firmware to my computer. The drivers are in the OS, but the firmware was not
To check if you have the firmware on your system, try

See [http://ubuntuforums.org/showthread.php?t=751719&p=7429560#post7429560](http://ubuntuforums.org/showthread.php?t=751719&p=7429560#post7429560) for details on how to obtain & place the firware in the right directory.

Here's what my system shows regarding the firmware.
> $ dmesg | grep saa7164
[   11.398458] saa7164 driver loaded
[   11.399226] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   11.399232] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xfe800000
[   11.556020] saa7164_downloadfirmware() no first image
[   11.556102] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   12.253080] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   12.253085] saa7164_downloadfirmware() firmware loaded.



All the best.

---

### Post by barrystolar on 2014-01-13
Well, I was able to use some of that thread but I hit a roadblock at the line "hg clone http://kernellabs.com/hg/saa7164-stable/". It apears Kernal Labs has removed that file. 

Arggggggh!

---

### Post by EternalStudent on 2014-01-13
I can't seem to find the original post where I located these instructions.  This is from my notes.
This works for me in ubuntu 12.04 64bit.


[LIST=1]
[*]**Download [http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw)  (Ubuntu 12.x 64bit)**
[*]From the dowload directory, copy to /lib/firmware  ```
sudo cp NXP7164-2010-03-10.1.fw /lib/firmware/
```
[*]**Reboot**
[/LIST]

---

### Post by barrystolar on 2014-01-14
SOLVED - Thanks [**[COLOR=#000000]cedyathome[/COLOR]**]("http://ubuntuforums.org/member.php?u=994639") and [**[COLOR=#000000]EternalStudent[/COLOR]**]("http://ubuntuforums.org/member.php?u=894759")! I used the info from both of your replies to solve my problem.

However, for other low tech guys like me, you do have to use "gksudo" and "sudo" Commands to get temporary permission to copy the nxp7164 file to your /lib/firmware folder. I used this thread to help me understand that process: [http://ubuntuforums.org/showthread.php?t=1888101](http://ubuntuforums.org/showthread.php?t=1888101). You'll also probably have to navigate within your directories. (i.e. cd /   etc.)

---

### Post by EternalStudent on 2014-01-14
Glad that worked for you.  I've edited by post to reflect your concern over detail level.

---

### Post by EternalStudent on 2014-01-14
PS: If you'd like to mark this solved, I think others searching the web might benefit.  Edit your original post, go Advanced, then add the prefix solved.

---

