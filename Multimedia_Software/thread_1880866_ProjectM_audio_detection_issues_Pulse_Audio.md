---
title: "ProjectM audio detection issues Pulse Audio"
date: 2011-11-14
forum: Multimedia Software
---

### Post by LordVeovis on 2011-11-14
I am trying to get ProjectM to work on my desktop that I recently installed 11.10 on.  I remember last time having to open up terminal and running a command to get ProjectM to detect audio output.  Any suggestions?

I have already gone into the options for ProjectM and tried to have it listen on the 3 different audio devices that are shown, but it does not detect the sound.  The is obvious by no change in the visualization despite change in the audio I am hearing.

---

### Post by inobe on 2011-11-14
you can go to **#projectM** irc channel on freenode to get instant support.

thought i should mention that.

---

### Post by LordVeovis on 2011-11-17
Did not get a reply in the few hours I was on the IRC.  I remember last time I 'un-muted' a device, but that does not seem to be the problem this time.  Any other suggestion much appreciated.

---

### Post by LordVeovis on 2011-11-17
I was able to fix the problem.  I muted all devices and then unmuted them again.  Solved!

---

### Post by chrispche on 2012-02-14
I was not able to fix the problem. I'm using Ubuntu 11.10 and Amarok on Unity and ProjectM is not picking up the sound on any app to be honest. Where can I find the settings for ProjectM? Or does anyone else have any other suggestions.

Thanks.

---

### Post by chrispche on 2012-02-14
OK Solved and sorted.

Just run the command:

```
pacmd set-source-mute 0 0
```

---

