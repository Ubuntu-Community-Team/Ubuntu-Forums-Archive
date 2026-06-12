---
title: "Video issue"
date: 2012-07-31
forum: Multimedia Software
---

### Post by FerasMoalla on 2012-07-31
Hi,

when I try to run a video file on my Ubuntu it says:

The playback of this movie requires a XVID MPEG-4 decoder plugin which is not installed.

I tried sudo apt-get install xvid but it gives the error:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Any suggestions? 

Thanks

---

### Post by evilsoup on 2012-07-31
Log out & log in again (to end any processes that might be using your resources), then install ubuntu-restricted-extras (which contains decoders for xvid and a bunch of other things).

---

