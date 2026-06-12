---
title: "Possible to block access to network connections?"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by zinc987 on 2009-12-28
For the last 4 months I've been using OpenDNS to prevent my teenagers from accessing adult web pages and other content on my system. However, I recently discovered that one of them simply removed the changes via network connections>editing "atho etho0"> and removing the DNS server addresses (208.67.222.222, 208.67.220.220). This allows them to turn the DNS filtering "on and off" by removing and adding the OpenDNS addresses.

I considered editing their user settings to remove the "administer the system" through the user settings. However, this would prevent them from un-installing or installing software and really restrict their use...

Would it be possible to place a password on network connections or specifically restrict their access to it?

Also, this appears to be a serious flaw with Open DNS and in many ways makes the filtering somewhat useless.

Thanks

---

### Post by iponeverything on 2009-12-28
Yes OpenDNS does have its drawbacks ;) Overall, I think the service is good when you can limit access to other DNS servers.

Here are a few options that you can do to only allow access the OpenDNS servers:

Option 1.
Add a firewall rule to router that you to access the Internet blocking all port 53 traffic, except that going to the servers at 208.67.222.222, 208.67.220.220.  Make sure that they don't have login password to the device in question.

Option 2.
Put a old linux between the Internet device and the Internal Network. This can be used for filter the DNS traffic and for monitoring. You could also install a basic Internet access authentication mechanism to tie deeds to users.

Option 3.
Add the iptables rules to block non-openDNS port 53 traffic directly to the machine in question then move the iptables binary off the machine on to thumb drive so that they can not change or flush the rules at will. Turn on command auditing and have it send email notifications, so that if someone did manage to work around lack of a binary, you would get an email that someone had ran the iptables command..

In my option, monitoring and recording the traffic is a good option.. Misbehaviour like circumventing access controls is mute when you have a report in your hand that says what was accessed and when.

---

### Post by dmizer on 2009-12-28
The above are all good solutions.

I'd also like to add the possiblity for requiring a proxy (one you controll of course) for internet access.

Otherwise, you could simply remove network editing/sudo priveledges from their accounts.

---

### Post by Project PWNED on 2009-12-29
Put the computer in the middle of the living room and enforce hours on their Internet access, for instance - if you are not home, they are unable to browse the Internet. If you are home, they can browse.

I was a teenager about 10 years ago before all this Myspace/Facebook stuff, but I'm telling you if you have a computer hidden in a back room or somewhere that the door can be closed, this is a bad idea.

However, if you wish to enforce something technical (who knows? They could be reading this forum right now!) go ahead and block 6667-7000/tcp and 6697/tcp (SSL over IRC) to prevent them from accessing IRC. My parents hated IRC.

Update:

You can put more things in place to prevent them from accessing anything, but the first chance they get the ability to tunnel things through SSH (stunnel), there would be nothing really to stop them. I know people who stunnel through the corporate firewall at their jobs to get on IRC, browse the web (Facebook), etc. because IRC is blocked and so is Facebook. If you keep trying to stop them technically, they will adapt stronger methods of bypassing whatever you put in their way.

---

### Post by iponeverything on 2009-12-29
> **Project PWNED said:**
> Put the computer in the middle of the living room and enforce hours on their Internet access, for instance - if you are not home, they are unable to browse the Internet. If you are home, they can browse.

I was a teenager about 10 years ago before all this Myspace/Facebook stuff, but I'm telling you if you have a computer hidden in a back room or somewhere that the door can be closed, this is a bad idea.

However, if you wish to enforce something technical (who knows? They could be reading this forum right now!) go ahead and block 6667-7000/tcp and 6697/tcp (SSL over IRC) to prevent them from accessing IRC. My parents hated IRC.

Update:

You can put more things in place to prevent them from accessing anything, but the first chance they get the ability to tunnel things through SSH (stunnel), there would be nothing really to stop them. I know people who stunnel through the corporate firewall at their jobs to get on IRC, browse the web (Facebook), etc. because IRC is blocked and so is Facebook. If you keep trying to stop them technically, they will adapt stronger methods of bypassing whatever you put in their way.

Stopping someone from setting an ssh tunnel on a compter and network that you control is easy.

I don't think that has to be an arms race with the kids. Having the PC in the living room is not a bad idea at all, but to be quite honest locking down a linux box into a kiosk like device that only has the ability to do a subset is things is fairly trivial -- and could be used if they violate your trust regarding rules that you need to enforce in your home. 

With regard to circumvention of company computer policies, there are couple of things at play here that I can think of.

- poor system administration
- an employee that does not appreciate their job enough to abide by an existing policy.

---

