---
title: "Pulse audio not working after setting up Jack/ardour"
date: 2013-08-05
forum: Multimedia Software
---

### Post by deathguppie on 2013-08-05
So I set up ardour/jack following instructions adding my user to audio, and changed the file in /etc/security/limits.d/audio.conf so that it looked as I've written it there.  

Ardour and Jack work fine.  However pulse audio does not work for this user.  If I log out and log in as another user pulse audio works fine.  The only program that seems to work not using jack is mpg123, and I can't figure out what sound card it defaults to.  

Anyway has anyone else dealt with this?

---

