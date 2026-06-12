---
title: "two modems, two linksys, split cable connection"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by 007casper on 2009-03-12
I have one cable connection that has been split into different parts of the house.  I had a connection on both sections of the house without a problem.  Then I lost connection on one side of the house.  I tried to solve the issue by cycling the modem, and also cycling the linksys that is attached to the modem... reseting...etc... have done so many things but still cant seem to work. 

when I ping 192.168.1.1 it sends 4 packets, and receives 4 100%
however, I cant ping google.com, or ping yahoo.com... and of course it doesnt tracert either... I am trobleshooting with win2K, so I turned off the zonealarm... still no connection. I have three laptops, one desktop, and one mega server.  Linksys unit is wifi model wrt54g v1.01.0.  Linksys used to have great support, after cisco bought it, I think support is connected to form letters, and some sorry a55 artificial intelligence.  
Whatever they suggested was useless.

then I did ipconfig/all

IP 192.168.1.101
subnet 255.255.255.0
default gateway 192.168.1.1
dhcp server 192.168.1.1
dns server 192.168.1.1

then checked linksys under status section, it gives

IP 192.168.100.1
subnet 255.255.255.0
default gateway 192.168.100.1
MTU 1500

under status>local
IP 192.168.1.1
subnet 255.255.255.0
dhcp enable
start ip 192.168.1.100
end ip 192.168.1.149
---------------------
the other side of the house where internet works flawlessly, the modem is attached to linksys BEFSR41 v2.00.4, it doesnt have wifi, I did ipconfig/all

IP 192.168.1.100
subnet 255.255.255.0
default 192.168.1.1
dhcp 192.168.1.1
dns server 66.70.160.20
dns server 66.70.160.21

then checked linksys under status section, it gives
login type dhcp
IP 79.90.146.75
subnet 255.255.255.0
default gateway 79.90.143.1
static dns1 66.70.160.20
static dns1 66.70.160.21
MTU1500

under status>local
IP 192.168.1.1
subnet mask 255.255.255.0
dhcp server enabled
****************************

please help:(

Thank you.

---

### Post by 007casper on 2009-03-12
I can ping localhost(127.0.0.1)

---

### Post by Hobgoblin on 2009-03-12
> **007casper said:**
> 

then checked linksys under status section, it gives

IP 192.168.100.1
subnet 255.255.255.0
default gateway 192.168.100.1
MTU 1500



This router (linksys) appears to be using it's self as the default gateway. Or the modem has the same IP as the router, that would cause problems. Can you change the IP?

Compare with...
> then checked linksys under status section, it gives
login type dhcp
IP 79.90.146.75
subnet 255.255.255.0
default gateway 79.90.143.1
static dns1 66.70.160.20
static dns1 66.70.160.21
MTU1500

Since you have two modems ??? I can't say what the IP address should be, though I would expect this to be configured by DHCP.

---

### Post by 007casper on 2009-03-12
I cant change the IP... the static IP is given by the ISP.  It worked around six hours, then it just died.  I reset it.... after that it was a black hole... I totally lost the connection.  

how can solve this issue through dhcp configuration?

Linksys suggested I cascade the routers.  I told them it is in the other side of the house, and it is not an option really.  

Then, they suggested to use befsr41 with wet54g which has bad reviews, then they suggested WAP54G with wrt54g, which has another set of bad reviews. I guess linksys cant make bridges, or repeaters.  When I asked them if I have to use another linksys product if there are any other options.  They said linksys is the way to go. 

when I told them it worked for six hours, how come there isnt any way to make it work... they said it wont be reliable/stable ???

---

