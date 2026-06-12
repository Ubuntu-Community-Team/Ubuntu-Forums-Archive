---
title: "alsa error: Device or resource busy (No sound in Boxee on 64bit Karmic)"
date: 2010-03-03
forum: Multimedia Software
---

### Post by _axiom_ on 2010-03-03
Kind folks in the _[boxee forum]("http://forum.boxee.tv/showthread.php?t=16378")_ were unable to help me.  I am pretty sure there is a problem with my audio setup.

Sound works in the rest of KDE, and sound also works with flash. (Actually flash video even works in boxee).

When I try to run Pandora in boxee though, I get a message that audio failed.  In my logs, I see this:

```
ERROR: Initialize - pcm_open_lconf, alsa error: -16 - Device or resource busy
```

I've tried suggestions to see what might be hogging my sound system and killing it, but that had no effect.

I have a feeling that boxee is trying to send audio to someplace that doesn't exist, but I not sure how I would tell, or how I would fix that.

[SIZE="1"]Note: I do not have pulseaudio (I am told that KDE people are not supposed to use this), nor do I have esound. Just ALSA version 1.0.22.1.[/SIZE]

---

### Post by Yellow Pasque on 2010-03-03
You might look at ~/.boxee to see if there's any settings for audio.

---

### Post by _axiom_ on 2010-03-04
There is this in guisettings.xml:
```
<audiodevice>iec958:CARD=CA0106,DEV=0</audiodevice>
```

That looks like the same sound card KDE is using.  (At least the CA0106 part shows in system settings.)

How would I tell if this is right, or if it isn't, what is?

---

### Post by tixetsal on 2010-03-26
same sporadic (most of the time) problem here.
can't find solution.

---

### Post by _axiom_ on 2010-03-28
Not sporadic for me, happens everytime I try to use the Pandora app.

There is a bug report about it.  Maybe they will fix it someday. 

[http://jira.boxee.tv/browse/BOXEE-4411](http://jira.boxee.tv/browse/BOXEE-4411)

---

### Post by Geremia on 2013-02-27
This sort of thing happens to me for every app that wants to use audio. It seems ALSA can only handle audio from one app at a time.

---

