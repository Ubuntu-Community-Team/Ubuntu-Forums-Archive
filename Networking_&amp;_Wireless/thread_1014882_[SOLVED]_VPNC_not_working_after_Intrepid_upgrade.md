---
title: "[SOLVED] VPNC not working after Intrepid upgrade"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by buddywilliams on 2008-12-18
Yesterday I upgraded to Intrepid and VPNC stopped working for me. I got the follow response:
vpnc: no response from target

I am connecting to a Cisco VPN server.

I tried all the fixes I could find on the internet aside from downgrading from vpnc 0.5.1 to 0.3.3 as one guy suggested. I tried adding these lines to my default.conf file:
```
NAT Traversal Mode cisco-udp
Local Port 10000
```

Nothing worked.

[Solution]

1. Use pcf2vpnc to convert .pcf to .conf file
I downloaded the .pcf file from my work and used:
```
/usr/share/vpnc/pcf2vpnc ~/Desktop/vpn.pcf ~/Desktop/vpn.conf
```

Which gave me two new settings:
```
IKE Authmode psk
IKE DH Group dh2
```

So my connection looked like:
```
IPSec ID Employee
IPSec gateway domain_to_vpn.com
IPSec secret my_secret
Xauth username my_username 
IKE Authmode psk
IKE DH Group dh2
```

2. My network changed the ip address for the vpnc server
ping domain_to_vpn.com
// get new ip address and replace in vpn.conf lines:

```
IPSec gateway domain_to_vpn.com
// with
IPSec gateway ip_address
```

3. Run vpnc with new .conf file
sudo vpnc ~/Desktop/vpn.conf

4. Replace old .conf file
```
cd /etc/vpnc
sudo mv default.conf old.conf
sudo mv ~/Desktop/vpn.conf ./default.conf

```

5. Run vpnc but don't press enter when promoted for password!
Whatever version of vpnc I was running before forced me to press return on the first password prompt for vpnc connect. Now I needed to enter my pin + passcode on the keyphab first! I was then able to connect.

---

