---
title: "Wifi Works but i cant log online"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by bsg221 on 2010-07-06
I just installed the 10.04 on my laptop a compaq 6510b that was was running xp. Ubuntu cant seem to connect to the internet unless i have it hooked up via ethernet cable but the wifi recognizes my network. in windows i use to log in via the wirless network to my boardband connection. Any thoughts?

---

### Post by pedro_orange on 2010-07-06
Couple of things...

1 - Does your wireless NIC get an IP Address? Is this static or dynamic? 
2 - Can it address the router?
3 - Whats it's default gateway?

ifconfig will give you some information. Ping will prove the rest.

---

### Post by bsg221 on 2010-07-06
> **pedro_orange said:**
> Couple of things...

1 - Does your wireless NIC get an IP Address? Is this static or dynamic? 
2 - Can it address the router?
3 - Whats it's default gateway?

ifconfig will give you some information. Ping will prove the rest.

Yes it seems to work fine i the problem is that my dsl can only work with eth0 i would like it to work with my wireless blekin connection which is just fine.

---

### Post by pedro_orange on 2010-07-07
Please can you provide the information I asked for, so this issue can be resolved? 

1 - ifconfig /all
2 - ping <RouterIP>

Can you also show us iwconfig please?

---

