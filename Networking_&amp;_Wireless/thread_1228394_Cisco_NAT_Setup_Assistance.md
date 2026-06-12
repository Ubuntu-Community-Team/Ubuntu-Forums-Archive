---
title: "Cisco NAT Setup Assistance"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by neilticktin on 2009-07-31
So, we've had the two weeks from hell with a Verizon DSL install -- but after four man days of our time spent, they finally have that working.  But, now I'm struggling with our LAN config.

In short, I have a Verizon DSL connection with 5 static IPs.  I want to NAT most of our machines through 1 static IP, and then the balance of static IPs would be used for public facing devices.

The design is:

   Verizon DSL Modem -> Cisco 2600 E1/0 ...
     Cisco 2600 E0/0 -> 24 port managed switch

The 2600's public interface is at 69.24.8.18. 

Below is the config that I currently have tried. 

10.20.60.0-255 is the private addresses for the LAN (e0/0). I would like the Cisco to give these out via DHCP. The dns-server 68.94.156.1 68.94.157.1 are good DNS servers. This all looks to be working fine. 

69.24.8.18-22 are our static IPs with Verizon. 69.24.8.1 is the default route through Verizon. Subnet mask is 255.255.255.0 

69.24.8.18 is the 2600 address as I said. 69.24.8.19 is the NAT pool address for 10.20.60.xxx addresses to share -- but I would love to conserve the IPs and make this pool use the same as the router address (69.24.8.18). I think that's possible, right?

192.168.1.1 is the address of the Verizon DSL Router. 192.168.1.10 is the address of the Cisco on that segment for convenience sake. 

The switch is where I'd like to plug in all VoIP phones, and computers into ... whether they have a 10.20.60.xxx or have a public address (e.g., 69.24.8.20-22). Is that doable?

This can't be that hard -- but I'm thinking I'm pretty lame.  Any advice? 

Thanks!

Neil

-----------------------------------------------------------


Cisco-2600#wr
Building configuration...
[OK]
Cisco-2600#sho run
Building configuration...

Current configuration : 2126 bytes
!
version 12.1
no service single-slot-reload-enable
service timestamps debug datetime
service timestamps log datetime
service password-encryption
!
hostname Cisco-2600
!
logging buffered 4096 debugging
no logging console
enable secret 5 $1$bNtd$Zc9axgSjxOr4nrts9kJVb/
enable password 7 010109114F0E0B0A
!
!
!
!
!
memory-size iomem 15
clock timezone PST -8
clock summer-time PDT recurring
ip subnet-zero
no ip source-route
ip dhcp excluded-address 10.20.60.1 10.20.60.99
ip dhcp excluded-address 10.20.60.200 10.20.60.254
!
ip dhcp pool dhcp-MainLAN
   network 10.20.60.0 255.255.255.0
   domain-name something.com
   default-router 10.20.60.1
   dns-server 68.94.156.1 68.94.157.1
   lease 0 2
!
no ip bootp server
!
!
!
interface Loopback1
 no ip address
!
interface Ethernet0/0
 description Lakefield Private LAN
 ip address 10.20.60.1 255.255.255.0
 no ip redirects
 no ip proxy-arp
 ip nat inside
 no ip mroute-cache
 half-duplex
 no cdp enable
!
interface Ethernet0/1
 no ip address
 no ip redirects
 no ip mroute-cache
 shutdown
 half-duplex
 no cdp enable
!
interface Ethernet1/0
 description Verizon-DSL
 ip address 69.24.8.18 255.255.255.0
 ip nat outside
 no ip mroute-cache
 half-duplex
 no cdp enable
!
router rip
 network 10.0.0.0
 network 69.0.0.0
!
ip nat pool NAT-Pool 69.24.8.19 69.24.8.19 netmask 255.255.255.0
ip nat inside source list 1 pool NAT-Pool overload
ip classless
ip route 0.0.0.0 0.0.0.0 69.24.8.1
no ip http server
!
logging trap debugging
logging facility local0
access-list 1 permit 10.20.60.0 0.0.0.255
no cdp run
snmp-server engineID local 000000090200003080F34140
snmp-server community RO RO
snmp-server community Cisco-2600 RO
snmp-server community public RO
banner login ^CC
********************************************
*     This is a private network. No        *
*     unauthorized usage without           *
*     permission.  Thank you.              *
********************************************
^C
!
line con 0
 exec-timeout 60 0
 login
line aux 0
line vty 0 4
 exec-timeout 1440 0
 password 7 0519091A3549430C
 login
!
ntp clock-period 17179828
ntp server 192.6.38.127
end

Cisco-2600#

---

