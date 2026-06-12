---
title: "Connect via Ethernet at a second location"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by SirShaggy on 2006-06-27
OK, I have a laptop with an ethernet connection at home. It works perfectly.
I want to be able to connect to Ethernet at work also. (Not at the same time;) )
Both the home modem/router and the work modem/router are set to Dynamic so they SHOULD provide IP information automatically.
How should I go about setting this laptop up for a second connection over the same device? (eth0)
In other words, I want to be able to plug it in at home, turn it on and it works. Plug it in at work, turn it on and it works. I realize in the real world it doesn't always happen, I just happen to think it should!:D 
Please steer me in a direction. I think I can get there, just not sure where/how to start.
Thanks,
Shaggy

---

### Post by digimars on 2006-06-27
If both locations are already set up for DHCP, and your Network Manager (System->Administration->Networking) is set up to recieve DHCP, you shouldn't have to do anything else.  Just plug and go.  Once you power down your computer, it should release its IP, or the router takes it back on its own once it realizes that it is no longer in use.  Now if your workplace uses a static IP, that will be slightly different.

But if you do have issues, you can try this (in this order)
```

sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0

```

---

### Post by SirShaggy on 2006-06-28
PERFECT. That is what I was hoping for. I am not sure why, networking is real foreign to me. I can do most things pretty well, networking requires me to ask. Anyway, thanks so much for the input. If I have troubles, I'll be back!
Shaggy

---

