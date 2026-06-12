---
title: "Wireless Access"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by mjm1049 on 2009-06-29
I have recently installed Ubuntu 8.04 on my laptop which has the Intel 4965agn wireless card...
 
I am trying to get the wireless working....I can see all of the available networks in the task bar dropdown, however, when I try to connect to one I am unable.
 
From the terminal I did a iwconfig and am seeing the proper ESSID and am seeing my wireless routers mac address for the Access Point.  This leads me to believe that my computer is seeing the router and can talk to it but cannot connect....Has anyone seen a problem like this?  If so, do you know how to fix it?
 
A little more info... the wireless router does not require a password, when i select any wireless network from the task bar the icon shows it is trying to connect and then doesn't (I get the message "wireless network disconnected - you are now offline"), I see all the other wireless networks around me as well...
 
Please help!
Thanks,
mjm1049

---

### Post by mjm1049 on 2009-06-29
Excuse me, version 9.04...

---

### Post by mjm1049 on 2009-06-29
I figured it out....
 
needed to type the following in the terminal while wired to internet:
 
sudo apt-get install linux-backports-modules-jaunty

---

