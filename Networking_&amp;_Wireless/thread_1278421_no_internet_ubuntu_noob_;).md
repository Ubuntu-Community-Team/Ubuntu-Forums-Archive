---
title: "no internet ubuntu noob ;)"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by joker012 on 2009-09-29
hi I'm a real noob as it comes to Ubuntu ans i I'm trying it for the first time and i finally got the 9.04 version working bud I don't have internet can some one lead me the way to become a Ubuntu owner 



i'm using a realtek ethernet controller dont know if that make a diferance

---

### Post by neotifa on 2009-09-29
Hi.
System->Preferences->Network Configuration
this is the place where you need to estabilish your connection, whereever you are using dsl, wirreless, vpn...
Hope this works

---

### Post by joker012 on 2009-09-29
i can find the setup function bud don't understand how to set it 
i thought i would be plug and play with utp but is just aint working

---

### Post by bigboy7foru on 2009-09-29
you have to manually insert the ip netmask and gateway
 
open your terminal and type ifconfig it should give you that info
 
in currently trying to find a way to save the config so i dont have to enter it everytime i restart the computer

---

### Post by Iowan on 2009-09-29
If all goes well (apparently it didn't...), Network Manager should get an IP address via DHCP, and you'd be surfing along. A few things are easier via terminal (Applications>Accessories>Terminal) - post results of **ifconfig -a**, and **lshw -C network**.That should tell you if you're getting IP address or if interface is recognized and has a driver (as well as what card Ubuntu thinks you have).

---

### Post by joker012 on 2009-09-30
i re instalt a other version (8.04) and it works correctly now

---

