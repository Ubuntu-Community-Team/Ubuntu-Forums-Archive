---
title: "how do I set up a second router?"
date: 2012-07-12
forum: Networking &amp; Wireless
---

### Post by Gatorade on 2012-07-12
when connecting a second router , does it matter which port I get the signal from ? 

I'm trying to connect a second router , but I keep getting a dns error.

I'll post more details when I get home later.

---

### Post by steeldriver on 2012-07-12
what are you trying to set it up **as**? are you trying to implement a separate subnet? or just use the 2nd router as a switch (effectively just multiplying one of the ports from your existing router)?

---

### Post by Gatorade on 2012-07-12
this > **steeldriver said:**
> just use the 2nd router as a switch (effectively just multiplying one of the ports from your existing router)?

---

### Post by steeldriver on 2012-07-12
OK in that case you should connect from the main router to one of the a LAN ports on the 2nd router (NOT the WAN port)

You probably need to go into the 2nd router's setup (via the web interface) and turn off any DHCP service so it's not potentially handing out conflicting IP addresses

I had a setup like that with a WRT54GL acting as a switch / wireless access point hanging off a Speedtouch DSL modem / router

Depending on the 2nd router model and firmware you *may* be able to reconfigure the WAN port as an additional LAN port to turn it into a true switch (and not lose a port).

---

### Post by Cheesehead on 2012-07-12
Steeldriver is 100% right.

---

### Post by Gatorade on 2012-07-12
ok, thanks.

I'll try it and post my results.

---

