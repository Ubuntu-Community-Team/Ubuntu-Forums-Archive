---
title: "No sound - &quot;device is being used by another application&quot;"
date: 2009-02-05
forum: Multimedia Software
---

### Post by bsmith1051 on 2009-02-05
Every couple of days my sound stops working.  I'm running Ubuntu 8.10 with all updates and everything's installed properly, i.e., it works perfectly after reboot.  But something somewhere is tying-up the sound system and I have no idea how to fix it (short of reboot).

Is there some way to identify what application is still using sound?  And, aren't we supposed to be able to play sound simultaneously through multiple programs anyway?  Clearly, something is not working as intended.

Or, is there a known bug I should be following?

---

### Post by kostkon on 2009-02-06
There is a possibility that this happens when you start an application that tries to access the sound card directly causing problems to PulseAudio (and that's why your sound stops). PulseAudio needs exclusive access to the sound card. 

Maybe some application kicks it out and then gets exclusive use of the sound card and that's why when you reboot everything works OK again.

The thing you need to do, first of all, is to try to identify the application that causes the problem and then try to make it to work well with PulseAudio (if this is possible).

If you need any help regarding the above, don't hesitate to ask here.

Hope that helps.

---

### Post by travmon69 on 2009-02-06
this command should tell you what is holding on to the sound,
```
lsof | grep pcm
```

this command restarts sound i think,
```
pulseaudio -k ; start-pulseaudio-x11
```
it worked for me when skype was killing the sound.

---

