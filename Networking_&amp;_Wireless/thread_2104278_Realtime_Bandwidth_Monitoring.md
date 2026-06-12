---
title: "Realtime Bandwidth Monitoring"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by psyllex on 2013-01-12
Hello all!  I'm trying to find a solution that offers real time 'graphical' bandwidth monitoring.  I've looked at Naigos, Icinga, PNP, Check_MD.  None are what I'm looking for precisely.  The SYSTEM MONITOR that comes with Ubuntu is actually perfect if you take away the CPU History and Memory graphs.  But I would like something I could perhaps have 4-5 graphs that represent routers,switches or servers all on one page or app. I've found bmon and ifsat but both aren't as 'graphical' as I would like.  I've looked ntop but haven't gotten very far with it.  Does anyone have any suggestions?

---

### Post by psyllex on 2013-01-12
83 views and no replies?  LOL.  I found darkstat which works pretty well.  It only allows me to view on node at a time, but it's pretty good.  I need to find a way to include the refresh rate....right now it's every 5 seconds but I'd like to get it to 1/sec.
[IMG]http://johnverber.com/screenshot.png[/IMG]

---

### Post by psyllex on 2013-01-20
118 views and still no responses...I'm getting concerned here!

---

### Post by tgalati4 on 2013-01-21
```
apt-cache search network monitor
```

Start installing some of these older monitor tools and find one that you like.

---

### Post by psyllex on 2013-01-21
> **tgalati4 said:**
> ```
apt-cache search network monitor
```

Start installing some of these older monitor tools and find one that you like.

I've done quite a bit.  Ifstat Ipstat bmon prtg mrtg cacti nagios icinga ntop etherape etc.  None run truly in real time.  So my search continues.  I'm thinking about just modifying the source of darkstat to work the way I want.

---

### Post by tgalati4 on 2013-01-21
What is considered realtime to you?  Monitoring is a tradeoff between the timeslice and interference with network throughput.  You might have to go with a real-time kernel or at least one with smaller timeslices, or an instrumented/profiled kernel to get the data that you are looking for.  For that, there are other tools like dtrace that can give you very fine granularity.

What is the purpose of the monitoring?  QoS tweaks, DoS analysis, Web server performance?

---

### Post by psyllex on 2013-01-21
> **tgalati4 said:**
> What is considered realtime to you?  Monitoring is a tradeoff between the timeslice and interference with network throughput.  You might have to go with a real-time kernel or at least one with smaller timeslices, or an instrumented/profiled kernel to get the data that you are looking for.  For that, there are other tools like dtrace that can give you very fine granularity.

What is the purpose of the monitoring?  QoS tweaks, DoS analysis, Web server performance?

We're monitoring bandwidth performance specifically.  And mostly we can get fine stats from programs like ifstat, but I need it graphically displayed.   The closest thing is darkstat.  

let me ask a question.  If I'm monitoring a router from darkstat binding it to the subnet/mask i.e.: 192.168.1.1.0/255.255.255.0 is it a solid representation of the traffic if I'm not seeing any in traffic and only out traffic?  Being that I'm trying to monitor the whole network through a router which is simply forwarding the packets along?  In fact isn't it kind of fool hardy to try and monitor a network through a router as it's sole purpose is to forward packets.  The only way we would see in traffic is if packets were addressed specifically to the router...am I correct?  I appreciate the help.

---

### Post by tgalati4 on 2013-01-21
There are hardware/software solutions that are designed to do just that.  

[http://www.ixiacom.com/](http://www.ixiacom.com/)

Trying to turn a generalized desktop/server operating system into a router performance monitor might be a stretch without recompiling the kernel and the TCP/IP stack and using instrumentation to pull out the data that you are trying to measure.

iperf, ifstat, and other userspace tools will give you some insight into performance, but dedicated measurement solutions are designed to get the data with little interference from the instrument itself.

Perhaps there is a linux kernel and a set of tools bundled into a "network performance measurement distro"?  I don't know of one, but perhaps some searching will find one.

I'm familiar with the industry tools, but not with recreating them in software alone in linux.

---

### Post by psyllex on 2013-01-21
Yes we're kicking around the idea of diving into the kernel and pulling things out.  Unfortunately I'm partner with a network guy who thinks he's Wozniak.  I know how long and difficult that will prove, but he either: doesn't have a clue, or is lying to everyone to try and make himself look good. LOL...gotta love those types.  Ambition is one thing but diving into the kernel and creating a program that pulls bandwidth data and sends it via some form to a web browser for a graphical interface that works in realtime....is not a week long process.  I am interested in doing this in the long term as I could see it being a decent tool to have around.  I cracked my linux kernel programming guide up.  I have seen a few tools that can do it like Netflow Analyzer or NST but they're integrated into a big page.  We night something light that can be embedded in a separate page. So it's kinda of specialized.  If we do build it I will post it up in GitHub for all to share.  Cheers.

---

### Post by tgalati4 on 2013-01-21
That's encouraging.  I'm surprised that their isn't a distro that is specialized for network performance measurement.  I haven't looked, but I did work next door to iXia and took a factory tour, so I've seen what real network monitoring looks like.  If you can get similar functionality with a few network cards, a PC and an instrumented kernel, then that would be helpful to the community.  It's not a trivial problem when you start getting into the details.  

What specifically are you trying to measure?  What is the network topology?  LAN performance, WAN performance?  Website service requests?

---

### Post by psyllex on 2013-01-22
> **tgalati4 said:**
> That's encouraging.  I'm surprised that their isn't a distro that is specialized for network performance measurement.  I haven't looked, but I did work next door to iXia and took a factory tour, so I've seen what real network monitoring looks like.  If you can get similar functionality with a few network cards, a PC and an instrumented kernel, then that would be helpful to the community.  It's not a trivial problem when you start getting into the details.  

What specifically are you trying to measure?  What is the network topology?  LAN performance, WAN performance?  Website service requests?

Yeah I'm surprised as well....although to be honest I haven't really looked for a specific network performance monitoring distro.  Specifically we are monitoring bandwidth...precisely bandwidth drop off when certain events happen...could be anything downloading a movie from netflix or what have you.  The network is simple...14 dual core 64 bit 4 GB Ram machines (cache..I'm not sure).  It's set up with 2 of the physical machines set up as servers, one as a monitor, 4 as firewalls, and 7 as bot/multiple purpose machines.  We have Vlans set up between the vm routers and the firewalls with their own subnets and I believe about 8 vm routers...not sure on that.  It's just a typical little lan set up.  As for performance...I'm not sure yet...we're still setting everything up and I've only been monitoring my (monitoring) machine and a few vm remote hosts on my desktop.  I believe we have 100Gbs switches but don't quote me on that...I'm the software guy....I"m still learning about this network stuff.  But yeah it'll be a long term project for sure..  I have 3 servers here, plan on buying a couple more powerful ones to through VM's on.  Then i'll setup with your typical server, vm routers and vlans type of topology (basically what I can find off Google search and actually do myself without screwing it up).  Then I can dive into the kernel and see what I can find.  I know a lot of the programs like ifstat get their data straight off the kernel (like..not specifically ifstat) so I plan on downloading their source code and then using that as a starting point.  I'm sure 2-3 books will be read in there as well as many questions on forums.  I think it's a worth-while cause though....real time bandwidth monitoring in graphical form...sounds good to me.

---

### Post by Vishal Agarwal on 2013-01-22
use iftop. It is good, I am using for a long time.

---

### Post by psyllex on 2013-01-22
> **Vishal Agarwal said:**
> use iftop. It is good, I am using for a long time.

I have that installed....no graphical interface with iftop...terminal only.  My requirements need a graphical interface.

---

### Post by psyllex on 2013-01-22
I should say no graphical browser or standalone window display.  Actually bmon has a sick tool...unfortunately it's in ASCII characters.  But it works and its a decent tool.  I aim to emulate something like that but one that does Ajax or some other kind of call from a browser to log files to get the data to a browser where I can make it look all pretty :-)

---

