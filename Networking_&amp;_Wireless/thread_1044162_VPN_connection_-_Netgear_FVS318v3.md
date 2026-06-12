---
title: "VPN connection - Netgear FVS318v3"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by maurelius on 2009-01-19
Hi guys,

first of all I'd like to thank everyone here for a great support - I have found most of answers to my questions without even having to ask! :)

But here is something I just can't get to work and I really need it to connect to my job-vpn..

On windows I can easily connect using TheGreenBow client with the following settings:

**- Lifetime: **
     Authentication (IKE): Default-3600, Min-360, Max-28800
     Encryption (IPSec): Default-3600, Min-360, Max-28800

**- Dead Peer Detection:**
     Check interval: 30
     Max. number of retries: 5
     Delay: 15

**- Misellaneous:**
     Retranssmissions: 2
     Delay: 15

**- PHASE 1 (Authentication)**
     Name: xxx
     Interface: Any
     Remote gateway: something.domain.com
     Preshared Key: xxxxx
     Certificate: None
     IKE:
     --Encryption: 3DES
     --Authentication: SHA
     --Key Group: DH2 (1024)
     Aggressive mode
     Local ID: DNS - xxx
     Remote ID: DNS - xxx

**- PHASE 2 (IPSec Configuration)**
     Name: xxx
     VPN Client address: 192.168.100.10
     Address Type: Subnet address
     Remote LAN address: 192.168.1.0
     Subnet mask: 255.255.255.0
     ESP:
     --Encryption: 3DES
     --Authenticaion: SHA
     --Mode: Tunnel
     Advanced: 
     --DNS Server: 0.0.0.0
     --WINS Server: 192.168.1.2

If anyone of you amazing guys can work this out on Ubuntu 8.10 or at least point me in the right direction, please answer this...

Many thanks in advance!

---

### Post by maurelius on 2009-01-20
Nobody has any idea how?

Please, help..

---

### Post by moresun on 2012-07-13
I have the same problem?

Any one

---

