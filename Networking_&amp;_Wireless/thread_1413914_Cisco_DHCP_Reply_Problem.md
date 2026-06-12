---
title: "Cisco DHCP Reply Problem"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by DGortze380 on 2010-02-23
Hi All,

I've got a really odd DHCP issue, hope someone has some insight.

I've got a Cisco 2610 router. It was previously configured as a DHCP client using the following procedure:

(config int)$ ip add dhcp client-id eth0/0 hostname 00.00.00.00.00.00

That's it. That's all it took. Worked correctly.

Now I have the same router in a different location, trying to pull an IP via DHCP from a different DHCP server. I doesn't get an address.

I've verified that it is sending BOOTP/DHCP requests. It's not getting any reply from the DHCP Server. 

I tried a different network with a different DHCP Server. Same problem.

Tried connecting a computer to each of the 2 DHCP servers mentioned above. Computer gets an IP Address no problem. I've verified that it sends BOOTP/DHCP Request and receives a BOOTP/DHCP reply.

It's not a cabling issue. One NIC is auto-sensing. Besides that, I tried both a straight through and cross-over cable.

I'm a loss. I don't understand why 2 of 3 DHCP Servers don't send a reply to this router.

---

### Post by koszta on 2010-02-23
Is the other DHCP also cisco or is it Linux? I would surely try to look at wireshark sniffer to see ALL the traffic. As for my cisco experience -I would try to re-up the intfces(sh & no sh) and surely would see "show run" command. Also see if there is a startup config... 
And just a question if you assign the ip manually does it work? I honestly didnt deal with very old IOSes much. I dont think that your router has any L2 security capabilities (if so make sure that some of those isnt causing the problems)
hope i helped at least some, just try posting more info if you dont get it working

---

### Post by DGortze380 on 2010-02-23
> **koszta said:**
> Is the other DHCP also cisco or is it Linux? I would surely try to look at wireshark sniffer to see ALL the traffic. As for my cisco experience -I would try to re-up the intfces(sh & no sh) and surely would see "show run" command. Also see if there is a startup config... 
And just a question if you assign the ip manually does it work? I honestly didnt deal with very old IOSes much. I dont think that your router has any L2 security capabilities (if so make sure that some of those isnt causing the problems)
hope i helped at least some, just try posting more info if you dont get it working

I don't have access to one of the other DHCP Servers. One is just my OS X laptop set up to act as a DHCP Server (for testing only).

I'll take a look at the rest of the traffic, but I'm not sure that would shed any more light on the issue.

I've tried re-up the interface, no change.

I've clear the config to eliminate any other issues. No ACLs in place, nothing, just the dhcp directive and no shutdown on one interface.

No L2 security to the best of my knowledge. It's a 2610 running 12.3

Everything works just great with manually assigned addresses. Helpful for troubleshooting, but unfortunately I need to receive a DHCP address on the WAN side of this router.

---

### Post by DGortze380 on 2010-02-23
#sh ver
```

Cisco Internetwork Operating System Software                                    
IOS (tm) C2600 Software (C2600-I-M), Version 12.3(17b), RELEASE SOFTWARE (fc2)  
Technical Support: http://www.cisco.com/techsupport                             
Copyright (c) 1986-2006 by cisco Systems, Inc.                                  
Compiled Mon 06-Mar-06 22:02 by dchih                                           
Image text-base: 0x80008098, data-base: 0x80CE0844                              
                                                                                
ROM: System Bootstrap, Version 11.3(2)XA4, RELEASE SOFTWARE (fc1)               
ROM: C2600 Software (C2600-I-M), Version 12.3(17b), RELEASE SOFTWARE (fc2)      
                                                                                
Router uptime is 5 minutes                                                      
System returned to ROM by power-on                                              
System image file is "flash:c2600-i-mz.123-17b.bin"                             
                                                                                
cisco 2610 (MPC860) processor (revision 0x203) with 28672K/4096K bytes of memor.
Processor board ID JAD05350F5Y (3879103548)                                     
M860 processor: part number 0, mask 49                                          
Bridging software.                                                              
X.25 software, Version 3.0.0.                                                   
2 Ethernet/IEEE 802.3 interface(s)                                              
1 Serial network interface(s)                                                   
32K bytes of non-volatile configuration memory.                                 
8192K bytes of processor board System flash (Read/Write)                        
                                                                                
Configuration register is 0x2102

```

#sh run
```

Building configuration...

Current configuration : 496 bytes
!
version 12.3
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname Router
!
boot-start-marker
boot-end-marker
!
!
no aaa new-model
ip subnet-zero
ip cef
!
!
!
!                                                              
!                                                                               
!                                                                               
!                                                                               
interface Ethernet0/0                                                           
 ip address dhcp                                                                
 half-duplex                                                                    
!                                                                               
interface Serial0/0                                                             
 no ip address                                                                  
 shutdown                                                                       
 no fair-queue                                                                  
!                                                                               
interface Ethernet1/0                                                           
 no ip address                                                                  
 shutdown                                                                       
 half-duplex                                                                    
!                                                                               
ip http server                                                                  
ip classless                                                                    
!                                                                               
!                                                                               
!                                                                               
line con 0                                                                      
line aux 0                                                                      
line vty 0 4                                                                    
 login                                                                          
!                                                                               
!                                                                               
end

```

#sh int
```

Ethernet0/0 is up, line protocol is up                                          
  Hardware is AmdP2, address is 0007.50a4.c900 (bia 0007.50a4.c900)             
  Internet address will be negotiated using DHCP                                
  MTU 1500 bytes, BW 10000 Kbit, DLY 1000 usec,                                 
     reliability 255/255, txload 1/255, rxload 1/255                            
  Encapsulation ARPA, loopback not set                                          
  Keepalive set (10 sec)                                                        
  ARP type: ARPA, ARP Timeout 04:00:00                                          
  Last input 00:00:31, output 00:00:09, output hang never                       
  Last clearing of "show interface" counters never                              
  Input queue: 0/75/0/0 (size/max/drops/flushes); Total output drops: 0         
  Queueing strategy: fifo                                                       
  Output queue: 0/40 (size/max)                                                 
  5 minute input rate 0 bits/sec, 0 packets/sec                                 
  5 minute output rate 0 bits/sec, 0 packets/sec                                
     236 packets input, 15216 bytes, 0 no buffer                                
     Received 221 broadcasts, 0 runts, 0 giants, 0 throttles                    
     0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored                       
     0 input packets with dribble condition detected                            
     74 packets output, 22755 bytes, 0 underruns                                
     9 output errors, 0 collisions, 1 interface resets                          
     0 babbles, 0 late collision, 0 deferred                                    
     9 lost carrier, 0 no carrier                                               
     0 output buffer failures, 0 output buffers swapped out                     
Serial0/0 is administratively down, line protocol is down                       
  Hardware is PQUICC with Fractional T1 CSU/DSU                                 
  MTU 1500 bytes, BW 1544 Kbit, DLY 20000 usec,                                 
     reliability 255/255, txload 1/255, rxload 1/255                            
  Encapsulation HDLC, loopback not set                                          
  Keepalive set (10 sec)                                                        
  Last input never, output never, output hang never                             
  Last clearing of "show interface" counters never                              
  Input queue: 0/75/0/0 (size/max/drops/flushes); Total output drops: 0         
  Queueing strategy: fifo                                                       
  Output queue: 0/40 (size/max)                                                 
  5 minute input rate 0 bits/sec, 0 packets/sec                                 
  5 minute output rate 0 bits/sec, 0 packets/sec                                
     0 packets input, 0 bytes, 0 no buffer                                      
     Received 0 broadcasts, 0 runts, 0 giants, 0 throttles                      
     0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored, 0 abort              
     0 packets output, 0 bytes, 0 underruns                                     
     0 output errors, 0 collisions, 0 interface resets                          
     0 output buffer failures, 0 output buffers swapped out                     
     0 carrier transitions                                                      
     DCD=down  DSR=up  DTR=down  RTS=down  CTS=down                             
                                                                                
Ethernet1/0 is administratively down, line protocol is down                     
  Hardware is AmdP2, address is 0007.50a4.c910 (bia 0007.50a4.c910)             
  MTU 1500 bytes, BW 10000 Kbit, DLY 1000 usec,                                 
     reliability 255/255, txload 1/255, rxload 1/255                            
  Encapsulation ARPA, loopback not set                                          
  Keepalive set (10 sec)                                                        
  ARP type: ARPA, ARP Timeout 04:00:00                                          
  Last input never, output never, output hang never                             
  Last clearing of "show interface" counters never                              
  Input queue: 0/75/0/0 (size/max/drops/flushes); Total output drops: 0         
  Queueing strategy: fifo                                                       
  Output queue: 0/40 (size/max)                                                 
  5 minute input rate 0 bits/sec, 0 packets/sec                                 
  5 minute output rate 0 bits/sec, 0 packets/sec                                
     0 packets input, 0 bytes, 0 no buffer                                      
     Received 0 broadcasts, 0 runts, 0 giants, 0 throttles                      
     0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored                       
     0 input packets with dribble condition detected                            
     0 packets output, 0 bytes, 0 underruns                                     
     0 output errors, 0 collisions, 0 interface resets                          
     0 babbles, 0 late collision, 0 deferred                                    
     0 lost carrier, 0 no carrier                                               
     0 output buffer failures, 0 output buffers swapped out

```

#sh dhcp lease 
```

Temp IP addr: 0.0.0.0  for peer on Interface: Ethernet0/0                       
Temp  sub net mask: 0.0.0.0                                                     
   DHCP Lease server: 0.0.0.0, state: 8 Purging                                 
   DHCP transaction id: 1C5E4                                                   
   Lease: 0 secs,  Renewal: 0 secs,  Rebind: 0 secs                             
   Next timer fires after: 00:00:06                                             
   Retry count: 0   Client-ID: cisco-0007.50a4.c900-Et0/0                       
   Hostname: Router

```

#sh ip route
(Gateway of last resort is set to DHCP. No DHCP lease received so it shows up as not set)
```

Codes: C - connected, S - static, R - RIP, M - mobile, B - BGP                  
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area           
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2           
       E1 - OSPF external type 1, E2 - OSPF external type 2                     
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2    
       ia - IS-IS inter area, * - candidate default, U - per-user static route  
       o - ODR, P - periodic downloaded static route                            
                                                                                
Gateway of last resort is not set

```

---

### Post by koszta on 2010-02-24
From my point of view everything seems to be fine...

I found a couple liks that might be useful (I guess you read or tried them anyway already tho)

[http://www.cisco.com/en/US/docs/ios/12_2t/12_2t8/feature/guide/ftwandhp.html]("http://www.cisco.com/en/US/docs/ios/12_2t/12_2t8/feature/guide/ftwandhp.html")

[http://www.dslreports.com/faq/10953]("http://www.dslreports.com/faq/10953")

This is from CISCO user guide and it seemed like a clear and good advice:
(the full thing is here [http://docs.google.com/viewer?url=http://www.ciscosystems.com/en/US/docs/ios/ipaddr/configuration/guide/iad_dhcp_client.pdf]("http://docs.google.com/viewer?url=http://www.ciscosystems.com/en/US/docs/ios/ipaddr/configuration/guide/iad_dhcp_client.pdf") )

[FONT="Tahoma"][I]You must configure the ip dhcp client commands before entering the ip address dhcp command on an
interface to ensure that the DHCPDISCOVER messages that are generated contain the correct option
values. The ip dhcp client commands are checked only when an IP address is acquired from DHCP. If
any of the ip dhcp client commands are entered after an IP address has been acquired from DHCP, it
will not take effect until the next time the router acquires an IP address from DHCP. This means that the
new configuration will only take effect after either the ip address dhcp command or the release dhcp
and renew dhcp EXEC commands have been configured.
1.
enable
2.
configure terminal
3.
interface type number
4.
ip dhcp client client-id {interface-name | ascii string | hex string}
5.
ip dhcp client class-id {string | hex string}
6.
ip dhcp client lease days [hours] [minutes]
7.
ip dhcp client hostname host-name
8.
[no] ip dhcp client request option-name
9.
ip address dhcp
[/I][/FONT]

I dont know, that is like all I can think of for now... Try the cisco guide. Hope it works at least some

---

### Post by DGortze380 on 2010-02-24
Unfortunately, I have seen all of those links, poured over them for 2 days now. No change.

Wireshark reveals just as I suspected.

- DHCP Server receives DHCPDISCOVER
- No reply
- Repeat

---

### Post by DGortze380 on 2010-02-26
Ok. I tried the configuration on another network. It works.

Brought it back and tried again. I overlooked another issue. I have a solid Activity light, but no collision warnings. Tried a cross-over cable, no change. Any ideas?

---

