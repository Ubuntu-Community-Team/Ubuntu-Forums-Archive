---
title: "shared dsl connection problems"
date: 2013-07-14
forum: Networking &amp; Wireless
---

### Post by bobx on 2013-07-14
I am upgrading my internet/gateway computer from a 1998 450mHz AMD K6 with Slackware 7 to a Dell Studio dual processor with Ubuntu 12. 

The Dell has a Ethernet connection to the DSL modem. I am running the modem in bridge mode. I want to connect a windows computer and a WiFi "modem" to the Dell. I have tried it two ways. The first way was to connect an Ethernet switch to a second Ethernet port on the Dell. Then connect the WiFi and Windows computer to the switch. The second way was to have three Ethernet ports on the Dell and connect the WiFi and Windows computer each to separate Ethernet ports on the Dell. In both cases I set up the Ethernet port to the DSL as a DSL connection and the other two ports as "Shared to Other Computers". The Windows computer has no issues but when I connect to the WiFi "modem" with my Archos tablet I have problems. The tablet connects using DHCP and gets an IP Address. I can see the other computers from the tablet. However I have problems connecting to the Internet. I can go to some web sites like Google. But I get timed out for most sites. I have tried setting up the Ethernet port on the Dell that connects to the WiFi with a static IP Address but then the tablet can not even see the Dell. The WiFi modem has a static IP address in the 192.168 range whereas the Dell assigns a 10.42 address to the second and third Ethernet ports and the tablet also gets a 10.42 address. Not sure if that is a problem.

I have also tried using my old computer as a gateway. In this setup the old computer connects to the DSL modem and it's Ethernet card is setup with two IP addresses, the external one and an internal in the 192.168 range. I then set up the Dell with a static IP Address in the 192.168 range and use the old computer as a gateway. Then I hook up the WiFi modem to a second Ethernet port on the Dell which is configured as "Shared to Other Computers". In this configuration the tablet can connect up and access the internet with no problem. The tablet in this case is set up with a staic IP Address, knows the old computer is the gateway and has been give DNS server addresses. 

Any suggestions?

Thank You
Bob

---

