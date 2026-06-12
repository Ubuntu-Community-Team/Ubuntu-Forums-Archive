---
title: "Music Codec?"
date: 2007-10-11
forum: Multimedia &amp; Video
---

### Post by mhgrier on 2007-10-11
Hello--

I'm a new user to Ubuntu and Linux in general, and this is my first forum post here.  Making the switch hasn't been terribly difficult on the whole, but I have still been having a few issues I could use some help with.

1) I have my music library on an external harddrive (let's call it HDD).  I downloaded VLC media player to play some music files (and video files), but I was looking for a library-based program more along the lines of iTunes or WMP that I could use for Ubuntu.  I came across several, such as Amarok, WMMS, and Songbird.  Interestingly enough, I can play all of my HDD music files on VLC-- there is no problem playing any of my mp3 files whatsoever.  However, when I try to use any of these other 3 media players, some give me an "error," while others give me a "cannot play file."  Either way, none of these players will accept my .mp3 files off the external HDD.  So then I took a song off of my external HDD and dragged it onto my desktop-- no dice-- the file still wouldn't play.  Is there a codec that VLC might have that these programs may not have by default?

2) On Windows, I could edit all of the properties of my external HDD, but on Ubuntu, the HDD seems to be something of a "read-only" drive, where I can drag stuff onto my desktop or play files on VLC right off of the hard drive, but I can't edit any of the contents (delete files or add files to the volume).  Any help here?

Thanks so much.

---

### Post by RomeReactor on 2007-10-11
Hi. VLC comes with its own codecs, so that's why it's able to play MP3s without installing any additional packages. To enable MP3 playback for most of the other players, open Synaptic (System->Adminsitration->Synaptic Package Manager) and search for **libxine1-ffmpeg**, **libxine-extracodecs**,  **gstramer0.10-plugins-ugly**, and **gstramer0.10-plugins-ugly-multiverse**. Or, to install them through the terminal (Applications->Accessories->Terminal):
```
sudo apt-get install libxine1-ffmpeg libxine-extracodecs gstramer0.10-plugins-ugly gstramer0.10-plugins-ugly-multiverse
```

---

### Post by Scheater5 on 2007-10-11
First off, what filesystem is the harddrive?  If it is NTFS, that would explain why you can read, but not write to it.  Read-write access to an NTFS drive is not by default supported on 7.04 and before, but will be on 7.10 through NTFS-3g.  Someone else will have to walk you through installing that on Feisty.  

As for the codecs, what you want is more than likely illegal in your area.  This is something often overlooked, but as a new user I feel you should know this as it is the reason these codecs are not included by default in Ubuntu.  I believe certain media players such as Amarok require you to download not only the codec, but additional libraries to use the codec on that particullar program.  I can't remember what you're looking for off the top of my head.  
As an aside, I highly recommend Amarok.  The solution to your problem is amazingly simple, I just can't remember exactly what you need.  And once that is solved I think you'll find Amarok beats the pants off of iTunes.

---

