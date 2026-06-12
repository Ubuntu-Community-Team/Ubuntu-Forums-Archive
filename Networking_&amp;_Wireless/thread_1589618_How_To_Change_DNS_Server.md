---
title: "How To Change DNS Server"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by joek71 on 2010-10-06
Hi Guys

Can someone please tell me how to convert DHCP to Static IP?

Thank you

---

### Post by e79 on 2010-10-06
Open     System --> Preferences --> Network Connections

Click on your working network card (could be eth0, eth1 etc) and click 'Edit'

Go to 'IPv4 Settings' Tab, scroll down from DHCP to 'Manual', click 'Add' and input your values there and don't forget to fill the 'DNS Server' box as well.

EDIT:  I added a screenshot with examples (these are not real values, change them accordingly to your installation)

Hope this helps

---

### Post by joek71 on 2010-10-07
Thank you, and that remain even after reboot?

---

### Post by e79 on 2010-10-07
> **joek71 said:**
> Thank you, and that remain even after reboot?
 
Yes it will since you set it up manually :)

---

### Post by dineshs on 2010-10-07
After giving IP mask and gateway,you should hit [COLOR="DarkRed"]enter[/COLOR].Then give DNS and apply

---

