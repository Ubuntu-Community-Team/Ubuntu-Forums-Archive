---
title: "Trying to access the internet..."
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by Bensky5012 on 2009-09-08
Hi everyone.  I am trying to connect to my windows network using ubuntu and am running into trouble.  I click on the connection icon in the upper right hand corner and a drop down comes up.  Next, I click on connect to hidden wireless network, I choose wep 128bit passphrase, I enter my network key and hit connect.  Then something funny happens.  As soon as I hit connect a little message pops up next to the connection icon that says, "The network connection has been disconnected."  Can someone tell me what I am doing wrong?  I just want to access the internet!

---

### Post by ductiletoaster on 2009-09-08
First have you tried usig any other security protocal. And second i would recomend switching from WEP to like WPA or WPA2. They are far more secure and i say this from experiance far less buggy. My gf laptop would drop connection randomly when i was one WEP 128bit so switched to WPA2 and no problems

---

### Post by Bensky5012 on 2009-09-09
Okay, I just changed my security protocol to wpa, then wpa2. Neither worked.  I ran into the same problem as before, so now I'm back to wep.  Any other suggestions?

---

### Post by Bensky5012 on 2009-09-09
anyone?

---

### Post by jml on 2009-09-09
Since you mentioned that you click on connect to hidden network, can I correctly assume that your wireless network does not broadcast it's ESSID?  If that is the case, try reconfiguring your access point to broadcast the ESSID.  Then, when you click on the network manager applet you will see the network listed.  Click on it from the drop down list and see if it connects.  I have read that network manager can occasionally have problems with hidden networks.  Hope that this helps.  Good luck.

Joe

---

### Post by alpage2 on 2009-09-09
Another possibility, if you are entering all the network details correctly, is if you have set MAC address filtering on your modem/router, but not entered the MAC address for the wireless adapter in use, in the allowed list.

Regards
Alan

---

### Post by community nerd on 2009-09-09
Wep is weaker and older than wpa

---

