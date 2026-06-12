---
title: "Wifi connection with network manager very unstable"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by Paloseco on 2006-07-03
I can succesfully connect to a wpa-eap encrypted wireless access poing, but network manager disconnects repeatedly, even some times a minute. Is really annoying, has someone experienced this same issue? Maybe it is a bug? :neutral:

---

### Post by spd106 on 2006-07-03
Which chipset are you using?

I have an atheros based card that uses the madwifi driver (ath0). NM causes it to disconnect and rescan for networks every two minutes. So I removed nm and went back to the the old network-admin tool instead.

---

### Post by Paloseco on 2006-07-04
I am using an ipw2200 centrino.

---

### Post by armalite on 2006-07-05
Same for me, ipw2200 + eap-tls + NetworkManager and keeps disconnecting after 30 seconds.

---

### Post by Paloseco on 2006-07-05
Here is the bug filed:
[https://launchpad.net/distros/ubuntu/+bug/51841](https://launchpad.net/distros/ubuntu/+bug/51841)

Please drop your opinion in launchpad.

---

### Post by Paloseco on 2006-07-05
edited

---

