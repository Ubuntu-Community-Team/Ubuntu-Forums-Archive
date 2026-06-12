---
title: "Wireless adhoc for ICS help"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by b1driver on 2009-09-21
Im new to linux ubuntu but from what I have experienced so far I have already switched completely over. What I'm having a problem with is the actual networking of computers. I have a laptop with ubuntu Jaunty x64 and I'm trying to share my wired internet connection with my roommate via my wireless. I have an aspire 5100 with a broadcom built in wirless card. I've tried multiple tutorials of which none have worked to include installing dnsmasq and another one I cant seem to remember. I know that DHCP doesnt seem to be working because my buddy doesnt get any IP address from my laptop, just a169.x.x.x number. I've also tried firestarter with no luck. I have also tried ufw, but that I gather is more for an actual firewall vs gateway enabling. Remember I'm new and Im trying to get my brain around how things work with this great new world I've discovered. Here are my results from ifconfig, iwconfig, and lspci. I think I somehow jacked up iptables or dhcp or something, is there anyway I can reset this to how it was before I started this? I dont want to have to reinstall everything, I'm in Iraq an the internet is extremly slow, I was lucky enough to receive the free disk ubuntu offers. Thanks for any help you can give.

Luis

```
luis@luis-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:d9:52:aa  
          inet addr:10.30.51.231  Bcast:10.30.51.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fed9:52aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9592995 (9.5 MB)  TX bytes:1509343 (1.5 MB)
          Interrupt:21 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:19:7e:78:50:fd  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fe78:50fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:482
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:62 (62.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5445 (5.4 KB)  TX bytes:5445 (5.4 KB)

luis@luis-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"EASL"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: B6:42:58:1D:42:2A   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          
pan0      no wireless extensions.

luis@luis-laptop:~$ sudo lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
luis@luis-laptop:~$ 
```

---

### Post by b1driver on 2009-09-21
Is there any more info I can post that would be needed to solve this problem? How about just a tip on how I can reset all my network files so I can try again? I know this sounds petty but I really need some help with this, I dont want to mess something up and I dont want to have to reload everything. I appreciate any help I can get. Thanks.

---

### Post by b1driver on 2009-09-21
Here is the iptables -L result:

```
luis@luis-laptop:~$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  127.0.0.0/8          anywhere            LOG level warning 
DROP       all  --  127.0.0.0/8          anywhere            
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  10.42.43.0/24        anywhere            
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
LOG        all  --  10.42.43.0/24        anywhere            LOG level warning 
DROP       all  --  10.42.43.0/24        anywhere            
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  anywhere             10.30.51.231        
ACCEPT     all  --  anywhere             10.30.51.255        
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  10.42.43.0/24        anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LOG        all  --  anywhere             10.42.43.0/24       LOG level warning 
DROP       all  --  anywhere             10.42.43.0/24       
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  anywhere             10.42.43.0/24       
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
LOG        all  --  anywhere             10.42.43.0/24       LOG level warning 
DROP       all  --  anywhere             10.42.43.0/24       
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  10.30.51.231         anywhere            
ACCEPT     all  --  10.30.51.255         anywhere            
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain ufw-after-forward (0 references)
target     prot opt source               destination         

Chain ufw-after-input (0 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-after-output (0 references)
target     prot opt source               destination         

Chain ufw-before-forward (0 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-before-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (0 references)
target     prot opt source               destination         

Chain ufw-reject-input (0 references)
target     prot opt source               destination         

Chain ufw-reject-output (0 references)
target     prot opt source               destination         

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination  
```

---

