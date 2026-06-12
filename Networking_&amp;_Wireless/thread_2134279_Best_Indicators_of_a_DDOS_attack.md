---
title: "Best Indicators of a DDOS attack"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by psyllex on 2013-04-10
Hello people.  I'm thinking about setting up some sensors to run some pretend DDOS attacks on like UDP, Flood, Hulk etc.  I'm wondering what tools, scripts etc might be useful to measure metrics (which I'm not sure) during an attack.  Bandwidth doesn't truly show everything so I would probably want network i/o, cpu load, I don't know whatever else I you could think of.  I'm just trying to get some ideas of what tools to use (command line) and then I can modify them to pipe the results to a .cvs file which I can then grab with envision.js and chart it out.  

I know that's kinda broad but I'm open to anything so please throw me any ideas pertaining to this.  Thanks a lot people.

---

### Post by somethingcatchy on 2013-04-10
I'm no guru. And I can tell by the question you've asked that you actually know more about this stuff than I do. However, I am in the process of setting up a learning platform for myself. This is a list of the tools that I have found in the repos that *may* be able to give you the information you're looking for. You might want to check them out:

Ether Ape
ettercap
Nmap
Umit Network Scanner
Wireshark
Zenmap

---

### Post by psyllex on 2013-04-10
> **somethingcatchy said:**
> I'm no guru. And I can tell by the question you've asked that you actually know more about this stuff than I do. However, I am in the process of setting up a learning platform for myself. This is a list of the tools that I have found in the repos that *may* be able to give you the information you're looking for. You might want to check them out:

Ether Ape
ettercap
Nmap
Umit Network Scanner
Wireshark
Zenmap

Yeah I have most of those...I forgot about nmap tho'.  I'm trying to find some tools that I can pipe to a txt or cvs file so I can use the data.  Basically I'm attempted to dodge learning snmp!  lol.

---

### Post by somethingcatchy on 2013-04-10
Well I'm still taking baby steps on scripting, but isn't it possible to pipe an output just about anyhwhere with the right syntax in a shell script?

---

### Post by psyllex on 2013-04-10
pretty much

---

### Post by lvlint67 on 2013-04-11
There are some iptables statements we use to log and block brute force attempts...

active ddos:
tcpdump
free
netstat
uptime (for load averages)

---

