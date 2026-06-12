---
title: "Terminal Services Options"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by plinydogg on 2008-12-04
Hi folks,

The sole remaining obstacle to completely removing Windows from my system is that I need to access my work computer through Terminal Services occasionally. However, for some reason, Firefox (3.0.4) can't access it (the "connect" button is grayed out when I access the web page). I installed ie4Linux and attempted to access terminal services but the browser just closes every time. 

Then I attempted to use the "Terminal Server Client" that is part of the standard Gnome setup. The problem is that there are too many options! When I log in from the web, all I have to do is enter my Exchange username and password, but there are a whole bunch of other options when using "Terminal Server Client."

I tried using various combinations of options in Terminal Server Client but I always get an error that reads:

Error: getaddrinfo: Name or service not known

Does anyone have any suggestions? Are there, perhaps, other browsers or Firefox plug-ins that will allow one to access Terminal Services via the web?

Thanks in advance!

---

### Post by plinydogg on 2008-12-05
<bump>

---

### Post by plinydogg on 2008-12-09
<bump> x 2

---

### Post by plinydogg on 2008-12-14
<bu-bump-dee-bump...bump>

---

### Post by alexandroid on 2009-01-03
I think the reason you did not get any answers is that nobody can understand your question.

You mentioned Windows, Terminal Server Client, Firefox, ie4Linux and Microsoft Exchange but I have no slightest idea what did you actually tried to do with all this.  Could you please explain your setup and goals once again?

---

### Post by richbl on 2009-01-19
> **plinydogg said:**
> Hi folks,

The sole remaining obstacle to completely removing Windows from my system is that I need to access my work computer through Terminal Services occasionally. However, for some reason, Firefox (3.0.4) can't access it (the "connect" button is grayed out when I access the web page). I installed ie4Linux and attempted to access terminal services but the browser just closes every time. 

Then I attempted to use the "Terminal Server Client" that is part of the standard Gnome setup. The problem is that there are too many options! When I log in from the web, all I have to do is enter my Exchange username and password, but there are a whole bunch of other options when using "Terminal Server Client."

I tried using various combinations of options in Terminal Server Client but I always get an error that reads:

Error: getaddrinfo: Name or service not known

Does anyone have any suggestions? Are there, perhaps, other browsers or Firefox plug-ins that will allow one to access Terminal Services via the web?

Thanks in advance!

You might want to make sure that your DNS is probably set. Try pinging the machinename to which you are attempting to connect. If you get an error that indicates that the name doesn't resolve, that's a clue that your DNS is not correct.

Beyond fixing your DNS, you may want to next try pinging the machinename IP address. Assuming this works (which it should, if it doesn't you won't be able to RDP, SSH, or anything into the machine because your box can't see it), try using tsclient (or rdesktop) with the IP address in place of the machinename.

That should solve your problem.

Best of luck.

rich

---

### Post by plinydogg on 2009-02-28
Rich and alexandroid, thanks for your replys. I have since fixed this problem. It was a problem with the people maintaining my work server...

It has since been fixed and I am now 100% Windows free (at home at least)!

---

