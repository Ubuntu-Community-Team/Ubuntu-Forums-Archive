---
title: "Rygel error of gstreamer"
date: 2012-03-08
forum: Multimedia Software
---

### Post by coleix on 2012-03-08
Hello everybody, I have a problem with rygel and looking through bugzilla and google couldn't find it, just something close which apparently is already resolved, [https://bugzilla.gnome.org/show_bug.cgi?id=645152](https://bugzilla.gnome.org/show_bug.cgi?id=645152) but I'm fairly newbie so I don't see if is the same thing or not. I ran ```
rygel -g 5
``` so here's the info [http://paste.ubuntu.com/874068/ ]("http://paste.ubuntu.com/874068/")

It says that > rygel-transcoder.vala:181 can encode it but it jumps back to > rygel-transcoder.vala:176 and it gives the error at the end of gstavidemux. I can use twonky to push music to the TV or with the TV directly but videos just crash even thou is compatible or at least as far as i can see, it is.

---

### Post by coleix on 2012-03-11
Bump,
Aparently the package of software center isn't the latest one 0.10.1, anyone knows where can I find the 0.12.7 on a .deb package so it is an easy install?

---

### Post by coleix on 2012-03-25
Well I installed the debiam package 0.12.6-2 from wheezy and forgot to say it was solved for anybody else that has this problem, It works but I'm guessing because is wifi, hd just plays a couple of seconds then freezes and plays again and keeps doing this cycle, sd quality does play nicely =-).

It would be nice if we had more control of the bitrate and buffer so it could help HD but it's still great overall.

---

