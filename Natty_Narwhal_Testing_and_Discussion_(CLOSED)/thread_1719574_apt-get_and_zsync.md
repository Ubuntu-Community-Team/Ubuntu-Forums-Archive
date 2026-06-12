---
title: "apt-get and zsync"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by quantumriff on 2011-04-02
I was excited to see that ISO downloads are available via zsync now (its been a few versions since I downloaded an ISO, I usually upgrade in place).

However, it would be wonderful if there was the ability to choose to use it for apt-get as well?  Looking on the Internet, this feature has been mentioned in the last several versions of Ubuntu coming out, but always seems to get dropped.

I have been testing the Alpha (and just downloaded the beta) but my daily update checks are usually 13MB, just to download the files that tell me what updates are available..  Without hardly installing anything, just cause of how often the repo's are changing, that's a few hundred MB a month for me of traffic.  I know that doesn't sound like much to many people, but I live in a rural area.  I can't imagine how people use their cell phones, when many plans in the US cap your download at almost ridiculously low amounts. (and many people have satellite as well).  I also can only imagine how much it would decrease the load on the update mirrors.

Is there any plan for Natty to finally implement zsync in apt-get?  It would really, really make my day...

---

### Post by VMC on 2011-04-02
I think what your referring to are called [delta's]("http://brainstorm.ubuntu.com/idea/13/").

As far as I know you already can with [Fedora Delta's]("http://duopetalflower.blogspot.com/2009/07/delta-updates-save-internet-bandwidth.html").

---

### Post by juancarlospaco on 2011-04-02
I always wondered why not to use an UDP transport like TFTP for .DEB,
since .DEB have Built-In per file CRC, so it really saves bandwidth...   :D

---

