---
title: "hardware setup questions"
date: 2008-08-24
forum: Mythbuntu
---

### Post by Jabes on 2008-08-24
Hi,
I'm building a home media server and I think Mythbuntu will meet my needs.  My plan right now is to have a server that will:
[LIST]
[*]Act as a back-end as well as a front-end for Mythbuntu
[*]Hold all my music and stream to other PCs in my home.
[*]Record up to 2 HDTV streams coming from an HDHomeRun Tuner (over Ethernet) and provide up to 2 HDTV streams to front ends. All of this possibly happening simultaneously.
[/LIST]
Here are a few questions I have:
[LIST=1]
[*]Is this feasible?
[*]With so many things going on at once, I was thinking that a Intel Quad Core would suit my needs perfectly.  Anyone agree or disagree?
[*]Am I asking too much as far as data rates go for the hard drives and your typical home network?
[/LIST]

Any recommendations for my setup is much appreciated!

Thanks,
Justin

---

### Post by nasha on 2008-08-25
Certainly a feasible option. However i think a quad core is serious overkill for what you want. I can record 2 HD streams on a Pentium D 2.8Ghz without any issues, so id say look at an entry level dual core, unless money is no object.
HDD access shouldn't be a problem with a 7200rpm sata drive if you buy a decent one. If your worried, or you want to prepare for future frontend additions, configure raid 0 with 2 or more HDD's.
Links below should be able to get you started :)

[HTML]http://www.mythtv.org/wiki/index.php/Silicondust_HDHomeRun
http://www.mythtv.org/wiki/index.php/RAID#RAID_0[/HTML]
Good Luck!

---

### Post by Jabes on 2008-08-25
Thanks.  Looks like wireless is out of the question which is what I had previously wanted to do.  After reading a few comments, 802.11n can barely keep up with two HD streams and that's on a good day.  I should have known better now that i look at the data rates.  Too borderline especially if there are others on the network surfing.

---

### Post by DutchLoki on 2008-08-26
> **Jabes said:**
> Thanks.  Looks like wireless is out of the question which is what I had previously wanted to do.  After reading a few comments, 802.11n can barely keep up with two HD streams and that's on a good day.  I should have known better now that i look at the data rates.  Too borderline especially if there are others on the network surfing.

lan over your powercables could be an option... great speed and stable.

---

