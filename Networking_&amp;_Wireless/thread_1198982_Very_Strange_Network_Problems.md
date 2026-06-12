---
title: "Very Strange Network Problems"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by HedgeBoar on 2009-06-28
Hi,
Running kubuntu 9.04, this machine has been running as a torrent/media machine perfectly for a few months now, until the other night.  For no reason I can think of, something seems to be blocking most network ports.  I can still use a web browser and reach local samba shares, but email clients, torrent clients etc. will not work at all.  If these are set to use our router's upnp port mapping, the mapping fails, and if I manually forward the ports they still appear closed.  I have tried a number of different torrent clients with the same result, I have removed the network-manager app and set the network up manually with no change.  Also tried reinstalling iptables.  No change.  

The only thing that happened in the days leading up to this was a couple of updates - i think a thunderbird one was the most recent, and I certainly don't remember seeing anything to do with network software.

One odd symptom, is when using utorrent/wine set to use upnp, the following error message occurrs after a few tries: 

[2009-06-28 23:23:36]  UPnP: Unable to map port 232.0.17.0:29135 with UPnP.

Now, I am pretty sure that the ip address in that should be this macines local address...?  It isn't.  Every attempt utorrent makes to use upnp, a different address comes up....  Is this strange?

Any ideas on what may be going on?  Cheers.

---

### Post by HedgeBoar on 2009-06-28
Forgot to mention - I've rebooted the router a few times and double checked the settings at that end. Can't see anything out of the ordinary, and the other machines on the network (WinXP) are not having any troubles...

---

### Post by MaindotC on 2009-06-28
Well this is difficult to troubleshoot because you could have any number of firewalls or restrictions on your machine but I'll do my best.  Post the ouput of:
```

sudo iptables -L -nv
sudo ufw status
#do not use 'localhost' please - I dunno if it really makes a difference but I'd prefer that you use your public ip address
nmap <your_public_ip_address>

```

---

### Post by HedgeBoar on 2009-06-28
```
lounge@lounge:~$ sudo iptables -L -nv
[sudo] password for lounge:          
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  eth0   *       192.168.2.101        192.168.2.255       
    4   160 logaborted  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED tcp flags:0x04/0x04                                                                                                                    
 2499 1877K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED            
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3                          
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11                         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12                         
  723 54995 nicfilt    all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                
  723 54995 srcfilt    all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3               
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11              
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12              
    0     0 srcfilt    all  --  *      *       0.0.0.0/0            0.0.0.0/0                                     

Chain OUTPUT (policy DROP 3 packets, 595 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
 2040  556K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3               
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11              
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12              
  619 53409 s1         all  --  *      *       0.0.0.0/0            0.0.0.0/0                                     

Chain f0to1 (3 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpts:6881:6889 state NEW                                                                                                                      
  121  6083 logdrop    all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                

Chain f0to2 (3 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 logdrop    all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain f1to0 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  196 10192 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:80 state NEW 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8080 state NEW                                                                                                                             
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8008 state NEW                                                                                                                             
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8000 state NEW                                                                                                                             
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:8888 state NEW                                                                                                                             
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:6969 state NEW                                                                                                                             
   35  1820 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpt:443 state NEW 
    4   208 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spts:1024:5999 dpts:6881:6889 state NEW                                                                                                                       
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:43627 state NEW              
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 state NEW                 
   94  6117 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:53                           
  290 35072 logdrop    all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                

Chain f1to2 (3 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:137 state NEW 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spts:1024:5999 dpt:137 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:137 dpt:137        
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spts:1024:5999 dpt:138 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:138 dpt:138        
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:139 state NEW      
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spts:1024:5999 dpt:139 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:445 state NEW      
    0     0 logdrop    all  --  *      *       0.0.0.0/0            0.0.0.0/0                                      

Chain f2to0 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 logdrop    all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain f2to1 (3 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:137 dpts:1024:5999 
   94  7872 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:137 dpt:137        
   71 16111 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:138 dpt:138        
   24  1152 logdrop    all  --  *      *       0.0.0.0/0            0.0.0.0/0                                      

Chain logaborted (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    4   160 logaborted2  all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED '                                                                                                    

Chain logaborted2 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    4   160 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `ABORTED '                                                                                                                             
    4   160 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED            

Chain logdrop (8 references)
 pkts bytes target     prot opt in     out     source               destination         
  787 52020 logdrop2   all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10 
    2   190 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED '                                                                                                    
   61 14064 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                

Chain logdrop2 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  787 52020 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `DROPPED '                                                                                                                             
  787 52020 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                

Chain logreject (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 logreject2  all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED '                                                                                                    
    0     0 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with tcp-reset                
    0     0 REJECT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable    
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                

Chain logreject2 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `REJECTED '                                                                                                                            
    0     0 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with tcp-reset                
    0     0 REJECT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable    
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                

Chain nicfilt (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  723 54995 RETURN     all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 RETURN     all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 RETURN     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 logdrop    all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain s0 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  121  6083 f0to1      all  --  *      *       0.0.0.0/0            192.168.2.101       
    0     0 f0to1      all  --  *      *       0.0.0.0/0            192.168.2.255       
    0     0 f0to1      all  --  *      *       0.0.0.0/0            127.0.0.1           
    0     0 f0to2      all  --  *      *       0.0.0.0/0            192.168.2.111       
    0     0 f0to2      all  --  *      *       0.0.0.0/0            192.168.2.105       
    0     0 f0to2      all  --  *      *       0.0.0.0/0            192.168.2.102       
  413 23777 logdrop    all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain s1 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 f1to2      all  --  *      *       0.0.0.0/0            192.168.2.111       
    0     0 f1to2      all  --  *      *       0.0.0.0/0            192.168.2.105       
    0     0 f1to2      all  --  *      *       0.0.0.0/0            192.168.2.102       
  619 53409 f1to0      all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain s2 (3 references)
 pkts bytes target     prot opt in     out     source               destination         
   24  1152 f2to1      all  --  *      *       0.0.0.0/0            192.168.2.101       
  165 23983 f2to1      all  --  *      *       0.0.0.0/0            192.168.2.255       
    0     0 f2to1      all  --  *      *       0.0.0.0/0            127.0.0.1           
    0     0 f2to0      all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain srcfilt (2 references)
 pkts bytes target     prot opt in     out     source               destination         
   28  6170 s2         all  --  *      *       192.168.2.111        0.0.0.0/0           
  161 18965 s2         all  --  *      *       192.168.2.105        0.0.0.0/0           
    0     0 s2         all  --  *      *       192.168.2.102        0.0.0.0/0           
  534 29860 s0         all  --  *      *       0.0.0.0/0            0.0.0.0/0           

```

```
lounge@lounge:~$ nmap -PN 118.90.137.57

Starting Nmap 4.76 ( http://nmap.org ) at 2009-06-29 14:18 NZST
Stats: 0:01:15 elapsed; 0 hosts completed (1 up), 1 undergoing Connect Scan
Connect Scan Timing: About 37.00% done; ETC: 14:21 (0:02:07 remaining)
All 1000 scanned ports on ip-118-90-137-57.xdsl.xnet.co.nz (118.90.137.57) are filtered

Nmap done: 1 IP address (1 host up) scanned in 201.52 seconds

```


Seems I don't have the ufw package installed... This should be installed by default, should it not?  Could this be the problem?

Thanks for your help.

---

### Post by HedgeBoar on 2009-06-29
Have now tried installing ufw and trying a few things with it - tried manually allowing ports for things, turning it off altogether, both with no change. 
Also, seems I was a bit hasty in saying that samba works - I can access other computers from here, but cannot access this computer from anywhere else.  So the only things that are working are web browsers (konq, opera, firefox all working fine) and apt etc...

---

