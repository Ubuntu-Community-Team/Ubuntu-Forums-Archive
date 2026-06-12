---
title: "Share printer with Windows PCs"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by brunces on 2011-05-19
Guys,

I'm new to Linux, so I really need some help. :) Here's the problem I'm facing...

I've installed Ubuntu 11.04 in dual boot with Windows XP on my computer at work. I have a printer (HP LaserJet 3020) and I've shared it with all my coworkers, and everything's working like a charm.

When a coworker wants to print here, first he has to select my shared printer on his computer and then print it. Cool! The point is... On his computer there are two network printers pointing to my PC: one for Windows and another one for Ubuntu. Now, here's the problem...

Sometimes I'm logged in Windows, sometimes in Ubuntu, here. But my coworkers don't know when I'm in Windows or Ubuntu. So, if they select my Windows shared printer and I'm logged in Ubuntu, it doesn't work. And vice-versa.

So, I'd like to know if there is a way to share my printer on Ubuntu as if it were Windows, I mean, I don't know if it's possible - that's what I want to know - but I thought maybe there could be a way to use a "single network printer link" on my coworkers' computers (instead of two distinct ones for each OS I use), so that they would select it and send their printing job to my printer, independently on which OS I'm using at the moment.

Summarizing... A coworker chooses my shared printer on his computer and send the job. Then it would be printed here anyway. It doesn't matter if I'm logged in Windows or Ubuntu.

Is that possible? If so, how?

Thank you very much for your attention.

brunces

EDIT: All my coworkers use Windows XP.

---

### Post by capscrew on 2011-05-19
> **brunces said:**
> ...

... On his computer there are two network printers pointing to my PC: one for Windows and another one for Ubuntu. 

This is because the *[COLOR="SeaGreen"]**printer is the driver in the running OS**[/COLOR]*.  That big piece behind you with the paper and ink in it is just the ***[COLOR="Navy"]printing device[/COLOR]*** and it just spews out what the printer (driver) tells it to.  > 

... Sometimes I'm logged in Windows, sometimes in Ubuntu, here. But my coworkers don't know when I'm in Windows or Ubuntu. So, if they select my Windows shared printer and I'm logged in Ubuntu, it doesn't work. And vice-versa.

See above for why.  :-)> 

So, I'd like to know if there is a way to share my printer on Ubuntu as if it were Windows, I mean, I don't know if it's possible - that's what I want to know - but I thought maybe there could be a way to use a "single network printer link" on my coworkers' computers (instead of two distinct ones for each OS I use), so that they would select it and send their printing job to my printer, independently on which OS I'm using at the moment.

Summarizing... A coworker chooses my shared printer on his computer and send the job. Then it would be printed here anyway. It doesn't matter if I'm logged in Windows or Ubuntu.

Is that possible? If so, how?

...

Given the above I don't see how that is possible.

---

### Post by brunces on 2011-05-19
capscrew, thanks for your reply.

I'm sorry, but I really didn't understand your point.

Even if my coworker has two different "network printer links" to my printer (one for each OS), isn't the driver on his machine the same? I mean, what I thought was...

Here in my Windows, the printer is shared as HP-LASERJET-3020. This is its name in Windows sharing settings. So, if I used the same name in Ubuntu, wouldn't it be the same? For example, there would be only one "driver" on my coworker's computer called "HP-LJ-3020-AT-BRUNCES", pointing to \\brunces\hp-laserjet-3020.

Considering that, wouldn't it be the same both for Windows and Ubuntu?

The name of my machine in Windows is "brunces". In Ubuntu too.

The name of my printer in Windows is "hp-laserjet-3020". In Ubuntu too.

So, when setting up a network printer on my coworker's computer, isn't the path the same (\\brunces\hp-laserjet-3020) for both Windows and Ubuntu? Isn't it possible to use only "one network printer" on my coworker's computer, with a fixed path which would do the trick both for Windows and Ubuntu on my machine? That's my point.

Maybe I don't know how things work exactly. I really don't get your point on "driver in the running OS". In my mind, there's only one driver and it doesn't matter where it points to. Does it?

Please, if possible, explain that to me again. Thank you very much.

brunces

---

### Post by capscrew on 2011-05-19
> **brunces said:**
> capscrew, thanks for your reply.

I'm sorry, but I really didn't understand your point.

Even if my coworker has two different "network printer links" to my printer (one for each OS), isn't the driver on his machine the same? I mean, what I thought was...

The printer driver is in your host (computer) not the your co-workers machine.  Your host is functioning as the print server.  When you boot to Ubuntu you use Linux printer drivers (CUPS).  When you boot up you machine in Windows you use windows printer drivers.  They are not the same.  They do not reside on the your co-workers machine.  When you configure your co-workers printer client you are only providing the ***printer port ***not the actual driver.> 

Here in my Windows, the printer is shared as HP-LASERJET-3020. This is its name in Windows sharing settings. So, if I used the same name in Ubuntu, wouldn't it be the same? For example, there would be only one "driver" on my coworker's computer called "HP-LJ-3020-AT-BRUNCES", pointing to \\brunces\hp-laserjet-3020.

Considering that, wouldn't it be the same both for Windows and Ubuntu?
I have 2 friends named John.  They are not the same person...

Seriously: each OS uses a different approach to provide the printer(driver).  What you name them is only meta-data (the name). > 

The name of my machine in Windows is "brunces". In Ubuntu too.

Try to think of this in OS terms.   A hostname is defined in the running OS.  The Ubuntu hostname is not the name of the hardware, so logically the Windows COMPUTER NAME is not the name of the hardware either.  In fact the Ubuntu hostname uses hostname routines to be identified internally and Windows uses NetBIOS names internally. > 

The name of my printer in Windows is "hp-laserjet-3020". In Ubuntu too.

I have two Hondas, but they are not the same vehicle.> 

So, when setting up a network printer on my coworker's computer, isn't the path the same (\\brunces\hp-laserjet-3020) for both Windows and Ubuntu? Isn't it possible to use only "one network printer" on my coworker's computer, with a fixed path which would do the trick both for Windows and Ubuntu on my machine? That's my point.

Maybe I don't know how things work exactly. I really don't get your point on "driver in the running OS". In my mind, there's only one driver and it doesn't matter where it points to. Does it?

Yes it does matter.  Each OS has its own printer driver. They are not the same.  Only one OS can be running at a time unless you virtualize one of them.  But if you did that, then each would have a differing endpoint (IP address) and you would still have to have two printer ports. > 

Please, if possible, explain that to me again. Thank you very much.

brunces

---

### Post by brunces on 2011-05-20
capscrew, thanks again for your time. I think now got the point.

My coworker's machine MUST have two separate drivers, one for each OS of mine, because it MUST know which OS I'm using when sending a printing job, right? I thought it was different.

I thought when a coworker sent a printing job from his machine (WinXP) to mine, it wouldn't matter wich OS here would receive the printing job, I mean, both Windows and Ubuntu would "understand" the incoming process and send it to the printer device right away, without any problem. Therefore, there would be only one driver on my coworker's machine.

Well, so to cut a long story short, my coworker's machine MUST always know which printer device I have and also which OS I'm running. Period! I thought it had to know only which printer device I have, independent on the OS. Good to know.

Thanks a lot, man. :)

brunces

---

