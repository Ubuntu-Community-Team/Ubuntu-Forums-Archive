---
title: "Networking Signal Strength Issue"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by MisterEx on 2009-09-16
Hey,  

I have quite a large problem with my wireless signal strength from Ubuntu 9.04. In the same room and 15 feet away, I am lucky if I break 70%, and I do not get connectivity at all if I am upstairs. I also have the network cut out on me on several occasions, as well as experience behaviour where I am unable to resolve any web pages, though Ubuntu still reports connectivity to the network. 

I am positive it is neither a hardware issue, nor an access point one. I am running Ubuntu using Wubi, my other OS being Windows 7 Rc1, which NEVER cuts out, reports full signal strength from this exact location, and gets a decent, even good connection upstairs, down the hall, and into my room, even with the door closed. There is a SIGNIFIGANT difference between my Win7 performance vs my Ubuntu one. 

This leads me to believe it is a driver problem.  

I have an Acer Aspire 6530 laptop, the AMD Athalon 64X 1.9GHz model (I am under the impression there are three different models of this laptop, with different levels of hardware quality and price), which includes an **Atheros AR5B91 b/g/Draft-N** NIC.   

Do I have alternative solutions for drivers? Is there a third-party driver for my card? Where would I find it, how would I install it? Am I wrong in assuming it is a driver problem? 

Thank you for your assistance.

*Edited: NoScript destroyed my paragraphs. Oops =D*

---

### Post by MisterEx on 2009-09-17
I hope this isn`t against the forum regulations...

Still don`t have a solution and it would be nice to get some feedback before I go to school in the morning - bump.

---

### Post by skatinjj on 2009-09-17
You can always try ndiswrapper which will attempt to let you use your windows driver for the wireless card.

reply if you need further assistance with ndiswrapper.

This is the FAQ I used.[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by MisterEx on 2009-09-17
This all seems way over my head, but I seemed to find that my card was listed: 

08:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

Yet, this is not on the [ndiswrapper supported card list](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:Company). How/can I proceed?

---

### Post by MisterEx on 2009-09-18
Anyone have any idea?

---

### Post by skatinjj on 2009-09-18
> **MisterEx said:**
> This all seems way over my head, but I seemed to find that my card was listed: 

08:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

Yet, this is not on the [ndiswrapper supported card list](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:Company). How/can I proceed?

If you have not already, go ahead and try ndiswrapper anyway using the FAQ I posted above.

It won't hurt the system if it does not work and you can uninstall it if it doesn't.

---

### Post by MisterEx on 2009-09-19
> **skatinjj said:**
> If you have not already, go ahead and try ndiswrapper anyway using the FAQ I posted above.

It won't hurt the system if it does not work and you can uninstall it if it doesn't.

There is no Windows driver for my cards ID [168c:002a]. Should I use the driver for [168c:001a]?

---

### Post by lawhorne on 2009-10-31
I am having the same problem with the same card.  did you have any luck?

---

