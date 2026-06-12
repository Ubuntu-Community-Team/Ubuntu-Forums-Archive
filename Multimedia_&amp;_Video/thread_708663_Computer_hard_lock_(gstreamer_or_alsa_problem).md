---
title: "Computer hard lock (gstreamer or alsa problem?)"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by fxjr on 2008-02-26
Hi, all!

I'm having problems on my laptop when playing sound with some gstreamer based applications (banshee, rhythmbox etc)

My machine suddenly hard locks and I can only hold power button pressed until it shuts down.

When I was using Gentoo, I also had this issue, but could track it down to be something with gstreamer and later with alsa as I did a downgrade and used 1.0.14rc2 which seemed to solve the issue.

Do you know if you have any issues like that? Also, could you point me to some directions about how I could get alsa 1.0.14rc2 installed on Ubuntu? May I need to compile it myself? I'd like to be able to create a package so I can uninstall it easily later to check if newer versions fix my problem. Maybe I could also start looking at newer versions to see if the problem still exists?

Thanks in advance.

---

### Post by fxjr on 2008-02-27
Hi, all!!

I forgot to say that I'm using Ubuntu Gutsy. 

Thanks in advance.

---

### Post by magnusbb on 2008-03-08
I can confirm this issue. I experienced it twice today. The best is to avoid GStreamer, I think.

---

