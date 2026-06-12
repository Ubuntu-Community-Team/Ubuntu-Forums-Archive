---
title: "VLC 1.0.5 play in Ubuntu 11.04"
date: 2011-04-16
forum: Multimedia Software
---

### Post by qzpac on 2011-04-16
Can i play .mp4, mp3, .mkv file in VLC 1.05 in [SIZE=2]ubuntu 11.04?[/SIZE]

---

### Post by KegHead on 2011-04-16
Hi!

Just a follow up;

I'm unable to play any video's in VLC.

Anyone?

KegHerad

---

### Post by varunendra on 2011-04-18
> **qzpac said:**
> Can i play .mp4, mp3, .mkv file in VLC 1.05 in [SIZE=2]ubuntu 11.04?[/SIZE]
It seems that version 1.05 did have some temporary issues, not sure if they persisted (see [here]("http://forum.videolan.org/viewtopic.php?f=14&t=73049") and [here]("http://forum.videolan.org/viewtopic.php?f=14&t=75415"))
But anyway, I think version 1.14 or higher is available in current repositories, so why not just try the latest?
Besides, you may certainly try 1.05 yourself if you already have it, although being such an older version, I guess it may have dependency issues with Ubuntu 11.04. But again, you always can remove or replace it with the newer version, if having issues, without affecting rest of the system. So I'd say go ahead, try for yourself if you already have it. Otherwise just install the latest one from the repositories.


> **KegHead said:**
> Hi!

Just a follow up;
I'm unable to play any video's in VLC.
KegHerad

Did you try reinstalling it? Maybe there's some broken plugin that will get fixed by 'completely remove - reinstall' operation..! Just a wild guess. If you already tried this then maybe a bit detailed info about your existing setup and what all you've tried may help.

---

### Post by wolfen69 on 2011-04-18
If you're going to reinstall, it's best to completely remove, then
```
sudo apt-get clean && sudo apt-get autoremove
```
then also remove the vlc config file in your home folder. Then reinstall.

If that doesn't work, then obviously there are other things we need to consider.

---

### Post by KegHead on 2011-04-18
Hi!

Did a reinstall...solved problem.

KegHead

---

