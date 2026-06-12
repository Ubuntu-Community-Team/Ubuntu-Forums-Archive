---
title: "X11 connection rejected because of wrong authentication"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by Alterax on 2007-07-03
I'm having a strange problem that popped up today after a power outage.  I am using Ubuntu Feisty (with Gnome).  

Normally, I can ssh -x ipaddress into my main box from my laptop and open applications remotely so that the actual display comes up on my laptop.  Done it for months with no problems.

Today, things are different.  Had a power outage while I was at work.  When I got home, the box had already rebooted and everything seemed fine at first.  But when I tried to ssh -X to my main box, everything worked fine up UNTIL I tried to remotely run an application.  None would work; the common thread was "X11 connection rejected because of wrong authentication".

So here's what I've checked so far:
/etc/ssh/sshd_config checks out that it does allow for X Session forwarding.
I checked the .Xauthority.conf file in my user's home directory.  It's blank.  Tried deleting it, then rebooting.  On a new remote logon it said it was rebuilding it.  No such luck; still comes up blank when I run a cat on it.

So I tried stealing the /root/.Xauthority file and setting the correct permissions on a copy of it there.  No dice.

Not finding anything relevant in dmesg or syslog. 

Anyone else had problems with this?  Nothing critical with this machine (everything is backed up) but it's got me curious as to why it's not working.

--Alterax

---

### Post by AchimRS on 2007-11-27
Hi,
I had the same problem,and now I found out that my /home partition was simply 100% full. After cleaning some files,also X applications are running again :-)

Cheers
  Achim

---

### Post by TorokLev on 2008-04-30
Hi!

Delete the .Xauthority file.
This helped me.


Lev

---

### Post by btboudreaux on 2008-04-30
In Gutsy I never had a problem with X11 forwarding.

I did a fresh install of Hardy and now I keep getting "cannot open display".

No one seems to have a solution.

deleting the Xauthority file didn't work for me.

---

### Post by sammydee on 2008-05-01
Mark another one up with the same problem as btboudreaux.

X11 forwarding always worked automagically on Gutsy server edition, now in hardy I get the exact same error as everybody else here.

---

### Post by riseringseeker on 2008-05-26
> **Alterax said:**
> I'm having a strange problem that popped up today after a power outage.  I am using Ubuntu Feisty (with Gnome).  

Normally, I can ssh -x ipaddress into my main box from my laptop and open applications remotely so that the actual display comes up on my laptop.  Done it for months with no problems.

Today, things are different.  Had a power outage while I was at work.  When I got home, the box had already rebooted and everything seemed fine at first.  But when I tried to ssh -X to my main box, everything worked fine up UNTIL I tried to remotely run an application.  None would work; the common thread was "X11 connection rejected because of wrong authentication".

So here's what I've checked so far:
/etc/ssh/sshd_config checks out that it does allow for X Session forwarding.
I checked the .Xauthority.conf file in my user's home directory.  It's blank.  Tried deleting it, then rebooting.  On a new remote logon it said it was rebuilding it.  No such luck; still comes up blank when I run a cat on it.

So I tried stealing the /root/.Xauthority file and setting the correct permissions on a copy of it there.  No dice.

Not finding anything relevant in dmesg or syslog. 

Anyone else had problems with this?  Nothing critical with this machine (everything is backed up) but it's got me curious as to why it's not working.

--Alterax

I had the same problem this morning.  What I did that made it work was to delete .Xauthority, .Xauthority-l, and .Xauthority-c. - I could have just as easily done ```
rm .Xauthority*
``` 

Don't know why I had the "-l" and "-c", but figure the "-l" at least may have been a lock file, don't really know.

Then:
```
touch .Xauthority
chmod 600 .Xauthority
```

I then rebooted, I could probably just have restarted the x-server, but was doing this remotely, and it was just as easy.  After the above, it works again.

---

