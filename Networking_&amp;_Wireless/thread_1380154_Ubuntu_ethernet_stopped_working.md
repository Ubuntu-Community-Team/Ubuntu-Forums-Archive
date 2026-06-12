---
title: "Ubuntu ethernet stopped working"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by sheldler on 2010-01-13
Hi,

I recently installed a Asus M3N78-EM with ubuntu 9.10.  Everything worked fine out of the box, except for sound and ethernet.

Sound I fixed after fiddling a bit with settings and now is great.

Ethernet I fixed by disabling the onboard LAN and buying a standard NIC. 

However, the problem is that to my surprise, after a reboot the NIC stopped working.  I thought it was the card, so I bought a new one, and same situation happened.  It worked fine for a couple of days, but then it suddenly stopped working.

I have searched all over the net and haven't found a solution.

Has anyone encountered a similar situation?

Thanks

---

### Post by Iowan on 2010-01-13
I'm kinda curious what the NIC's are (brand/chipset).
What are results of **lshw -C network**? 
Just in case... what are results of **ifconfig -a**?

---

### Post by sheldler on 2010-01-13
*- I'm kinda curious what the NIC's are (brand/chipset).*
Onboard: Asus M3N78-EM motherboard
NIC: Advantek ALN-318C 


* - What are results of **lshw -C network**? *
Shows some scan activity and after a few seconds displays nothing but another prompt

*Just in case... what are results of *[B]*ifconfig -a*
[/B]Only shows loopback interface (no eth0 although it used to be there a couple of days ago)
In addition: lspci and dmesg don't show any evidence of eth0 around, but the card is correctly plugged in, network cable connected and a network light flashes in the backThanks for any help you may give me! I'm desperate

---

### Post by Iowan on 2010-01-13
I keep forgetting to add "sudo", but I suspect **sudo lshw -C network** won't show devices, either.

---

### Post by sheldler on 2010-01-13
I ran all the commands as root... thanks :)

---

