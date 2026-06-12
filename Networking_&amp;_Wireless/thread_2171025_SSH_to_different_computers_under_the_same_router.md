---
title: "SSH to different computers under the same router"
date: 2013-08-28
forum: Networking &amp; Wireless
---

### Post by mamboknave on 2013-08-28
At home I always had a single PC with Ubuntu, connected to a router via eth0.

I can easily login to that PC from remote with ssh.
I simply use the command (it's a fake address here):

> ssh 12.345.678.90

where the 12.345.678.90 is the external/wan IP address that I obtained with [www.whatismyip.com](www.whatismyip.com)

Now, to the same router I connected a second PC, still via eth0, and I want to login to either of the two from remote.

**Big, Critical Question: How can I select which machine to login to?**

Lesser qs: what command line outputs the external/wan IP address without resorting to a website?

Thanks a bunch.

Disclaimer1: I know nearly noting about networking.
Disclaimer2: I did google the matter obtaining so much material but nothing clear to me.

---

### Post by bkline on 2013-08-28
What you'll want to do is to tell your router to pass traffic coming in on port 22 traffic to port 22 traffic on machine A and traffic coming into port 2222 (picked at random) to go to port 22 on machine B.  So when you ssh to B it looks like this:

ssh -p 2222 12.345.678.90

The details for configuring the router will vary from router to router.  You should be able to find documentation for most common routers on the web.

Good luck!

---

### Post by 1clue on 2013-08-28
You seem to be configured to pass the public IP address through to your PC.  That has to stop.

You can do this several ways.  Here's the big ones in order of what I consider to be most likely:
Use NAT and map through your router.
[LIST=1]
[*]Set your router up to have an internal network.
[*]Your existing PC gets one static address. Say 192.168.1.4
[*]Your new PC gets another static address. Say 192.168.1.5
[*]Configure your router (probably through an apps or gaming section) to forward some port to the first host (.4) on port 22.
[*]Configure your router to forward a different port to the second host (.5) on port 22.
[/LIST]

Use multiple public IPs (which costs extra money)
[list=1]
[*]Call your ISP
[*]Get them to give you multiple public IPs, which is usually available only for business accounts.
[*]Configure your second box for one of the public IPs.
[/LIST]

---

### Post by sanderj on 2013-08-28
So you forwarded port 22 to PC1 (port 22), right?

If so, the answer is easy: forward port 1022 (for example) to PC2 (port 22), and then use 'ssh -p 1022 12.345.678.90' to connect to PC2

Solved

---

### Post by 1clue on 2013-08-28
Another thing:
You might want to check your logs to see if somebody's been trying to brute force your system through ssh.

It's a really bad idea to expose SSH directly on the net, on the default port.

It's a crazy bad idea to just expose a box with no security measures.

---

### Post by mamboknave on 2013-08-28
Ok, Thanks. I must go step by step. Will try the easier way first, then will take care of security.

In the router config screen I enable port 122 for the second machine, DT1. Among other things, the screen says:

**Allowed Apps: sshandsftp; Port Num: 122, Public IP: 12.345.678.90, IP address: 192.168.1.66**

(yes, in order to assign a port I had to define any custom application name - could not pick 'SSH server' from the apps list because 'SSH server' is assigned to DT0)

For DT0, the one that was always accessible, the router config screen says:

**Allowed Apps: SSH Server; Port Num: 22; Public IP: 12.345.678.90; IP address: 192.168.1.64**

(hence, port 22 is assigned to DT0 as SSH server)

With all this done, when I try

> ssh -p 122 12.345.678.90

the answer is:

**> ssh: connect to host 12.345.678.90 port 122: Connection refused.**

Why so? Do I have to set up something on DT1 ?

---

### Post by CharlesA on 2013-08-28
> **1clue said:**
> You can do this several ways.  Here's the big ones in order of what I consider to be most likely:
Use NAT and map through your router.

That is how I have my network setup and it works wonders, even though you do need to remember which port to forwarded.

> **1clue said:**
> Another thing:
You might want to check your logs to see if somebody's been trying to brute force your system through ssh.

It's a really bad idea to expose SSH directly on the net, on the default port.

It's a crazy bad idea to just expose a box with no security measures.

+1. If you are going to expose SSH to the internet, give it a strong password and disallow root logins at the minimum. I prefer using RSA keys, myself.

@mamboknave: You will need to test the connection from outside your local LAN. You can use canyouseeme.org to see if the port is open.

Otherwise you run into problems trying to connect to your own external IP from inside the network.

---

### Post by mamboknave on 2013-08-28
>> You will need to test the connection from outside your local LAN. You can use canyouseeme.org to see if the port is open

Done. Output:
Error: I could not see your service on 12.345.678.90 on port (122) Reason: Connection refused

With port 22:
Success: I can see your service on 12.345.678.90 on port (22) Your ISP is not blocking port 22

---

### Post by 1clue on 2013-08-28
Here's one more clue:  (1clue!)

Don't post a real public IP address and ask basic questions about ssh and port forwarding on any Linux forum.  It shouts, "Come get me!"

Here's another one:  Don't tell people what port you forwarded.

Here's another one:  Don't map a port under 5000.  Most black-hat hackers choose lower ports to scan.

Do yourself a favor, and change those ports.  And don't tell us what you changed to.  And you might as well make sure all your other ports are turned off by default.

From inside your router you need to use the 192.168.1.x address, and the regular port 22.  That is, unless you change the port sshd is listening on on that host.

It's only from outside the network you would hit the public address and the mapped IPs.

---

### Post by steeldriver on 2013-08-28
Have you forwarded public IP port 122 to the second machine's port **22**? or does the router only allow forwarding the same port number (i.e. 12.345.678.90:**122** --> 192.168.1.66:**122**)? if the latter, then you may need to change the actual port that 192.168.1.66's SSH server is listening on (in /etc/ssh/sshd_config) to match

---

### Post by mamboknave on 2013-08-28
Steeldriver:

>> or does the router only allow forwarding the same port number (i.e. 12.345.678.90:122 --> 192.168.1.66:122)? if the latter, then you may need to change the actual port that 192.168.1.66's SSH server is listening on (in /etc/ssh/sshd_config) to match 

Rightfully so!

Now I can login (brutally) through the public IP address. Next: take care of security. I'll get back here soon.

Thanks to everyone.

---

### Post by mamboknave on 2013-08-30
**Sorry, this was easy. I posted before googling. Pls disregard. RESOLVED: -oPort=nnn**

Now I can ssh from outside the network to a specific computer behind the router/gateway using the specific forwarding port number and the gateway IP-address:

> ssh -p 2222 12.345.678.90

What is the equivalent for sftp?
I mean, how can I sftp to that specific port (which connects to a specific computer)?

---

### Post by steeldriver on 2013-08-30
For historical (I think) reasons, the port for both sftp and scp is specified with an uppercase -P (as opposed to the lowercase -p used by ssh), i.e.

```
sftp -P 2222 user@rem.ote.host.com
```

```
scp -P 2222 user@rem.ote.host.com:/path/to/remote/file /path/to/local/file
```

---

### Post by mamboknave on 2013-08-30
Thanks Steeldriver. But I see that the option -P 2222 does not work for me, while -oPort=2222 works. So, I am all set.

On a side topic: now I can do ssh and sftp from outside the network to each of the computers via the gateway IP address (say 12.345.678.90) and the forwarding port:

> ssh -p 2222 username@12.345.678.90

It works very fine.

Is there anything special I should do for security reasons?

---

### Post by 1clue on 2013-08-30
Why not use scp -P 2222 ./myFile username@<address>:

---

### Post by sanderj on 2013-08-31
> **mamboknave said:**
> **Sorry, this was easy. I posted before googling. Pls disregard. RESOLVED: -oPort=nnn**

Now I can ssh from outside the network to a specific computer behind the router/gateway using the specific forwarding port number and the gateway IP-address:

> ssh -p 2222 12.345.678.90

What is the equivalent for sftp?
I mean, how can I sftp to that specific port (which connects to a specific computer)?

self-help tip: "man sftp | grep -i port"

HTH

---

