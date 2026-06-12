---
title: "Fixing X config"
date: 2009-01-11
forum: Multimedia Software
---

### Post by Amzer zo on 2009-01-11
I removed (deactivated) a NVIDIA hardware driver (#177) driver through the GUI menu of KDE 4.1.3. (motivation being that this driver is believed to make most of the screen black when using OpenOffice and make the machine unusable)

After reboot, everything goes fine (graphics come out clean at the login screen) until comes the time to render the Desktop which first turn all white then black.

I tried the "safe" mode including the restore X environment menu item.  Still same thing.

Is there a way to fix this?  Any pointers will be appreciated...

---

### Post by melojo on 2009-01-11
open a terminal and try the commands below.
```
sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Amzer zo on 2009-01-12
Thanks for the reply, I managed to work around the issue by renaming my .kde home directory.

I typed Alt-Ctrl-F1 to enter a shell based session, I then typed "mv .kde .kde.bak".  Once I rebooted, I got the default KDE environment.

---

### Post by schicanoloco on 2009-03-31
I am a longtime Ubuntu User .. I use Kubuntu 8.10 and recently had the black screen issue after I made the mistake of trying an older driver ( when I already had my Nvidia 774 Driver working fine) . I tried many methods..  This guy ^^^^ is correct - This is the easiest procedure , since kde rebuilds itself.. Other methods should also work , in theory but you have to know what goes where in the .conf files! Not an easy task! Thanks Saved Headaches! Remember people , you should always try the easiest fixes first just like in Science !

---

### Post by rolandrock on 2009-03-31
> **schicanoloco said:**
> I am a longtime Ubuntu User .. I use Kubuntu 8.10 and recently had the black screen issue after I made the mistake of trying an older driver ( when I already had my Nvidia 774 Driver working fine) . I tried many methods..  This guy ^^^^ is correct - This is the easiest procedure , since kde rebuilds itself.. Other methods should also work , in theory but you have to know what goes where in the .conf files! Not an easy task! Thanks Saved Headaches! Remember people , you should always try the easiest fixes first just like in Science !

Indeed.  In life as in science.  cf. [Occam's Razor]("http://en.wikipedia.org/wiki/Ockam%27s_Razor").  Nice advice.

---

