---
title: "Wireless works flawlessly, then after a period of time just stopped working completly"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by MadnessRed on 2009-12-26
When I start up linux I am connected the wireless network almost instantly, then after a while it stops working, and it asks for me to re-enter the wireless passkey again. If I enter it, waits a couple of seconds, then asks again. If I press cancel it looses the network completely and nothing is listed in the Wireless Networks list.
The wireless works fine in Windows, and after a restart will work in Ubuntu again, for a time, before repeating the above.

I have Ubuntu9.10 on a WPA netowrk.
lspci gives my adapter as a Atheros AR928X

Any help would be great,

thanks

---

### Post by MadnessRed on 2009-12-30
bump

---

### Post by MadnessRed on 2010-01-02
anyone, can you please help, I cannot use ubuntu if I am going to have to restart every 20 minutes

---

### Post by thierrybo on 2010-01-04
Hi,

just bought a new laptop 2 days ago with this chip and I am experiencing the same problem (ubuntu 9.10). 
I have no solution but I discovered that after restarting network manager it connects again automatically, so I added this command to a launcher in my taskbar :
```

gksudo service network-manager restart
```

---

### Post by MadnessRed on 2010-01-04
> **thierrybo said:**
> Hi,

just bought a new laptop 2 days ago with this chip and I am experiencing the same problem (ubuntu 9.10). 
I have no solution but I discovered that after restarting network manager it connects again automatically, so I added this command to a launcher in my taskbar :
```

gksudo service network-manager restart
```

thanks, ill try that, I don't mind just clicking a button to sort.

---

### Post by thierrybo on 2010-01-06
Well,

after two days using > gksudo service network-manager restart, it does not always work. Some times the command hangs and does not respond at all, neither > gksudo service networking restart.

---

### Post by MadnessRed on 2010-01-06
> **thierrybo said:**
> Well,

after two days using , it does not always work. Some times the command hangs and does not respond at all, neither .

it does nothing for me either, I switched to wicd and it seems to be working a bit better now.

---

### Post by MadnessRed on 2010-03-03
nope still dies, any suggestions?

---

### Post by thierrybo on 2010-03-04
Hi,

I left Network Manager / Wicd and configured "the old way" manually using /etc/network/interfaces file and I have no more problem, but I loose the easy network switching ability. I use mainly my laptop at home, so  for me it is OK.

---

### Post by MadnessRed on 2010-03-06
i use network in 2 locations regularly and also some places i go give free wifi which I would need to connect to.

---

### Post by MadnessRed on 2010-04-23
I found a work-around.

Open terminal and type
```
ping [address]
```

It doesn't matter what address you use.
You could ping google.com or an ip. Eg my router is 192.168.2.1 so I type ```
ping 192.168.2.1
```

You could probably do ```
ping localhost
```. I don't think the address you are pinging needed to exist. The point is that the ping is on a loop. Which means its pings constantly. As a result. The wireless card is always in use so never goes to sleep, and its going to sleep which seems to be the problem as it can't wake up.

Maybe you can add ping localhost to the startup to get it done automatically. I found this almost by accident, so I haven't experimented with it much. I just though that I would share.

---

