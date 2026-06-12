---
title: "Connecting to DSL via Wireless"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by 0mbr3 on 2011-10-25
Hi all,

I often have to connect Internet with my laptop from a friends place. He doesn't have a router but only a wireless modem. (We are in china the setups are a little strange..) 
So problem is that i can connect to the modem with wireless, but then i don't have access to the DSL as it s listed under Wired connection. 
Is there anyway to still reach the DSL via wireless?

Thanks a lot

---

### Post by 0mbr3 on 2011-10-29
Still have the same problem, any ideas please ?

---

### Post by 0mbr3 on 2011-10-31
Is this just me or ubuntuforum is not the palce to get ubuntu answers ? So far i didn't have one usefull reply in the 6 detailed thread i have posted...:confused:

---

### Post by dineshs on 2011-11-04
Can you tell us how your friend is connecting to internet?If he is using PPPoE dialler,you may try this.
Create a connection using```
sudo pppoeconf wlan0
```(assuming your wireless device is detected as wlan0) 
Then connect using```
sudo pon dsl-provider
```.Please also post what you get for ```
sudo lshw -C network
```

---

### Post by pqwoerituytrueiwoq on 2011-11-04
does this modem have a gateway?
if your friend is using over 1 computer/device it probably does (check his/her machine's ip address if it is not a private ip address there is no gateway)
if it does not have a gateway you would have to get another IP address from the isp
or make your friends computer act as a router

---

