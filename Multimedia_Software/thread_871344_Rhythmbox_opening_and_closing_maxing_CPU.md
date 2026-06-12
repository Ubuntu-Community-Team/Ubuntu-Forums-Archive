---
title: "Rhythmbox opening and closing maxing CPU"
date: 2008-07-26
forum: Multimedia Software
---

### Post by ThrashJazzAssassin on 2008-07-26
Rhythmbox seems to use a lot of CPU power to open and close. The length of time it hogs my CPU is related to how many songs I have in my library.

6100 songs in library
Open:32 seconds
Close:42 seconds

0 songs in library
Open:1 seconds
Close:1 seconds

I cant remember when it started doing this. It may be around the time I had a total system lock-up a couple of days ago or when I tried ticking the crossfade box last week or maybe it's always been this way and I haven't noticed. I've tried different settings and done a complete reinstall (of rhythmbox) and tried deleting rhythmbox folders I've found in my home dir. please help.

btw I have an AMD +2500 CPU and banshee and listen dont do this but I want to use rhythmbox.

---

### Post by ThrashJazzAssassin on 2008-07-27
I had a look at the system monitor and noticed a process called at-spi-registryd was using lots of CPU while opening and closing Rhythmbox. It's apparently used for accessibility functions. Ending this process fixes the Rhythmbox CPU hogging.

Can anyone reproduce this?

---

### Post by ThrashJazzAssassin on 2008-07-27
I fixed this by disabling Assistive Technologies. I dont know why this was enabled. It's not enabled by default is it?

---

