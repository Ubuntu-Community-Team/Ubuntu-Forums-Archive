---
title: "Help with two network interfaces"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by reyals140 on 2010-03-14
I'm having trouble configuring two network cards.
I've tried googleing but everything I find is way too complex for what I need.
The computer has a wireless and wired connection both are connected to the internet on diffrent networks but I want to use the wireless as 'primary' and the wired connection as just a way to ssh into it to it for control.  But every time I try to connect both it likes to 'default' over to the wired connection.....
Thoughts?

---

### Post by Iowan on 2010-03-14
I presume you're using Network Manager... Traditionally, (at least in previous versions) Network Manager only "manages" one interface at a time (though my Jaunty laptop sometimes connects to wired/wireless concurrently) - and it "prefers" the faster wired connection.
Previously, you could let NM control one interface, and configure another via */etc/network/interfaces* - and both would work. There's some debate as to whether this is still possible - you're welcome to "assist" with the research...
IF you configure the wired connection via */etc/network/interfaces*, it should be in a different subnet than the wireless connection.

---

