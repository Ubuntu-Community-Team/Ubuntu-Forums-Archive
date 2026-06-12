---
title: "wifi problems with ubuntu 9.10"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by qwe_poi on 2010-02-27
hello
I have installed ubuntu 9.10 on my notebook packard bell mx65-100 (a little old). I have problems with the wifi card (intel pro wireless 3945ABG) since the hardware button for the activation is always turned on (since the boot) and the card doesn't work. I think that the drivers are installed, but the wifi network is always disabled and it is not possible to use it. 
Thanks

---

### Post by spaceinvader on 2010-03-04
packard bell easynote   ispci can see card (atheros) but messin with drivers and nothing ..card works fine in arch but not in 9.1
add acpi=force pnpbios=off to end of boot line and it all works !! hope this helps

---

