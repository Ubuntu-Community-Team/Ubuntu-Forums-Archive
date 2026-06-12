---
title: "Sound in multiple programs?"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by ekuliak on 2006-06-25
Hello

I have a Sound Blaster Live! soundcard (2 normal speakers for now, but I plan to buy  a 5.1 system soon)


My issue is that my sound doesn't always play in programs.  It seems like when I have a program open that is using sound (AmaroK for instance), other programs won't get sound (firefox, for instance).  But it also seems that even when I'm not running those programs that use sound when trying to run another program (UT2004, for instance) I still won't get sound most of the time.  

However, I seem to be able to run multiple multimedia apps at the same time with sound for some reason (I tried AmaroK and VLC and both produced sound at the same time)


My questions:  Can I configure something so that multiple programs can use sound always (Like AmaroK and firefox both running and having sound)?  If so, how?


If that isn't possible, how can I check what is using sound that might make it so UT2004 or firefox cannot get sound (even when AmaroK isn't running)?  

Do I need to refresh something (when I used Mandriva I was able to restart kmixer or whatever and that seemed to work 70% of the time)?  If so, how do I do that in Ubuntu?

Ideally I want all my programs to have sound when they are running even if another program also has sound.  

Thanks

---

### Post by deadgobby on 2006-06-25
I did this little diddy, but FF sound will not come through my SB.
[http://ubuntuforums.org/showthread.php?t=192026&highlight=sound+blaster](http://ubuntuforums.org/showthread.php?t=192026&highlight=sound+blaster)
If there is more info on getting the SB to do all the sound liek it did in Breezy. I would too be a happy camper.

---

### Post by ekuliak on 2006-07-18
I'm still not able to get sound to work in multiple programs, but after getting my 5.1 system (Logitech X-530 if anyone wanted to know, or if it helps with search results) I was able to get it to have sound in all speakers (in AmaroK, as well as some other programs) by following what was posted here: [http://www.ubuntuforums.org/showthread.php?t=184814&]("http://www.ubuntuforums.org/showthread.php?t=184814&")

This page: [https://help.ubuntu.com/community/SoundProblemsHoary]("https://help.ubuntu.com/community/SoundProblemsHoary") looks like it could possibly help.  I'll try it out soon (hopefully) and see if it does help or not.

and mostly for future personal reference I'm posting my current esd.conf file (I havn't touched it yet):
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```

---

### Post by ekuliak on 2006-07-19
I do not notice any differences with the changed esd.conf file.

Oh well.  Anyone have any other ideas? :confused:

---

