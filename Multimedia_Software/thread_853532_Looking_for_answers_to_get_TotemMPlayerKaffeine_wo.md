---
title: "Looking for answers to get Totem/MPlayer/Kaffeine working."
date: 2008-07-08
forum: Multimedia Software
---

### Post by Roasted on 2008-07-08
So, I'd like to get all of these media players working so I can pick and choose what I'd like to use. After a serious audio issue I've been having with VLC, I decided to look elsewhere.

Kaffeine - When I put a DVD in and play it through Kaffeine, I get this error. This DVD Video is encrypted. To be able to watch it you will need to install libdvdcss by running from a console: sudo /usr/share/doc/kaffeine/install-css.sh. In some countries it is illegal to install the decryption software without permission from the video copyright holder.

Thing is, I did the libdvdcss thing. I got the updates. Still.. I get this error.

MPlayer - Error I get is "No stream found to handle url dvd://1"
How do I fix that?

Totem - I installed Ubuntu-restricted-extras and now Totem works. Thing is, when I go to fast forward through the DVD, it just freezes, as if it has to buffer... yet... it buffers forever... I watch a lot of live concert DVDs, so I don't always want to watch from front to back, sometimes I want to pick and choose the song. Is Totem known to be slow at fast forwarding??

Note - I installed the Medibuntu package. I thought the point behind the Medibuntu package was to eliminate the hassle of doing this and finding particular codecs that each program uses. Yet, I'm still running into this. Is there something additional to the Medibuntu package I was supposed to install or something??

---

### Post by y6FgBn)~v on 2008-07-08
Roasted I was wondering did you follow the instructions from this guide?

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I know you said you installed the Medibuntu package but the steps listed in the guide go into a bit more detail.

Let us know if worked or not.

---

### Post by mc4man on 2008-07-08
Both kaffeine and mplayer have a default dvd device set. The default for both is /dev/dvd. Change that in settings -> xine engine parameters-> media for kaffeine and in preferences -> misc in mplayer (gmplayer). If you don't know what to change to (/dev/dvd1 would be a good bet) then run sudo lshw -C disk to see your drive(s) and some logical names.

---

### Post by Roasted on 2008-07-08
I followed that guide, and it got me no where. This is unreal.

I right clicked on my dvd drive where the dvd was inserted and hit play in kaffeine. Kaffeine has video that is unviewable and awful audio. There is clearly something wrong with that program. MPlayer provides nothing of any help, seeing as though it gives me the same error.

What I don't get is... I installed the medibuntu repository. Isn't the medibuntu repository supposed to make everything just consolidated into 1 step? I thought everything I needed would be included in it. Why am I having issues?

I'm half tempted to just format it and try everything else over with medibuntu again. I installed 64 bit last night and everything was working perfect. I go back to 32 bit and now I'm in a train wreck again.

---

### Post by Roasted on 2008-07-08
I'm formatting it once I get done with this post.

I tested the same mp3 in the following programs.

MPlayer Movie Player - horrible audio.
Totem Movie Player - clear audio.
Audacious - clear audio.
Gecko Media Player - horrible audio.
VLC Media Player - horrible audio.
Kaffeine Media Player - middle of the road in terms of audio.

I'm just going to do a fresh format and redo the medibuntu repository.

---

