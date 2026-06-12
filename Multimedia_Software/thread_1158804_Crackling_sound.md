---
title: "Crackling sound"
date: 2009-05-14
forum: Multimedia Software
---

### Post by txfiddler on 2009-05-14
Dell Inspiron E1505   Dual core T2300 @ 1.66 ,  1 Gig Ram.

I am having problems with the sound on certain applications in 9.04.  Most sound from websites, (MySpace, YouTube etc.)  and the boot up Ubuntu sound come out as a crackling noise.  Other sources like CDs or MP3s will play without issue.  If I go to System>Preferences>Sound  and test the various listings,  I either get the crackling sound, total silence or this message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

Or

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

I would appreciate any input.
Thanks

---

### Post by kpkeerthi on 2009-05-14
If your audio hardware can handle hardware mixing by itself (and if you don't need the fancy stuffs pulseaudio can do), try [disabling pulseaudio altogether]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/"). This worked for me.

---

### Post by txfiddler on 2009-05-14
> **kpkeerthi said:**
> If your audio hardware can handle hardware mixing by itself (and if you don't need the fancy stuffs pulseaudio can do), try [disabling pulseaudio altogether]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/"). This worked for me.

I followed the directions.  Now I have no sound sound crackling or otherwise.  Even the CD or the Wave files do not work now.

---

### Post by gewitty on 2009-05-14
Check this thread: [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

Watch out for the lib32asound2-plugins file though. On a couple of my 64 bit machines, installing this removed Skype and any Wine-dependant apps, such as Picasa. If you get that problem, remove lib32asound2-plugins and install the lib32asound2 file instead.

I also experienced the crackling problem with multimedia apps. In my case, this was solved when I discovered that the Front Mi slider in Gnome Alsa mixer was set to zero. Setting it to its maximum solved the problem.

---

### Post by txfiddler on 2009-05-14
Well.  After the 2nd reboot.  IT WORKS!  It did run the latest batch of updates but I don't think that had anything to do with it.  Thanks for the help.
Cheers
TXFIDDLER

---

