---
title: "HP mini netbook 110-3000 no wireless connection  ubuntu 11.04"
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by hocke4me on 2011-06-25
:(     Newbie

I cannot get my wireless to work.  It appears to work when connected to wirelessnetwork with no encrytion.  Tested and  it works just fine.  However when encrypted with WPA/WPA2 personnel, it will not link.  The card appears to be on, and no blocks.  I hope I'm close.  searched through a bunch of post, and tried the ideas but still not working.  Updated everything, I hope.   Please help.  FYI the LAN connection works just fine for me, so I can follow commands.  Below is enough info on what I have to hopefully get some help.


et@et-HP-Mini-110-3000:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:cc:51:46:f8  
          inet addr:192.168.0.143  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ccff:fe51:46f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19791 (19.7 KB)  TX bytes:10173 (10.1 KB)
          Interrupt:42 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:6b:90:7b  
          inet6 addr: fe80::76f0:6dff:fe6b:907b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:8607 (8.6 KB)

et@et-HP-Mini-110-3000:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
et@et-HP-Mini-110-3000:~$ sudo apt-get update
[sudo] password for et: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty InRelease                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates InRelease             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg            
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty Release.gpg                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates Release.gpg           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty Release                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates Release                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main Sources                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted Sources                                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe Sources                                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main i386 Packages            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted i386 Packages      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe i386 Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse i386 Packages                                 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main TranslationIndex                                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse TranslationIndex                              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted TranslationIndex                              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe TranslationIndex                                                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main Sources                                                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted Sources    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Sources                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse Sources                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main i386 Packages                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted i386 Packages                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse i386 Packages                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main TranslationIndex                       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted TranslationIndex                 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe TranslationIndex                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main Translation-en_CA                              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted Translation-en_CA                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_CA                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_CA                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_CA            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_CA
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 72 B in 3s (23 B/s)                              
Reading package lists... Done
et@et-HP-Mini-110-3000:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
et@et-HP-Mini-110-3000:~$

---

### Post by chili555 on 2011-06-25
Please see my reply on your other thread.

---

### Post by hocke4me on 2011-06-25
Did as suggested under thread ** Atheros wireless not working on Natty**.  Setting the wireless to WPA only worked perfectly.  Wirelessly typing and love it.  See reply 25/6.

Thanks again chil555:D



> **chili555 said:**
> Please see my reply on your other thread.

---

