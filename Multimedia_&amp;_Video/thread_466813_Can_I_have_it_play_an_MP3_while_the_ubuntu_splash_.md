---
title: "Can I have it play an MP3 while the ubuntu splash screen is up?"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by diablo75 on 2007-06-07
I think I read in a book about making carputers with ITX form factor motherboards the author mention something about Linux being so customizable, that you could have it play a song while the OS was booting of your choosing.  And mp3 file at that!  I was wondering if anybody out there knows how this is done and if they could share the magic.  ;)  Thanks for the help!

---

### Post by joselin on 2007-06-07
Sure.

System / Preferences / Sound / Log in... and then select the file you want to play.

Regards

---

### Post by JohnLeoZ on 2007-06-07
> **joselin said:**
> Sure.

System / Preferences / Sound / Log in... and then select the file you want to play.


Ok, but how about **before** that?

How about [COLOR="DarkOrange"]during boot up [/COLOR]as soon as sound has been configured?

Or when the [COLOR="#ff8c00"]sign on screen [/COLOR]is displayed?

regards,
JohnLeoZ

---

### Post by joselin on 2007-06-07
Perhaps you can modify /etc/init.d/alsa-utils adding there a line like 'mpg123 file'. But I never try it, so you have to try at your own risk.

---

