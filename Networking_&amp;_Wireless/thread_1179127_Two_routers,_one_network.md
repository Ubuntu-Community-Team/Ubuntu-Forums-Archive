---
title: "Two routers, one network?"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by MonsterDuc on 2009-06-05
Networking not my strenght here so I may be asking for the impossible...

Setup:
ISP modem -> Linksys WRT54G router -> SMC7004VBR router
I have devices connected to both the Linksys and the SMC router.  

Problem:
Devices on the Linksys gets an addy of 192.168.1.100-150, and the ones on the SMC gets 192.168.2.100-150.  The 192.168.2 must be assigned by the ISP modem.  With these two networks I can't have my xbox (on 192.168.1) see my ushare library on my ubuntu pc on 192.168.2.

Question:
1) Anyone know a way to have the SMC act as switch and not assign IPs? (fw hacks ok, but I haven't found any yet). Or an alternate config that would allow the devices to see each other?

Not sure if that has the necessary info or not.  Just ask and I'll add more if needed.

Thanks!

---

### Post by dewmanstl on 2009-07-18
> **MonsterDuc said:**
> Networking not my strenght here so I may be asking for the impossible...

Setup:
ISP modem -> Linksys WRT54G router -> SMC7004VBR router
I have devices connected to both the Linksys and the SMC router.  

Problem:
Devices on the Linksys gets an addy of 192.168.1.100-150, and the ones on the SMC gets 192.168.2.100-150.  The 192.168.2 must be assigned by the ISP modem.  With these two networks I can't have my xbox (on 192.168.1) see my ushare library on my ubuntu pc on 192.168.2.

Question:
1) Anyone know a way to have the SMC act as switch and not assign IPs? (fw hacks ok, but I haven't found any yet). Or an alternate config that would allow the devices to see each other?

Not sure if that has the necessary info or not.  Just ask and I'll add more if needed.

Thanks!

Try turning off DHCP for the SMC, give it a ip address outside of the range of the DHCP on the Linksys, then give it dns of the linksys, so now in theory you should be able to grab a ip address from the linksys when you are plugged into the smc....

Thats kinda what I did with my two linksys routers....I also gave my xbox a static ip address.

Hope this helps....

---

