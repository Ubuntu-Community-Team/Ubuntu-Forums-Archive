---
title: "Miro - No sound"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by bowsercake on 2007-08-19
I got Miro to work yesterday with gstreamer instead of xine so that the video plays instead of crashing.  However, there is no sound with any video played through Miro even though I have sound for every other program.  The volume in the bottom right is all the way up and I've looked through the preferences for more options but I can not find anything useful.  Alsa mixer shows that nothing is muted.  I'm not sure if this is just me because I don't think this issue has been brought up before.  If anyone has any insight into my problem I would appreciate any help.

---

### Post by darkrabbit on 2007-11-17
I'm having the same problem with Miro on Suse 10.3. I don't have xine. It can play the video but won't play the audio. VLC will play both. Still trouble shooting.
--------------
Solution: Needed to Install Python Als
(I also installed jack but I don't know if that is needed too)

---

### Post by komputes on 2008-03-21
I'm using Hardy and have the same problem. VLC plays what miro downloads perfectly but Miro has no sound output.

---

### Post by Corey on 2008-04-07
I'm having the same trouble too. :( Prolly a conflict with pulseaudio. Say.. how did you get miro to use gstreamer?

---

### Post by komputes on 2008-04-07
I tried to find all the multimedia codecs and put them all on, now Miro worked for a bit, then all my computer audio went dead (can't get out of mute). Hardy seems to be having a lot of audio problems. Another issue is that no more than one audio application can work at once (try playing youtube video with rythymbox playing a song). I'm hoping all these bugs will be fixed shortly.

---

