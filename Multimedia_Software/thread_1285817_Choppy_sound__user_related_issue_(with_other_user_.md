---
title: "Choppy sound / user related issue (with other user profile sound is perfect)"
date: 2009-10-08
forum: Multimedia Software
---

### Post by knarfomat on 2009-10-08
Hi there...

here goes another sound trouble:

what has happened:
- fresh install, sound was perfect
- installed Mplayer and ever since sound is skipping and choppy every 4 to 5 seconds or so 
- this problem does occur system wide now! so also in Rythmbox, etc. (In the meantime I purged Mplayer)

what I found so far:
- I created a new user and with the new user profile the sound is perfect!

what I tried so far:
- followed the Comprehensive Sound Guide (with no success)
- adjusted the pulse daemon.conf values: default-fragments default-fragment-size-msec
- purged and reinstalled almost everything related to sound confs
- since the new user-profile gives clear sound, I tried to copy the .pulse-cookie and the .pulse dir into my standard user profile but no lasting success either

So has anyone an idea how/where to reset all sound related conf-files in a home directory? I tried to purge and reinstall alsa and pulse to get rid of the problem but no success :-( Another thing I found was that I dont have a .asoundconf file anymore?! its gone...

Thanks for your help!!!

---

