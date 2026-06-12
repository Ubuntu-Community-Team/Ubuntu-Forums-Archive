---
title: "No sound in Flash (may be a challenge)"
date: 2009-01-18
forum: Multimedia Software
---

### Post by AmandaKerik on 2009-01-18
This is the second thread I've posted about this issue, but as the default choice on the forums (here) is to NOT subscribe... I have no idea where it is.

I used a torrent version of Ubuntu's livecd (and then alt livecd due to limited space to work) [edit] to upgrade to Intrepid from Hardy [/edit]. At first I had no sound, but reverting to an older kernel fixed most of those issues.

Unfortunately reverting the kernel wasn't the first thing I tried - I've uninstalled all the sound related packages (and it took more than that with it) then reinstalled them (and had to put other packages back - like gnome and ubuntu-desktop).

As it stands I have sound on everything except flash.

Yes, I've tried editing Firefox's "which sound driver do I use" to aoss, but it didnt' work.

I've also reinstalled all the flash packages and sound packages I have installed in case there was something wonky there.

I started to uninstall pulseaudio but as it would take ubuntu-desktop with it (again!?) I aborted.

Please tell me the info I need to provide to get good assistance with this, I'm at my wit's end.

---

### Post by gandaran on 2009-01-19
if you are running ubuntu 8.04 remove flash 9 try flash 10 from adobe.com or just fix pulseaudio [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by AmandaKerik on 2009-01-19
Ok, I've narrowed it down to pulseaudio - if I kill it and restart Firefox, flash videos work.
I seem to be using Flash 9.

I'm going to try Flash 10, then tinker with the pulseaudio if it doesn't quite work.

Also: thank you sooo much for the fast reply!

---

