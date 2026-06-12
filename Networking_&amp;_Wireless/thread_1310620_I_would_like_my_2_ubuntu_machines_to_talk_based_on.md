---
title: "I would like my 2 ubuntu machines to talk based on computer name. How?"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-11-01
Let's say I'm setting up a very large DHCP network with several hundred Ubuntu machines. We all know the quick and easy fix of making the Ubuntu machines with a static IP and adding each host name to /etc/hosts, and that's all well and good, but not practical at all for large networks who run on DHCP.

What do I need to get my Ubuntu machines to talk based on computer name alone? I want to be able to ping in terminal other machines and run ssh to the host name instead of the IP.

What do I need to do?

---

### Post by null77 on 2009-11-02
Just posted the same issue, no solution ATM.

[http://ubuntuforums.org/showthread.php?t=1310632](http://ubuntuforums.org/showthread.php?t=1310632)

---

### Post by houstonbofh on 2009-11-02
Not that y'all are in a hurry or anything.  But here is a solution. [http://m0n0.ch/wall/](http://m0n0.ch/wall/)  The problem is in your name server, not your desktops.

---

### Post by Technophobia on 2009-11-02
I always just installed the winbind package and then added wins under host in /etc/nsswitch.conf.

---

### Post by Roasted on 2009-11-02
> **houstonbofh said:**
> Not that y'all are in a hurry or anything.  But here is a solution. [http://m0n0.ch/wall/](http://m0n0.ch/wall/)  The problem is in your name server, not your desktops.

I'm a little confused. The description on the web site didn't really give me any indication as to how it would apply with aiding in the issue I'm having. What exactly does this do to help computers talk by name?

---

### Post by sanderj on 2009-11-02
> **Roasted said:**
> 


What do I need to do?

Use <ubuntu-name>".local.", so for example "mybox.local.", and use that name to ping/ssh/telnet/browse to. Please note the trailing dot.

```

sander@quirinius:~$ ping quirinius.local.
PING quirinius.local. (192.168.2.163) 56(84) bytes of data.
64 bytes from quirinius.lan (192.168.2.163): icmp_seq=1 ttl=64 time=0.047 ms
64 bytes from quirinius.lan (192.168.2.163): icmp_seq=2 ttl=64 time=0.080 ms
^C
--- quirinius.local. ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.047/0.063/0.080/0.018 ms

sander@quirinius:~$ ping macintosh.local.
PING macintosh.local. (192.168.2.146) 56(84) bytes of data.
64 bytes from Macintosh.local (192.168.2.146): icmp_seq=1 ttl=64 time=8.22 ms
64 bytes from Macintosh.local (192.168.2.146): icmp_seq=2 ttl=64 time=1.41 ms
64 bytes from Macintosh.local (192.168.2.146): icmp_seq=3 ttl=64 time=1.32 ms
^C
--- macintosh.local. ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 1.325/3.654/8.222/3.230 ms

sander@quirinius:~$ ssh macintosh.local.
ssh: connect to host macintosh.local. port 22: Connection refused
sander@quirinius:~$


```

---

### Post by Roasted on 2009-11-02
I tried that. I have SSH installed on two Ubuntu computers, but when I ssh skynet.local, it still doesn't find the computer, yet I have avahi-daemon installed (which I was informed in IRC is what I want to make sure the Ubuntu machines talk to each other based on PC name).

---

### Post by sanderj on 2009-11-02
> **Roasted said:**
> I tried that. I have SSH installed on two Ubuntu computers, but when I ssh skynet.local, it still doesn't find the computer, yet I have avahi-daemon installed (which I was informed in IRC is what I want to make sure the Ubuntu machines talk to each other based on PC name).

Can you ping your own system name?

So, what's the output of 'uname -n'? Can you ping that <name>".local."

Please post output here. Example:

```

sander@quirinius:~$ uname -n
**quirinius**
sander@quirinius:~$ **ping quirinius.local.**
PING quirinius.local. (192.168.2.163) 56(84) bytes of data.
64 bytes from quirinius.lan (192.168.2.163): icmp_seq=1 ttl=64 time=0.051 ms
64 bytes from quirinius.lan (192.168.2.163): icmp_seq=2 ttl=64 time=0.056 ms
^C
--- quirinius.local. ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.051/0.053/0.056/0.007 ms
sander@quirinius:~$ 


```

---

### Post by Roasted on 2009-11-02
No, I could not ping my name. It just said host not found.

---

### Post by Grenage on 2009-11-02
Am I missing something obvious here?  Why not just use a DNS server?

---

### Post by Roasted on 2009-11-02
Sure, a DNS server would work I guess. I just (don't mean to stir up a ruckus here) thought MAYBE Ubuntu computers could talk to each other by computer name in the same manner Windows machines do... After all, I have no DNS server here, yet Windows can see other Windows machines. And even at that, Windows machines can see my main Ubuntu computer (Samba Server) by computer name too. I just didn't see why Ubuntu-to-Ubuntu would be that different.

---

### Post by sanderj on 2009-11-02
> **Roasted said:**
> No, I could not ping my name. It just said host not found.

Are you willing & able to post the output I asked for?

---

### Post by Roasted on 2009-11-02
> **sanderj said:**
> Are you willing & able to post the output I asked for?

Oh absolutely. I'm just stuck at work right now. :P I'll post back here this evening after I get home from work and have access to the Ubuntu machines at home that this thread is about.

---

### Post by houstonbofh on 2009-11-02
You are talking about two different things here.  One is Windows browsing via smb, or cifs.  This does not require name resolution, as it runs by broadcast.  (Much to the frustration of network admins everywhere) While it works, it is a noisy protocol.

The other is TCP/IP name resolution.  This is usually handled by your router.  A lot of cheap broadband routers tie DHCP and DNS togeather.  The firewall link I posted does this as well.  But if your router does not, you will have no TCP/IP name resolution, whatever system you use.

---

### Post by Iowan on 2009-11-02
**dnsmasq** is package that will do that. Another option might be **djbdns**.
Editing */etc/hosts* file works if addresses are static.

---

### Post by null77 on 2009-11-02
Make sure samba is running/restart it. That was my problem.

---

### Post by renkinjutsu on 2009-11-02
> **Iowan said:**
> **dnsmasq** is package that will do that. Another option might be **djbdns**.
Editing */etc/hosts* file works if addresses are static.

but that would mean editing the /etc/hosts file for ALL the machines =[. Not good for large networks =\

---

### Post by Roasted on 2009-11-02
> **null77 said:**
> Make sure samba is running/restart it. That was my problem.

Did that. Many times.

uname -n on my main rig = Area51
uname -n on my other rig = skynet

---

### Post by ibuclaw on 2009-11-03
[LIST=1]
[*]Ensure your router supports local name resolution (enter the router configuration and check the attached devices).
[*]Ensure there are no system firewalls blocking the ICMP protocol.
[/LIST]

As adamant you seem to accept it, it is the DNS server here, or whatever is acting as the DNS Server that is at fault here if you cannot ping local workstations.

Regards

---

### Post by Roasted on 2009-11-03
> **tinivole said:**
> [LIST=1]
[*]Ensure your router supports local name resolution (enter the router configuration and check the attached devices).
[*]Ensure there are no system firewalls blocking the ICMP protocol.
[/LIST]

As adamant you seem to accept it, it is the DNS server here, or whatever is acting as the DNS Server that is at fault here if you cannot ping local workstations.

Regards

I'm not too sure if it supports it. I'm using a WRT54G router.

I can assure you there is no firewall in the situation here, though.

---

### Post by ibuclaw on 2009-11-03
> **Roasted said:**
> I'm not too sure if it supports it. I'm using a WRT54G router.

I can assure you there is no firewall in the situation here, though.

and running:
```
ping Area51.local
```
or
```
ping AREA51.local
```
from skynet shows nothing?

and
```
ping skynet.local
```
or
```
ping SKYNET.local
```
from Area51.


Login to your router, it's usually
```
http://192.168.1.1
```
in the firefox browser and enter in the username/password (both are usually 'admin' if no set already) and for attached devices to see the name as the router has it.

Regards
Iain

---

### Post by Roasted on 2009-11-03
I was informed that avahi-daemon does what I need. I have it installed on both machines.

skynet can ping area51
area51 cannot ping skynet

weird?

---

### Post by ibuclaw on 2009-11-03
> **Roasted said:**
> I was informed that avahi-daemon does what I need. I have it installed on both machines.

skynet can ping area51
area51 cannot ping skynet

weird?

I'd try a third device on the network.

ie: Fred

If area51 can ping Fred, the issue may be with the firewall settings of skynet. (This can be confirmed if you try pinging skynet from Fred too).

If area51 can't ping Fred, the issue may be with how area51 is receiving it's name resolution. (Although, try pinging Fred from skynet too, just incase Fred blocks echoing calls).

Are both area51 and skynet Linux machines?

If so, post the output of:
```
sudo iptables -L
```
from both of them.

Regards
Iain

---

### Post by Roasted on 2009-11-03
I'll check it when I get home, but to answer what questions I can now:

Yes, both machines are Ubuntu 9.04 machines.

But - what firewall? I did not install a firewall. Unless Ubuntu comes out of box pre-configured with a firewall that I don't know about, no firewall exists in this situation.

---

### Post by Iowan on 2009-11-03
> **renkinjutsu said:**
> Not good for large networks =\I completely agree,  but for "my 2 Ubuntu machines"...

---

### Post by Roasted on 2009-11-03
> **Iowan said:**
> I completely agree,  but for "my 2 Ubuntu machines"...

Yeahhhhhh... but you see... I'm a computer tech at a large school district with well over a thousand machines.

Naturally, being a Linux head in a Windows environment, I often try to envision the entire district running Ubuntu. What would be different? What would I need to do? Change? Set up? etc.

So despite me only having 2 computers to set up, I'm (at the same token) curious on how I could mimic my 2 computer set up to be equivalent to a huge 2,000+ computer district all running Ubuntu. Only difference would be - I'm on a much smaller scale @ 2 computers. :P

---

### Post by lykwydchykyn on 2009-11-03
> **Roasted said:**
> Yeahhhhhh... but you see... I'm a computer tech at a large school district with well over a thousand machines.

Naturally, being a Linux head in a Windows environment, I often try to envision the entire district running Ubuntu. What would be different? What would I need to do? Change? Set up? etc.

So despite me only having 2 computers to set up, I'm (at the same token) curious on how I could mimic my 2 computer set up to be equivalent to a huge 2,000+ computer district all running Ubuntu. Only difference would be - I'm on a much smaller scale @ 2 computers. :P

You'd need the same thing a network of 2000+ Windows boxes needs -- a DNS server that talks to the DHCP server.  I've set this up at work on debian boxes for our WinXP clients.  There's really no difference between OS on this one.

Now, if you're talking about smb/cifs (NetBIOS) name resolution, that's another issue.  I suppose samba can do that, but it doesn't affect services like ssh/ping/nfs.

---

### Post by Iowan on 2009-11-03
> **Roasted said:**
> Yeahhhhhh... but you see... I'm a computer tech at a large school district with well over a thousand machines.I still completely agree... ;) 
and a thousand machines *probably* use DHCP - which is the other (another) shortcoming - so the */etc/hosts* file probably isn't practical. But, on a network that large, (as mentioned) a DNS server becomes more practical than for 2 machines...

---

### Post by Roasted on 2009-11-04
> **Iowan said:**
> I still completely agree... ;) 
and a thousand machines *probably* use DHCP - which is the other (another) shortcoming - so the */etc/hosts* file probably isn't practical. But, on a network that large, (as mentioned) a DNS server becomes more practical than for 2 machines...

Yeah, it makes sense. I wasn't completely thinking thoroughly with this, but it's true. We rely on our DNS server at work in our Windows network, so it makes sense that the same would be needed with a comparably sized Ubuntu network.

Is it possible I could install a DNS service on my Area51 rig to somehow do the dirty work? 

It's not that I'm trying to avoid /etc/hosts, because that's a real easy bam-done thing to do. But I'm trying to play around with other options here so I'm more aware of what I can do to get the job done.

---

### Post by lykwydchykyn on 2009-11-04
> **Roasted said:**
> Yeah, it makes sense. I wasn't completely thinking thoroughly with this, but it's true. We rely on our DNS server at work in our Windows network, so it makes sense that the same would be needed with a comparably sized Ubuntu network.

Is it possible I could install a DNS service on my Area51 rig to somehow do the dirty work? 


Bind, dnsmasq, and several other DNS servers are available from the repositories.  dnsmasq has the simplest config file, but webmin offers a decent Bind module if you prefer a more graphical approach.

---

### Post by Roasted on 2009-11-04
> **lykwydchykyn said:**
> Bind, dnsmasq, and several other DNS servers are available from the repositories.  dnsmasq has the simplest config file, but webmin offers a decent Bind module if you prefer a more graphical approach.

Awesome. Good deal. I'll check that out.

In terms of my LAN at home, which is all XP boxes with my 2 Ubuntu boxes, what would resolve names at that point? Would my Ubuntu machine take priority, with the router being a secondary? 

I'm just curious because if I'm in Ubuntu with DNS installed if my machine would be the one handling that traffic. BUT - I dual boot. So if I'm in Vista I assume it would fall back to the router or WINS or whatever takes priority then for the XP boxes - ehh?

---

### Post by lykwydchykyn on 2009-11-04
> **Roasted said:**
> Awesome. Good deal. I'll check that out.

In terms of my LAN at home, which is all XP boxes with my 2 Ubuntu boxes, what would resolve names at that point? Would my Ubuntu machine take priority, with the router being a secondary? 

I'm just curious because if I'm in Ubuntu with DNS installed if my machine would be the one handling that traffic. BUT - I dual boot. So if I'm in Vista I assume it would fall back to the router or WINS or whatever takes priority then for the XP boxes - ehh?

Any machine, whether it's Ubuntu, Windows, or anything else, is going to use whatever DNS server it's set to use.  If your machines have static IP's, this is one of the settings you typically configure.  If they are on DHCP, this is one of the settings you have to configure on the router/DHCP server to send to the clients.

WINS is not a replacement of DNS.  WINS is simply name resolution for smb/cifs (aka windows file sharing).  Windows sometimes uses this name resolution for other things, but for general internet services (web, ssh, etc) it's going to use DNS.

---

### Post by Roasted on 2009-11-04
So does your average home router often take care of this?

---

### Post by Iowan on 2009-11-04
[One]("http://ubuntuforums.org/showpost.php?p=8237832&postcount=3") of them uses **dnsmasq**...

---

### Post by lykwydchykyn on 2009-11-04
> **Roasted said:**
> So does your average home router often take care of this?

I don't know; mine does not, but I've had it for about 4 years now.  Maybe some do, I'm no expert on home routers.

I would guess most home routers are limited to passing DNS requests up to the ISP's DNS, which of course isn't going to store hostnames of anything on your network.  

My router does allow me to assign IP's to specific MAC addresses (the MAC address is a unique identifier built into every network card) so that I can use DHCP but still effectively have "static" addresses.  This allows me to put names in my DNS server without having to have the DHCP server update it every time.

---

### Post by Roasted on 2009-11-04
On my XP virtual machine, if I ping another XP computer on the network by name, it works.

What's resolving its name?

---

### Post by lykwydchykyn on 2009-11-05
> **Roasted said:**
> On my XP virtual machine, if I ping another XP computer on the network by name, it works.

What's resolving its name?

No idea.  Type "nslookup computername" and see what it tells you.  nslookup strictly looks up DNS records.  It'd tell you what DNS server it's getting the info from as well.

For all I know microsoft's ping implementation uses netbios resolution.

---

### Post by Iowan on 2009-11-05
Could be it's using WINS... or not.

---

