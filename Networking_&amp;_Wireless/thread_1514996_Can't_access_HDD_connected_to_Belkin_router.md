---
title: "Can't access HDD connected to Belkin router"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by joaor10 on 2010-06-21
Hello,

Well, I have an external hard drive connected to my router. From Windows I can access it, but from Ubuntu I can see the hard drive, but when I try to access, I'm asked for a password. However my network does not have a password neither the hard drive.
What must I do?

Thanks in advance!

---

### Post by acrazyplayer on 2010-06-21
It may just be asking for the super user password. So whatever password you use once synaptic package manager wants to open, try that.

---

### Post by joaor10 on 2010-06-21
Nop, it's not that one... I've tried it and doesn't work. :(

---

### Post by joaor10 on 2010-06-22
Sooo, any ideas?

---

### Post by mariodab on 2011-03-09
I'm reviving this thread. I have had this same issue for over a year now and have not found a solution. Everything I look at just tells you how to set up samba and how to access network shares.  None of this helps me because everything is working the way it is supposed to. I just keep hitting a brick wall with that login screen.

Is there anyone who has found out what login credentials you need to access the HDD?

It has to be something built into the router, since you are accessing it thru the router. I just don't see where that information can be found in the setup menu. Calling tech support for the router is pointless because they have no idea what I'm talking about. I know more about networking than they do and I don't know very much.

I have seen this same question scattered all over the internet by different people over several years and each was met with silence. Is ubuntu (or any Linux distro for that matter) incapable of accessing a HDD connected to routers via usb? Someone at least answer me that because that seems to be the case. Linux just seems to be incapable of authenticating mounting a usb HDD connected to a router. 

You know what, I am just going to say it. This is for those people like me that run into this problem. Your Linux OS is not capable of accessing a HDD networked in this fashion. Over years of off and on sifting thru thread after thread I can say with confidence that Linux simply does not have the capability. Sad but true. So if you want to access that drive, you will have to do it with windows. Stop wasting you time looking for an answer.  This is your answer. It cannot be done, and probably will never be able to. I invite anyone to prove me wrong but I highly doubt anyone can. Until then take my advice, use windows to access it.

And don't anyone take this the wrong way either. I love Linux and would get rid of windows in a hear beat but simple crap like this not working is what keeps me from doing that. I am not a PC gamer so I don't care about playing games, that being said I should be able to step away from windows entirely, but that is not the case.

---

### Post by joaor10 on 2011-03-09
Well, I did eventually found the solution. However, I don't know if it is only for Belkin routers, or every router.

Write "guest" in Username, and see what happens. That worked for me.

---

### Post by mariodab on 2011-03-09
It probably is just Belkin routers. I'll try it and see what happens. Leave password and domain name blank I am assuming.


EDIT
Go figure. Using guest as the user name and leaving the domain as workgroup and the password blank allowed access.  Something so simple and the fine folks of Belkin had no documentation on it. Absolutely ridiculous. Thanks jaor10 you succeeded where Belkin customer support failed miserably. I hope others out there having this same problem find this thread in their searches.

---

### Post by joaor10 on 2011-03-10
Well, I'm glad to help :)

---

### Post by ed062178 on 2011-06-30
ok... new to ubuntu. found the right place to enter "guest" once upon a time, cant remember how to get there. anyone care to give me a simple step by step. im really over the windows thing. :D

---

### Post by joaor10 on 2011-07-07
Well, that box only appears when you try to access an HDD connected to a router.

---

