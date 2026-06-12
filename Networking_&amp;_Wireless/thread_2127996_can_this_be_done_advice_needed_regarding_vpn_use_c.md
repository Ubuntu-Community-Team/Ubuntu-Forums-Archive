---
title: "can this be done? advice needed regarding vpn use cctv..."
date: 2013-03-21
forum: Networking &amp; Wireless
---

### Post by glen99 on 2013-03-21
i really would like to know if this can be done... and would gladly make a paypal payment for help setting this up .......its been on my mind for months

i install cctv cameras for a living.

i routinely connect  cameras using  3g routers - for external access ,   ( i use fixed ip addressed sim card) which can then be reached from the the public wan.

these 3g fixed ip sims are really expensive - and come with data caps.

 ive always used them because pre paid sims  though cheap - are NOT nattable , thus they can not  be setup for port forwarding etc ,,, anything plugged into them , or using them - cant be reached from wanside.,,,, great for web surfing but nothing else

ive recently been playing with openvpn/ pptp vpn and from the client side have been able to access cctv cameras plugged into the same lan range as the vpn server...


but what i want to do ,,, is to be able to reach the cctv which is located on the vpn client side - 

imagine having an ip camera with a built in vpn client, which is always on - always connected to a vpn server ,,,,
if my laptop is on the vpnserver side i would wish to connect to this camera via its inbuilt vpn client.


is this setup doable?


usually , people connect via a vpn client to anything on the vpn server side...

but if i configured a vpn server ( residing on a router with a 3g sim card - which has a non accessable public ip) what address would i point my client to?

if a client could be configured , maybe installed on a wrt-dd router or raspberry pi  , configured to always "stream" an ip camera plugged into it , or ip device - thru to the vpn server ,,, then from server side i could connect to this ip camera / device.



can a networking pro help me out ?


glen uk. london

---

### Post by Cheesemill on 2013-03-21
It certainly can.

There is no reason at all why the VPN server has to be on the remote client side like you have it at the moment

The more usual setup is to a machine on the internet with a fixed IP that runs as a VPN server, and then have a  VPN client on all of the other remote networks. These clients don't need to have fixed IP addresses to be able to connect to the server, so your 3G wouldn't be a problem. You'd also have your home/work network connected as well. It makes no difference which is the server side and which is the client side, as long as you have the routing sorted out properly you can contact any of the cameras from your home/work network as if everything was plugged into the same switch (it is a Virtual Private Network after all).

As an example you could have the 192.168.0.0/24 network for the office, and then 192.168.1.0/24 network for the first remote site, 192.168.2.0/24 for the second and so on. If you sort out your DNS as well you could have proper names for all of your cameras instead of having to remember IP addresses (outside.workshop.mydomain.com for example).

+1 for the Raspberry Pi idea, you could plug an IP camera directly into the Pi with a crossover cable and then use a USB 3G dongle as your internet access. Because the Raspberry Pi OS is based on Debian the OpenVPN client is available in its standard repositories. Also the camera module for the Raspberry Pi is released next month, for some situations you might be able to get away without a separate IP camera altogether and your total hardware cost for a Pi + camera + 3G dongle would only be around £65.

Start with checking out the official Ubuntu documentation for OpenVPN in the 12.04 Server Guide...
[https://help.ubuntu.com/12.04/serverguide/openvpn.html](https://help.ubuntu.com/12.04/serverguide/openvpn.html)

---

### Post by glen99 on 2013-03-22
re:"[COLOR=#000000]The more usual setup is to a machine on the internet with a fixed IP that runs as a VPN server, and then have a VPN client on all of the other remote networks"

that is exactly what i envisage.

im only just playing with vpns ,,, ive managed to install a simple pptp vpn server on a raspberry and have it plugged into someones adsl router.

the vpn client is on my windows 7 laptop - can surf the internet fine..... 

it would be great to configure a raspberry as client - and as you say via the cross lead , be able to connect the ip video server in to it....and be able to reach this anywhere on the internet

but putting all remote networks on a different range - eg 192.168.1.0/24 , second remote network 192.168.2.0/24  , how would you setup up the main adsl router ( where the vpn server is connected)to port forward to the particular network- particualry if the remote network is on a different  ip range to the adsl router .
everytime ive setup a router - ive only ever set up port forwarding to ip addresses on the same range as the router itself ... eg: router ip add is 192.168.0.1 ,,, camera ip is 192.168.0.3 ... port forward 1024 to 192.168.0.3 - not 192.168.1.3 (for example)


ideally i would set up port forwarding on the main adsl router. so from the outside world ,  i can be  forwarded to the remote ip address of the pi running the client - and hopefully via that to the ip device plugged into it - and be prompted for the usual password/username etc....

i would give the client the static public ip of the  router ,the router port fowards to the pi client , and via his browser ( suffixed with the port my cameras always use -1024) reach the camera system linked via the crossover cable to the pi client ...
[/COLOR][COLOR=#000000]


still doable?.[/COLOR]

---

