---
title: "How to test a route through a machine"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2010-11-19
I have a 10.04 install with 2 network cards. wlan0, and eth0.

wlan0 is the internet connection. eth0 is the local network. I want to be able to have internet connection sharing between eth0 and wlan0. I have set everything up, using firestarter.

is there a way of testing the eth0->wlan0 routing from the machine itself? The routing table looks sound, but I would like a quick way of confirming it. Is there a tool, like PING or TRACEROUTE which will let me say "ping [www.google.com](www.google.com) going through eth0" ?

---

### Post by SeijiSensei on 2010-11-19
Use the -I switch to select a source interface like this: "ping -I eth0 some.destination.host".

For future reference, you should consider reading the "man" pages for commands like ping.  They'll specify all the options you have available to you.  See "man ping" for instance.  Using the "--help" switch will often also display an abbreviated set of options at the command prompt, e.g., "ping --help".

---

### Post by Jethro_uk on 2010-11-19
> **SeijiSensei said:**
> Use the -I switch to select a source interface like this: "ping -I eth0 some.destination.host".

For future reference, you should consider reading the "man" pages for commands like ping.  They'll specify all the options you have available to you.  See "man ping" for instance.  Using the "--help" switch will often also display an abbreviated set of options at the command prompt, e.g., "ping --help".

I just tried that. It's not what I wanted, it appears to be trying to route OUT of eth0. I wanted to try and simulate a packet coming IN though eth0, so I could test the routing in the machine.

Not to worry, I have reconfigured a PC to connect to the Ubuntu machine via eth0, and tested it that way. Of course that was what I was trying to avoid.

---

