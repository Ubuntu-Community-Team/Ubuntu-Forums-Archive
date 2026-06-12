---
title: "Linux Noob wireless problems"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by jefe3404 on 2009-11-20
I have a sotec 1320 laptop I have installed ubuntu 9.10. I have a Dynex **DX-NNBC pcmica wireless n card. I have a 2 wire wireless router with 64 bit WEP. I am able to connect with the wired connection. **
 
**I have download WICD and setup the 64 bit password. I can see my router and the light on the card comes on. but the wireless activity light never flashs. **
 
**It never obtains ipaddress. I'm not sure what wireless chipset it uses either. **
 
**Please help.**

---

### Post by jefe3404 on 2009-11-23
I double checked the card using windows xp and it works properly. What else can I check. I have no idea what to check next.
 
Thanks,

---

### Post by jefe3404 on 2009-11-24
Someone please help. I'm bout to pull my hair out.

---

### Post by chili555 on 2009-11-24
With the card inserted in the slot, please open a terminal and do:```
lspcmcia -v
iwconfig
```Please post the results. Thanks.

---

