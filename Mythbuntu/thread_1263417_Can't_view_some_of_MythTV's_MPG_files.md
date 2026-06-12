---
title: "Can't view some of MythTV's MPG files"
date: 2009-09-11
forum: Mythbuntu
---

### Post by yonkiman on 2009-09-11
I'm trying to delete all the orphaned mpg files (2441_20090828233000.mpg for example) in my myth recordings directory.  I tried some of the scripts to do this, but wanted to view the file before I deleted it to make sure it was nothing I cared about.  This is where it gets weird...

I noticed that when I try to directly play many of those files, my movie players (vlc, movie player, mplayer) have a lot of trouble with them.  Some files play fine, but others freeze on the first frame, or skip ahead at around 100x, flying through a one hour file in just a few seconds.  And the weird thing is that as it flies through the file, I seem to see frames from multiple different recordings.  For example, one file might starts off as an episode of Nova, then show a few frames from Saturday Night Live, before ending as a family guy.

So it seems like my mpg files (or my filesystem) are messed up.  But all these shows play back absolutely fine inside Myth.  I haven't had any problems watching any of the recordings I've made.

Is this just me or has anyone else run into this?  Can everyone else play their MythTV mpg files outside of MythTV without any problem?

---

### Post by Tclarkie on 2009-09-11
Use mplayer, it works

---

### Post by shazbut on 2009-09-11
I get this with anything recorded on my TV card, whether in MythTV or otherwise.  Apparently it's caused by recording errors throwing the streams out of sync.  I get around it by demuxing then remuxing the file:
use projectx to demux, then mplex to remux the resultant files (.m2v, .mp2, .ac3).  It's a bit of work, but after that I can view and skip through the files.

---

### Post by yonkiman on 2009-09-12
> **Tclarkie said:**
> Use mplayer, it works

I explicitly said mplayer doesn't work.  Which I agree is odd, because I thought mplayer was the engine mythTV used to play the files.

Hence my posting...

---

### Post by yonkiman on 2009-09-12
> **shazbut said:**
> I get this with anything recorded on my TV card, whether in MythTV or otherwise.  Apparently it's caused by recording errors throwing the streams out of sync.  I get around it by demuxing then remuxing the file:
use projectx to demux, then mplex to remux the resultant files (.m2v, .mp2, .ac3).  It's a bit of work, but after that I can view and skip through the files.

Thanks, shazbut.  I've installed Project X but it's looks like it's nontrivial to operate!  Fortunately it's the weekend...  :D

---

### Post by klc5555 on 2009-09-12
> **yonkiman said:**
> I'm trying to delete all the orphaned mpg files (2441_20090828233000.mpg for example) in my myth recordings directory.  I tried some of the scripts to do this, but wanted to view the file before I deleted it to make sure it was nothing I cared about.  This is where it gets weird...

I noticed that when I try to directly play many of those files, my movie players (vlc, movie player, mplayer) have a lot of trouble with them.  Some files play fine, but others freeze on the first frame, or skip ahead at around 100x, flying through a one hour file in just a few seconds.  And the weird thing is that as it flies through the file, I seem to see frames from multiple different recordings.  For example, one file might starts off as an episode of Nova, then show a few frames from Saturday Night Live, before ending as a family guy.

So it seems like my mpg files (or my filesystem) are messed up.  But all these shows play back absolutely fine inside Myth.  I haven't had any problems watching any of the recordings I've made.

Is this just me or has anyone else run into this?  Can everyone else play their MythTV mpg files outside of MythTV without any problem?

Generally I use xine to play my mythtv mpg files when not using the internal player (sometimes I'll have copied the files over to a Windows box, and will use Media Player). As long as the file's not corrupt, none of these methods have any problems. Sometimes file corruption (or rarely audio sync problems) will render these files unusable by other players, while they will still play acceptably in myth. In some cases, the file can be made usable for other players by doing a mythtranscode --mpeg2 which fixes small errors; sometimes the file is salvageable by using nuvexport (--transcode or --ffmpeg) to make a high-quality avi, which in the process is repaired and becomes playable in just about anything. 

But every once in a while, the file is just toast. Myth corrects errors to play it internally, but the file is just not worth trying to do anything else with.

---

### Post by shazbut on 2009-09-13
> **yonkiman said:**
> Thanks, shazbut.  I've installed Project X but it's looks like it's nontrivial to operate!  Fortunately it's the weekend...  :D

The graphical front end is confusing, but it seems to work with the defaults.  Fortunately it has a command line mode too, so the whole process can be scripted.  It's still a fair bit of messing around just to find out what's in a particular file.  [Here]("http://www.avidemux.org/admWiki/index.php?title=Editing_MPEG_capture_%28DVB_or_IVTV%29") is where I got the info about this issue from.

---

