---
title: "Problems obtaining an ip addr via DHCP"
date: 2006-02-26
forum: Networking &amp; Wireless
---

### Post by aosmith on 2006-02-26
using WPC54GX and a 2wire modem.  With dhclient i get the error messge "No working leases in persistent database - sleeping."

---

### Post by drachir on 2006-02-26
are you wep encripted?

---

### Post by aosmith on 2006-02-26
turned the wep off in order to fix this problem...

---

### Post by drachir on 2006-02-26
/have you set your DNS under the networksettings tab?

---

### Post by aosmith on 2006-02-26
i set them but they never "save" ie when i open networksetting up after hitting "ok" all fields are empty.  Just a note the status of my card blinks between idle and recieving every few seconds and the "local network" light on my wirless router is on even when all other computers are off/dissconnected.

---

### Post by drachir on 2006-02-26
When I set mine up I had the same problems. Go to 
 System
 Aministration
 Networking

Set you default gateway to you wireless. it is the lower left of the Network settings box.

Set up you DNS

Click you wireless and press Properties
Check enable this connection(if its not already enabled)
Set your ESSID
Set your key type (default is plain ASCII it should be set to Hexidecimal)
Set your WEP Key


I use a static ip so if you choose to set you ip subnet and gateway

Click OK

It should be up after that. I hope it works for you

---

### Post by aosmith on 2006-02-26
still doesnt work...i copied dns and search domains straight from the desktop im using.  doesnt work with static ip either :cry:

---

