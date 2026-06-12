---
title: "SB Audigy SE quit working - no clue why"
date: 2010-12-23
forum: Multimedia Software
---

### Post by Vi3GameHkr on 2010-12-23
So my Sound Blaster Audigy SE installed quite easily and worked like a charm in both Windows 7 and Ubuntu 10.10, however recently it randomly stopped working on a reboot from Ubuntu to Windows, another reboot back to Ubuntu and it still didn't work, but now it works in Windows only but not Ubuntu.

I went through the first post in the [Comprehensive Sound Problem Solutions Guide](http://ubuntuforums.org/showthread.php?t=205449) including checking if the volume was muted in alsamixer, following each of the steps in General Help, reinstalling ALSA drivers, but I didn't try to compile my own drivers (ultimately because it worked before)

Every once in a while, I'll hear a small pop through my speakers, but overall, I can't hear anything that I am supposed to be hearing.

I would appreciate any help I can get with this,
Thanks
 - Vi3

---

### Post by Vi3GameHkr on 2010-12-23
Well I got gnome-alsamixer, opened it up, started playing with settings.. Heard something faint so I turned the volume all the way up.  Well that faint noise was actually my headphones plugged into an mp3 player.

Anyways in Gnome ALSA mixer I unchecked IEC958 and it worked (at the time the volume was at max and I had a video playing in the background to test sound)

Heh I'm happy.  Bye

---

### Post by Vi3GameHkr on 2011-01-13
Well this has happened a couple more times and every time I just have to go into gnome-alsamixer and disable IEC958.  I don't understand why, but every once in a while it re-enables itself (and I'm not entirely sure what triggers it.  Actually I don't even have a clue.)

Is there like an easy script that could just run at startup and check if IEC958 is enabled,

--OR--

Does anyone have any ideas as to what could trigger that and how to fix it?  I guess I could check out the launchpad a little later for bugs related to this, and see if I can find anything else.

---

### Post by daszz on 2011-10-16
Well, I'm having the same issue, finally I got a clue (thanks to you), if I find something that help on this I'll post it here
EDIT: The solution lead to low quality audio (noises and clicks), the funny thing is, my internal audio is working just fine.

---

