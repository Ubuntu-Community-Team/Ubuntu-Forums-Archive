---
title: "Weird OpenVPN behavior (D/C when used)"
date: 2013-05-16
forum: Networking &amp; Wireless
---

### Post by Ferrat on 2013-05-16
So I got my OpenVPN client up and running however as soon as there is even a little bit of traffic out on the net the openvpn service stops and the tap0 interface goes away and the connection crashes?? 

Mean I got it up and running, can see ip when using ifconfig but connection drops when used?

Edit: 
When using 
```
sudo openvpn config.ovpn
``` 
This crash does not occur and the tap0 dev handles the traffic just fine

Edit2: 

Seems to have solved itself as if by magic

---

