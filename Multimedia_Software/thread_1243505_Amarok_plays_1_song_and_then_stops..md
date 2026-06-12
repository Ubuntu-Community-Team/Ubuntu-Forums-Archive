---
title: "Amarok plays 1 song and then stops."
date: 2009-08-18
forum: Multimedia Software
---

### Post by Killroykill on 2009-08-18
I have been using amarok to play my music. I haven't really messed with settings or anything, but ever since last night it will only play the selected song off the play list and then it will stop (like it is the last song or something)

In the past it has played the next song and that is the whole point of a playlist. with it stopping after each song and requiring me to click on the next song, it kinda defeats the purpose. 

Anybody know how to fix this?

I am using 9.04. with kernal 2.6.28-15-generic and Gnome 2.26.1

---

### Post by resist1390 on 2009-09-01
I am having this problem as well.

---

### Post by Beta54 on 2009-09-06
Hey, make sure that you have phonon-xine and xinelibs installed, then go to systemsettings-> multimedia-> backend and select xine

---

### Post by mechgt on 2009-10-13
Amorok was playing fine for me, and is now doing this for me as well.  I checked the settings and Xine was already selected.  phonon-backend-xine and libxine1 were already installed as well.

I wonder if some update caused this, because I had no problem before.

---

### Post by deniswal on 2009-11-24
Taken from a redhat user list :

[I]Comment #6 From  Thomas Janssen  2009-07-10 09:01:23 EDT  -------

I think i recall how i "fixed" it. I removed .kde/share/apps/amarok/* and
started then amarok. I had to scan my music again and it was working as
expected after.

HTH

-- 
Fedora Bugzappers volunteer triage team
[https://fedoraproject.org/wiki/BugZappers](https://fedoraproject.org/wiki/BugZappers)  [/I]

This worked for me...
Denis

---

### Post by arrancaru on 2009-11-24
How I fix: Settings -> Configure Amarok -> Playback -> Configure -> Music -> PulseAudio -> Prefer -> Apply.

---

### Post by biodiesel-bri on 2009-11-30
Deniswal's suggestion worked for me, thanks!

---

### Post by peddanet on 2010-03-14
> **arrancaru said:**
> How I fix: Settings -> Configure Amarok -> Playback -> Configure -> Music -> PulseAudio -> Prefer -> Apply.

This Is The Solution! Much better than the stupidity of deleting the whole directory of kde!
 

Thanks!:popcorn:

---

### Post by daemonraco on 2010-03-27
My solution was quite easy
mysql> drop database amarokdb;

I hope it could help to someone
Seeya! ^__^'

---

### Post by shamun on 2011-04-25
for me a plain restart of amarok did it :)

---

