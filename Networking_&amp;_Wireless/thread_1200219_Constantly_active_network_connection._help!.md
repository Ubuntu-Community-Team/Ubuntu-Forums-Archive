---
title: "Constantly active network connection. help!"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by Pharmacore on 2009-06-29
I recently noticed that my network connection reports constant inbound traffic. Even after a fresh install, system monitor reports that there is a constant stream of inbound traffic (~50kb/s) and an increasing total data transfer (to be expected from this constant download. If the reported values are true, it explains part of the reason why the ITS department has been on my back about excessive bandwidth use since switching to jaunty. My first thought was that I had incorrectly configured some application but this seems unlikely as it still exists with a completely clean install. It even seems to persist without any proxy configuration (required for internet access here at uni), even though no other internet based services work without configuration (which I would expect). It seems to also occur with linuxmint, but as mint is derived from ubuntu, I should expect this.

I am curious as to what this constant downloading may be caused by.

Is this representative of actual data transfer, or just some bug that reports data transfer falsely? 

Is there away around this (if it is infact representative of real  bandwidth use)? 

what diagnostics can i use to try and get mor einformation about the process causing this?

Any insight is welcome

p.s. sorry if this is poorly worded, I have tried to describe it best I can.

---

### Post by dtoronto on 2009-06-29
I would run a wireshark or tshark to a log file to give you an idea of what's going on inside your system.  Do you know what port all the inbound traffic is coming over?  If so you might want to UFW those ports shut.  also you might want to try a nmap on your own interface to find out if you have open inbound ports.  Just a little food for thought.

---

### Post by Pharmacore on 2009-07-01
OK, I'm fairly new to getting things done in Linux. Had a quick look at both wireshark and zenmap which both confused the hell out of me. I will have to sit down when I have some time and nut it out. 

I have noticed the same thing with several live CDs i have tried, both Gentoo (Sabayon) based and several Debian based (Ubuntu & LinuxMint) distros and found that they all have this spontaneous activity, with [according to system monitor] data coming in but not going out. This only occurs when I am at uni where I must connect via poxy. This does not occur when directly connected to the internet. I am starting to think that it may be something to do with the university proxy rather than my computer. I am going to request the bandwidth lods for my connection from ITS to see if it matches the logs I have for total downloaded. This happens even before any proxy details including authentication has been inputted and thus no connection to outside the uni network should be possible [and isnt when any internet based service is tested as expected].

Hopefully this is some sort of artifact and not representative of actual traffic. At least I've learned a lot more about the nuts and bolts and possibly found a convenient scapegoat to get me off a few months of very high bandwidth ;)

---

### Post by superprash2003 on 2009-07-01
firestarter has a really nice app to do this.. also try etherape

---

