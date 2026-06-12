---
title: "Monitor network traffic per user"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by s3gfault on 2008-12-03
I'm running a proxy server for myself and a few mates.  It has a few different proxy applications on it, a socks 5 proxy, a http proxy, etc.  I don't necessarily want to put traffic quotas on each user, but i do want to figure out how to do that if it becomes necessary.  At this point I can't even tell which user is using which traffic.  What i want is just like a graph view of each username and the associated amount of network traffic tied to that account.  I know you may be thinking that this won't account for proxy traffic because the instances spawned of the proxy servers are not owned by the users that are connecting to the service, but that doesn't matter because i require everyone to connect through ssh tunnels.  So i can just monitor the amount of traffic generated for each user in sshd and that would be accurate.

I looked a bit at the iptables documentation, but this doesn't seem well suited to my needs.  i mean it has a match extension called "owner" that would let me test for traffic for a specific user, but i don't want to be updating my firewall script as i add and remove users.

so, any suggestions?

---

### Post by s3gfault on 2008-12-08
bump

---

### Post by Dr Small on 2008-12-08
What are you using for the proxy server? Squid?

---

### Post by s3gfault on 2008-12-08
oops and danted
I have authentication disabled on both of them though, because users are required to connect by ssh tunnel, so the logging facilities of those proxies aren't very useful.

---

### Post by s3gfault on 2008-12-09
have you heard of this new dance?  its called the BUMP

---

### Post by s3gfault on 2008-12-09
google chrome has a few bugs left in it.

Even though the edit button has a tooltip that says "change/delete" i don't see a control to delete the post.  I'm just a noob i guess.

---

### Post by s3gfault on 2008-12-10
le bump

---

### Post by s3gfault on 2008-12-12
Has anyone got advice on the subject in post #1?

---

### Post by s3gfault on 2008-12-21
any ideas?

---

### Post by s3gfault on 2008-12-22
[quote=fergy]my bumps, my bumps, my lovely lady bumps.[/quote]:ks

---

### Post by andguent on 2008-12-22
The program iptraf will help you see what IP addresses are creating the most traffic at the current time. It really isn't meant for logging though.

Also see ntop, tcpdump, wireshark, and munin.

---

### Post by s3gfault on 2008-12-22
did i forget to mention that all of my users connect through the same http proxy?  they all have the same ip address :(

ive looked at munin but i dont think there is a plugin that meets my needs

---

### Post by andguent on 2008-12-22
Do they all come from the same IP, or go out to the same IP? If they come from different places (as far as your server is concerned), then it is good enough.

---

### Post by s3gfault on 2008-12-22
> **andguent said:**
> Do they all come from the same IP, or go out to the same IP? If they come from different places (as far as your server is concerned), then it is good enough.

no, they come from the same ip.  i make them make a ssh tunnel in putty and it goes through a http proxy to my server.  they authenticate with unix accounts.  then they connect through the tunnel to the loopback device and one of my proxy servers.  It's an anonymizing service i provide to a select few coworkers.  So they all have the same source ip address.

The only way i can tell who is using what traffic is by matching the TCP Source port of incoming packets against the owner of the sshd process that is connected to the other end of that stream.

I don't have to measure traffic that flows in and out of my server to/from the internet, all of the interesting traffic will be forwarded out of the ssh tunnel back to the user gateway.

I don't make them authenticate to the proxy service because the proxy only listens on the loopback device, so any user who can connect to it is already authenticated.  If i did turn on the authentication features of the proxies i run, then i could use the logging facilities of those proxies and measure traffic, but i'm not that interested in the problem right now.

Probably i will install munin and write a perl plugin for it that does what i need, but i think that can only be done by polling an iptables logfile, idk how that works exactly.

What i was hoping was for a package that supports my use case to be already developed.  oh well.

EDIT:
even if i could find a program that will report the amount of traffic used by each process, then i could write my own logic to map that back to users.

---

