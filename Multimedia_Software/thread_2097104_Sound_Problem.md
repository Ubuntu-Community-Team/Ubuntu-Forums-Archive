---
title: "Sound Problem"
date: 2012-12-22
forum: Multimedia Software
---

### Post by afreerun on 2012-12-22
Sound Problem
I am new to this system and have just wiped my hard drive and installed Ubuntu 12.4. Now I have no sound. I have searched the web for 3 days and still have no sound.
Can anybody help with this problem please as I do not wish to return to my old OS also I do not fully understand Ubuntu but wish to keep and learn.
Thanks for any help

---

### Post by stooey34 on 2012-12-22
Hi, I too am a new Ubuntu user and have sound issues everytime there is an update that requires a reboot.
The solution that works for me is the following...

1. Reboot the system
2. Select Recovery Mode from the list
3. Select Repair Broken Packages from the next list

say yes to any questions that may occur

4. Normal Reboot from the list

hope this helps

---

### Post by mörgæs on 2012-12-22
Does this help?

[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

---

### Post by afreerun on 2012-12-22
> **mörgæs said:**
> Does this help?

[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)
I have done all as requested and still no sound. Can play dvd without sound. Confusion with different operating systems is probably my problem, but I am willing to learn as I find Ubuntu excellent otherwise.
Thanks guys, any extra help is appreciated

---

### Post by afreerun on 2012-12-22
I have tried all of the above and still no sound. Will play dvd but without the sound. Confusion is probably my problem and I appreciate all your help. I shall persevere for I find the os excellent.
Any extra help welcome
Thanks guys

---

### Post by afreerun on 2012-12-24
below is the link to the script if anyone can help

[http://www.alsa-project.org/db/?f=72b4cb79c5be4a216dfa79b217f6f746e97a1440](http://www.alsa-project.org/db/?f=72b4cb79c5be4a216dfa79b217f6f746e97a1440)

maybe if I try changing sound cards it might help, any thoughts on that.

---

### Post by HeresYourShovel on 2012-12-24
I have experienced this same problem for two days now.  I have attempted various fixes from this site and others. Did the alsamixer unmute and check sound card. Tried to uninstall and reinstall sound drivers. Checked output device in sound settings. I just reinstalled 12.10 fresh and still cant get sound to work. **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
This is what I got after aplay -l.
Any help would be appreciated.

I ran hwinfo --sound but it wasnt installed so i ran sudo apt-get install hw info and then ran hw info --sound.  Then copied and pasted some errors from freenetwork.org hal. Anyways, i ended up running sudo apt-get install hal and picking correct sound device to fix mine. Im a rookie but finally found the answer copying and pasting in google search.

In the first place, I installed Quantal Quetzal from Natty Narwhal (where everything was working fine) but then started trying to get java and a poker room installed.  Kept asking me to send error reports after I downloaded different versions of java (i think icedtea is what i ended up with) and 4 or 5 different poker sites. Not sure when my sound went out but it worked after clean install of Quantal.

---

### Post by afreerun on 2012-12-25
This is all I got out of aplay command

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

About to give up, too many hours trying to fix.
I also have tried all resources on internet. Sound is the only thing missing.

Is there a system that works that I may try, other then windows.

Thanks all. Maybe try again tomorrow.

---

### Post by afreerun on 2012-12-28
Hi all,
             After spending many hours and lots of help from this forum, I have solved my No Sound Problem..
              After all else failed,there was only one thing else to try. I installed and old sound card and went into Bios, Left the on-board sound set to auto and guess what. Instant sound.
  I would like to thank all for their help and I am very grateful. I have learned a lot being a new user of this system.
Cheers All

---

