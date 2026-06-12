---
title: "ADSL connectivity/router issues"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by masoomac on 2010-08-17
Hi All, 
 
 **Current set up:**

**OS:**
Ubuntu 10.04 Lucid Lynx (April 2010)

 **ISP:**
MTNL, Mumbai, Thane region. ADSL 1MBPS 
 
 **Hardware:**
1 PC, 1 laptop (Acer 5536, AMD). D-Link DSL-502T router (modem), SMC WBR14-G wifi access point. PC connected to wifi access point with lan cable and laptop connects through wifi to the wifi access point.
 
 **Problem:**
Frequent disconnection (every 10 mins) even though ADSL line led is lit steadily and all other lights functioning normally. ISP has checked and ok'ed physical line connections and say no problems on their end either.
 
 **Observations:**
The DSL-502T router settings automatically resets from PPPOE to bridged mode. So if we manually restart adsl router and then change setting to PPPOE internet connectivity starts and goes on for about 10 mins to half an hour. Then back to square one. This happens whether the pc is connected to 502T directly or through wifi access point. 
 
 **Current solution:**
We now have connected DSL-502T router directly to PC with lan cable and set router to bridged mode (no DHCP server). This is working fine and even when the connection drops (about twice a day) the redial option is activated and we nearly have continous connectivity.
 
 **Why we still need a SOLUTION:**
The current solution means that i have no internet on my laptop (coz bridge mode doesn't work with the SMC wifi access point and works only if pc is directly connected to the DSL-502T). :-( :-(
 
Please guide!
Warm regards

---

### Post by dineshs on 2010-08-17
> The DSL-502T router settings automatically resets from PPPOE to bridged mode.I think it is the problem with your D-link modem.After configuring the modem in PPPoE mode did you save and reboot the modem(may be under the menu admin-commit and reboot)

---

### Post by masoomac on 2010-08-17
Yes i have saved and rebooted. Checked settings logging into router again (within a min) and settings were as done. Then after a while (10 - 30 mins) connection drops and when i check it shows reset to bridge mode.

---

### Post by dineshs on 2010-08-17
> I think it is the problem with your D-link modemI suggest you try another modem.May be your ISP can help you try another modem for 1 or 2 days

---

### Post by masoomac on 2010-08-18
@Dineshs, I tried another Dlink router GLB 802*** . Same problem. Had to use bridge connection to dial, pppoe didnt work there either. Friend who exchanged routers said he faced disconnections using my router. Could i be having dual problems - Router issue and connection wire issues? Should i re-install firmware on my router dlink dsl-502t to see if that helps?

---

### Post by dineshs on 2010-08-18
> **masoomac said:**
> @Dineshs, I tried another Dlink router GLB 802*** . Same problem. Had to use bridge connection to dial, pppoe didnt work there either. Friend who exchanged routers said he faced disconnections using my router. Could i be having dual problems - Router issue and connection wire issues? Should i re-install firmware on my router dlink dsl-502t to see if that helps?I am not sure.Can you contact D-link service?Maybe they can help you.

---

### Post by masoomac on 2010-08-26
Thx! Contacting D-Link India helped....
They asked me to change the router password. Weird but it worked.... Am posting from my lap-top connected by wi-fi!!! :-)

---

### Post by dineshs on 2010-08-26
> They asked me to change the router password. Weird but it worked..good

---

