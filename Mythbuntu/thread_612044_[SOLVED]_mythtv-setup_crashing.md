---
title: "[SOLVED] mythtv-setup crashing"
date: 2007-11-13
forum: Mythbuntu
---

### Post by Stevieo85 on 2007-11-13
I wander if you can help, i have just reinstalled mythbuntu for the 2nd time and when I try to run mythtv-setup the system restarts xconf. Before it does this it displays a pattern on the monitor as if the display settings are wrong. 

This also happens when I try to run the terminal, I have had to insatll konsole to get a shell. 

I think the problem with the mythtv-setup is that the first section of this has to run in terminal if what my google search have returned are true. 

Any help would be appriciated.

---

### Post by superm1 on 2007-11-13
> **Stevieo85 said:**
> I wander if you can help, i have just reinstalled mythbuntu for the 2nd time and when I try to run mythtv-setup the system restarts xconf. Before it does this it displays a pattern on the monitor as if the display settings are wrong. 

This also happens when I try to run the terminal, I have had to insatll konsole to get a shell. 

I think the problem with the mythtv-setup is that the first section of this has to run in terminal if what my google search have returned are true. 

Any help would be appriciated.
Using Xgl?
Have a backtrace in /var/log/Xorg.0.log or /var/log/Xorg.0.log.old?
In ~/.xsession-errors?

---

### Post by Stevieo85 on 2007-11-13
Thanks for the reply, my google skills just took a while to shine through. What I had to do was edit xorg.conf and change the colour depth i think it was from 24 to 16. TBH it makes it look better on my tv screen aswell when i use that at 800x600 (TV's max) rather than my monitor.

---

### Post by trubblemaker on 2007-12-15
I think I have the same problem when ever I try to open a terminal -> logs me out of X, I'll try the fix and get report back,,, if only I could get a terminal from myth...

---

