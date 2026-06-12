---
title: "Can't use my DHCP connection"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by timtaves on 2010-08-20
Hey there, I had my laptop at work for a few days and when I brought it home I couldn't open up web pages any more. I have a DHCP connection (shaw cable). 
 
When I plug the chord from the modem into my windows machine I can open up web pages. When I plug it into my ubuntu laptop I can't open up web pages. 
 
I have tried unplugging the modem and restaring my computer.
 
I think that there is some sort of connection because when I open up Network tools it shows that I am continually receiving packets. As soon as I unplug the ethernet wire I stop receiving packets. For some reason I just can't open web pages.
 
I also tryed typing 'sudo ifconfig' and 'sudo dhclient' in a terminal. I don't fully understand what this means but I saw it in another forum.
 
Thanks in advance for your help, Tim

---

### Post by pricetech on 2010-08-20
Power Cycle the modem with the laptop turned on and connected.  Cable modems pair themselves to a specific MAC address and while they'll "talk" to another MAC, they won't pass traffic.

If that fixes the problem, and it should, pick yourself up a cheap router to share your connection with.

---

### Post by JBAlaska on 2010-08-20
What do you have setup as a DNS server? try pri-8.8.8.8 sec-8.8.4.4

---

### Post by timtaves on 2010-08-21
Thanks a lot guys, the first comment did the trick so I didn't look into the second one.  I don't know how many times I reset my modem yesterday.  I don't know how I didn't manage to try it with my computer on.  :~
 
Thanks again, Tim

---

### Post by pricetech on 2010-08-23
You're welcome.

---

