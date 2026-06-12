---
title: "firewalls, ports, and netstat -s, oh my!"
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by mushr00m on 2006-06-21
Well, I've had to put my home server work on the back burner mostly because the local thrift store's $1 Network Everywhere router is having a meltdown....  it came without ac adapter so I had to fudge one I had around with the same voltage but half the amperage.  I keep losing traffic due to "brownout"; I guess that without enough power the poor little box is just not up for routing the external network traffic along with my internal stuff.

With my gaze back on my computer I caught something in my firewall logs:
Time: Jun 21 11:05:50 Source: 192.168.1.101 Destination: xx.xxx.xx.xx In IF:  Out IF: eth0 Port: 6969 Length: 44 ToS: 0x00 Protocol: TCP Service: Gatecrasher (Gatecrasher is a root-kit btw)

Of course my first thought was, WTF!?, then I settled down and thought about it a bit... I'm behind a firewalled router and both this computer and my server use Firestarter and manual IP rules to control internal/external traffic, I can't believe this is a rootkit.

What I know:
- whatever this is happens most often around 5 past and 5 to the hour.
- "sudo netstat -vepac -tu" doesn't show me any listening ports I don't know about.
- rkhunter doesn't find anything

How can I tell for sure?

](*,) ,
mushr00m

**edit** - Problem solved! I used:
```
sudo netstat -vepac -tu |grep "6969"
```
and the output eventually gave me my answer; it was the scrape to a torrent tracker with an odd port that was giving me grief.

So my new question is how would I describe the above command in whole english or in *unix-ese?

*...so I grep'd my sudo'ed netstat's continuous standard output for port 6969 and that eventually returned what I was looking for.*

does that work? :),
mushr00m

---

