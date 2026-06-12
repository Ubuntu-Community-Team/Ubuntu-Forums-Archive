---
title: "Command-line application volume control"
date: 2011-08-05
forum: Multimedia Software
---

### Post by GraysonPeddie on 2011-08-05
I'd like to be able to control the volume of the application as I'm running Ubuntu Server 10.04. This is handy, so I can do something like this in Asterisk PBX:

```
exten => *80,1,System(Lower the applicationname's volume to 50%.)
exten => *80,n,Dial(CONSOLE/dsp,20,A(beep)) ; uses /dev/dsp (chmod 777)
exten => *80,n(HANGUP),System(Restore the applicationname's volume to 100%.)
```

Imagine you are at a retail store with music playing through the speakers that are in the ceiling. An employee picks up the phone and dials *80. The system automatically lowers the background music volume to 50%, makes a beeping sound, and the employee begins to speak into the handset's microphone, which then gets picked up by the speakers. When done, the system detects a hangup and restores the background music volume to 100%; thus, not compromising in intercom's (/dev/dsp) volume level.

Yes, I know that the permission for /dev/dsp gets reset as it gets dynamically recreated after every reboot and that it's a bad idea to let everyone outside a root user access the /dev/dsp directory and that I'm trying to find an alternative to /dev/dsp that I have Asterisk access when I take advantage of the intercom, but I'll leave this up to DSLReport.com's VoIP Tech Chat forum, since I'll need to have Asterisk be able to adjust the volume of an application by making a call to System(), as shown in the code above.

---

