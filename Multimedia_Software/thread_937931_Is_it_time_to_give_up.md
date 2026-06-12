---
title: "Is it time to give up?"
date: 2008-10-04
forum: Multimedia Software
---

### Post by g500 on 2008-10-04
I have been trying for 3 weeks to get Ubuntu 8.04 working with Flash on a Sony Vaio laptop.  

I started with Flash 9, tried all the fixes I could find in these forums (remove / replace libflash, try different sound options etc) but still either had video frozen after 2-3 seconds or no sound.  No combination would give me sound and video.

I then updated to Flash 10 Beta which the forums suggest would resolve all my problems, but still video freeze after 2 seconds and no sound.

This has now got to the stage where I can no longer accept Ubuntu as a robust tool.  Is there any way forward, or is it time to run back to the nasty Mr Gates' software.

---

### Post by wolfen69 on 2008-10-04
completely remove whichever version of flash you are using and then do: ```
sudo apt-get clean
``` then ```
sudo apt-get autoremove
``` then ```
sudo apt-get install flashplugin-nonfree
``` then ```
sudo apt-get install libflashsupport
``` report back how it went.

---

### Post by g500 on 2008-10-04
> **wolfen69 said:**
> completely remove whichever version of flash you are using and then do: ```
sudo apt-get clean
``` then ```
sudo apt-get autoremove
``` then ```
sudo apt-get install flashplugin-nonfree
``` then ```
sudo apt-get install libflashsupport
``` report back how it went.

Sameold sameold!  I am now back to Flash 9, 2 seconds worth of silent video, then freeze.  Sound is set to Alsa, I don't know if this makes any difference.

---

### Post by eye208 on 2008-10-04
> **g500 said:**
> I started with Flash 9, tried all the fixes I could find in these forums (remove / replace libflash, try different sound options etc) but still either had video frozen after 2-3 seconds or no sound.  No combination would give me sound and video.
I bet you didn't try [this](http://ubuntuforums.org/showthread.php?t=885437).

---

### Post by g500 on 2008-10-04
> **eye208 said:**
> I bet you didn't try [this](http://ubuntuforums.org/showthread.php?t=885437).

I'm afraid I did.  That is why I am now set to Alsa instead of Pulseaudio. Made no diff.

---

### Post by mumuwenwu on 2008-10-04
hey, g500, if windows works better for you in this case, i would say maybe Mr. Gates is better for you than linux.

don't take me as a windows advocate, i am always in for linux, with over 8 years experience of linux.

i've encountered problems like you, spending days to work it out. that's painful.

so i understand your feelings.

computer is just a tool. don't rush into linux just because everyone else does. find a way that works best to you.

---

### Post by gandaran on 2008-10-04
try this, right click the flash video, configurations, disable hardware acceleration, maybe it'll help.

---

