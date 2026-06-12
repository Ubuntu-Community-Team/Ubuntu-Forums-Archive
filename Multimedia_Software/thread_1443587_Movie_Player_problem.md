---
title: "Movie Player problem"
date: 2010-03-31
forum: Multimedia Software
---

### Post by solomon88 on 2010-03-31
Hey everyone, I recently downgraded from Karmic back to Jaunty and today tried for the first time to play a DVD. The following came up (see below) and I am at a bit of a lose as to what to do now.

I tried installing mplayer, GNOME Mplayer, and Dragon Player but none of those are working either.
Needless to say, this is becoming increasingly frustrating, so any ideas or solutions would be most appreciated. Cheers. :)

---

### Post by Ghost|BTFH on 2010-03-31
libdvdcss2?

---

### Post by conradin on 2010-03-31
I usualy go with vlc, it runs with 3 times less system resources. In any case, you might want to verify that your DVD file is legit, that its not a 0 kb file or some nonsense like that, and try installing additional dvd codex for what ever format youre using. Was this a torrent DVD?

---

### Post by solomon88 on 2010-03-31
This is a legit DVD, I bought it an hour ago. I tried installing vlc, but when I ask it to play the DVD the drive sounds like it wants to but nothing happens. 
I also tried installing libdvdcss2 and the following showed up. Any ideas? I feel like I might be missing something obvious...

---

### Post by Ghost|BTFH on 2010-03-31
Yeah, you can't install libdvdcss2 from a "normal" repository.  You have to add medibuntu to your repository list first.

Go into Synaptic and then into your repositories (Settings - Repositories) and add this one:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

And that should take care of your problem of not being able to get libdvdcss2.

---

### Post by solomon88 on 2010-03-31
Cheers mate, everything seems to be working fine :). Thanks for the advice.

---

### Post by Ghost|BTFH on 2010-03-31
No worries, glad to be of service. :D

Cheers,
Ghost|BTFH

---

