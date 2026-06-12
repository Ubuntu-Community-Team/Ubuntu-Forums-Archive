---
title: "MP3 support in Amarok 2, Kaffeine"
date: 2008-12-20
forum: Multimedia Software
---

### Post by ostracize on 2008-12-20
Since I upgraded from Amarok 1.4 to Amarok 2, mp3 files are no longer playing in Amarok. There was no problem before, now it doesn't work anymore. Amarok shows the right length in the display, but if I try to play something, it just sits there and does nothing. If I keep trying to play the same file, it eventually pops up with "Too many errors encountered in playlist. Playback stopped." (5 errors I think). This problem occurs regardless of which mp3 file I try.

Kaffeine also doesn't play MP3 files (I think this worked fine before).
Amarok plays OGG files fine.
Mplayer plays MP3 files fine.
I have kubuntu-extra-codecs installed.
I have libxine1-ffmpeg installed.
I am running KDE 4.1.3.

---

### Post by logos34 on 2008-12-20
> **ostracize said:**
> 
Amarok plays OGG files fine.


I don't have an answer to your question (I'm still using amarok 1.4) but tell me, do you have gapless playback of ogg files on amarok 2?  ogg and mp3s often skip on mine (never have figured out if it's amarok or the xine backend engine that's causing the problem)

---

### Post by ostracize on 2008-12-21
> **logos34 said:**
> I don't have an answer to your question (I'm still using amarok 1.4) but tell me, do you have gapless playback of ogg files on amarok 2?  ogg and mp3s often skip on mine (never have figured out if it's amarok or the xine backend engine that's causing the problem)
I can't say I've ever experienced any trouble with Ogg files on Amarok (1.4 or now on version 2).

Back to my original problem, can anyone provide any insight please? I have basically no music now. 99% of my collection is in mp3 form.

---

### Post by motoperpetuo on 2008-12-21
i have basically the same problem. happens with m4a (itunes format) files too. i don't have anything on .ogg format, but maybe i'll rip a cd to it to test.

i can't find any answers to this on the amarok or fedora forums (i recently switched to fedora 10, which has amarok 2 in its repositories). a few others on those forums have mentioned the problem, but so far no solutions.

---

### Post by SuperSonic4 on 2008-12-21
amarok 2 would play some mp3 files but not others. It is possible that it does not support vbr mp3 or something like that, say a certain bitrate.

---

### Post by ostracize on 2008-12-22
> **SuperSonic4 said:**
> amarok 2 would play some mp3 files but not others. It is possible that it does not support vbr mp3 or something like that, say a certain bitrate.
If that were the case, does anyone have an example of an mp3 that DOES work? 

I've been trying podcasts in mp3 format too and none of them work either.

---

### Post by ostracize on 2008-12-22
*Bump* (to try to take advantage of a different time of day.)

---

### Post by oiad on 2008-12-29
sudo aptitude install libxine1-ffmpeg


I found this on the amarok forum and it fixed the problem for me.

---

### Post by pingoo on 2009-01-03
> **oiad said:**
> sudo aptitude install libxine1-ffmpeg


I found this on the amarok forum and it fixed the problem for me.
Thank you, it works also here.
@others: installing libxine1-ffmpeg, make sure that you have selected xine as backend in the system settings->Multimedia->Backend Tab. I switched from gstreamer ;)

Bye

---

### Post by ostracize on 2009-01-08
Googlers can refer to this thread for my solution:

[http://ubuntuforums.org/showthread.php?p=6519558](http://ubuntuforums.org/showthread.php?p=6519558)

---

### Post by abn91c on 2009-01-08
I had that problem upgrading to 2.0, I solved by completely purging amarok, reinstalling 1.xx then upgrading to 2.0 with ```
sudo apt-get install amarok-kde4
```
Also add this repository **First **if you haven't done so already:
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

---

### Post by Speed Demon on 2009-01-11
I couldnt even launch amarok with out it asking me to install libxine-blah blah blah. It works fine for me!

---

### Post by ScttN485 on 2009-02-08
By an chance, was anyone trying to get it to work in gnome? It worked for me when I first installed ubuntu, but I haven't been able to get Amarok 2 to play my MP3s on here when I reinstalled the operating system. I'm having the same problems as described by the first post, and none of these solutions have helped.

I am rather new at this so I'm a little lost :-P

I already have libxine1-ffmpeg installed and I don't have a permissions problem. Any help would be greatly appreciated. :)

---

### Post by DaanRiver on 2009-05-06
> **ScttN485 said:**
> By an chance, was anyone trying to get it to work in gnome? It worked for me when I first installed ubuntu, but I haven't been able to get Amarok 2 to play my MP3s on here when I reinstalled the operating system. I'm having the same problems as described by the first post, and none of these solutions have helped.

I am rather new at this so I'm a little lost :-P

I already have libxine1-ffmpeg installed and I don't have a permissions problem. Any help would be greatly appreciated. :)
this fixed it for me! (also a gnome user with the same problems):

**sudo apt-get install phonon-backend-xine**

got the solution from:
[http://bamit0890.wordpress.com/2009/04/27/amarok-2-sound-problem-in-ubuntu-904/#comment-14](http://bamit0890.wordpress.com/2009/04/27/amarok-2-sound-problem-in-ubuntu-904/#comment-14)

---

### Post by spedoinkle on 2009-11-05
ok to update the solution for this fix. instead of running libxine1-ffmpeg
do this:

sudo aptitude install libxine1-all-plugins

Description for all of you:

This is the xine media player library (libxine).

Libxine provides the complete infrastructure for a video/media player. It
supports MPEG 1/2 and some AVI and Quicktime videos out of the box, so you
can use it to play DVDs, (S)VCDs and most video files out there. It
supports network streams, subtitles and even MP3 or Ogg files. It's
extensible to your heart's content via plugins for audio and video output,
input media, demuxers (stream types), audio/video and subtitle codecs.

This empty package is just for your convenience and depends on all
available xine plugin packages.

---

