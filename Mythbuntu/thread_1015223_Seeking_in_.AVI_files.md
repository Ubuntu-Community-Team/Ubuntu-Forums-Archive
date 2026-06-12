---
title: "Seeking in .AVI files?"
date: 2008-12-18
forum: Mythbuntu
---

### Post by SiHa on 2008-12-18
Most of my videos are .AVI's. MythTV's internal player doesn't seek very well in these. Although they do a better job, I'd rather not change to Mplayer / xine - I want to keep the user interface the same to keep the WAF up.

Any ideas gratefully received...

---

### Post by managementboy on 2008-12-19
> **SiHa said:**
> Most of my videos are .AVI's. MythTV's internal player doesn't seek very well in these. Although they do a better job, I'd rather not change to Mplayer / xine - I want to keep the user interface the same to keep the WAF up.

Any ideas gratefully received...

When you describe "not seeking well" what do you mean?

AVI=Container... what is in that container of your files?

What version of MythTV are you currently using?

---

### Post by Caps18 on 2008-12-19
I was going to post the same thing.  When I use MythVideo for any  videos (non 1080i video, I haven't tried this yet, but it might be differnt), the fast forwarding and rewinding are very slow.  It does it right for a second and then waits for another few seconds before it jumps back or forward again.

It works fine using the Watch TV or Watch Recordings features.

I think I am using Xine as my MythVideo player, but I have to exit out of MythTV in order to watch some high-res videos, but not others due to my system not being the fastest.

---

### Post by SiHa on 2008-12-19
> When you describe "not seeking well" what do you mean? 

Well, in recorded shows, I can fairly smoothly change the FF speed from 3 x up to 120x in all the increments, and it winds smoothly. When I press play, it neatly drops down to play at the intended position, backing up by the 1.5s I have specified in the setup.

When playing videos, I have to press the FF/RW keys quite a few times to get any effect at all. The video appears to FF, but the audio can be heard in realtime, with the occasional jump. When I drop out to play at, say 13m it actually returns to where the audio was, at about 3m - not much further then if I'd just played in realtime.

I can FF though a 2-hour TV recording in a couple of minutes, but the same size video takes about 10-20 minutes, and it's hit-and-miss where it will end up when I press play.

> AVI=Container... what is in that container of your files?
Sorry - mostly Xvid & DivX Video, MP3 Audio.

> What version of MythTV are you currently using?
Mythbuntu 8.04.1 (MythTV 0.21.20080304-1)


I've seen something in the Mencoder manpages about using the -idx switch to rebuild the index 'to allow seeking'. Could I just run the files through mencoder to rebuild the index without reencoding?

TIA,

Simon

---

### Post by Plebster on 2008-12-21
Same problems here too. 

I have two myth frontends all showing the same symptoms:

Live TV - FF/RW works fine
Recorded TV - FF/RW works fine
DVD Disc - FF/RW works fine
DVD iso file - FF/RW works fine
divx/xvid file - FF/RW behaves as described above

I'm now sort of thinking this could be an FFMPEG codec issues...

Any views?

---

### Post by managementboy on 2008-12-22
> **Plebster said:**
> Same problems here too. 

I have two myth frontends all showing the same symptoms:

Live TV - FF/RW works fine
Recorded TV - FF/RW works fine
DVD Disc - FF/RW works fine
DVD iso file - FF/RW works fine
divx/xvid file - FF/RW behaves as described above

I'm now sort of thinking this could be an FFMPEG codec issues...

Any views?

I have never FF as you described, I will test it at home. Check the output of mythfrontend -v playback and see if you can make any sense of what it outputs. Sometimes its trivial.

have you updated your Mythbuntu setup to the latest "daily" builds? a lot of fixes with ffmpeg have been added over time.

---

### Post by SiHa on 2008-12-22
> Check the output of mythfrontend -v playback 
Good idea, I'll do that, thanks.

> have you updated your Mythbuntu setup to the latest "daily" builds

Ye Gods no! Quite apart from the fact that I wouldn't have a clue how to. I'm firmly of the 'if it ain't broke don't fix it' school. Everything else is great, and the WAF is starting to increase from a perilously low level. This is a minor niggle that I can live with if I have to. Certainly not worth potentially breaking a working frontend for.

---

