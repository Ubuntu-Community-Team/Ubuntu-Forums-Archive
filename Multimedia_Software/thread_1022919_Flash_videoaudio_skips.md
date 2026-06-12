---
title: "Flash video/audio skips"
date: 2008-12-27
forum: Multimedia Software
---

### Post by psycovic23 on 2008-12-27
Hey,

I'm running FF3 and Flash 10, and for some reason, when FF has be open for a while and I try and watch a video, it progresses for a few seconds and then the audio starts skipping like a broken record. I can seek past a few seconds, and it'll play another second and do the same thing. If I close firefox and reopen it, it'll be okay. 

I've found threads about this problem in the past, but they were all with flash 9.  I have "nonfree-plugin" installed. After this problem showed up, I tried also installing "nonfree-plugin-extras", but it didn't help.

Any ideas?  

Thanks

---

### Post by linux_tech on 2008-12-27
Installing libasound can help resolve stuttering
```

sudo apt-get install libasound2

sudo apt-get install libasound2-plugins

```
give it  a try

---

### Post by psycovic23 on 2008-12-27
I already had those installed.

---

### Post by cb34 on 2008-12-28
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

i would look through that whole post carefully checking everything, and specifically i think APPENDIX B will help you.. the part about modifying the daemon.conf file.

peace.

---

### Post by psycovic23 on 2008-12-28
Unfortunately, pulseaudio mucks up a lot of stuff on my system, so I'm back to esound. Any other possible ideas?

---

### Post by eightysix on 2009-01-07
I had the same problem. Did you try installing the **libasound2-dev** package? That did it for me.

Cheers.

---

### Post by damonjablons on 2012-09-25
> **eightysix said:**
> I had the same problem. Did you try installing the **libasound2-dev** package? That did it for me.

Cheers.

*For anyone who lands on this old thread. This solution does seem to alleviate a lot of the skipping audio issues I've had with flash.*


[LIST=1]
[*]Open a terminal, and run the following command to install [FONT="Courier New"]**libasound2-dev**[/FONT]
[*]```
$ sudo apt-get install libasound2-dev
```
[/LIST]


If you have **Google Chrome**, the following steps will help too. What this will do is disable the native Google Chrome Flash player in favor of Adobe's.

[LIST=1]
[*]Open a new tab, paste this link, and then hit [FONT="Courier New"]**Enter**[/FONT] to get to the Chrome plugins page: [FONT="Courier New"]**chrome://plugins/**[/FONT]
[*]On the top right hand side of the page, you'll see the **Details** button. Make sure it's expanded. It should show a minus sign after clicking it.
[*]There should be two versions of Flash. Click **Disable** on the version which has a location field which looks something similar to this: [FONT="Courier New"]**/opt/google/chrome/PepperFlash/libpepflashplayer.so**[/FONT]
[*]Finally, open up a [Flash site]("http://youtube.com") in a new tab to test your audio. It should be working a lot better.
[/LIST]

---

