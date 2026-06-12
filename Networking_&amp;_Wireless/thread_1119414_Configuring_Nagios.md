---
title: "Configuring Nagios"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by arbulus on 2009-04-07
Can anyone point me in the direction of information on configuring Nagios?  I've installed Nagios on an Ubuntu 8.10 machine following the Quick Start instructions provided by Nagios.  But the rest of their documentation is completely and utterly useless.  It tells you *very* generally about what you need to put in a config file, but in the location where the config files should be, they don't exist. Nor does it tell me what the name of the files should even be, so I don't even know how to create them, if I'm supposed to. 

I want to be able to monitor the availability of several windows server 2008 servers, windows vista and xp workstations and a router and have it send email alerts should those machines become available and an SMS if the router is unavailable.

I've been searching around the web for an easy to follow guide on how to set this thing up and have found almost nothing, and what I have found is out dated. 

I'm an IT Admin trying to find an good network monitoring software, and trying to be cost-conscious.  I've also been an Ubuntu user for a number of years, so networking and Linux are very familiar to me, and I hate getting stumped by this. 

Can anyone provide any assistance?

Thanks in advance!

---

### Post by Iowan on 2009-04-08
[Here]("https://help.ubuntu.com/community/Nagios") is a help page, but it seems a bit dated (written for 7.10)

---

### Post by arbulus on 2009-04-09
Thanks Iowan!

Ok, so I have Nagios monitoring a few machines now, but I need to get it set up to notify me when there is a problem. The Nagios documentation doesn't say anything about how to do this.

---

### Post by arbulus on 2009-04-09
Ok, so I was able to configure ssmtp to send emails from nagios.  I've also had to tweak Nagios' commands to make it work, but so far it seems to be doing fine.

Does anyone have any suggestions for sending sms messages from Nagios?  I've seen a package around the web called smsclient.  Does anyone have any experience with this?

---

