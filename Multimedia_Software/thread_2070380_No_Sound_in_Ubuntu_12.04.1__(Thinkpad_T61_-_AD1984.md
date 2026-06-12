---
title: "No Sound in Ubuntu 12.04.1  (Thinkpad T61 - AD1984)"
date: 2012-10-12
forum: Multimedia Software
---

### Post by FliGi7 on 2012-10-12
I just loaded 12.04.1 onto my Thinkpad T61 and I can't seem to figure out the issue with having no sound. My Master Volume is all the way up in the alsamixer and I've added the option "options snd-hda-intel model=thinkpad" line to my alsa-base.conf file (and rebooted) to no avail. 

My alsa info results are at the following:
[http://www.alsa-project.org/db/?f=ccef55ccac55c5be126cedb9dca81bbf6c282f65](http://www.alsa-project.org/db/?f=ccef55ccac55c5be126cedb9dca81bbf6c282f65)

Any help would be appreciated.

---

### Post by litiform on 2012-10-12
Do you have no sound when you play media, or are you meaning just the OS sound effects?

---

### Post by FliGi7 on 2012-10-12
I have no sound whatsoever, for anything.

---

### Post by FliGi7 on 2012-10-12
Here is a screenshot of the AlsaMixer, if that helps. 
[http://i.imgur.com/E57rI.png](http://i.imgur.com/E57rI.png)

---

### Post by litiform on 2012-10-12
Do any proprietary drivers show up when you look at Dash > Additional Drivers?

---

### Post by FliGi7 on 2012-10-12
Only my NVIDIA drivers.

---

### Post by FliGi7 on 2012-10-15
Any other ideas?

---

### Post by FliGi7 on 2012-10-16
Bueller? Is this a lost cause?

---

### Post by pqwoerituytrueiwoq on 2012-10-16
> **FliGi7 said:**
> I just loaded 12.04.1 onto my Thinkpad T61 and I can't seem to figure out the issue with having no sound. My Master Volume is all the way up in the alsamixer and I've added the option "options snd-hda-intel model=thinkpad" line to my alsa-base.conf file (and rebooted) to no avail.
since that did not work take that line out
post output of
```
lspci | grep Audio
aplay -l
```
and try each command this command gives you
```
aplay -l | grep card | sed 's/://g' | awk '{print "speaker-test -Dplughw:"$2","$7" -c2"}'
```
and post the command (if any) that makes noise

---

### Post by FliGi7 on 2012-10-16
**jp@jp-lnx-tp:~$** lspci | grep audio
**jp@jp-lnx-tp:~$** aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**jp@jp-lnx-tp:~$** aplay -l | grep card | sed 's/://g' | awk '{print "speaker-test -Dplughw:"$2","$7" -c2"}'
speaker-test -Dplughw:0,0 -c2
speaker-test -Dplughw:0,1 -c2

Executing either of the above commands yields no sound.

---

### Post by pqwoerituytrueiwoq on 2012-10-17
commands are case sensitive *points at your 1st command*

---

### Post by FliGi7 on 2012-10-17
Sorry about that. 

**jp@jp-lnx-tp:~$** lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by pqwoerituytrueiwoq on 2012-10-17
try this
```
echo "options snd-hda-intel model=ref position_fix=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf > /dev/null
```
then reboot

---

### Post by FliGi7 on 2012-10-17
I took the "options snd-hda-intel model=thinkpad" line out of my alsa-base.conf file before echoing that line into it. I rebooted and still no sound.

---

### Post by pqwoerituytrueiwoq on 2012-10-17
delete the line you just added 
the file should be like it was before you started trying to get it working
then reboot
and try those speaker-test commands again

---

### Post by FliGi7 on 2012-10-17
Still no sound.

---

### Post by pqwoerituytrueiwoq on 2012-10-17
i would suggest making google searches using 82801H, that is your chip set
you could try booting 12.10 and seeing if sound works on it, if it does all you likely need it a kernel upgrade on 12.04

---

### Post by FliGi7 on 2012-10-17
That's what I've done and couldn't find a fix that worked, which is why I came on here hoping for more specific suggestions. 

I'm currently using the 3.2.0-32-generic-pae kernel. Is there a different one I should try?

---

### Post by pqwoerituytrueiwoq on 2012-10-17
did it work on 12.10?
edit:
[http://thinkwiki.org/wiki/AD1984](http://thinkwiki.org/wiki/AD1984) - may be useful
sound like your sound card is part of the 54kmodem, in my exp 56k modems are nutritious for not working on linux

---

### Post by FliGi7 on 2012-10-17
Upgrading to 12.10 right now...

Yea, I came across that link as well and all the links contained are extremely outdated (404 errors on all the alsa-project.org links).

---

### Post by FliGi7 on 2012-10-17
Performed the upgrade via Update Manager and still no sound. Current kernel is 3.5.0-17-generic.

---

### Post by pqwoerituytrueiwoq on 2012-10-17
i meant on a live cd
it is possible your card is no longer supported, you can try [10.04]("http://releases.ubuntu.com/lucid/") as a live cd
10.04 goes EOL in April next year

---

