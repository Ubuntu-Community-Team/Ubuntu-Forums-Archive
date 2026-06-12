---
title: "Cisco Config Question"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by DGortze380 on 2009-07-22
Any input appreciated ...

I can't get traffic through this Cisco Router with the current config, and for the life of me can't think of why. I'm sure I'm just missing something simply.

Current Network Diagram

Cable Modem - D-link Router (192.168.0.1) - Switch - Cisco Router (192.168.0.14 / 172.16.0.14) - Ubuntu Host (172.16.0.2)

There are other hosts on the 192.168.0.0 network.

I can ping from 172.16.0.2 to 172.16.0.14 and 192.168.0.14 but NOT to 192.168.0.1 and not to the internet.

I can ping from the Cisco Router to any address on either network and to the internet.

I can ping from a host on the 192.168.0.0 network to 192.168.0.14 but not to anything on the 172.16.0.0 network.

Goal for the moment is to be able to route between the three networks, 192.168.0.0, 172.16.0.0 and the 'internet' (ie. my ISP on the other side of the modem).

What am I missing? Or is the problem my cheap D-Link router being in the mix (as I suspect)?

```

Current configuration : 690 bytes                                               
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
enable secret 5 $1$U6tP$LGLs763fVgm86OE5w2q8t.                                  
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
 ip address 192.168.0.14 255.255.255.240                                        
 ip access-group 100 in                                                         
 half-duplex                                                                    
!                                                                               
interface Serial0/0                                                             
 no ip address                                                                  
 shutdown                                                                       
!                                                                               
interface Ethernet1/0                                                           
 ip address 172.16.0.14 255.255.255.240                                         
 ip access-group 100 in                                                         
 half-duplex                                                                    
!                                                                               
ip http server                                                                  
ip classless                                                                    
ip route 0.0.0.0 0.0.0.0 192.168.0.1                                            
!                                                                               
!                                                                               
access-list 100 permit ip any any log                                           
!                                                                               
line con 0                                                                      
line aux 0                                                                      
line vty 0 4                                                                    
 login                                                                          
!                                                                               
!                                                                               
end        

```

---

### Post by joebeasley on 2009-07-22
The dlink router needs a route for the 172.16.0.x network.  It would send this traffic out to the internet using it's default route. Add a route (if possible) to the dlink router for the 172.16.0.x network using 192.168.0.14.

Once the routing is working, the dlink router has to be able to NAT the 172.16.0.x network out to the internet.  Check the docs for that.

---

### Post by DGortze380 on 2009-07-23
> **joebeasley said:**
> The dlink router needs a route for the 172.16.0.x network.  It would send this traffic out to the internet using it's default route. Add a route (if possible) to the dlink router for the 172.16.0.x network using 192.168.0.14.

Once the routing is working, the dlink router has to be able to NAT the 172.16.0.x network out to the internet.  Check the docs for that.

Agreed. I think the problem is that I'm unable to add a route to the D-Link. I'm pretty sure traffic is getting routed out to the 192.168.x.x correctly (from the logs and tests I've done) but it's not getting back from the 192.168.x.x to 172.16.x.x. 

I've also been unable to determine what Dynamic Protocol the D-Link uses, doesn't appear to be RIP v1 or v2, or OSPF. I think the temporary solution is to move the Cisco Router to the border behind the modem and use the D-Link on the 172.16.0.0 network.

---

### Post by doas777 on 2009-07-23
so you have a router that won't take static routes, or use any standard routing protocols? I'd say that the device you have is decidedly not a router, though it may say so on the box.

---

### Post by DGortze380 on 2009-07-23
> **doas777 said:**
> so you have a router that won't take static routes, or use any standard routing protocols? I'd say that the device you have is decidedly not a router, though it may say so on the box.

Again, agreed. It's a cheap P.O.S., but it's what I have at the moment.

---

### Post by DGortze380 on 2009-07-23
Better solution .. just set up NAT Overload on the Cisco router. All traffic to the POS D-Link looks like it's from a local host and doesn't need to be 'routed'.

---

