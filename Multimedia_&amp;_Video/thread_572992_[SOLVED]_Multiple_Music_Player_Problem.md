---
title: "[SOLVED] Multiple Music Player Problem"
date: 2007-10-11
forum: Multimedia &amp; Video
---

### Post by sunil.pawar on 2007-10-11
I have Rhythmbox music player and totem music player, when i start any of them, and select any song it just hang off. and the whole screen get freeze . so re-install all music player , but it could not work. So what can i do? please..give any solution for that..

---

### Post by RomeReactor on 2007-10-11
Hi. Please open a terminal (Applications->Accessories->Terminal) and enter the following:
```
rhythmbox
```
then open a music file; if Rhythmbox crashes, post the error messages left on the terminal.

Is your music in another partition?

---

### Post by sunil.pawar on 2007-10-11
> **RomeReactor said:**
> Hi. Please open a terminal (Applications->Accessories->Terminal) and enter the following:
```
rhythmbox
```
then open a music file; if Rhythmbox crashes, post the error messages left on the terminal.

Is your music in another partition?

i  run rhythmbox in terminal it open the rhythmox, no error in terminal,   and i try to play it hang up again

---

### Post by RomeReactor on 2007-10-11
After trying to play a file, does it crash? or does it just freeze? If you have desktop effects on, try disabling them and try again. What version of Ubuntu do you have?

---

### Post by sunil.pawar on 2007-10-11
> **RomeReactor said:**
> After trying to play a file, does it crash? or does it just freeze? If you have desktop effects on, try disabling them and try again. What version of Ubuntu do you have?

After Playing it just freeze and i also desktop effect is off, i use ubuntu 7.04(feisty fawn), i try VLC, Rhythmbox,XMMS, totem Movie Player, it freeze for every player.

---

### Post by soxs on 2007-10-11
Same for me...

I allready purged and reisntalled gnome, but it didn' change anything. (running 7.10 beta)

---

### Post by Boef666 on 2007-10-11
Reading this, my guess is your codecs, it was what caused the problem of freezing while trying to play some formats in embedded pages. on my xubuntu 6 version till I installed them all.
Looking for them now in this forum to do it again for version 7.
Must be using the wrong search terms though as I can't seem to find the list off all synaptic packages to install. But they are here, as I found them here before, somewhere...

Hope this helps.

---

### Post by soxs on 2007-10-12
It's definitly realted to alsa-stuff, as my login sound still workx (as i'ts oss)

---

### Post by sunil.pawar on 2007-10-15
> **soxs said:**
> It's definitly realted to alsa-stuff, as my login sound still workx (as i'ts oss)

My login sound work fine, i m not able to run the mp3, wmv, file format

---

### Post by sunil.pawar on 2007-10-16
i have problem with freezing the player when started, when i forcely check the system it check all configuration and recover the problem simply..

---

### Post by ubromtoo on 2007-12-31
Sunil.Pawar  :

      I have the same problem now ; please tell me how to do what you did to fix things !

---

### Post by lurkus ignoramus on 2008-01-01
I also had a number of issues getting my media to function correctly.  Unfortunately, I did not keep good track of the various methods I attempted to fix this issue.  I'm certain that installing **gstreamer**, and some other codecs, was a major part in fixing my issues... However, after a day of troubleshooting, I realized that my speakers were plugged into the wrong output.  Switching that, after all the other troubleshooting, got things working with a quickness. :?

I also found that Rhythmbox and Totem did not meet my multimedia needs satisfactorily.  I installed Kaffeine (KDE, but it runs fine in GNOME) and have found it to play every type of media I need.

All the information I needed to fix my problems was found in the forums. I know I read more than one thread, but I think much of the relevant information is located here (have you tried this?): [http://ubuntuforums.org/showthread.php?t=413624]("http://ubuntuforums.org/showthread.php?t=413624")

Good luck!  We all need it. ;)

---

