---
title: "[SOLVED] Cannot play DVD's"
date: 2008-08-26
forum: Multimedia Software
---

### Post by Mhawkins1 on 2008-08-26
I cannot find a dvd player for ubuntu that will play my netflix dvds. I've tried Movie Player, Mplayer, Ogle, and Windows media player under wine. I have no problem playing copied dvds but I can't play legitimate legal dvds

---

### Post by kaibob on 2008-08-26
Install totem-xine and libdvdcss2 from synaptic and you will be able to play the DVD's.

---

### Post by Mhawkins1 on 2008-08-27
> **kaibob said:**
> Install totem-xine and libdvdcss2 from synaptic and you will be able to play the DVD's.

I already have both of those installed. I reinstalled them and it still doesn't work.

---

### Post by kaibob on 2008-08-27
I don't know what is going on then. Totem-xine with libdvdcss2 works for me and is all that is required as confirmed by:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

You may want to try the VLC media player, although if totem-xine doesn't work VLC may not either. Perhaps someone else has a suggestion that will help.

---

### Post by Mhawkins1 on 2008-08-27
> **kaibob said:**
> I don't know what is going on then. Totem-xine with libdvdcss2 works for me and is all that is required as confirmed by:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

You may want to try the VLC media player, although if totem-xine doesn't work VLC may not either. Perhaps someone else has a suggestion that will help.

Could it be my DVD drive itself? It reads all CD's and DVD's but it just won't play any DVD that isn't copied. When I copy my DVD's maybe I'm removing something that allows them to play on my drive under Ubuntu because I didn't have this problem under Suse. Is this even possible? All of my copied DVD's are reigion free, but the DVD's I'm trying to play are Reigion 1 (North America) and they also worked under Microshaft Winblows Xplode (MS Win XP).

---

### Post by djRobbieF on 2008-08-29
At first glance it sounds to me that you don't have decryption installed for encrypted DVDs.  Try this thread:  [http://ubuntuforums.org/showthread.php?t=903573](http://ubuntuforums.org/showthread.php?t=903573)

---

### Post by Mhawkins1 on 2008-08-29
> **djRobbieF said:**
> At first glance it sounds to me that you don't have decryption installed for encrypted DVDs.  Try this thread:  [http://ubuntuforums.org/showthread.php?t=903573](http://ubuntuforums.org/showthread.php?t=903573)

I followed the directions. It still doesn't work with some DVD's. I get the error message 'An error occured cannot read from resource' but only with some DVD's others work. Must be the encryption. What can I do about this?

---

### Post by Mhawkins1 on 2008-09-01
> **kaibob said:**
> I don't know what is going on then. Totem-xine with libdvdcss2 works for me and is all that is required as confirmed by:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

You may want to try the VLC media player, although if totem-xine doesn't work VLC may not either. Perhaps someone else has a suggestion that will help.

I tried these steps again and it's working now. Thanks!!!

---

