---
title: "Port forwarding not working.."
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by jonnyboysmithy on 2012-06-16
What I'm trying to do:
Setup minecraft server so that my friends can join (I have the server setup properly and running).

Problem: I cannot connect using my external ip, _openport check tool_  says that the port is closed (the server is running.


My server is up and running on port 25565 and my internal ip is fixed (static).
I have port forwarding setup on my router.. see attached screenshot (yup I did apply the changes and restart it).

I plugged the modem straight into my pc bypassing the router to see if that would work. nope..
Could it be that the firewall in ubuntu is blocking it?

---

### Post by poolet on 2012-06-16
hello,
 please check the links below: and re-forward the port that you want with your ip  (if you haven't already do)
[http://en.wikipedia.org/wiki/Iptables#Tutorials](http://en.wikipedia.org/wiki/Iptables#Tutorials)
[http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)
**::more links**::
[http://www.netfilter.org/](http://www.netfilter.org/)
[http://linux.die.net/man/8/iptables](http://linux.die.net/man/8/iptables)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

I am sure that you will be able to fixed your problem.. :) 
if you need any other help am glad to help you..

---

### Post by SeijiSensei on 2012-06-16
> **jonnyboysmithy said:**
> Could it be that the firewall in ubuntu is blocking it?

Maybe your ISP is blocking inbound connections to make running servers impossible?  

Have you looked at the "terms of service" for your connection?  Are you allowed to run servers?

---

### Post by jonnyboysmithy on 2012-06-16
I'll have to check with my isp. I've always had problems with incoming connections on all our computers with all sorts of p2p clients. If its our isp then that would explain it all.
Thanks for the help.

---

### Post by The Cog on 2012-06-16
Just a thought, but if you're trying to test by connecting to your public address from inside your home, that won't work. NAT won't work doubling the connection back from inside to inside. You will only be able to connect to the public address from outside - from the real internet.

---

### Post by jonnyboysmithy on 2012-06-16
> **The Cog said:**
> Just a thought, but if you're trying to test by connecting to your public address from inside your home, that won't work. NAT won't work doubling the connection back from inside to inside. You will only be able to connect to the public address from outside - from the real internet.
Ok, I didn't know that. That'll be part of the problem. Thanks for letting me know.

Still doesn't explain why [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) says that my ports are closed. Must be the isp.
 I'll wait till tomorrow and I'll contact my isp and see what they say.

---

### Post by SeijiSensei on 2012-06-16
You can run an nmap scan against your IP address [here]("http://nmap-online.com/").  It will show you which ports, if any, are open.

---

### Post by jonnyboysmithy on 2012-07-02
------------------------------------------------

---

### Post by jonnyboysmithy on 2012-07-02
Turned out to be that the isp was blocking ports.. [SIZE=4]**Solved!!**[/SIZE]

Thanks for the help guys! much appreciated.

---

