---
title: "Audio Permissions Problem.  alsa is confused!"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by nixitup on 2007-09-05
Alright so I just completed a manual install of Ubuntu so that I could use dmraid with my SATA drives.  Everything went well except for a few minor things that seem to be all related to the same issue.

minor note; my terminal prompt only shows a $ instead of 'user@ubuntu$' etc.. which I assume is because I didn't give my user an alias?

More Importantly, this may be an easy fix, so here's the most peculur sound issue:

Upon startup I noticed my speaker icon showed a disabled icon.  I proceeded to follow the [comprehensive audio solution]("http://ubuntuforums.org/showthread.php?t=205449") and it appears I have incorrectly setup some permissions.  The following commands produce perfect results only if I use sudo before them:

Example:
```
$ aplay -l  
aplay: device_list:222: no soundcards found...

```
Yet with sudo:
```
$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Same issue with alsamixer:
```
$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
```

Yet, again preceeding the alsamixer command with sudo, the mixer pops right up, and it appears to be receiving audio.

Did I simply miss something when I was configuring permissions?  My user is part of the group audio, and I have reinstalled all the alsa packages.  alsa appears to work, just not on my logged in account.

Any ideas that could get me moving or better yet hearing? 

I would assume this is a borderline newb question however I have exhausted all other options: tutorials, comprehensive sound guide, google.  sigh.

---

### Post by TSandman on 2007-11-23
I had the same problem with my Audigy following an update yesterday

Everything looks OK but Alsa doesn't find anything

I followed the many "no sound" threads, uninstalling/re-installing alsa, compiling it etc... only to find out that  I had the "User deleted from /etc/group" problem (had to restore it for Admin etc) and that restarting alsa-utils (sudo ./alsa-utils restart), logging out and then back  in solved my problem.

You have to make sure that alsa is reloaded and that your (gnome/kde/xfce) see the change (CTRL-ALT-Backspace & Login is the dirty way to do it ;)

---

