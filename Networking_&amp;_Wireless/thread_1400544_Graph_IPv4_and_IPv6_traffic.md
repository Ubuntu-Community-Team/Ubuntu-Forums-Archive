---
title: "Graph IPv4 and IPv6 traffic"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by chielchiel on 2010-02-07
Hi all,

Is there a tool that can both graph my IPv4 and IPv6 traffic? I'm running a dualstack (IPv4 and IPv6) network and I would like something like "System Monitor" that gives two graphs for both IPv4 and IPv6.
The reason I want this is to easily visualize what type of traffic is coming in/out without the need of starting wireshark or something.
I know this is also possible with MRTG of Cacti or something (and already doing this) but I just need a quick and real-time solution (like the network graph in "System Monitor").

Thank you

---

### Post by sanderj on 2010-02-07
I tried iftop and vnstat, but no (separate) IPv6 traffic.

Not an answer to your question: The IPv6 traffic can ben seen via the CLI:
```

sander@quirinius:~$ netstat -s -6 | grep -i octets
    Ip6InOctets: 751060530
    Ip6OutOctets: 24726411
    Ip6InMcastOctets: 9840
    Ip6OutMcastOctets: 88968
sander@quirinius:~$ 
sander@quirinius:~$ netstat -s -6 | grep -i octets
    Ip6InOctets: 761048514
    Ip6OutOctets: 24974767
    Ip6InMcastOctets: 9840
    Ip6OutMcastOctets: 88968
sander@quirinius:~$ netstat -s -6 | grep -i octets
    Ip6InOctets: 914510167
    Ip6OutOctets: 28855368
    Ip6InMcastOctets: 10104
    Ip6OutMcastOctets: 88968
sander@quirinius:~$ 

```

---

### Post by sanderj on 2010-02-07
Combine netstat -s -6 with conky and ${execi time /location/to/script/score_script.sh} , and should be able to see your IPv6 traffic in a GUI.

---

