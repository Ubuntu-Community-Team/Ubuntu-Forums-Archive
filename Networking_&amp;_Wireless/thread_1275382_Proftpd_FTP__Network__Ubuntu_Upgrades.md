---
title: "Proftpd FTP / Network / Ubuntu Upgrades"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by Whyzer on 2009-09-25
I am a semi-weak Linux user so bear with me.
I have been running Ubuntu since 8.10, I mainly use it to set up an ftp for family, friends and clients (back ups of their computers). I use proftpd, I have a setup that works great, until Ubuntu goes through about 4 - 5 months of updates when all the sudden no one outside my LAN can connect. I don't think this has anything to do with my IP address changing. I am running Ubuntu 9.04 - the Jaunty Jackalope.

  Proftp info (remember these settings worked fine for a long period)
I use DYNDNS.org, so I use masquarade address (had always worked fine).
  When I start proftpd I used to message that said 
linux-desktop - myftpname.net masquerading as 68.xxx.xxx.xxx (real numbers there) and it worked fine. 
   Now it gives me
linux-desktop - 127.0.1.1:1313 masquerading as 68.xxx.xxx.xxx (real numbers there) and it no longer works off the internet, but still works on my LAN.
   I have 2 NICS one goes directly to my router and one goes to a switch which then goes to the router as well. I have the router assign (via MAC Address) my one NIC a constant IP address, and ive confirmed it is correct, both at the router and at the Linux box.
   I use password & group scripts for user control, again they worked fine.
AuthUserFile			/home/ftp/scripts/passwd
AuthGroupFile			/home/ftp/scripts/group

My FTP went down several weeks ago, and I could still give people my real IP address (68.xxx.xxx.xxx) instead of my DYNDNS Ip and it would work, but took several tries to get thru. But now it doesn't work at all. 
I really think it's somehow tied to some other security feature within Ubuntu or an update to my network, that shut it down.
     I really feel that one of the numerous updates Ubuntu made has something to do with it, but don't know how to check or confirm that suspicion.
I could reinstall Ubuntu and have the FTP running rather quickly, but setting up other features is too time consuming to be doing this a couple times a year.

Any recommendations?
This happened about a year ago to me, and I seem to remember switching NICS and it worked again, but I am not positive, nor is that practical.

Any suggestions would be greatly appreciated, again I am not terribly strong on Linux, but with minor guidance I can usually do whats needed.
Much thanks in advance
(not so) Whyzer

---

