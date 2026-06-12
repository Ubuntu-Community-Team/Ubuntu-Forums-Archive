---
title: "ToDisc error"
date: 2009-05-10
forum: Multimedia Software
---

### Post by thedoctor81877 on 2009-05-10
I am having trouble burning a DVD. I am still new to ubuntu, and am using toDISC, and get the following error in th terminal.

Loading style from config file /home/thedoctor/.metagui/config
Missing a required option: -out
Running command: todisc -files /home/thedoctor/Documents/Doctor_Who-Season_4/doctor.who.s04e01.ws.pdtv.xvid-angelic.avi /home/thedoctor/Documents/Doctor_Who-Season_4/doctor.who.confidential.s04e02.ws.pdtv.xvid-bia.rmvb -titles 'Partners in Crime' 'The Fires of Pompeii' -dvd -ntsc

Any help would be appreciated.
-Michael

---

### Post by grepster on 2009-06-18
> **thedoctor81877 said:**
> I am having trouble burning a DVD. I am still new to ubuntu, and am using toDISC, and get the following error in th terminal.

Loading style from config file /home/thedoctor/.metagui/config
Missing a required option: -out
Running command: todisc -files /home/thedoctor/Documents/Doctor_Who-Season_4/doctor.who.s04e01.ws.pdtv.xvid-angelic.avi /home/thedoctor/Documents/Doctor_Who-Season_4/doctor.who.confidential.s04e02.ws.pdtv.xvid-bia.rmvb -titles 'Partners in Crime' 'The Fires of Pompeii' -dvd -ntsc

Any help would be appreciated.
-Michael



The error seems pretty clear.  You are missing the '-out' switch.  todisc -files ... [COLOR="Red"]-out my_dvd [/COLOR]...
"man todisc" for details.

grepster

---

