---
title: "ffmpeg Crashes upnp Media Server"
date: 2010-04-19
forum: Multimedia Software
---

### Post by SkilletHead on 2010-04-19
I run Ubuntu 9.10. I have updated all installed packages. I run a 32bit 3.6 ghz Intel P4 dual core with three monitors running on two video cards. All this works correctly. I am able to play video in Video Player and Audacious2 on any monitor.

I'm trying to run a upnp media server for my house. Myself and both my tenants have Playstation 3s, and I would like to host music, music videos, original content, and the backup copies of legally purchased DVDs over the network. I recently converted from Windows XP, and all of my media files were created by VLC on Windows XP, ripped with Winamp, edited and rendered with Sony Vegas, or downloaded from YouTube. I have tried both Mediatomb (from the repository) and Fuppes (from subversion) and had the same result with both.

Basically, whenever the media center tries to populate the database and search the files, ffmpeg returns an error that crashes the Media Center. I do not know enough to implement better error handling in the source. Both media servers, when running in the terminal, eventually return the same error message when scanning my sepearate hard drive for media. (~100GB of mp3, AVI, mpeg, and MP4 files) 

error code: /build/buildd/ffmpeg-0.5+svn20090706/libavformat/mov.c:1456: mov_read_trak: Assertion `st->duration % sc->time_rate == 0' failed.

The process then ends.

The weird thing is that this does not happen when I disable MP4 files in mediatomb (although I have not figured out how to replicate this feature in Fuppes) so I have reason to believe that something in the metadata for MP4 Files is throwing ffmpeg off. Even if the metadata is bad in the mp4 file, it shouldn't cause a crash.

I tried to compile mediatomb without ffmpeg support, but the ./configure script returned errors whenever I tried to append an option to the configure command. I then reinstalled all the ffmpeg packages in the Symantec Package Manager and still no luck.

Any other suggestions?

---

### Post by saviour on 2010-05-01
I have the exact same problem, it's a shame no one know the answer to this as it makes Mediatomb completely unusable.
How do you disable MP4 files?

---

### Post by Shhnap on 2010-05-07
To disable the mp4's in fuppes I believe that you just remove them from the default config. And you can compile fuppes without the ffmpeg support; actually it does that by default.

Also if you are getting that error then why not report it on the [fuppes bugtracker]("https://sourceforge.net/tracker/?group_id=141999&atid=751213") so that the developers can see it too. :)

---

### Post by buntunoob on 2010-05-07
Have you tryed the mediatomb forums?

---

