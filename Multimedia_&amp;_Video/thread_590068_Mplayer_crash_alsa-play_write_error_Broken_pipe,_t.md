---
title: "Mplayer crash: alsa-play: write error: Broken pipe
, trying to reset soundcard"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by userthebuntu on 2007-10-24
Hello people.


I'm running kubuntu 7.04 the feisty of fawness and have the following soundcard in my system:

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller

Doing lsmod I find: 

atiixp                  7440  0 [permanent]

Which I thought was the correct alsa driver for my soundcard.

Anyways, now when going to my shell and starting up mplayer (mplayer soundfile.mp3 or mplayer -playlist playlist.txt) mplayer does actually run and play my music - for as long as I keep the shell it is running in active and focused.

That is to say whenever I minimize the shell, click on another window or change virtual desktops mplayer crashes and keeps printing:

alsa-play: write error: Broken pipe
alsa-play: trying to reset soundcard
alsa-play: write error: Broken pipe
alsa-play: trying to reset soundcard
alsa-play: write error: Broken pipe
alsa-play: trying to reset soundcard
alsa-play: write error: Broken pipe
alsa-play: trying to reset soundcard
alsa-play: write error: Broken pipe
alsa-play: trying to reset soundcard
etc....


Anyone have any suggestions?


Thanks in advance!

---

### Post by userthebuntu on 2007-10-25
Nodody have an idea?

Do you require additional infos from my computer?

---

### Post by userthebuntu on 2007-10-26
Thought I'd give this a last bump.

Please anyone have an idea?

---

### Post by ColdFusionEESG on 2008-03-03
Same issue here...same ATI card...same errors and behavior....just on 7.10 Gutsy.

Really flipping annoying ;-)

Cheers

---

### Post by ripps818 on 2008-04-11
I have this error too. But for some reason, I just select OSS instead of Alsa and it works. Sounds perfect too.

---

### Post by Peter Cordes on 2008-04-17
> **ripps818 said:**
> I have this error too. But for some reason, I just select OSS instead of Alsa and it works. Sounds perfect too.

 Yeah, OSS works better for me, too.  But it fast-forwards sometimes ("playing" maybe 30 seconds of audio in 1 second.)  This is better than getting permanently stuck, at least.  The glitches happen when e.g. switching windows.  (metacity gnome, playing audio with audacious.)


 Anyone reported this on lauchpad or upstream to alsa-project.org?

---

