---
title: "CDP equivelent?"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by ghstwalker on 2009-10-20
Hey guys, 
     I'm running MINT 7 on my Dell Mini 9, and I've been up and running a few days now. The problem is: At work I gotta lug around this 9lb behemoth to do a simple CDP. I was wondering if there was a CDP client equivelent for linux. All i need to find is the switch IP and port number. I really dont want to do a dual boot into XP cause its a 16gb HDD. I, also, don't want to run a VM cause its only a 1.6Ghz. I searched a few times, but nothing significant came up. Any recommendations? 

Seriously, TIA!

---

### Post by juancarlospaco on 2009-10-20
theres a CDP package on repos :)

---

### Post by ghstwalker on 2009-10-20
Thanks juan! Uhm, like i said, I've only been up and running for a few days. I did a search in the software manager for CDP but returned only with a CDrom application. is there a command I can use to get this, or Is there something I am missing? 

Again, TIA!

---

### Post by wirelessmonkey on 2009-10-20
cdpr  - Cisco Discovery Protocol Reporter

there is also 

lldpd

If you run LLDP on your network.


BOL

---

### Post by ghstwalker on 2009-10-20
Thanks wireless. Sorry for being a new person. 

I downloaded CDPR-2.3 from sourceforge, and it states: "CDPR requires teh pcpap library (libpcap). I downloaded this from sourceforge as well. When i run the ./configure I get the following message: 
"Error: your operating system's lex is insufficient to comple libpcap. flex is a lex replacement that has many advantages, including being able to compile libpcap. for mof info . . . " 

Can someone guide me through this. All I want to do is run a CDP, but this seems to be more trouble than it is worth.

---

### Post by wirelessmonkey on 2009-10-20
Sorry ghstwalker, I didn't pay attention as closely as I should have....

You can install both of those packages with synaptic, apt-get or aptitude.

I'm going to give you the command line way of doing it, because I'm not near an ubuntu machine at the moment.

First open up a terminal/shell

```
 
sudo nano /etc/apt/sources.list

```

Remove the hash (#) from the line following lines, or just paste mine (assuming you're using jaunty)
```

deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

```

Do a "CTRL X", "yes" to save these changes.

Then:
```

sudo apt-get update
sudo apt-get install cdpr 

```


It's not hard, just a matter of getting used to the package system.  You can do much the same with a few mouse clicks using Synaptic


Let me know if I can help any more.

WM

---

### Post by ghstwalker on 2009-10-21
Thanks wireless, I will try when I get home! Much, Much appreciated!

---

