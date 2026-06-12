---
title: "Route netmask error"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by DueceMcSteege on 2009-04-09
I am trying to setup a route to my xbox360 on the same network as my computer. The xbox has DHCP turned on, and it's automatically recieving the netmask 255.255.255.0 from my router. I try to add it with:  ```
route add -net 192.168.1.116 netmask 255.255.255.0
``` and route kindly returns this error:```
route: netmask doesn't match route address
```

Yeah... but, My whole network is running on that subnet and everything works just fine, I have several routes in the table with the same netmask. 

Someone please tell me what kind of shenanigans these are.

---

### Post by Iowan on 2009-04-09
I haven't used the **route add** command, but looking over the **man** page... is it possible the **-net** option doesn't like what appears to be a host address?  Might it be happier with```
route add -net 192.168.1.0 netmask 255.255.255.0
```

---

