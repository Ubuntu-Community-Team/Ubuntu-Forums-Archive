---
title: "Network down on system startup"
date: 2006-01-27
forum: Networking &amp; Wireless
---

### Post by orangejon on 2006-01-27
My wi-fi network used to work just fine, but ever since creating a profile in the "Network Settings" tool, the network is now dysfunctional when I boot the machine. I have to go into the network settings tool, click "disactivate" and then "activate" in order to bring it up.

I have since deleted the profile, to no effect. I had a look in /var/log/messages and can't see anything obviously wrong. Any ideas?

---

### Post by ]Nbx*cmD[ on 2006-01-27
Hmm i had a similar problem, i just changed the router config from dhcp to static and it works now but i'm sure there must be a better solution.

---

### Post by Titus A Duxass on 2006-01-27
This is mentioned in a previous thread.

You have to edit /etc/network/interfaces to make sure that the card you want is selected as auto.

---

