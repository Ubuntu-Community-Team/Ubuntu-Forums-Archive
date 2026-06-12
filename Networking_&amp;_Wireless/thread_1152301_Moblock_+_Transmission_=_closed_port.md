---
title: "Moblock + Transmission = closed port?"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by DeusExM1 on 2009-05-07
I have the necessary port forwarded on transmission. If i open transmission and check the port it says "port is open"

If i run moblock and transmission at the same time, it reports that the "port is closed". 

I thought moblock was only supposed to block IPs, not ports? So what gives?

---

### Post by uthturn on 2009-05-07
install mobloquer its a gui for moblock if its moblock you should be able to fix it easier with this

---

### Post by DeusExM1 on 2009-05-07
yes i have the mobloquer GUI, thats how i see that the port is "closed".

I still dont get how moblock manages to block everything, even the ports. im pretty sure thats why my download speeds are in the 80kb range instead of the normal 400-1000 kbs.

any ideas?

---

### Post by DeusExM1 on 2009-05-08
bump

---

### Post by jre on 2009-05-08
Please don't bump only after a few hours ...

MoBlock doesn't close or open ports. (I guess) What happens is that transmission checks if the port is open by requesting a connection from some test host. This test host's IP is in MoBlock's blocklist, so the connection gets blocked, so transmission thinks the port is closed - but it's just the blocked IP, not the port.
To recapitulate: connection = IPs and port. Or just think of IPs as houses, and ports as streets between them. The street may be blocked or the house door may be blocked - in both cases you can't get from one house to the other.

To solve your problems: either whitelist the test host's IP in MoBlock (blockcontrol/mobloquer), or use fewer blocklists.
See [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

---

### Post by DeusExM1 on 2009-05-08
sorry about posting only after a few hours, i lost the sense of time. 

So my port is open despite the fact that transmission thinks its closed? So i assume it does not affect download speeds, correct?

---

### Post by jre on 2009-05-08
> **DeusExM1 said:**
> So my port is open despite the fact that transmission thinks its closed? So i assume it does not affect download speeds, correct?

Other good hosts might still be blocked because of too restrictive  blocklists. Otherwise you are fine now.

---

### Post by DeusExM1 on 2009-05-08
Thanks for the hep =]

---

