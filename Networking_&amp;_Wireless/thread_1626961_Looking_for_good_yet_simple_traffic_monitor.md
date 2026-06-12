---
title: "Looking for good yet simple traffic monitor"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by terminator14 on 2010-11-20
I'm looking for a powerful network traffic monitor that can do all of the following (or at least a combination of tools that can do the following):

[LIST]
[*]tell me how much data was downloaded/uploaded on an interface this month and the previous month
[*]tell me how the traffic was used throughout the month
[LIST=1]
[*]show which internal IPs (IPs in the 192.168.1.0/24 network) used how much traffic
[*]show which ports/protocols on those IPs used all that traffic
[/LIST]
[/LIST]
[LIST]
[*]show LIVE traffic flow statistics that can tell me total speed of traffic going through an interface as well as
[LIST=1]
[*]show which internal IPs (IPs in the 192.168.1.0/24 network) are using how much of the traffic
[*]show which ports/protocols on those IPs are using that traffic
[/LIST]
[/LIST]

This tool will run on a linux router through which all my internal PCs are connected to the Internet. This means the tool(s) need to work with NAT (traffic being forwarded and not necessarily destined for the interfaced being monitored). 

The distribution being run doesn't have a package manager so any packages or dependencies have to be manually compiled and SCPed over file by file. For this reason, the tool/tools need to be simple (things like vnstat, not things like ntop that have their own web interface).

I know that vnstat can tell me the first bullet point so it's only there incase there's a tool out there that can do everything. If there's a tool that can only do the second or third bullet point, that's great too - I'll just keep using vnstat and look for something else to do the other task.

---

### Post by terminator14 on 2010-11-22
After searching for a while, I can't seem to find the tool(s) I'm looking for so I'm seeing if I can build it instead. I have a bit of skill in C# programming so that's what I'm using. Anyone know of any libraries I can use to tell me what packets are going by on an interface so I can see their source/destinations and collect some statistics on them? For now, I'm using libpcap (through sharppcap). Are there better/easier libraries I can use?

---

### Post by t4thfavor on 2010-11-22
What type of router, how much hardware power? can you build software on it, and can it run php/perl?


I know of:

webalyzer
[http://www.webalizer.org/](http://www.webalizer.org/)

RRDTool:
google it: [http://martybugs.net/linux/rrdtool/traffic.cgi](http://martybugs.net/linux/rrdtool/traffic.cgi)

Or try:
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

I'm sure there are more out there if you know what your looking for.

Also be aware that C# only runs on top of Mono on linux, and you could probably get what you need by running a simple php or shell script with a cron job.

Much easierto let others do the coding, and just use the software.

---

### Post by SeijiSensei on 2010-11-23
How about [ntop]("http://www.ntop.org/overview.html")?  Or the crusty [MRTG]("http://oss.oetiker.ch/mrtg/")?  You can customize the hell out of that.

Whoops, not ntop, I guess.  You can't just build it under /usr/local, tar up the resulting image, and distribute that?  I've only installed ntop from rpm's or deb's.

MRTG is written in perl.  I don't know about things like port monitoring, though; I haven't used it in quite some time.  It certainly plots anything that can be monitored via SNMP and lots of other things as well.

---

### Post by terminator14 on 2010-11-23
> **t4thfavor said:**
> What type of router, how much hardware power? can you build software on it, and can it run php/perl?


I know of:

webalyzer
[http://www.webalizer.org/](http://www.webalizer.org/)

RRDTool:
google it: [http://martybugs.net/linux/rrdtool/traffic.cgi](http://martybugs.net/linux/rrdtool/traffic.cgi)

Or try:
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

I'm sure there are more out there if you know what your looking for.

Also be aware that C# only runs on top of Mono on linux, and you could probably get what you need by running a simple php or shell script with a cron job.

Much easierto let others do the coding, and just use the software.

The router is a 3.0GHz HT (so single core) machine that is running Astaro firewall/router. I'm pretty sure it has php and perl but I'd rather not use tools with a web interface since it's bad enough that I'm messing with the router's insides by adding software it was never meant to run - messing with web server options to make its web interface run in parallel with another tool's web interface is not something I want to do. It doesn't have gcc so I can't build software on it but I can build software for it and SCP it over to it (which I've done with one or two tools already). The architecture is simply x86 so it's simple enough to build software for it - as long as I make sure to copy any libraries the software needs as well.

Webalizer seems to be a log analyzer that is mainly used to analyze web server traffic. I'm not running a web server (well the router is but that's not the traffic I'm trying to analyze). It sounds like webalizer can't show me what I'm looking for because logs can't tell you the speed of live traffic (AFAIK), and I don't know of any logs that keep track of the type of traffic being forwarded from one interface to the next. 

RRDTool, from what I've read, is something that creates graphs from data you give it - it does not generate its own data which is what I need. And even if I'm wrong and it does generate data, looking at the screenshots of the link you gave, it looks like the best RDDTool can do is tell me what the total current speed is of traffic going through an interface - it says nothing about what's using all that bandwidth (which IPs or ports or anything). Am I wrong about this?

As for [http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html), I've looked at it, and several other lists. The problem is that I can't possibly test every single tool out there. I have tried tools that sounded promising though (like pktstat and others), but so far haven't found what I was looking for.

Despite having started on the C# project, the one thing I hadn't tested is to see if it would work on the router. Now that you mentioned that C# needs mono, I remembered hearing that somewhere else too so I tried to run a C# hello world on the router. It failed. I guess I can't use C# after all. Bummer.

> **SeijiSensei said:**
> How about [ntop]("http://www.ntop.org/overview.html")?  Or the crusty [MRTG]("http://oss.oetiker.ch/mrtg/")?  You can customize the hell out of that.

Whoops, not ntop, I guess.  You can't just build it under /usr/local, tar up the resulting image, and distribute that?  I've only installed ntop from rpm's or deb's.

MRTG is written in perl.  I don't know about things like port monitoring, though; I haven't used it in quite some time.  It certainly plots anything that can be monitored via SNMP and lots of other things as well.

ntop has a web interface which I'm trying to avoid. MRTG seems to display some simple statistics about speed but doesn't break it down into IPs or ports (and is also web-based). I can get the total speed of an interface with pktstat (which already works on the router). What I really needs is the breakdown of what's using that speed.

My latest attempt is to get tshark to display some statistics about the ports/protocols and IPs of an interface that I can sum up with bash.

---

### Post by terminator14 on 2010-11-30
An almost idea solution that I found was to use iptables (since it's already built into the linux based Astaro router) in the following way:

```
sudo iptables -N my_house
sudo iptables -A FORWARD -d 192.168.1.0/24 -j my_house
sudo iptables -A FORWARD -s 192.168.1.0/24 -j my_house

sudo iptables -N Me
sudo iptables -A my_house -d 192.168.1.100 -j Me
sudo iptables -A my_house -s 192.168.1.100 -j Me

sudo iptables -A Me -p tcp -s 192.168.1.100 --dport $Port
sudo iptables -A Me -p tcp -d 192.168.1.100 --sport $Port
sudo iptables -A Me -p udp -s 192.168.1.100 --dport $Port
sudo iptables -A Me -p udp -d 192.168.1.100 --sport $Port

sudo iptables -N Someone_Else
sudo iptables -A my_house -d 192.168.1.101 -j Someone_Else
sudo iptables -A my_house -s 192.168.1.101 -j Someone_Else

sudo iptables -A Someone_Else -p tcp -s 192.168.1.101 --dport $Port
sudo iptables -A Someone_Else -p tcp -d 192.168.1.101 --sport $Port
sudo iptables -A Someone_Else -p udp -s 192.168.1.101 --dport $Port
sudo iptables -A Someone_Else -p udp -d 192.168.1.101 --sport $Port
```

After which point, I can run:

```
sudo iptables -vnL Me
```

to see statistics about how much I downloaded/uploaded over a period of time on each port. The problem with that is - each port needs 4 rules (as seen above). That means in order to monitor every single port I would need (65535 x 4 = ) 262,140 rules (per IP I want to monitor).

Since I created a short script to read the output of 

```
sudo iptables -vnL Me
```

and summarize it (it ignores any ports that had no data on it), it wouldn't be much of a problem if it weren't for the speed. Not only will it take a script that autocreates all 262,140 rules (in a loop) hours to finish, but it also makes my script (the one that summarizes the data) take forever to get through each line of output to determine if it should be displayed or not.

Is there any other way to get iptables to output statistics for EVERY port, not just the ones you made a rule for? Or perhaps there's a way to make one (or a few) rules that can accomplish what I need?

PS. I know there's a way to do multiport rules - this isn't what I'm looking for since that would only give me a summary of how much that particular IP was downloading and would defeat the purpose of breaking it down into different ports.

---

### Post by terminator14 on 2010-12-01
After a little more searching, it looks like I found what I was looking for.

I came across this article:

[http://www.anchor.com.au/hosting/tools/IPTrafficAccounting]("http://www.anchor.com.au/hosting/tools/IPTrafficAccounting")

Which basically calls the iptables way of doing traffic accounting (the way I was trying to do it for the last couple of days) an ancient practice (because of the limitations I wrote about earlier) and offers a better way - pmacct.

Looking into pmacct, it appears it does exactly what I need. The only problem is - it seems to be a bit more complex than what I was hoping. Time to do some reading...

---

