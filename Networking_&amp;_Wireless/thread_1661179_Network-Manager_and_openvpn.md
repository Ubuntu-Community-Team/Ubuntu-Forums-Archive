---
title: "Network-Manager and openvpn"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by keithspg on 2011-01-06
Running 10.10 (Maverick) 32 bit fully up to date. 
I have set up my router with openVPN and have a fuctional VPN configuration. It works flawlessly from the command line. I cannot figure out how to configure network manager to connect, though. I believe it is due to a missing 'float' checkbox in the NM-openvpn package. 

My config:
remote XXXXXX.dyndns-office.com 1194
client
dev tap0
proto udp
resolv-retry infinite
nobind
persist-key
persist-tun
float
ca ca.crt
cert client1.crt
key client1.key
ns-cert-type server

Am I doing something wrong in NM? I cannot seem to get all these settings into the NM configuration box. In the 'advanced' key, I have only "Use LZO data compression" and "Use TAP device". If I tell NM to connect to this VPN, it acts like it is connected, but I cannot connect to anything on the server end of the VPN. Is there a workaround that I can put these settings into NM and have it connect?

KeithSPG

---

