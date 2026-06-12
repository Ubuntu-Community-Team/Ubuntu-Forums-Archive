---
title: "audio for wma, wmal"
date: 2010-02-16
forum: Multimedia Software
---

### Post by raymondvillain on 2010-02-16
I have 64 bit Karmic installed, works well.

Does anyone know of an audio package available for Ubuntu that will play windows music files, such as .wma, or .wmal?  VLC, Rythmbox, and Amarok defintely will not work with these files.

If not, is there a package that will convert these files to a lossless format that can be played on Ubuntu?

---

### Post by andrew.46 on 2010-02-18
Hi raymondvillain,

> **raymondvillain said:**
> Does anyone know of an audio package available for Ubuntu that will play windows music files, such as .wma, or .wmal?  VLC, Rythmbox, and Amarok defintely will not work with these files.

If not, is there a package that will convert these files to a lossless format that can be played on Ubuntu?

It is all a little harder when you use the ***64bit*** Karmic but this is changing fast. At the moment libavcodec offers native decoding support for *wmapro* and *wmavoice* with the upcoming FFmpeg SOC offering a project to create a *wmalossless* decoder. So your best bet with a 64bit Karmic is to use the svn FFmpeg for any conversions:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

But if your copy of vlc uses a *current* libavcodec you will have playback of all wma files except for wmalossless...

All the best,

Andrew

---

### Post by mc4man on 2010-02-18
Having spent a little time with a 64 bit karmic a few suggestions.
As mentioned thru ffmpeg, mplayer and vlc you can deal with wma3 quite nicely, -  so only in regards to wmal.

One way was to build a 32 bit mplayer, which while is a little bit of work,  when done gives you all the capabilities found in 32 bit, and also works well with the 2 common front-ends - smplayer and gnome-mplayer. (the 64 ver. of these players is fine.

Certainly something I'd consider if keeping a 64 bit install

What was very easy to do was [run a 32 bit windows cli mplayer]("http://ubuntuforums.org/showthread.php?p=8752368#post8752368") build thru wine - though mainly useful for converting wmal to .wav, no tags. Having to use win. command line form is a bit of a pain.

If you have a number of wmal you wish to convert to flac, wavpack, apple lossless, whatever, then I'd consider this - plus also transfers tags and is extremely quick. (uses multicores

Won't go into details unless needed but I'd use [dbpoweramp]("http://www.dbpoweramp.com/") running in **wine 1.2**, there's a free 21 day full feature trial (lasts much longer but not relevant here), Used flac but virtually every format is available.

---

### Post by raymondvillain on 2010-02-20
Thanks for all your suggestions.  I tried dbpoweramp.  For some reason it chopped off the tail end of each track that it converted from wmal to flac.  I've about decided to just go ahead and rip all my music CD's one more time (from within Ubuntu) and save them as flac files.

Is brasero the best way to rip music CD tracks to flac files?

---

### Post by mc4man on 2010-02-20
> For some reason it chopped off the tail end of each track 
Interestinng, never seen that here, anyway I'm sure brasero would do ok for flac (hard to mess up a flac encoding), though I use either rubyripper or abcde.

If you have any issues with brasero there are several posts concerning using either RR or abcde. (atm rubyripper gui is broken in lucid, works fine otherwise or in other ubuntu releases

edit
some basic abcde info from andrew.46
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

a rr. thread, have an all .deb in post 86
[http://ubuntuforums.org/showthread.php?p=8219590#post8219590](http://ubuntuforums.org/showthread.php?p=8219590#post8219590)

---

### Post by raymondvillain on 2010-02-20
I have falsely accused dbpoweramp of "chopping off the tail end" of a file in the process of converting from .wma to .flac.  Actually Amarok is the culpirt.  The same file played in windows media player or rythmbox does just fine, only in amarok does the last second or so of sound get terminated.

Is there some trick to setting up Amarok so that it doesn't exhibit this glitch?

---

