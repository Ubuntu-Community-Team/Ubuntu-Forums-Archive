---
title: "My wifi blocks my mobile broadband"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by brucekev on 2010-01-08
Hi, I have Ubuntu 9.10 installed as a dual boot on my Acer 5810T notebook. My problem is this, when I am connected to my home wifi connection (no internet, just used for printing) and to my mobile broadband (at&t tethered) neither chrome or firefox will download a web page. As soon as I disconnect from my wifi network, I can browse the internet fine. If I re-connect to my wifi network again the next time I click on a link nothing happens. Any help for this? Can I prioritize the connections so that the browsers look at the mobile broadband connection first? 
Thanks

---

### Post by changingstate on 2010-01-08
This is possible. What I'm interpreting the situation here to be is that ubuntu is changing the default route to pass through your wifi device rather than your mobile broadband adapter when the wifi is connected. You can change this and observe the routing table using the route command. 

There's some great advice in this thread on the subject that should prove helpful : [http://ubuntuforums.org/showthread.php?t=1373049](http://ubuntuforums.org/showthread.php?t=1373049)

---

