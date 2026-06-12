---
title: "Huawei E353 USB Stick: Mobile Broadband Sharing (ICS)"
date: 2012-11-28
forum: Networking &amp; Wireless
---

### Post by guyrichie@hotmail.com on 2012-11-28
Hello All,
[B]
RE: Huawei E353 USB Stick: Mobile Broadband Sharing (ICS)[/B]

I have a Huawei E353 HSPA+ USB mobie broadband stick.  I wish to share this internet connection to other computers on my local home network.  

My existing home network comprises of an ADSL router with 4xLAN ports and WiFi.  The WAN (ADSL) port is not connected as I have ditched my telephone line.  The router has DHCP enabled with the following settings:

Start IP:    192.168.5.1
End IP:      192.168.5.100
Primary DNS: 192.168.5.1

All computers on this local network whether wired or wireless all comunicate as expected.

On one of the wired network computers (eth0), connection information as follows:

IP Address:    192.168.5.2
Subnet Mask:   255.255.255.0
Default Route: 192.168.5.1
Primary DNS:   192.168.5.1

...I have attached the above named USB modem.  This modem attaches as a new network device, eth1 with connection information as follows:

IP Address:    192.168.1.100
Subnet Mask:   255.255.255.0
Default Route: 192.168.1.1
Primary DNS:   192.168.1.1

From this computer I can ping and access all computers on 192.168.5.0/24 and I can ping 192.168.1.1.  Likewise I can access the web UI for my router and the USB modem alike.

Following the guide: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) I follow the steps to enable "Shared to other computers" on eth0 under IPv4, knowing that eth1 has a connection to the internet.  I then follow through with checking th installed/not-installed dnsmasq packages and run:

$ sudo iptables -t nat -A POSTROUTING -j MASQUERADE

I then reset connection eth0, which then has connection information as follows:

IP Address:    10.42.43.1
Subnet Mask:   255.255.255.0

I can ping [www.bbc.co.uk](www.bbc.co.uk) sucessfully.  I am unable to ping 192.168.5.1, however that I guess is understandable as the IP address of eth0 is not on 192.168.5.0/24.  On another computer on the local network (192.168.5.3) I am unable to ping [www.bbc.co.uk](www.bbc.co.uk), I get the following reply:

ping: unkown host [www.bbc.co.uk](www.bbc.co.uk)

According to: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) this should work???

I decided to do some trouble shooting with my limited knowlege.  I reset eth0 to DCHP (i.e. disbaled "Shared to other computers") under IPv4.  This brought me back to be able to ping 192.168.5.0/24 and 192.168.1.1.  However when I ping [www.bbc.co.uk](www.bbc.co.uk) I get the following reply:

From (192.168.5.1) icmp_seq=1 Destination Net Unreachable

If I disconnect eth0 and ping [www.bbc.co.uk](www.bbc.co.uk) I get a reply.

I think I can get this working without setting eth0 to "Shared to other computers".  I believe this is a routing issue but my networking knowledge and configuration is limited.

Any assisatnce would be greatly appreciated.

Many thanks,
Guy

---

### Post by guyrichie@hotmail.com on 2012-11-29
Bump!

---

