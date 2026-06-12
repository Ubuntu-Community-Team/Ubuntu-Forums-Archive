---
title: "audio problems for one user only"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by Mateo on 2006-12-23
I have 2 users set up.  For one of my users I have audio problems.

For this user, when I watch video files (divx, mpg, etc.) the sound is choppy.  Sounds like a constant stutter.  Also, the sound doesn't work in Firefox.  However, when listening to mp3 files or radio stations in rhythmbox, i do not experience the problem.

My other user has no audio problems (that I have found).  I have used the exact same video files and online video websites for testing purposes.

So that makes me believe that the problem is not with codecs or sound card drivers, because these are the same for all users (correct?).  What problems should I be looking for.  Thank you.

---

### Post by Mateo on 2006-12-23
bump.

not sure how to even begin to tackle this problem.

---

### Post by Mateo on 2006-12-24
Update:

I tried playing the exact same mp3 file in rhythmbox and in VLC (with the user with the sound problem).  Worked fine in rhythmbox but choppy in VLC (as had been tested with video files previously).  This is the first time I tried with exact same files.

So in summary:

_User 1_
VLC:  Choppy audio.
Firefox:  No audio.

_User 2_ (which is actually my mythtv user)
No one audio problems.

In VLC I reset the preferences but it didn't affect the choppiness.

---

### Post by Mateo on 2006-12-25
bump

---

### Post by Mateo on 2006-12-27
bump

---

### Post by majoridiot on 2006-12-27
some troubleshooting thoughts for you...

did you double-check to ensure that user has privileges for sound? 

System-->Users & Groups... select the appropriate user, then- Properties-->User privileges (tab)

if no luck there, try adding the problem user to the same group as your mythtv user-
(likely group mythtv)... setting also changed as above under "advanced" tab to see if that
makes a difference.

you might also try adding a new user (giving priv to sound as well) and see if it has similar 
audio problems too

It might also be worth a try to give the problem user full admin privs to see if it is some 
other permission problem.

holla back with any results.

---

### Post by Mateo on 2006-12-27
Thank you for replying.  I tried your suggestions with no luck.

First, the mythtv user doesn't even appear in "Users and Groups" but I know it exists (because i use it!).  Not sure if that's important but just thought i'd mention it.

There was no sound option for privileges.  And the user already had admin privileges.

I'm starting to think this is purely a software problem.  I tried 1 video with VLC where I got the problem.  Then tried with Mplayer and the sound wasn't choppy.  Of course, the same video works perfectly under the mythtv user.

I tried a complete removal of VLC, and then reinstalling it.  Didn't help.

---

### Post by Mateo on 2006-12-27
UPDATE:

I have fixed VLC.  I installed the alsa VLC addon and went into the settings and selected my sound card (it has been set as default) for asla to use.  It cleared up the sound in VLC great.

However, still no sound in Firefox.  But it does work with mythtv user.

---

### Post by Mateo on 2006-12-30
bump.  still have problems.  sound is choppy in some programs, doesn't work in others.  For my main user only, of course.

Also my /dev/dsp file is 0kb, if that means something.

---

### Post by Mateo on 2006-12-30
fixed it.  all I had to do was delete these two files from my home/user/ folder .asoundrc and .asoundrc.asoundconf.  My mythtv user that didn't have the sound problem didn't have these files.  so i copied them to flash drive for safety's sake, then deleted them.  here's what they contained, in case someone is curious:

.asoundrc
```
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
```

.asoundrc.asoundconf
```
# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card Intel
defaults.ctl.card Intel
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix_max_periods 0
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0

```

---

