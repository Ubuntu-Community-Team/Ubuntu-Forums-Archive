---
title: "wireless not working"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by kilgore9 on 2009-02-25
Hello!  I'm using the ACer Extensa 5630Z. 
Wireless card: Acer Nplify 802.11b/g/Draft-N WLAN

I don't know how to set it up.  I don't think Ubuntu recognizes the card.  How do I do this?  Thanks!

---

### Post by moonport on 2009-02-25
Hi, Kilgore:
            I had the same problem with my Compaq.
The main cause is that the wireless driver is not compatible with the last versions of the Ubuntu's Kernel.
Here is the link where I founded a new driver: [http://www.madwifi.org/](http://www.madwifi.org/)

Previously, you can check your current wi-fi card with this command (console): lspci | grep Wireless

Based on that result, may be, you can find your driver too.

I hope that helps.
best
moonport

---

### Post by kilgore9 on 2009-02-26
Thanks moonport, though the problem is not yet solved.  The madwifi.org hasn't been updated for four years and most of the links are dead.  That command you suggested doesn't bring up any info in the terminal either... I know which Wifi-card I have, just not sure how to proceed from here....

---

### Post by kilgore9 on 2009-02-26
well with lots of searching through the forums I was able to find a link for the driver that I need.  Now I can see my WLAN!!  But I still can't connect... I know that I need to put in my username and password from my ISP somewhere... the same one I use for the DSL connection.  The network manager even tells me that the WLAN requires another password, but doesn't give me any place to put it in.  (I'm not talking about the WEP, but a normal username and PW.)   Any ideas?

---

### Post by rakmoh on 2009-03-16
I have the same laptop and having the same problem. Can you please tell me instructions and driver(s) you installed to solve this issue.

Thanks,
-Rakesh

---

