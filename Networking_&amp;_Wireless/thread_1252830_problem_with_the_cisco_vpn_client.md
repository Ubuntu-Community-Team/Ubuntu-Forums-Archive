---
title: "problem with the cisco vpn client"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by dagarshali on 2009-08-29
hi,
i was given a .sh file to set up the vpn client from our school. When i ran it, it installed the client and it was put in the application-->internet menu. When i clicked on that, it would open an UI for me to enter the user id and password. All of a sudden it stopped working yesterday. I can't figure out why. I reinstalled it and the case is the same. 

The item on the menu points to /opt/cisco/vpn/bin/vpnui

When i went to the terminal and typed that, it get GThread error. can be initialized only once.

I have no ideal about these things.. Can anybody please help?

Vishwa

---

### Post by cabez0n on 2009-08-31
Was there a kernel upgrade involved ? 
Cisco vpn client uses kernel modules, so if you change kernel you should reinstall the module.

---

### Post by dagarshali on 2009-08-31
yes, I think I instaleld the server kernel to accomadate 4gb of ram that I have. Can you please give the procedure for reinstalling the module.?

Regards,
vishwa

---

