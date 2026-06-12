---
title: "Internet Usage monitor meter (daemon/service)?"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by ddastoor on 2011-07-24
Hi,
I'm using ubuntu 11.04 and have a DSL connection straight from my local telephone (landline) provider.

I need a ubuntu app, preferably a daemon/service (that I can start up on boot) that, in essence, can simply log to a file, on a per session basis (with timestamps of course), the bandwidth I use (download + upload bytes).

I'm not interested in logging site info etc., just want raw data usage so at the end of the month I can run some summary reports on it.

Basically I was to see if my ISP is cheating me or not :) (and in general to control myself on my HUGE youtube + ISO download habbits)..


I need nothing fancy, even a basic command will do in which case i'll be happy to write my own basj script for that... 


Thanks, 
Dinshaw

---

### Post by Elfy on 2011-07-24
I used vnstat in the past. 

[https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals#vnstat](https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals#vnstat)

---

### Post by ddastoor on 2011-07-24
many thanks, i'll try this.

are these numbers cumulative ? or are they a snapshot per session (in which case i can script around this)

---

### Post by Elfy on 2011-07-24
Pretty sure they are cumulative - I have vague memories of resetting it monthly.

---

### Post by speedygarth on 2013-01-29
i recently installed vnstat on my computer and i am glad to say that its very simple and gives good output and is easy to configure

[http://linux.die.net/man/1/vnstat](http://linux.die.net/man/1/vnstat)

---

### Post by howefield on 2013-01-29
Old thread closed.

---

