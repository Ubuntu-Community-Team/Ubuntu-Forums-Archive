---
title: "VLC won't play .mp3s"
date: 2015-02-15
forum: Multimedia Software
---

### Post by wilberfan on 2015-02-15
The GUI opens, the file length is shown, but nothing plays.   I can watch VLC in the TaskManager run at 50% CPU--and it won't stop unless I kill it (ie, it won't 'close' normally).   I've purged and reinstalled a couple of times.  Ditto ubuntu-restricted-extras.   Plays video fine.  Lubuntu 14.10.

[edit]  Audacity plays the .mp3 without a problem.  Audacious crashes with a core dump.

---

### Post by wilberfan on 2015-02-15
Well, there's something about the particular .mp3 I was trying to open that is causing the problem.  I have no idea what it is, though.   A link to the file, if you're curious:  [http://www.mediafire.com/listen/71l6zk2cgmnxtl0/wait.wait.mp3](http://www.mediafire.com/listen/71l6zk2cgmnxtl0/wait.wait.mp3)

Other .mp3s open fine.

---

### Post by Yellow Pasque on 2015-02-15
I'm using Debian sid and the file plays okay for me, though it shows incorrect length in Audacious, and VLC gives some errors while seeking.
mp3val doesn't see anything wrong with the file.
*shrug*

---

### Post by mc4man on 2015-02-15
Something off about that mp3, with vlc-3.x here doesn't play, hangs vlc without error
(pretty much everything else plays, most with wrong time
running thru ffmpeg with copy seems to clean up, vlc is then happy, timeline seems correct, ect. (file loses 8MB of something?
[http://www.datafilehost.com/d/317611b4](http://www.datafilehost.com/d/317611b4)
^ seems a little slow today..

---

### Post by SeijiSensei on 2015-02-15
Plays fine here in the browser using Firefox 35.0.1 on Kubuntu 14.04.  Why do you need to use VLC?

I have ubuntu-restricted-extras installed and the Cisco H.264 codec.  I don't have anything else installed other than pipelight+Silverlight, which I don't think affects MP3 playback at all.

---

### Post by mc4man on 2015-02-15
> **SeijiSensei said:**
> Plays fine here in the browser using Firefox 35.0.1 on Kubuntu 14.04.  Why do you need to use VLC?

I'd assume the file is local & the OP likes to use vlc

---

### Post by SeijiSensei on 2015-02-15
Well, the OP pointed to a URL.  When I visited the URL, the file played in my browser. If I download the file, it plays in smplayer or Clementine.

---

