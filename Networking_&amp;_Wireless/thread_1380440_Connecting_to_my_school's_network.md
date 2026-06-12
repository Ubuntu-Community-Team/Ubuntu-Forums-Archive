---
title: "Connecting to my school's network"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by kevindubrow on 2010-01-13
Hey, I am trying to connect to the network at my school. The latest guide they have for connecting with Ubuntu is for 6.10. It involves a lot of terminal work and I'm worried that what I type in isn't compatible with 9.10.

Can someone look through the attached guide and make sure that the terminal code they want me to put in is compatible with Ubuntu 9.10. The guide itself is only the front of two pages. 

Thanks so much in advance if you can look through this for me!

--Edit--
Also, is there no way to just put the information into Network Connections? It would be cool if I didn't have to run a script every time I need to connect to the internet.

---

### Post by changingstate on 2010-01-13
Assuming I've got this correctly if you edit eth0 in the connection manager applet ( right click on it and choose edit connections, then click eth0, edit, enter password ) in the edit connection window, there's a window for 802.1x security. Tick the box, select Protected EAP (PEAP), set the PEAP version to 0, leave inner authentication on MSCHAPv2. Then pop your user and password for the network. 

Success?

---

### Post by kevindubrow on 2010-01-13
Thank you so much for the advice.

I think its going to work! The problem is that I'm having account problems now...I should be online shortly though. Thanks again!

---

