---
title: "problem occurs every time computer is shut down and restarted."
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by williamsld8 on 2011-02-22
so i have v 10.10 and i had to hook up with ethernet cord to download and activate both broadcom b43 and sta drivers. once they were both downloaded and activated my wireless worked fine. (also i have an hp mini 210-1000 if that helps.) after unplugging my laptop and using it, if it dies or if things are running really funky and it seems like it could use a restart, or on one of the many occasions where im not going to be using it for a few days and just shut it down, as soon as i start it back up, i find that sta driver still says activated under system - admin - additional drivers, however the b43 now says inactive, and my wireless wont connect to ANY router, even though it can detect them, until i connect with the ethernet cord and redo the whole driver activation for both, and then restart. this happens every time, and although i dont often take my laptop out of my room, my router is away from my desk, so this is a major inconvenience when i have work to do, or if i WERE to ever take it out somewhere with me. please help. im hoping this can be fixed permanently. and just in case, i lack all knowledge of coding, how the terminal works, and what not. i look forward to your advice 


-williamsld8

---

### Post by williamsld8 on 2011-02-23
anybody have any suggestions?

---

### Post by Bigtime_Scrub on 2011-03-06
The problem is probably because you have both the b43 and the sta driver. I think they conflict. Which broadcom device do you have?

Open a terminal and please post the out put of ```
lspci
``` So I can see which one you need.

---

### Post by williamsld8 on 2011-03-09
well even if i disable the b43 driver which i have found i can still access the internet without, the sta driver will work for a bit and then just stop altogether. then i have to remove it, reinstall it, restart the computer before i can use wireless again. and then the next time i have to restart my computer the whole deal starts over again.

---

