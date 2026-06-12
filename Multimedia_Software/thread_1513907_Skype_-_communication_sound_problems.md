---
title: "Skype - communication sound problems"
date: 2010-06-20
forum: Multimedia Software
---

### Post by pium on 2010-06-20
Hi all,

I have sound problems wih skype 2.1.0.81 on ubuntu 10.04.
(everything was fine on ubuntu 9.10)

The sound (entry and output) has a very poor quality, 1sec with sound, 1sec with blank....
I can't understand other people and they can't understand me.
Note that it only happens on communication sound. The "notification sounds" work perfectly.

My mic / speakers work well on others applications.
I use pulse audio.

I don't know if it modifies the sound, but to have my webcam working, I have to run Skype with
"bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'"

Do you have an idea where it can come from ?

Thank you.

-- pium

---

### Post by pium on 2010-06-21
Nobody has an idea?
I tried everything in my knowledge without a result.

Please I need help!

--pium

---

### Post by pium on 2010-06-21
Hey :)

I found something, I uncomment these lines in /etc/pulse/daemon.conf

high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5

It does not sound perfect since it's the configuration for pulse in general, but at least it works before finding something better.

-- pium

---

### Post by mbeierl on 2010-06-21
Sorry to disappoint, but in Lucid, at least, those are the default values that are in effect in the comments.  So simply uncommenting them does not actually change anything.  It sounds more like your internet connection is not reliable.

---

