---
title: "Can't SSH out of my home network"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by CrusaderAD on 2012-05-09
I can't SSH out of my home network. Example, I can SSH from my phone on 3G to the office, but I can't from the wireless at my home. I used to be able to. I haven't changed any settings on my home router. Happens on multiple machines. I can't even ping the office ip. Can the firewall at the office block in such a way? Maybe the ISP is blocking me?

---

### Post by papibe on 2012-05-09
Hi CerealCypher.

Hard to say without more information. Could you post the result of a connection attempt, but using the verbose option?
```
ssh -vvv user@office
```
Regards.

---

### Post by CrusaderAD on 2012-05-11
Thanks for the reply. Just says connection timed out, did a ping request too... 100% packet loss.

---

### Post by Peter09 on 2012-05-11
Are you attempting to connect using the ip address or the DNS name?

---

### Post by CrusaderAD on 2012-05-11
IP address. I'm going to try connecting my laptop straight to the cable modem to see if it's my router. Any other ideas are welcome.

---

### Post by CrusaderAD on 2012-07-10
It was the router. Belkin. Got a netgear and it works great now.

---

