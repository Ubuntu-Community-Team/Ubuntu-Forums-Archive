---
title: "[SOLVED] No Audio- Already followed LordRaiden's Comprehensive Sound Problem Solution"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by bcn17 on 2007-12-26
I had no sound to begin with and got no errors when following the Comprehensive Sound Problem Solutions Guide v0.5e by LordRaiden in the section where i use the updated alsa-drivers. 

When i type lspci -v i get:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
 
when i type aplay -l i used to get something saying i had a 82801H (ICH8) family but after the things i did below it says no soundcards found... so after the commands i used to try and fix it my problem has worsened, Audio used to "seem to work." I could adjust volume, play songs etc, but there was never any sound.. no it doesn't even detect it and i have a little red X next to my volume button. 

I'm using Gutsy 64 bit alternate cd install. 

i did this: same as in guide except i used latest alsa: alsa-driver-1.0.15 found on their mainpage and i for the driver i used hda-intel.

 mkdir src cd src
      
mkdir alsa
      
cd alsa
      
sudo apt-get install build-essential linux-headers-$(uname -r)
                
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)

tar xvjf alsa-driver-1.0.15.tar.bz2 

cd alsa-driver-1.0.15 

sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel --with-oss=yes 

sudo make 

sudo make install


Any help would be greatly appreciated.

---

### Post by Yellow Pasque on 2007-12-26
If ALSA's not working out, try OSSv4 (see the link in my sig)

---

### Post by bcn17 on 2007-12-28
Thank you very much! The drivers worked right away. I couldn't get ALSA drivers to work no matter what I did. I still need to figure out the mixer but the sound of sweet Led Zeppelin after so many attempts was great!
**EDIT:** for those who are wondering (because it doesn't say anything about it if you man ossmix) for a graphical ossmix enter the command ossxmix into the terminal.

---

### Post by Yellow Pasque on 2007-12-29
Thanks for the feedback bcn17.  A lot of people seem to miss step 8 of my walkthrough or don't quite understand it. Would you say that's true? Step 8 is to remove the volume control icon from the panel (right click, remove). Then you can right click the empty panel left behind and add a custom app launcher for ossxmix.

I'm glad everything worked out for you. If you wouldn't mind, can you click the "Thanks" icon at the bottom of the HowTo post so that it gets starred a bunch of times and exposed to more people. Thanks.

If you have any more issues with sound or OSS, don't hesitate to ask, and we'll see if we can straighten hem out.

---

### Post by bcn17 on 2007-12-29
I took another look at step 8 and I now see that you clearly said to use ossxmix. The problem I ran into was not that I didn't understand what you were saying but that I misread ossxmix for ossmix. I would not be surprised if other people did the same thing.

---

### Post by Yellow Pasque on 2007-12-29
Yeah, you're not the first one to misread it. I'll put a note in about it. Thanks for the feedback.

---

### Post by bcn17 on 2007-12-29
Okay so a couple have problems have been popping up. First of all, I can't get sound in flash. I tried the above suggestions and also tried these: 

[http://ubuntuforums.org/showthread.php?t=204022&highlight=flash](http://ubuntuforums.org/showthread.php?t=204022&highlight=flash)

The other problem that is sort of annoying is that the sound will stop working eventually and a reboot is in order to fix it. For instance a play list will be playing and eventually will stop and I'll come back to my computer and sound will be not working again. There is an error message in the terminal window that opens up when i run ossxmix and there are errors if i run osstest. I can copy the error message next time i get this problem but sound is working find right now.

---

### Post by Yellow Pasque on 2007-12-29
bcn17, I noticed you're running Gutsy64. I assume you got the flashsupport file to build and made the necessary links?

---

### Post by bcn17 on 2007-12-30
Okay, So I'm not exactly sure what I did but sound IS working in flash now. I re went over all the steps at the end. It was weird though because I rebooted and it didn't work and then my computer got messed up (fell asleep or something) and when i rebooted i had a youtube tab open that started playing and WALA! i had sound. The other problem is the consistency of the sound. Sound doesn't work after computer falls asleep and is waken back up. Logging out and back in won't fix it but a reboot will. See [this new thread]("http://ubuntuforums.org/showthread.php?t=662177") because i do have sound and this will be marked as solved.

---

