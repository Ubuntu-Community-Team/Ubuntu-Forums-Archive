---
title: "IPv6 tunneling on Lucid 10.04"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by ReetP on 2011-11-17
Hi,

I've been struggling getting the setup right on my 10.04 desktop.

Following the guide here : [https://wiki.ubuntu.com/IPv6](https://wiki.ubuntu.com/IPv6) I have most of it right, but the guide is not quite clear on the network manager settings.

I have a Hurricane account with the following settings :

IPv6 Tunnel Endpoints
Server IPv4 Address:216.66.80.26
Server IPv6 Address:2001:470:1f08:150b::1/64
Client IPv4 Address:my.static.IPv4.IP
Client IPv6 Address:2001:470:1f08:150b::2/64

From the guide I have the following in my /etc/network/interfaces :


auto he-ipv6
iface he-ipv6 inet6 v4tunnel
    endpoint 216.66.80.26
    address  2001:470:1f08:150b::2
    netmask  64
    up ip -6 route add default dev he-ipv6
    down ip -6 route del default dev he-ipv6


In the guide it says :
"Right click on the network manager icon in the tray and click Edit Connections. Select the connection to your local network and click Edit. Go to the IPv6 Settings tab and set the Method to Manual. Click Add. For the address put the first address in your Routed 64. (In this example it would be 2001:470:b:d29f::1 .) For the prefix put in 64 . 
For the gateway, put in the address from the "Client IPv6 address" of the tunnel details page (in this example it would be 2001:470:a:d29f::2)."

It's the Route part that is not quite clear as it requires and Address, Prefix and Gateway.

I have added what I thought were the correct settings :

Adresses:
Address 2001:470:1f08:150b::1
Prefix 64

Routers:
Address 2001:470:1f08:150b::1
Prefix 64
Gateway 2001:470:1f08:150b::2

I am pretty sure this is wrong but I can't see quite what the right numbers should be.

Any help would be gratefully appreciated - I am happy to edit the wiki to clarify it a little more.

B. Rgds
John

---

