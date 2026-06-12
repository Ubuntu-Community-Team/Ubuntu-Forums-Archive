---
title: "SSH from outside a LAN"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by jus71n742 on 2010-02-16
I have SSH enabled on my laptop/Desktop and FreeBSD server using openSSH.  It works flawlessly when I am on my personal LAN, even wirelessly.  However if I go to my girlfriends place or School.  It won't connect at all.  just hangs until I <ctrl> c out of it.

What do I need to do to use SSH from outside my personal LAN?
I havn't gotten many clear answers in my research.

---

### Post by ask21900 on 2010-02-16
Do you have port forwarding configured?

---

### Post by Iowan on 2010-02-16
There are several SSH help pages at [help.ubuntu.com]("https://help.ubuntu.com/community/SSH")

---

### Post by BrandonBan6 on 2010-02-16
This is an awesome setup, I use it myself quite a bit. 

1.) You have to make sure you forward the ports in your router
2.) you have to know your external IP, the one that you get from your ISP. It often changes (DHCP) so you can use a free service from no-ip.com to generate a host redirect (i.e. every time your ip changes, the server updates a hostname, then you only have to remember the hostname).

---

### Post by jus71n742 on 2010-02-16
> **BrandonBan6 said:**
> This is an awesome setup, I use it myself quite a bit. 

1.) You have to make sure you forward the ports in your router
2.) you have to know your external IP, the one that you get from your ISP. It often changes (DHCP) so you can use a free service from no-ip.com to generate a host redirect (i.e. every time your ip changes, the server updates a hostname, then you only have to remember the hostname).

I found that online but was gunshy of it for obvious reasons.  Can I use it on more than one machine for free? cause I have a few...or should I just set it up for one machine, then use that machine to log into the others? Kinda like when I remotely log into my Free BSD and then su into root?

and one last small thing that is probably a really stupid questions but I am going to ask it anyways.
yesterday I looked at 
```

ifconfig 

```
and again today. the IP address is the same.  and then checked with what I wrote down last week.  same. Sooo how can I not connect with ```

ssh user@ipadd

```

---

### Post by BrandonBan6 on 2010-02-17
> **jus71n742 said:**
> I found that online but was gunshy of it for obvious reasons.  Can I use it on more than one machine for free? cause I have a few...or should I just set it up for one machine, then use that machine to log into the others? Kinda like when I remotely log into my Free BSD and then su into root?

and one last small thing that is probably a really stupid questions but I am going to ask it anyways.
yesterday I looked at 
```

ifconfig 

```
and again today. the IP address is the same.  and then checked with what I wrote down last week.  same. Sooo how can I not connect with ```

ssh user@ipadd

```

Well, I've never set it up to use more than one computer. For security, I like to just SSH to one machine and do most of what I can from that one machine, then transfer locally later if I need to. I would advise you to do whatever makes you more comfortable. 

when you say you can't connect with:
```
ssh user@ipadd
``` 
Are you saying that you can't connect locally, like from within your network? Or are you saying you can't connect remotely, from starbucks or wherever? If it is the latter, then you need to go to whatsmyip.com; use your external IP address (ifconfig won't tell you that) and then use:
```
 ssh user@external_ipaddress
```
If you have forwarded your ports in your router correctly; when SSH pings your router, it will know which workstation to forward the ports too. 


If you are saying that when you use:
```

ssh user@ipadd

```

From inside your LAN, then perhaps try a ping or tracert to that IP address; see if you can trace down where it is getting stuck. Also try using the hostname instead of the IP.

---

### Post by jus71n742 on 2010-02-18
Yes I am refering to ssh from a remote location.  I will try that and see what I can do. Thanks


The site is [http://whatsmyip.org](http://whatsmyip.org)  
I will try it out tomorrow

---

### Post by jus71n742 on 2010-02-19
I finally figured out how to enable port forwarding on the router (Westel Versalink 327W) I am having someone attempt to connect to me from a remote location.  All they are getting is timeouts.  I enabled it on PORT 22 and to my ip address.  What else do I need to do so that SSH will work and I can remotely log into my machine?

---

### Post by ask21900 on 2010-02-20
Are you able to ssh OUT of your local network? (Your ISP might be blocking 22 for whatever reason..  Some do)

When configuring port forwarding on your router, make sure you enable the port forward (some routers have a check box to enable each forward).  Also, verify that the IP you entered in the port forwarding options is your local IP, not your public IP.

Sorry if this sounds obvious to you but I don't know your level of expertise.

---

### Post by jus71n742 on 2010-02-20
I have tried to ssh out and I can.  I used to do it all the time into a school machine.  I have made sure that I enabled port forward (no check boxes just it is or isn't).  I have tried both DNS address, Local ip and external ip.  I did notice one thing. my hostname on the machine I am trying to log into is not the same as what the router shows.  example:  I have it listed as ubuntu2.launchmodem.com (this is what works on the LAN) but the router shows this machine as edwards-desktop as the name.  Sooo outside the LAN which should I use.

---

### Post by jus71n742 on 2010-02-22
I tried setting up no-ip and I have it installed and running but my connection is still timing out
I am not really sure what all I need to do on no-ip for it all to work.  I did set up a host name and that is it.  I am starting to think its my Router (Westel VersaLink W367) 
I did have a guy give me some Cisco VPN routers. I am tempted to try one of them out to see if I can SSH into them
any other idea's? that sound like a good idea?

---

### Post by BrandonBan6 on 2010-02-24
If you/your friend runs a trace route from an outside location to your address, it may reveal where you are getting snagged. 

```

# sudo apt-get install traceroute
#sudo tracert XXX.XXX.XXX 

```

Where xxx.xxx.xxx is your external IP address.

---

### Post by jus71n742 on 2010-02-24
> **BrandonBan6 said:**
> If you/your friend runs a trace route from an outside location to your address, it may reveal where you are getting snagged. 

```

# sudo apt-get install traceroute
#sudo tracert XXX.XXX.XXX 

```

Where xxx.xxx.xxx is your external IP address.

forgot all about that command 
thanks

---

### Post by harisund on 2010-02-24
ok let me try and explain my take on this - 

1. Let's deal strictly with numeric IP addresses. For now, no hostnames. It is confusing at first, but let's get it to work with numbers first. 

2. The IP address you see as the result of "ifconfig" is Local IP. Let's call this 192.168.0.100. This is the number the router assigns your desktop. Let's also assume 192.168.0.101 is the IP the router has assigned to your laptop, as long as you are at home. So, at the moment, you are able to ssh into your desktop by "ssh 192.168.0.100" and it works. 

3. The router has 2 interfaces. One is the private interface, 192.168.0.1 that you use to access its web interface, one is the public interface, whose address you find by going to [http://whatismyip.com](http://whatismyip.com) or something (Let's call this x.y.z.w) 

4. Navigate to the router interface, and do a port forward of port 22 to 192.168.0.100 (your desktop local IP). Or better still, port forward external port 8000 odd to internal port 22. Some ISPs might block ports under 1024

5. Go to your school or girlfriends' place, and connect to the public IP, the x.y.z.w address). But connect to port 8000.

Keep in mind the problems you could potentially face - 
a. ISP has blocked the port. The work around is to use the higher numbered port to connect. 
b. Your desktop might have acquired a new IP. In other words, you would have asked your router to forward to port 22 of 192.168.0.100, but your desktop might now have 192.168.0.101. The work around is to let your desktop have a static IP instead

---

### Post by bpalone on 2010-02-24
I don't know your experience level, so don't be offended if this is to elementary. It might help someone else, though.

Your command from outside should look something like this:

```
ssh -p 8000 -l username x.y.z.w
```

 username is your user name on your desktop

the -p instructs to use port 8000

the -l tells it login as username


If all goes well you get greeted with a request for your password.

---

### Post by jus71n742 on 2010-02-24
C:\Documents and Settings\mtunions>tracert xx.xx.xxx.xxx

Tracing route to adsl-xx-xxx-xxx.tys.bellsouth.net [xx.xx.xxx.xxx]
over a maximum of 30 hops:

  1    <1 ms    <1 ms    <1 ms  c-ssr-eth-36.mtsu.edu [161.45.228.1]
  2    <1 ms    <1 ms    <1 ms  TelecomX4.mtsu.edu [161.45.254.98]
  3     *        *        *     Request timed out.
  4     *        *        *     Request timed out.
  5
is one from a friends machine. 

Note that since I am primarily trying to do this from a remote windows machine at a local Community college.  So I am forced to use PuTTy.

Here is what I have done so far:
Logged into my router and enabled port forwarding on Port 22.  
tried using no-ip for and remotely logging in this way...nothing.
Remotely logging into the IP of the router, timeout.
Logging in with various Hostnames from no-ip to what I have named the desktop.

experience level is mostly know some commands but I haven't used them enough to really do much.

---

### Post by bpalone on 2010-02-24
I don't know anything about Putty.  But, try this link to make sure the outside world can see you: [http://www.canyouseeme.org/]("http://www.canyouseeme.org/")

That way you can rule that out.  Good luck, I'll back away and maybe someone that know putty can help.

---

### Post by harisund on 2010-02-25
Don't publicly enter your IP address !!!! :) :) 

Anyway, since you did I tried doing a tracert too. 

And after 20 different hops I was able to reach your IP. 

Maybe the problem is with the friends' computer in this college? Is he on a restricted  network? 

Or perhaps the university blocks accesses to certain websites, and your address is on one of such black lists? 

Given what you have posted I am tempted to think the problem might not necessarily be on your end alone. 

> **jus71n742 said:**
> C:\Documents and Settings\mtunions>tracert  w.x.y.z

Tracing route to adsl-70-126-128.tys.bellsouth.net [ w.x.y.z]
over a maximum of 30 hops:

  1    <1 ms    <1 ms    <1 ms  c-ssr-eth-36.mtsu.edu [*.*.*.*]
  2    <1 ms    <1 ms    <1 ms  TelecomX4.mtsu.edu [*.*.*.*]
  3     *        *        *     Request timed out.
  4     *        *        *     Request timed out.
  5
is one from a friends machine. 

Note that since I am primarily trying to do this from a remote windows machine at a local Community college.  So I am forced to use PuTTy.

Here is what I have done so far:
Logged into my router and enabled port forwarding on Port 22.  
tried using no-ip for and remotely logging in this way...nothing.
Remotely logging into the IP of the router, timeout.
Logging in with various Hostnames from no-ip to what I have named the desktop.

experience level is mostly know some commands but I haven't used them enough to really do much.

---

### Post by BrandonBan6 on 2010-02-25
> **harisund said:**
> Don't publicly enter your IP address !!!! :) :) 

Anyway, since you did I tried doing a tracert too. 

And after 20 different hops I was able to reach your IP. 

Maybe the problem is with the friends' computer in this college? Is he on a restricted  network? 

Or perhaps the university blocks accesses to certain websites, and your address is on one of such black lists? 

Given what you have posted I am tempted to think the problem might not necessarily be on your end alone.

Me too, and I'm able to ping the address. What command are you using to remotely SSH?

---

### Post by 2hot6ft2 on 2010-02-25
Is the firewall on your SSH server set to allow only connections from within your LAN, your clients ip when on the LAN, or everyone which would include from outside your LAN?

---

### Post by jus71n742 on 2010-02-25
I am trying to use PuTTy since where I will mostly need remote access will be in a Windows environment.  The 2 networks I have been testing from and the one I will be using, The one shown, I have no clue about their policies, Network 2 I used to use all the time with SSH into their machines.  and the last one I spoke to the Admin and he said their is nothing wrong with connecting in.

firewall settings are set to allow the pretty much everything including telnet, and FTP. However there isn't a setting showing SSH...sooo I am not real sure

---

