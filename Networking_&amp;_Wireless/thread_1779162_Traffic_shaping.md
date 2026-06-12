---
title: "Traffic shaping"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by btse on 2011-06-10
Behind an Ubuntu firewall sits a number of machines, among them a sip-telephone. I'd like some sort of traffic shaping so that a download of the lastest Ubuntu iso does not interfere with the sip traffic. Also ssh traffic should be somewhere in between. Basically three levels of priority.

How do I best go about such a venture? Setup is Ubuntu 11.04 64-bit.

---

### Post by btse on 2011-06-15
Does nobody know how to do traffic control on Ubuntu? It is possible with qdisc and tc but maybe not on Ubuntu? Shame...

---

### Post by jtholb on 2011-06-15
I think what you're looking for is QoS (you should probably start with a search for that). 

Although I've never set up QoS on an Ubuntu router it looks to be a little more complex than what I would guess you're looking for--have a look at

[http://ubuntuforums.org/showthread.php?t=7990](http://ubuntuforums.org/showthread.php?t=7990)

and

[http://ubuntuforums.org/showthread.php?t=927705](http://ubuntuforums.org/showthread.php?t=927705)

I hope that helps to get you started

---

### Post by btse on 2011-06-16
Wow, thanks alot! That was really good!

---

