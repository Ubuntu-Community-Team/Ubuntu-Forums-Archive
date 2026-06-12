---
title: "how much is broken in 9.10?"
date: 2009-11-10
forum: Multimedia Software
---

### Post by Muahdib on 2009-11-10
I did not mean to "upgrade" I saw the automatic update window pop up and I kind of hit it without really reading I guess.. anyway now I have upgraded to 9.10 and I wish I had not. one of the programs that I use all the time is no longer working. handbreak, is not compatible. I cant find an eta on when it will 9.04 version of handbreak will be out which is supposed to work. 

anyone else have problems or work arounds for this?

---

### Post by mc4man on 2009-11-10
try installing the ubuntu .deb from here (latest snapshot

I don't use handbrake but installs, opens fine
(note that hb has dropped support for encoding with xvid

[http://handbrake.fr/snapshot.php](http://handbrake.fr/snapshot.php)

---

### Post by Muahdib on 2009-11-10
thanks Ill give that a try.

I dont use xvid at all.. h.264 all the way.

---

### Post by Muahdib on 2009-11-12
the snapshot works.. (ubuntu 9.10 32bit) its striped of lots of options but the next release will be striped as well. the only thing thats really broke is i can't get the silly thing to output a mp4. it wants to output everything to a m4v. that is a format I know nothing about not to mention that m4v wont play on my G2 which is the reason for ripping in the first place.. 
 
so maybe there is a conversion tool? that will take m4v to mp4? both use the same inccoder so thats good? anyone know of a conversion tool?

ron

---

### Post by HappyFeet on 2009-11-12
Uninstall the handbrake you have. There is a ppa version for karmic. Go [here]("https://launchpad.net/~handbrake-ubuntu/+archive/ppa") for it. Ask if you don't know how. Next time, clean install!

---

### Post by mc4man on 2009-11-13
> it wants to output everything to a m4v

I don't use hb but never uninstalled from other day. A few ....

If under view you get rid of the presets window then mp4 will be used as ext. (with either mpeg4 or h.264 encoding

If you leave preset window up then you need to click on legacy and below.

Maybe try changing the file ext. of the m4v to .mp4 and see (reads the same in mediainfo, plays with pc players the same

Use ffmpeg to copy to .mp4

Ex.
ffmpeg -i /home/doug/Videos/1.m4v  -acodec copy -vcodec copy 1.mp4


edit; make sure you uncheck that box about m4v in preferences

---

### Post by VertexPusher on 2009-11-13
M4V is MP4.

M4A is MP4, too.

The M4V/M4A extensions were introduced to distinguish between movies (MP4 Video) and music (MP4 Audio). M4A files do not contain video tracks.

There are similar conventions for Matroska (MKV/MKA) and Ogg (OGV/OGA) files.

Just rename the files.

---

### Post by Muahdib on 2009-11-19
HappyFeet, I went where you told me but.. I dont know what a PPA version.. also I did not find anything to download. is this a package? or is it something else.

---

