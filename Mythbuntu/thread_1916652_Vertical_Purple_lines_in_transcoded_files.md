---
title: "Vertical Purple lines in transcoded files"
date: 2012-01-28
forum: Mythbuntu
---

### Post by sdsnyr94 on 2012-01-28
I had upgraded my 11.04 setup to 11.10 a while back, and had multiple issues. Once I got everything stable again, I noticed that when I did a lossless transcode, there would be vertical purple lines right where the cut points were, and they would stay on screen for roughly 10-20 frames. I also had these same lines appear randomly, but roughly every 2-3 minutes throughout the show.

Thinking that it was from my botched upgrade, I backed up all my data and setup a fresh 11.10 install. Needless to say, I am still sitting in the same boat.

This is very similar to a closed trac ticket : [http://code.mythtv.org/trac/ticket/10110](http://code.mythtv.org/trac/ticket/10110)
You can use the example posted there to see what the vertical purple lines look like for me. According to the user who posted that Trac ticket, they resolved this by upgrading ffmpeg/libav*..... that has not helped my problem at all.

One other note is that if I go into the Transcoder Profiles, and edit one of the profiles (Let's say 'High Profile') to not do a lossless transcode and to use the 'MPEG-4' Codec, the whole video is full of those purple lines.

Has anyone come across this issue and been able to resolve it? Anyone have any suggestions?

Thanks in advance for the help!

P.S. I just updated to 0.24.2 yesterday and that did not help. Also, before I wiped out my setup I tried upgrading to 0.25, and that did not help either (but I was still thinking it was my botched OS upgrade at that point.)

---

### Post by sdsnyr94 on 2012-01-29
Anyone?!?   Please don't make me go through the hassle of setting up a new backend based on 11.04, which is what I will have to do if there are no suggestions.

---

### Post by nickrout on 2012-01-29
make sure you are not using a playback profile that includes libmpeg2.

Does this occur when playing back via other software, eg vlc or mplayer?

---

### Post by sdsnyr94 on 2012-01-29
> **nickrout said:**
> make sure you are not using a playback profile that includes libmpeg2.

Does this occur when playing back via other software, eg vlc or mplayer?

Happens in everything I play it in... VLC, Mplayer, XBMC, MythTV.... and it happens in every MythTV playback profile.

I just finished restoring my database to an 11.04 fresh install ..... no purple lines in the transcode. I can't believe this has not happened to more people.

---

### Post by nickrout on 2012-01-29
> **sdsnyr94 said:**
> Happens in everything I play it in... VLC, Mplayer, XBMC, MythTV.... and it happens in every MythTV playback profile.

I just finished restoring my database to an 11.04 fresh install ..... no purple lines in the transcode. I can't believe this has not happened to more people.

Maybe not many are transcoding. Always seemed like a waste of CPU cycles to me...

---

### Post by sdsnyr94 on 2012-01-30
I use the lossless transcode to remove the commercials that I flagged, so that I can watch using XBMC as my frontend.

So what is different between 11.04 and 11.10 that would affect the transcoder? 

I still have my 11.10 install on a separate HDD, so if there are any suggestions I can go back and see if they resolve it.

---

### Post by nickrout on 2012-01-30
mythtranscode links to a large number of libraries as ldd $(which mythtranscode) will show you. Could be an update to any of them.

Have you tried ffmpeg/libav from medibuntu?

---

### Post by sdsnyr94 on 2012-01-30
> **nickrout said:**
> mythtranscode links to a large number of libraries as ldd $(which mythtranscode) will show you. Could be an update to any of them.

Have you tried ffmpeg/libav from medibuntu?

Yeah, I tried that first based on the resolution in the TRAC ticket that was opened, but that did not help... then I tried ffmpeg/libav direct from ppa:jon-severinsson/ffmpeg... still no change.

---

