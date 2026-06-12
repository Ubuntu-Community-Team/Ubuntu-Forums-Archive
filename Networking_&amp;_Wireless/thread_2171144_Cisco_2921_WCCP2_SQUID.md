---
title: "Cisco 2921 WCCP2 SQUID"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by akshayj2 on 2013-08-29
**I have setup a network like this**

[ATTACH=CONFIG]245814[/ATTACH]

[COLOR=#006400]**The config of router is as follows:**[/COLOR]

[COLOR=#006400]Current configuration : 1717 bytes                                              
!                                                                               
! Last configuration change at 14:14:33 UTC Wed Aug 28 2013                     
version 15.2                                                                    
service timestamps debug datetime msec                                          
service timestamps log datetime msec                                            
service password-encryption                                                     
!                                                                               
hostname Router                                                                 
!                                                                               
boot-start-marker                                                               
boot-end-marker                                                                 
!                                                                               
!                                                                               
enable secret 4 WO0e1OHJD7UrwZEfi032q1nH.KJvsEn5t6wG.AJgGhM                     
!                                                                               
no aaa new-model                                                                
!                                                                               
ip cef                                                                          
!                                                                               
!                                                                               
!                                                                                                                                          
!                                                                               
!                                                                               
!                                                                               
ip name-server 202.56.230.5                                                     
ip wccp web-cache password 7 02050D480809                                       
no ipv6 cef                                                                     
multilink bundle-name authenticated                                             
!                                                                               
!                                                                               
!                                                                               
!                                                                               
license udi pid CISCO2921/K9 sn FGL171411LT                                     
!                                                                               
!                                                                               
!                                                                               
!                                                                               
!                                                                               
!                                                                               
!                                                                               
!                                                                               
interface Embedded-Service-Engine0/0                                            
 no ip address                                                                  
 shutdown                                                                       
                                                                                 
Router#show run                                                                 
Building configuration...                                                       
                                                                                
Current configuration : 1717 bytes                                              
!                                                                               
! Last configuration change at 14:14:33 UTC Wed Aug 28 2013                     
version 15.2                                                                    
service timestamps debug datetime msec                                          
service timestamps log datetime msec                                            
service password-encryption                                                     
!                                                                               
hostname Router                                                                 
!                                                                               
boot-start-marker                                                               
boot-end-marker                                                                 
!                                                                               
!                                                                               
enable secret 4 WO0e1OHJD7UrwZEfi032q1nH.KJvsEn5t6wG.AJgGhM                     
!                                                                               
no aaa new-model                                                                
!                                                                               
ip cef                                                                          
!                                                                               
!                                                                               
!                                                                               
!                                                                               
!                                                                               
!                                                                               
ip name-server 202.56.230.5                                                     
ip wccp web-cache password 7 02050D480809                                       
no ipv6 cef                                                                     
multilink bundle-name authenticated                                             
!                                                                               
!                                                                               
!                                                                               
!                                                                               
license udi pid CISCO2921/K9 sn FGL171411LT                                     
!                                                                               
!                                                                               
!                                                                               
!                                                                               
!                                                                               
!                                                                               
!                                                                               
!                                                                               
interface Embedded-Service-Engine0/0                                            
 no ip address                                                                  
 shutdown                                                                       
!                                                                               
interface GigabitEthernet0/0                                                    
 ip address 182.72.34.82 255.255.255.248                                        
 ip nat outside                                                                 
 ip virtual-reassembly in                                                       
 duplex auto                                                                    
 speed auto                                                                     
!                                                                               
interface GigabitEthernet0/1                                                    
 ip address 172.16.1.1 255.255.255.0                                            
 ip wccp web-cache redirect in                                                  
 ip nat inside                                                                  
 ip virtual-reassembly in                                                       
 duplex auto                                                                    
 speed auto                                                                     
!                                                                               
interface GigabitEthernet0/2                                                    
 ip address 192.168.1.1 255.255.255.0                                           
 ip nat inside                                                                  
 ip virtual-reassembly in                                                       
 duplex auto                                                                    
 speed auto                                                                     
!                                                                               
ip forward-protocol nd                                                          
!                                                                               
no ip http server                                                               
no ip http secure-server                                                        
!                                                                               
ip nat inside source list NATTABLE_HOSTS interface GigabitEthernet0/0 overload  
ip route 0.0.0.0 0.0.0.0 182.72.34.81                                           
!                                                                               
ip access-list standard NATTABLE_HOSTS                                          
 permit 172.16.0.0 0.0.255.255                                                  
 permit 192.168.1.0 0.0.0.255                                                   
!                                                                               
!                                                                               
!                                                                               
!                                                                               
control-plane                                                                   
!                                                                               
!                                                                               
!                                                                               
line con 0                                                                      
 exec-timeout 0 0                                                               
 logging synchronous                                                            
line aux 0                                                                      
line 2                                                                          
 no activation-character                                                        
 no exec                                                                        
 trans                                                                          
 transport input all                                                            
 transport output pad telnet rlogin lapb-ta mop udptn v120 ssh                  
 stopbits 1                                                                     
line vty 0                                                                      
 password 7 050A0D1C20475D                                                      
 login                                                                          
 transport input telnet                                                         
line vty 1 4                                                                    
 login                                                                          
 transport input none                                                           
!                                                                               
scheduler allocate 20000 1000                                                   
!                                                                               
end                               [/COLOR]                                              
        

[COLOR=#0000cd]**The squid config is as follows:**
wccp2_router 192.168.1.1     
#Designate the router intercepting the traffic

wccp2_forwarding_method gre     
#Router to squid encapsulation

wccp2_return_method gre     
#Squid to router encapsulation

wccp2_service standard 0 password=cisco     
#Standard service defines http traffic interception, with password protection between squid and the router

http_port 192.168.1.2:3128 intercept


#
# Recommended minimum configuration:
#

# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl localnet src 10.0.0.0/8    # RFC1918 possible internal network
acl localnet src 172.16.0.0/12    # RFC1918 possible internal network
acl localnet src 192.168.0.0/16    # RFC1918 possible internal network
acl localnet src fc00::/7       # RFC 4193 local private network range
acl localnet src fe80::/10      # RFC 4291 link-local (directly plugged) machines

acl SSL_ports port 443
acl Safe_ports port 80        # http
acl Safe_ports port 21        # ftp
acl Safe_ports port 443        # https
acl Safe_ports port 70        # gopher
acl Safe_ports port 210        # wais
acl Safe_ports port 1025-65535    # unregistered ports
acl Safe_ports port 280        # http-mgmt
acl Safe_ports port 488        # gss-http
acl Safe_ports port 591        # filemaker
acl Safe_ports port 777        # multiling http
acl CONNECT method CONNECT

#
# Recommended minimum Access Permission configuration:
#
# Deny requests to certain unsafe ports
http_access deny !Safe_ports

# Deny CONNECT to other than secure SSL ports
http_access deny CONNECT !SSL_ports

# Only allow cachemgr access from localhost
http_access allow localhost manager
http_access deny manager

# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost

#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#

# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
http_access allow localnet
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

# Squid normally listens to port 3128
#http_port 3128

# Uncomment and adjust the following to add a disk cache directory.
cache_dir ufs /var/cache/squid 100 16 256

# Leave coredumps in the first cache dir
coredump_dir /var/cache/squid

#
# Add any of your own refresh_pattern entries above these.
#
refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440
refresh_pattern -i (/cgi-bin/|\?) 0    0%    0
refresh_pattern .        0    20%    4320[/COLOR]


[COLOR=#8b4513]**When I run the following setup I see following messages on Console with debug IP WCCP enabled:**[/COLOR]

[COLOR=#8b4513]*Aug 28 14:30:26.355: WCCP-EVNT:IPv4:S0: updating wc 192.168.1.2 orig assign in)
*Aug 28 14:30:26.947: WCCP-REDIR: IN: C 172.16.1.2(Gi0/1)->173.194.36.38(Gi0/0)2
*Aug 28 14:30:27.195: WCCP-REDIR: IN: C 172.16.1.2(Gi0/1)->74.125.135.99(Gi0/0)2
                                                                     
*Aug 28 14:30:27.399: WCCP-REDIR: IN: C 172.16.1.2(Gi0/1)->74.125.135.99(Gi0/0)2
                                                                         
*Aug 28 14:30:29.955: WCCP-REDIR: IN: C 172.16.1.2(Gi0/1)->173.194.36.38(Gi0/0)2
*Aug 28 14:30:30.199: WCCP-REDIR: IN: C 172.16.1.2(Gi0/1)->74.125.135.99(Gi0/0)2
*Aug 28 14:30:30.399: WCCP-REDIR: IN: C 172.16.1.2(Gi0/1)->74.125.135.99(Gi0/0)2
                                                                      
*Aug 28 14:30:35.955: WCCP-REDIR: IN: C 172.16.1.2(Gi0/1)->173.194.36.38(Gi0/0)2
*Aug 28 14:30:36.203: WCCP-REDIR: IN: C 172.16.1.2(Gi0/1)->74.125.135.99(Gi0/0)2
*Aug 28 14:30:36.351: WCCP-EVNT:IPv4:S0: updating wc 192.168.1.2 orig assign in)
*Aug 28 14:30:36.403: WCCP-REDIR: IN: C 172.16.1.2(Gi0/1)->74.125.135.99(Gi0/0)2
                                                                      
*Aug 28 14:30:46.351: WCCP-EVNT:IPv4:S0: updating wc 192.168.1.2 orig assign in)
                                                                       
*Aug 28 14:30:47.947: WCCP-REDIR: IN: C 172.16.1.2(Gi0/1)->173.194.36.37(Gi0/0)2
*Aug 28 14:30:48.607: WCCP-REDIR: IN: C 172.16.1.2(Gi0/1)->74.125.234.47(Gi0/0)2
*Aug 28 14[/COLOR]





[COLOR=#b22222]**The contents of cache.log is as follows:**
2013/08/28 19:54:58 kid1| Starting Squid Cache version 3.3.8 for x86_64-unknown-linux-gnu...
2013/08/28 19:54:58 kid1| Process ID 2600
2013/08/28 19:54:58 kid1| Process Roles: worker
2013/08/28 19:54:58 kid1| With 1024 file descriptors available
2013/08/28 19:54:58 kid1| Initializing IP Cache...
2013/08/28 19:54:58 kid1| DNS Socket created at [::], FD 7
2013/08/28 19:54:58 kid1| DNS Socket created at 0.0.0.0, FD 8
2013/08/28 19:54:58 kid1| Adding nameserver 127.0.0.1 from /etc/resolv.conf
2013/08/28 19:54:58 kid1| Logfile: opening log daemon:/var/log/squid//access.log
2013/08/28 19:54:58 kid1| Logfile Daemon: opening log /var/log/squid//access.log
2013/08/28 19:54:59 kid1| Unlinkd pipe opened on FD 14
2013/08/28 19:54:59 kid1| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2013/08/28 19:54:59 kid1| Store logging disabled
2013/08/28 19:54:59 kid1| Swap maxSize 102400 + 262144 KB, estimated 28041 objects
2013/08/28 19:54:59 kid1| Target number of buckets: 1402
2013/08/28 19:54:59 kid1| Using 8192 Store buckets
2013/08/28 19:54:59 kid1| Max Mem  size: 262144 KB
2013/08/28 19:54:59 kid1| Max Swap size: 102400 KB
2013/08/28 19:54:59 kid1| Rebuilding storage in /var/cache/squid (clean log)
2013/08/28 19:54:59 kid1| Using Least Load store dir selection
2013/08/28 19:54:59 kid1| Set Current Directory to /var/cache/squid
2013/08/28 19:54:59 kid1| ERROR: No forward-proxy ports configured.
2013/08/28 19:54:59 kid1| ERROR: No forward-proxy ports configured.
2013/08/28 19:54:59 kid1| ERROR: No forward-proxy ports configured.
2013/08/28 19:54:59 kid1| ERROR: No forward-proxy ports configured.
2013/08/28 19:54:59 kid1| ERROR: No forward-proxy ports configured.
2013/08/28 19:54:59 kid1| ERROR: No forward-proxy ports configured.
2013/08/28 19:54:59 kid1| Loaded Icons.
2013/08/28 19:54:59 kid1| Accepting WCCPv2 messages on port 2048, FD 17.
2013/08/28 19:54:59 kid1| Initialising all WCCPv2 lists
2013/08/28 19:54:59 kid1| HTCP Disabled.
2013/08/28 19:54:59 kid1| Pinger socket opened on FD 20
2013/08/28 19:54:59 kid1| Squid plugin modules loaded: 0
2013/08/28 19:54:59 kid1| Accepting NAT intercepted HTTP Socket connections at local=192.168.1.2:3128 remote=[::] FD 18 flags=41
2013/08/28 19:54:59 kid1| Done reading /var/cache/squid swaplog (0 entries)
2013/08/28 19:54:59 kid1| Store rebuilding is 0.00% complete
2013/08/28 19:54:59 kid1| Finished rebuilding storage from disk.
2013/08/28 19:54:59 kid1|         0 Entries scanned
2013/08/28 19:54:59 kid1|         0 Invalid entries.
2013/08/28 19:54:59 kid1|         0 With invalid flags.
2013/08/28 19:54:59 kid1|         0 Objects loaded.
2013/08/28 19:54:59 kid1|         0 Objects expired.
2013/08/28 19:54:59 kid1|         0 Objects cancelled.
2013/08/28 19:54:59 kid1|         0 Duplicate URLs purged.
2013/08/28 19:54:59 kid1|         0 Swapfile clashes avoided.
2013/08/28 19:54:59 kid1|   Took 0.04 seconds (  0.00 objects/sec).
2013/08/28 19:54:59 kid1| Beginning Validation Procedure
2013/08/28 19:54:59 kid1|   Completed Validation Procedure
2013/08/28 19:54:59 kid1|   Validated 0 Entries
2013/08/28 19:54:59 kid1|   store_swap_size = 0.00 KB
2013/08/28 19:54:59 kid1| ERROR: No forward-proxy ports configured.
2013/08/28 19:54:59| pinger: Initialising ICMP pinger ...
2013/08/28 19:54:59|  icmp_sock: (1) Operation not permitted
2013/08/28 19:54:59| pinger: Unable to start ICMP pinger.
2013/08/28 19:54:59|  icmp_sock: (1) Operation not permitted
2013/08/28 19:54:59| pinger: Unable to start ICMPv6 pinger.
2013/08/28 19:54:59| FATAL: pinger: Unable to open any ICMP sockets.
2013/08/28 19:55:00 kid1| storeLateRelease: released 0 objects[/COLOR]

With the above setup, on client PCs, websites keep loading and loading and they never finish and finally die.
Two things concern me:
[COLOR=#000000](1)[/COLOR][COLOR=#b22222]
2013/08/28 19:54:59|  icmp_sock: (1) Operation not permitted
2013/08/28 19:54:59| pinger: Unable to start ICMP pinger.[/COLOR]
Is this because I have not configued IP V6 address ?
I have already tried these 2 commands
# chown root /usr/lib/squid/pinger
# chmod 4755 /usr/lib/squid/pinger



(2)
[COLOR=#b22222]2013/08/28 19:54:59 kid1| ERROR: No forward-proxy ports configured.
2013/08/28 19:54:59 kid1| ERROR: No forward-proxy ports configur[/COLOR]ed

Please let me know what am I missing in the config.
Let me know if more details are needed.

Thanks in advance.

---

### Post by Luke_Newey on 2014-03-30
I know this is an old thread but im also having this issue, all the how tos keep saying you need to build some sort of GRE tunnel. Im not certain of the specifics but iver tried with or with out it and my access log stays empty no matter what. So even though the WCCP client on the squid server speaks to the router (and vice versa) none of the redirected web requests ever makes it to the squid. Thus the loading loading - shes dead jim.

For the one above you could try an l2 wccp redirect, i dont know how to do it personally but it looks like your setup would allow for it (ive heard the guys talking about it at work) you need multiple vlans and do some funky routing in between them

Anyone out there know what has gone wrong here ? - my squid is in the same subnet as the redirect but i have an access-list that deny's it from redirect we use the same technique with an iron port at work (in fact 3 of) and its all good. it must have something to do with the squid/ubuntu os

---

