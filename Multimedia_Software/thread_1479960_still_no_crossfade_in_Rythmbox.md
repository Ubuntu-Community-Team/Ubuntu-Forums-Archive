---
title: "still no crossfade in Rythmbox"
date: 2010-05-11
forum: Multimedia Software
---

### Post by therieb on 2010-05-11
I have been unable to successfully use the crossfade backend in Rhythmbox since Intrepid.  I'm currently running a upgrade to Lucid (netbook remix) on an Asus eee 1005pe.  I am trying to use the crossfade backend to emulate gapless playback.  I have enabled the backend with the crossfade time set at 0.0 and the network buffer at maximum.  I made sure to restart Rhythmbox before testing.  I hear a significant gap with the crossfade set at 0.0 in m4a, mp3, and FLAC.  Making the crossfade longer doesn't work either.  Here is a list of the Gstreamer packages I have installed:

gstreamer 0.10 ffmpeg 0.10.10-1
gstreamer 0.10 pitfdll 0.9.1.1+cvs200802
gstreamer 0.10 tools   0.10.28-1
gstreamer 0.10-sdl 0.10.18-1ubuntu1
gstreamer 0.10-nice 0.0.10-2build1
gstreamer 0.10-gnonlin 0.10.15-1
gstreamer 0.10-pulseaudio 0.10.21-1ubuntu2
gstreamer 0.10-alsa 0.10.28-1
gstreamer 0.10-plugins-good 0.10.21-1ubuntu2
gstreamer 0.10-X 0.10.28.1
gstreamer 0.10-plugins-bad 0.10.18-1ubuntu1
gstreamer 0.10-plugins-base-apps 0.10.28.1
gstreamer 0.10-plugins-bad-multiverse 0.10.18-0ubuntu1
gstreamer 0-10-plugins-ugly 0.10.14-1
gstreamer 0-10-plugins-ugly-multiverse 0.10.14-0ubuntu1
bluez-gstreamer 4.60-0ubuntu8

Any help with this problem would be greatly appreciated.  I was able to crossfade m4a files at 0.0 seconds in Intrepid and haven't been able to since.  Is it possible to use the crossfade backend to emulate gapless playback with m4a and mp3 files?  Am I missing a package?  Do I need to get rid of something?  Any other diagnostics to run?  Thanks

---

### Post by lores on 2010-05-23
Same here - Asus Eeepc 1005p, Ubuntu Netbook Edition 10.04, most of the ubuntu-desktop packages installed, all up-to-date.

---

### Post by timkoop on 2010-05-25
Crossfade doesn't work for me either in 10.04, but it worked fine in 9.04.

---

### Post by lores on 2010-09-13
Any news here?
RB crossfading works well on my desktop PC (with Ubuntu 10.04), but doesn't work on my EeePC 1005p (with Ubuntu 10.04 UNE + desktop edition packages).

---

### Post by timkoop on 2010-09-13
It might have to do with the difference between an upgrade and a fresh install.  I also did a fresh install of 10.04 and I think it started working correctly after that.

---

### Post by lores on 2010-09-13
Not im my case. Both installs (desktop and eee) were clean.

---

### Post by therieb on 2010-09-19
Hey Timkoop:

If the crossfade engine is currently working, would you please post a list of Gstreamer packages on your machine as I did in the original post?  Thanks

---

### Post by therieb on 2010-10-03
Hello anyone and everyone who may still be reading this thread:

I recently came across a post on a German message board saying that the Clementine player successfully crossfades on an Asus 1005 PE.  I tried it on mine and IT DOES WORK!  That's the good news.  The bad news is that the minimum crossfade time appears to be 1000 miliseconds, which is not fast enough to use as fake gapless playback like I used to be able to do in Rhythmbox.  So for me, Clementine isn't the answer, but if you are looking for crossfading on the 1005 PE, this may work for you.  Thanks to whoever in Germany for posting, I can't remember your name.

---

### Post by lores on 2010-10-03
I just realised that, in fact, the crossfading effect in Rhythmbox **does work** on my 1005P, but the problem is that every time it is to be applied (e. g. when switching songs), there is a short (a few ms) period of silence - and if the crossfade duration is set long enough, a perfect crossfade can be heard after the short "muted" period is over. This, of course, completely contradicts the idea of crossfading, as the silence begins and ends totally abrupt.

Note: I have not realised this before as I had my crossfade duration set too short - so that the crossfading effect would be generated during the muted milliseconds...

---

### Post by ixifx on 2011-07-23
I am writing a couple of plugins for rhythmbox because I'm beginning to use my pc to dj at parties.  I noticed the gap and I can't seem to get it to go away.  this isn't very noticeable on headphones or with the volume low or possibly on much faster computers, but on my old AMD Athlon 2ghz it's VERY noticeable.  it's about a half second gap then the crossfade works as intended.

---

### Post by therieb on 2013-01-30
In case anyone is still reading this thread:

I have found a solution for 99% of my gapless playback needs

I am running Ubuntu 12.10 and Banshee 2.6.0

I can transfer music files to a Sansa Clip 8gb player from Banshee and gapless works in FLAC and (converted) Mp3.  Much of my music is legacy m4a and Banshee converts it to MP3 before putting it on the clip.  It is flawless, no pause, no pop, nothing.

Banshee plays gapless in FLAC without a problem.  The only issue left Banshee playing M4a files, which have a 1/10 second pop between tracks.

Anyone with a clue on how to get Banshee to recognize gapless in M4a, please respond.

---

