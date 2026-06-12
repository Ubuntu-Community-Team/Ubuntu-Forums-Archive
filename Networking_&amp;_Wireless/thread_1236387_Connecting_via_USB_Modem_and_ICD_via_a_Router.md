---
title: "Connecting via USB Modem and ICD via a Router"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by Neill_R on 2009-08-10
Hi

can any help me determine how and what I have to do to get  ICS (inetenet connection sharing) dolled out via a router to my internal windows PC NETWORK. Router is LinkSys WRK54G. Internet PC (laptop) Xubuntu 9.04 with an orange USB ICON 225 Dongle (hsO0). Dynamic IPAddress. Firestarter is configured for ICS on Hso0/eth0 (Eth0 is pluged into the internet port of router. 

I think the problem lies with the ubutu DHCP server (used to dole ot yhe internet side ip address of the router and hence not passing on default gateway and DNS servers. The main problem is my lack of understanding so I hope you can help.

Thanks
Neill

---

### Post by Macchi on 2009-08-10
Try the following:
1) Turn off DHCP from firestarter. 
2) Configure a static IP address for your computer ethernet interface towards the router and likewise add a static address on the router WAN port. Be use they are both on the same network. 
3) Set the gateway of the WAN port of the router to the address of the computer. Set the gateway of the computer to the IP address you have assigned to the WAN port of the router.
4) Check the DNS servers from your mobile broadband with cat /etc/resolv.conf and copy those values to the router.

PS: It works, but such arrangements have their advantages and disadvantages. After some time you may experience a drop in the connection and it has to be restarted. I have used such a scheme for more that a year but recently replaced everything with a Dovado UMR router.

---

