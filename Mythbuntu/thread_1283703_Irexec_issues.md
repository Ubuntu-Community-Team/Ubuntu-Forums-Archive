---
title: "Irexec issues"
date: 2009-10-05
forum: Mythbuntu
---

### Post by azmyth on 2009-10-05
I'm using Mythbuntu Jaunty. I'm having an issue with irexec crashing (I guess it's crashing) after being idle for a few days. I thought I saw some lircd tainted in the dmesg but not sure if it's related. Is anyone else seeing this?

Unfortunately, you can't restart irexec by simply restarting lirc so I have to reboot. I tried using monit but I cannot figure out how to make monit restart irexec. When I try it just starts and then crashes, not sure if it has to do with export display. On boot, I added a part to my rc.local so it'll create an irexec.pid so I could use monit.

Irexec will start on boot since I added a irexec file to my home /.lirc directory. I guess I don't understand which script reads this file and then starts irexec.

---

### Post by azmyth on 2009-10-06
Looks like it's a display issue

DISPLAY=:0 irexec -d /home/mythtv/.lircrc

So far, I can use this with monit to monitor irexec.

---

### Post by pssturges on 2010-05-19
> **azmyth said:**
> Looks like it's a display issue

DISPLAY=:0 irexec -d /home/mythtv/.lircrc

So far, I can use this with monit to monitor irexec.

I'm have the same issue, but only on one of 3 my boxes (zotoc ion). Does this bit of code fix the problem for you? And where do I put it?

Cheers,
Phil

---

### Post by pssturges on 2010-05-19
Ah, Ok found monit. So obviously I need to put that bit of code in the monit config file. There seems to be a bewildering number of possibilties to configure monit. I just need some help to configure it to monitor my irexec and restart it if it crashes.

TIA
Phil

---

### Post by azmyth on 2010-05-22
I put this in the start command in monit for irexec. I ran into other issues though. The irexec started at boot caused issues so I had to kill this and just let monit start irexec on it's own. In the end due to other reasons, I had to compile and use a back version of lirc so I stopped using my previous setup.

---

