---
title: "no sound in 16.04"
date: 2017-11-03
forum: Multimedia Software
---

### Post by raymondvillain on 2017-11-03
HP laptop, running Ubuntu 16.04.  No problems with sound until today, for reasons unknown I have no sound.  Rhythmbox doesn't work, and the sound icon under settings cannot be used to  change the volume.  The bar (status bar?) at the top of the display has some symbols showing wifi, battery level, time of day, etc. and a symbol of a speaker that is greyed out with an "X" to show there is no volume.

If I open "sound" under system settings, the box showing the "Play through" information is empty.  

What's going on?  How to get my sound back?  Can't think of anything I've done out of the ordinary.  Youtube and Facebook are all I ever listen to, video on both of those still work, but obviously no sound.

Any suggestions greatly appreciated.

---

### Post by RobGoss on 2017-11-04
Hello **raymondvillain, ** Have you tried going in to the sound settings to see if your device output is listed?

After checking if your device is listed you might want to try reloading **alsa**, I would even  rebooting after

```
sudo alsa force-reload 
```


You can also try reinstall Pulseaudio if Reload does not correct the issue. Run the following commands
 
```
 sudo apt-get remove --purge alsa-base pulseaudio
``` 


```
sudo apt-get install alsa-base pulseaudio 
```

---

### Post by raymondvillain on 2017-11-04
Thanks for the tip, I tried re-installing pulseaudio.  After reboot, the greyed out image of a muted speaker went away.  Went to "sound" and a window opens, "volume control" with a message "Establishing connection to PulseAudio.  Please wait..."

Waited and waited, nothing happens.

Should I re-install rhythmbox, or something else? 

Have to go to work now, will check back in a couple of hours.  Thanks again for your help!

P. S. still no sound in YouTube.

---

### Post by raymondvillain on 2017-11-04
Fixed it!  Found this post [https://bbs.archlinux.org/viewtopic.php?id=202860](https://bbs.archlinux.org/viewtopic.php?id=202860) and the last entry suggested starting pulseaudio with "pulseaudio --start", so I tried that and everything works.

Marking this solved.

P. S. 
but I have to do that every time I re-boot.  So not everything is fixed.

---

### Post by RobGoss on 2017-11-05
Glad you found a fix for it and thank you for marking this thread as **solved** and sharing your solution with everyone

---

### Post by RobertoRecordo on 2017-11-06
I am using Ubuntu Studio 16.04
I had the same problem several days ago, immediately after doing a security update.
Ray d'Villian,  did you do an update suggested by the update manager?

-Rob

---

### Post by raymondvillain on 2017-11-17
Not sure if I did or not.  I just update every time the app sez there is an update available.  could be that I did.  How did you fix things?  I can't get any sound at all now.  If I open settings> sound I can test "front left" and "front right" and hear the test tones but If I open Audacity and try to play a .flac file nothing comes out.

Perplexing.

---

### Post by RobGoss on 2017-11-20
If you can hear sound from let's say YouTube, it's something to do with **Audacity** settings I would suggest opening Audacity and check to see if your device is listed from the drop-down menu, I'm not at my desk so I would have to check what I have to give you more details

---

### Post by Yellow Pasque on 2017-11-20
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by tombibs on 2018-08-23
I am on a Acer Chromebook powered by Intel. I just re-mounted crouton running Linux 16.04. I have no sound whatsoever. I have tried everything on this thread. I have no speakers, only the ones embedded in my laptop. Please help!

---

