---
title: "intel pro wireless 3945abg workaround"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by ktechman on 2009-06-12
I just read [https://lists.ubuntu.com/archives/kernel-bugs/2009-January/046785.html]("https://lists.ubuntu.com/archives/kernel-bugs/2009-January/046785.html") and the advise worked in my situation is there anyway to make this persistent between boots here is the code

```

 sudo bash
 rmmod iwl3945
 modprobe iwl3945

```

I believe all that is needed is sudo modprobe iwl3945 but I cannot figure out how to include that command at boot or even after startup

---

### Post by ktechman on 2009-06-12
Okay I answered my own question again, the script is
```

#!/bin/bash
rmmod iwl394
modprobe iwl3945

```

Name the script WirelessStart

Then:
```
sudo update-rc.d WirelessStart defaults
```

Then:
```
sudo chmod +x /etc/init.d/WirelessStart
```  

Wireless works:)

---

