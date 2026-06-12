---
title: "no sound in flv videos...."
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by mincho on 2007-11-01
there is no sound in flv files .....

 even in firefox there is no sound when i open youtube video...whats the solution

---

### Post by patis on 2007-11-01
Please try the following commands on an open terminal:


```
~$ asoundconf list
Names of available sound cards:
Intel
U0x47f0xc001
~$ asoundconf set-default-card U0x47f0xc001
```


The above is an example from my system.
Re-start firefox and see (hear!) if there is any sound.

Hope this helps.

---

### Post by Maxono on 2007-11-01
> **patis said:**
> Please try the following commands on an open terminal:


```
~$ asoundconf list
Names of available sound cards:
Intel
U0x47f0xc001
~$ asoundconf set-default-card U0x47f0xc001
```


The above is an example from my system.
Re-start firefox and see (hear!) if there is any sound.

Hope this helps.

i had the same problem, now it works thanks :)

---

### Post by aamod on 2007-11-01
Try shutting dowm Gnome sounds from System > Preferences > Sound. then unselect Enable ESD.

---

### Post by mincho on 2007-11-01
when i enter this in terminal...

asoundconf list

the output show only intel like this 

asoundconf list

Names of available sound cards:
Intel

.....................

now what i choose for my default sound card

---

### Post by jubilee33 on 2007-11-03
> **aamod said:**
> Try shutting dowm Gnome sounds from System > Preferences > Sound. then unselect Enable ESD.

I tried this solution and it worked.  I had audio for CD, MP3, DVD playback (in Totem but no Mplayer) and no sound in flash/mplayer plugin in Firefox.  Now they are all there.  The only tradeoff is that I lost the mouse-over audio preview of MP3 files.  It&#347; very odd.

---

### Post by mincho on 2007-11-03
I have solved my problem... :D

Thanks for replying and helping me.

---

### Post by aamod on 2007-11-06
> **jubilee33 said:**
> I tried this solution and it worked.  I had audio for CD, MP3, DVD playback (in Totem but no Mplayer) and no sound in flash/mplayer plugin in Firefox.  Now they are all there.  The only tradeoff is that I lost the mouse-over audio preview of MP3 files.  It&#347; very odd.

Ok. Open MPlayer. Right click and go to preferences. Under Audio tab use different drivers. Mostly OSS or ALSA must work. Dont forget to restart MPlayer each time you change driver. Restarting is not mandatory but advised.

This must solve your problem..

---

