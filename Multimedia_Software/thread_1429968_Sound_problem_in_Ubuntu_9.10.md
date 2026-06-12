---
title: "Sound problem in Ubuntu 9.10"
date: 2010-03-14
forum: Multimedia Software
---

### Post by ulriksvensson on 2010-03-14
I have a strange problem with the sound on my laptop. If I right-click on an mp3 file and open it with either Amarok or mplayer the tune starts playing but there's no sound. If I do sudo mplayer path/to/some/tune.mp3 it works fine.

I run spotify under wine and it works fine.

If I do grep 'audio' /etc/group I can see that my user is listed there as it should be.

How can I fix this? I'm using KDE4 as desktop env.

//Ulrik

---

### Post by ulriksvensson on 2010-03-18
> **ulriksvensson said:**
> I have a strange problem with the sound on my laptop. If I right-click on an mp3 file and open it with either Amarok or mplayer the tune starts playing but there's no sound. If I do sudo mplayer path/to/some/tune.mp3 it works fine.

I run spotify under wine and it works fine.

If I do grep 'audio' /etc/group I can see that my user is listed there as it should be.

How can I fix this? I'm using KDE4 as desktop env.

//Ulrik

Solved this by following [this]("http://ubuntuforums.org/showthread.php?t=789578").

---

