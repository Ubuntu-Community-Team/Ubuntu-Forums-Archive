---
title: "Server noob: is it ssh setup, or the firewall?"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by yah.shoor on 2010-05-04
It's been a long time since I've done anything like this, so please point out to me what I'm doing wrong.

I have a fresh install of Ubuntu Server in a rackmount, which is attached to a Sonicwall firewall, which is attached to a Comcast biz switch/modem. Server is running ssh, and I've looked over the sshd.config file and changed very little. It's listening on port 22 and willing to accept connections from any IP. 

When I attach a laptop to one of the other ports on the firewall, I can ssh to the behind-the-firewall internal IP address. I can't ssh in from the outside world. We've set up the firewall to allow outgoing traffic, but only ssh and ping incoming. I can ping the server, and I can watch that get logged, but ssh doesn't touch the machine at all. Nothing in the logs on the server.

This says to me: ssh is running and correctly configured, and the incoming ssh is being blocked at the firewall, or (maybe) at the modem. According to the Sonicwall documentation, everything is set up corr[COLOR=black]ectly. What should my next steps be? Should I try to skip the firewall? (Install ufw, set up rules, set up /etc/network/interfaces to attach server directly to the modem?) Should I ask the fellow in charge for access to log into the modem to see if it's being blocked there? What next?

Edit: and yes, I can ssh to localhost as well. 
[/COLOR]

---

### Post by gzarkadas on 2010-05-04
Check first the modem; typically they have the low ports blocked by default if I remember well.

---

### Post by yah.shoor on 2010-05-04
Yup! Finally got my sysadmin to let me into the admin interface for the modem; I tweaked it a bit, and now I can ssh into the sonicwall, at least. However, instead of flat-out nothing, now when I try to use PuTTY to ssh into the server, I get a "connection refused." Which boils down to firewall configuration, I think - perhaps I don't know where to look in the logs for ssh activity, but nothing new is happening at the server. So, that pretty much proves it's the firewall, now.

---

### Post by gzarkadas on 2010-05-04
Before turning to your firewall, check first your PuTTY configuration. This [link]("http://www.unixwiz.net/techtips/putty-openssh.html") may be of help.

PS: Also check the iptables rules in your ssh box (with `iptables --list-rules').

---

### Post by yah.shoor on 2010-05-05
I'm sure that link for PuTTY setup will be really useful in the future, but at the moment neither PuTTY nor iptables looks like a useful way to proceed. I can see an entry in the Sonicwall logs, coming from my IP address of my workstation (coming from outside, on a completely separate network), of a SSH connection being dropped. It really is being stopped at the Sonicwall. If my connection was getting past the Sonicwall, then there wouldn't be a dropped connection in my Sonicwall logs, and there would be *something* in the server logs. There's nothing there - cron jobs, basically. Logs of me logging in and out. So, if I'm wrong in my assumption that this issue is best dealt with over at the Sonicwall forums, and not here, someone please do let me know!

---

### Post by gzarkadas on 2010-05-06
If you see your firewall logs dropping the connection, then it is the firewall that needs configuration, indeed. As I see, apart from the forums Sonicwall also provides documentation for its products, so as a last resort you can search for an administration guide for your specific model.

---

### Post by yah.shoor on 2010-05-06
Well, I guess that this is a success. With the Sonicwall set up in an ostensibly correct way, all I see is connections being blocked at the firewall. If I remove the Sonicwall and set up Ubuntu correctly, I can SSH in. I've used ufw to close all incoming ports but my one SSH port. I think that this is everything I needed, so I can close this thread (and open a new one "Server noob: I'm relying on ufw, what do I do to lock this system down?").

1000x thanks.

---

