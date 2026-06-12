---
title: "ssh wireless login time out"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by MichaelBurns on 2010-06-09
I can ssh just fine (over wireless) at home:
```

ubuntu@ubuntu:~$ ssh burns@phys.ufl.edu

```

However, from a different location (i.e. different wireless network), ssh times out before the password prompt.  After reading manpages and searching for suggestions on the internet for a while, I have tried a few things:
```

ubuntu@ubuntu:~$ ssh -o "UsePrivilegedPort no" burns@phys.ufl.edu
ssh: connect to host phys.ufl.edu port 22: Connection timed out

```
```

ubuntu@ubuntu:~$ ssh -o "AddressFamily inet" burns@phys.ufl.edu
ssh: connect to host phys.ufl.edu port 22: Connection timed out

```
```

ubuntu@ubuntu:~$ ssh -o "UseDNS no" burns@phys.ufl.edu
command-line: line 0: Bad configuration option: UseDNS

```
```

ubuntu@ubuntu:~$ nslookup burns@phys.ufl.edu
Server:		[*I hide the IP address in this post.*]
Address:	[*I hide the IP address in this post.*]

** server can't find burns@phys.ufl.edu: NXDOMAIN

```
```

ubuntu@ubuntu:~$ nslookup phys.ufl.edu
Server:		[*I hide the IP address in this post.*]
Address:	[*I hide the IP address in this post.*]

Non-authoritative answer:
Name:	phys.ufl.edu
Address: 128.227.64.7

```
```

ubuntu@ubuntu:~$ ssh -l burns 128.227.64.7
ssh: connect to host phys.ufl.edu port 22: Connection timed out

```
```

ubuntu@ubuntu:~$ ssh -4 128.227.64.7
ssh: connect to host phys.ufl.edu port 22: Connection timed out

```
```

ubuntu@ubuntu:~$ ssh -v burns@phys.ufl.edu
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to phys.ufl.edu [128.227.64.7] port 22.
debug1: connect to address 128.227.64.7 port 22: Connection timed out
ssh: connect to host phys.ufl.edu port 22: Connection timed out

```
and various combinations of the above.  The time out takes several minutes.  I emphasize that I can ssh just fine at home.  I can browse the interent just fine (using Firefox), but ssh times out when I try to log in.  Could the ISP be preventing ssh somehow, for some reason?

---

### Post by BoneKracker on 2010-06-09
Before you started fiddling with ssh options, I assume you tried (and succeeded) to ping the host from where you are? Yes?

It is likely something specific to the network you are on.  I get to it no problem from where i am (in Upstate New York):

```
~ $ nmap -p 22 phys.ufl.edu

Starting Nmap 5.21 ( http://nmap.org ) at 2010-06-09 15:09 EDT
Nmap scan report for phys.ufl.edu (128.227.64.7)
Host is up (0.089s latency).
rDNS record for 128.227.64.7: neptune.phys.ufl.edu
PORT   STATE SERVICE
22/tcp open  ssh

Nmap done: 1 IP address (1 host up) scanned in 0.52 seconds
```

I would assume first (before blaming ISP) that a firewall is blocking it.  Are you sure the firewall on the machine you're using allows ssh?  How about a firewall on the network?

---

### Post by MichaelBurns on 2010-06-09
Perhaps my description was unclear.  Same computer: a laptop with wireless.  I can ssh at home, on a network with IP address = x.  I cannot ssh at the particular other location with different IP address = y.  Both are unsecured networks that I just let networkmanager find and then I select them to connect.  (I am not paying for it, so I can't very well contact the ISP for assistance.)  In my naive understanding, the only difference that I see is the name and IP address of the network (which I thought the ISP was responsible for).

You assumed incorrectly.  I do not even know what "ping the host" means, much less did I do it.  "pinging the host" didn't come up in my internet search for a solution.  I assume that you assume that I know what I'm doing.  I hope that I have cleared up that false assumption.  ;)  I will look into "pinging the host", but I won't "ping the host" at the problem location until tomorrow (I'm home for the night, and this is beginning to sound a bit lecherous.)

Anyway, I am disappointed in the -v option to ssh; it just tells me what I already knew: that ssh times out when it tries to connect to that IP address.  How do I find out if there is a firewall on the network?

One other thing that I forgot to mention: I was able to browse to the phys.ufl.edu website in Firefox, so the network allows that IP address (right?).

---

### Post by BoneKracker on 2010-06-10
> **MichaelBurns said:**
> Perhaps my description was unclear.  Same computer: a laptop with wireless.  I can ssh at home, on a network with IP address = x.  I cannot ssh at the particular other location with different IP address = y.  Both are unsecured networks that I just let networkmanager find and then I select them to connect.  (I am not paying for it, so I can't very well contact the ISP for assistance.)  In my naive understanding, the only difference that I see is the name and IP address of the network (which I thought the ISP was responsible for).

You assumed incorrectly.  I do not even know what "ping the host" means, much less did I do it.  "pinging the host" didn't come up in my internet search for a solution.  I assume that you assume that I know what I'm doing.  I hope that I have cleared up that false assumption.  ;)  I will look into "pinging the host", but I won't "ping the host" at the problem location until tomorrow (I'm home for the night, and this is beginning to sound a bit lecherous.)

Anyway, I am disappointed in the -v option to ssh; it just tells me what I already knew: that ssh times out when it tries to connect to that IP address.  How do I find out if there is a firewall on the network?

One other thing that I forgot to mention: I was able to browse to the phys.ufl.edu website in Firefox, so the network allows that IP address (right?).

Yeah, I did assume you knew what you were doing because you did a pretty good job exhausting the diagnostic possibilities with ssh.  You seem to have a knack for this.

Ping is a way of testing a connection.  You can send out a single packet and, if it gets there, the computer on the other end will reply with a single packet.  They call it "ping" because it's kind of like using sonar to check if something's there.  Using it is simple:
```
ping -c 3 phys.ufl.edu
```
That will send out three packets with a delay between each, and wait for the computer on the other end to respond.  That will tell you whether you have basic network connectivity with whatever is answering for phys.ufl.edu on the other end.  You can learn about ping (or any other linux command) by opening up a terminal and typing "man <command name>", in this case
```
man ping
```
If you forget the "-c <number of packets>" option, it will ping forever, until you hit ctrl+c.

I went one step further and used a program called 'nmap' to probe the computer to see if port 22 is open (which would indicate that we're actually talking to a machine that is hosting sshd).  It did have port 22 open, so I don't think the problem is on the university's end.  (You don't need to install nmap.)

You should try pinging it, but the fact that you can reach the site via html indicates it's probably not a problem of basic network connectivity.

It could easily be that port 22 is blocked for some reason on the wireless LAN you are using.  Maybe you can try a different wireless or wired connection from your location?  Another possibility is that the university only accepts ssh connections from certain IP addresses and drops other connection attempts.  Most ISPs don't block ssh traffic (and if they did, they'd probably "reject" it (which courteously provides and immediately rejection notification to the sending computer so it can move on with its life), as opposed to "dropping" it (which causes the sending to computer wait and wait for a response and eventually time out).

Also, before continuing to bang your head against the wall, you should also verify that you are actually using the same address to which you have successfully connected before.  Don't be trying to ssh to "burns@phys.ufl.edu" if you should actually be connecting to "burns@orion.phys.ufl.edu" or "burns@31k2j3g.ufl.edu"; your Linux/UNIX accountname and hostname don't necessarily match your email address.

---

### Post by MichaelBurns on 2010-06-10
Wow, another elaborate and useful reply from the BoneKracker.  Good stuff.  Thank you!

> **BoneKracker said:**
> ... I did assume you knew what you were doing because you did a pretty good job exhausting the diagnostic possibilities with ssh.  You seem to have a knack for this.Aw, shucks *^_^*  No, seriously, this isn't the first "problem" that I've dealt with in Linux.  I don't know what I'm doing, but I "know the routine". ;)

> **BoneKracker said:**
> You can learn about ping (or any other linux command) by opening up a terminal and typing "man <command name>", in this case
```
man ping
```Yeah, I just didn't know (from your previous post) that there was actually a command named "ping".  But, I do know about the wonderful little "apropos" command.  That may very well be on my top 10 list of reasons why Linux is pretty darn nifty.  (Well, bash, I guess, but, what's the difference between bash and Linux if you actually try to do something nontrivial :P )  Anyway:
```

ubuntu@ubuntu:~$ ping -c 1 phys.ufl.edu
PING phys.ufl.edu (128.227.64.7) 56(84) bytes of data.
64 bytes from neptune.phys.ufl.edu (128.227.64.7): icmp_seq=1 ttl=240 time=64.8 ms

--- phys.ufl.edu ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 64.801/64.801/64.801/0.000 ms

```
So, if I understand that "diagnostic" correctly, there is no problem with the connection between this IP address and the phys.ufl.edu server.

> **BoneKracker said:**
> It could easily be that port 22 is blocked for some reason on the wireless LAN you are using.Uh oh ...

> **BoneKracker said:**
> Maybe you can try a different wireless or wired connection from your location?Well, yes, as I wrote in my previous posts: I can connect from the network at home.  Actually, there are two unsecured networks at home, and I can ssh on both of them.  However, there is only one unsecured network that networkmanager is picking up here at the other location.  So, that doesn't solve the problem.  I suppose actually paying for internet service might solve my problem, but let's not be ridiculous.

> **BoneKracker said:**
> Another possibility is that the university only accepts ssh connections from certain IP addresses and drops other connection attempts.I should mention that the location where I have this problem is in the same town as my house.  So, would the university possibly be so selective with the IP addresses that they allow to ssh?  (I'm assuming that IP addresses somehow encode the localle.)  I suppose they may have been blatantly attacked from this IP address?  But, then, why would they allow access through Firefox?  What's the difference?  (Whoops, my ignorance is showing again.)

> **BoneKracker said:**
> Also, before continuing to bang your head against the wall, you should also verify that you are actually using the same address to which you have successfully connected before.  Don't be trying to ssh to "burns@phys.ufl.edu" if you should actually be connecting to "burns@orion.phys.ufl.edu" or "burns@31k2j3g.ufl.edu"; your Linux/UNIX accountname and hostname don't necessarily match your email address.Right.  I did think of that.  Maybe I didn't mention that in my list of attempts, but I tried various (subdomains?), such as neptune.phys.ufl.edu, which I believe is what phys.ufl.edu defaults to (which seems to also be confirmed by your ping attempt).  I'm pretty sure that the "neptune" part is a physical computer somewhere in the physics building.  I think that, in general, their web addresses are of the form machine_name.phys.ufl.edu.  Anyway, I tried a few different machine_names (or subdomains?), but always with the same time out problem.

---

### Post by BoneKracker on 2010-06-10
> **MichaelBurns said:**
> ```

ubuntu@ubuntu:~$ ping -c 1 phys.ufl.edu
PING phys.ufl.edu (128.227.64.7) 56(84) bytes of data.
64 bytes from neptune.phys.ufl.edu (128.227.64.7): icmp_seq=1 ttl=240 time=64.8 ms

--- phys.ufl.edu ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 64.801/64.801/64.801/0.000 ms

```
So, if I understand that "diagnostic" correctly, there is no problem with the connection between this IP address and the phys.ufl.edu server.
Correct.  If you can ping it, you're actually talking over the wire to it, and it's talking back.  So the problem is that your attempts to connect to port 22 are being "dropped" (we must assume, intentionally) somewhere.

> **MichaelBurns said:**
> Uh oh ...

Well, yes, as I wrote in my previous posts: I can connect from the network at home.  Actually, there are two unsecured networks at home, and I can ssh on both of them.  However, there is only one unsecured network that networkmanager is picking up here at the other location.  So, that doesn't solve the problem.  I suppose actually paying for internet service might solve my problem, but let's not be ridiculous.

I should mention that the location where I have this problem is in the same town as my house.  So, would the university possibly be so selective with the IP addresses that they allow to ssh?  (I'm assuming that IP addresses somehow encode the localle.)  I suppose they may have been blatantly attacked from this IP address?  But, then, why would they allow access through Firefox?  What's the difference?  (Whoops, my ignorance is showing again.)
It's not likely that they would restrict access in such a haphazard manner.  I thought maybe the university may have been accommodating you at home, because of some arrangement you had unknowingly signed up for when they set up your account, but since you're actually piggy-backing on somebody else's connection at home, that's not likely.

As to your various attempts, as long as you are using precisely the same command you used from home -- the command that worked before -- it should work again.  Trying other things won't solve the problem.  (The only case in which that might not be true is if "home" for you is actually on the university's campus (i.e., you have been connecting from "inside" their actual network), but I gather that's not the case.)

It sounds like the administrator of the wireless lan you are using (at the "alternate" location -- the one that's "not home") has port 22 blocked.  Theoretically, it could also be their ISP, but that's less likely.  One reason port 22 gets blocked by some firewall administrators is that ssh can be used to create an encrypted "tunnel" through which a user can send traffic the firewall would otherwise block.

You could check and see if the university also has a different, non-standard port open for ssh connections, although that's relatively unlikely.  What I think you should do is contact the IT people at the university and ask if they support VPN connections by people away from the campus.  They probably do.  They may be able to help get you set up.

If they tell you "yes but we don't support linux", just find out what kind of VPN (or VPNs) they have (e.g. OpenVPN, IPSec, etc.), tell them you want access anyway, get any information they would normally provide for someone to configure their VPN client, and then come ask in the Ubuntu forums for help to get that set up (if you can't figure it out).

Good luck.

---

### Post by MichaelBurns on 2010-06-10
> **BoneKracker said:**
> It sounds like the administrator of the wireless lan you are using (at the "alternate" location -- the one that's "not home") has port 22 blocked.OK.  I will be researching this "port 22" thing,  (and "sockets", too).

> **BoneKracker said:**
> You could check and see if the university also has a different, non-standard port open for ssh connections, although that's relatively unlikely.  What I think you should do is contact the IT people at the university and ask if they support VPN connections by people away from the campus.Excellent, I will do that.  But I don't want to draw too much attention to myself, since they have graciously allowed me to keep my university email account active for 8 months now after graduation.  So, I will only get minimal assistance from them - nothing account specific.

> **BoneKracker said:**
> If they tell you "yes but we don't support linux", ...That will certainly be the least problem.  I was forced to use Linux by the IT department, and I'm glad.  Now I cringe at the thought that some company may require me to use a Windows machine for work (when I finally get a job).  The IT guys would rather not support Windows, but they are forced to because most people ...

Thanks for the help.  You have given me some good suggestions to look into.

UPDATE:

Apparently they're on to me.  I no longer find the unsecured network in networkmanager (for the last few days).  Maybe they went on vacation (and shut down their network).  I will let you know whether any of your suggestions worked if the network ever reappears.

---

