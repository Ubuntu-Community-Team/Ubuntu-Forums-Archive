---
title: "CHAP  authentication failed"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by Sandman1983 on 2010-04-10
After 72 hours googling for this I found nothing. I have problem with pppoe on ubuntu 9.10.
On fresh installed ubuntu i tried to establish pppoe connection with this command:
```
sudo pppoeconf
```After the wizard shows I type my username and password given from my ISP.
When the configuring for pppoe finishes I used the plog command and it shows
pppd[2185]: Using interface ppp0
pppd[2185]: Connect: ppp0 <--> eth0
pppd[2185]: Warning - secret file /  etc/ppp/pap-secrets has world and/or group access
pppd[2185]: Warning - secret file /etc/ppp/chap-secrets has world and/or group access
pppd[2185]: CHAP authentication failed: Access Denied
pppd[2185]: CHAP authentication failed
pppd[2185]: Connection terminated.

Any suggestions how to solve this:confused:

PS: This (pppoe) doesn't work from the live cd

---

### Post by alexfish on 2010-04-10
Hi

Have a look here it may just be a permissions issue, hope it will help 


[LIST]
[*][User  Priviledges- the dip and dialout groups ]("http://www.pcurtis.com/ubuntu-mobile.htm#dip_dialout")
[*][Permissions  for /etc/ppp/pap-secrets and etc/ppp/chap-secrets]("http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets")
[/LIST]
regards

alexfish

---

