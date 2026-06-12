---
title: "Jaunty X-Fi Mic issues"
date: 2009-05-31
forum: Multimedia Software
---

### Post by Ron Overdrive on 2009-05-31
I am running Ubuntu 9.04 with a Creative X-FI Xtreme Music sound card (don't blast me for it, I've had the card for years before I switched to Ubuntu). Apparently the playback and recording mixers are linked somehow. If I mute the playback on the Mic so I don't get an echo it also mutes the Mic recording. Anyone know what the issue is?

---

### Post by Nerevar on 2009-06-30
Bumping this because I am having the exact same issue.  I'm using the X-Fi Xtreme Gamer (using the linux drivers from Creative's website) and my mic works but I am able to hear everything I say through my headphones and I have not been able to mute this without muting the mic as well.  I have not spent much time trying to resolve this issue yet.  Hopefully someone else has experienced this problem and was able to figure it out...I'll keep messing with it and reply if I get it working.

---

### Post by inmatal on 2009-08-13
Hi I bump this, and ill raise it with a temp solution, which someone perhaps could work on, and find a final solution.

 My XFi card is registred in the hardwaredriver for restricted drivers.
I can hear my voice, but i cant get it to record it, or use skype without doing this:

I go into "Hardware drivers", and there I disable the XFi drivers. Then I have to reboot the computer. When you get back inside you open the "Hardware drivers" and then you enable them again, and you DO NOT restart after. This will enable your sound and your microphone will now record and work with all apps. 

This is a temp solution, because i have to shut of the XFi drivers before i shut my PC down every night. I hope someone could come up with something less idiotic than this.

Regards.

---

### Post by inmatal on 2009-08-15
bump. anyone got anything to add to this please?

---

### Post by bluestix on 2009-08-31
> **inmatal said:**
> 

I go into "Hardware drivers", and there I disable the XFi drivers. Then I have to reboot the computer. When you get back inside you open the "Hardware drivers" and then you enable them again, and you DO NOT restart after. This will enable your sound and your microphone will now record and work with all apps. 




I have the same problem.

This worked for me.


Hopefully this doesn't take long to fix because the temporary workaround is kindof a pain.

---

### Post by bluestix on 2009-08-31
I was wrong. It only worked for the test call. After that it went back to mute.


Here is how I got it working:


[http://ubuntuforums.org/showpost.php?p=7878068&postcount=3]("http://ubuntuforums.org/showpost.php?p=7878068&postcount=3")

---

