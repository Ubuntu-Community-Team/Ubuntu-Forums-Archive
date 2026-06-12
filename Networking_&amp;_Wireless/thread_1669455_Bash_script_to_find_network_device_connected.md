---
title: "Bash script to find network device connected?"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by telmo on 2011-01-17
Hello everyone!

I need a bash script to run ARPON for the connected network device, eth1 or eth2. (ethernet or wireless)

Arpon has an option (-o) to select the network automatically, but it only works for ethernet, hence i need this script. I've also tried running arpon for ethernet and wireless at the same time, but the arpon process running the inactive device will consume all of my CPU.

So, basically i need a script to find which device is connected, eth1 or eth2 and then to run arpon -d -i <device connected> (or something like that). 

Is there an easy way to do this?

Something like this in Bash:

```
IF eth1=connected
   THEN arpon -d -i eth1
ELSE
   quit
ENDIF

IF eth2=connected
   THEN arpon -d -i eth2
ELSE
   quit
ENDIF
```(please don't make fun of this...) :D

I've searched everywhere how to find the connected device via bash, but i couldn't find anyhting...

Help please!? I need to protect my arp cache.

---

### Post by telmo on 2011-01-17
Found the solution [**HERE**]("http://forums.debian.net/viewtopic.php?f=5&t=59312&p=344193#p344193")

---

