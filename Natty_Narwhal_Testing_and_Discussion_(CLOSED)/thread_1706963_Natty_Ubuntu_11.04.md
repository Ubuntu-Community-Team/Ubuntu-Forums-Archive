---
title: "Natty Ubuntu 11.04"
date: 2011-03-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by wcipolli on 2011-03-14
Hi, have the intel HM55 graphics which only will run this version, I've tried 6 others. I got it running, it allows me to enable wireless but wireless networks is greyed out and none show up. I have a broadcom 4313 wireless card.

Please let me know what I can do, I tried a few things listed on the forum to no avail.

Thanks in advanced!

---

### Post by wcipolli on 2011-03-14
update
```

billy@wc3-LENOVO-Ideapad-U160:~$ sudo apt-get update
[sudo] password for billy: 
Ign http://security.ubuntu.com natty-security InRelease
Ign http://extras.ubuntu.com natty InRelease                        
Ign http://archive.canonical.com natty InRelease                     
Get:1 http://security.ubuntu.com natty-security Release.gpg [198 B]  
Get:2 http://extras.ubuntu.com natty Release.gpg [72 B]                                               
Get:3 http://archive.canonical.com natty Release.gpg [198 B]                                        
Get:4 http://security.ubuntu.com natty-security Release [23.2 kB]                                     
Get:5 http://extras.ubuntu.com natty Release [39.8 kB]                                             
Get:6 http://archive.canonical.com natty Release [5,916 B]                                                    
Ign http://us.archive.ubuntu.com natty InRelease                                                                        
Ign http://us.archive.ubuntu.com natty-updates InRelease                                                                
Get:7 http://us.archive.ubuntu.com natty Release.gpg [198 B]                                      
Hit http://archive.canonical.com natty/partner Sources                                                            
Hit http://security.ubuntu.com natty-security/main Sources                     
Get:8 http://us.archive.ubuntu.com natty-updates Release.gpg [198 B]           
Hit http://archive.canonical.com natty/partner i386 Packages                                                    
Ign http://archive.canonical.com natty/partner TranslationIndex                                      
Hit http://security.ubuntu.com natty-security/restricted Sources                                     
Hit http://security.ubuntu.com natty-security/universe Sources       
Hit http://security.ubuntu.com natty-security/multiverse Sources     
Hit http://security.ubuntu.com natty-security/main i386 Packages     
Hit http://security.ubuntu.com natty-security/restricted i386 Packages
Hit http://security.ubuntu.com natty-security/universe i386 Packages 
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages
Ign http://security.ubuntu.com natty-security/main TranslationIndex  
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Get:9 http://us.archive.ubuntu.com natty Release [39.8 kB]           
Hit http://extras.ubuntu.com natty/main Sources                                                     
Ign http://security.ubuntu.com natty-security/universe TranslationIndex                             
Hit http://extras.ubuntu.com natty/main i386 Packages                                                
Ign http://extras.ubuntu.com natty/main TranslationIndex                                             
Get:10 http://us.archive.ubuntu.com natty-updates Release [23.2 kB]                                                 
Hit http://us.archive.ubuntu.com natty/main Sources                                                   
Hit http://us.archive.ubuntu.com natty/restricted Sources                                  
Hit http://us.archive.ubuntu.com natty/universe Sources              
Hit http://us.archive.ubuntu.com natty/multiverse Sources            
Hit http://us.archive.ubuntu.com natty/main i386 Packages            
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty/universe i386 Packages        
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com natty/main TranslationIndex
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://archive.canonical.com natty/partner Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex     
Hit http://us.archive.ubuntu.com natty-updates/main Sources                                
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources                          
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                            
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources                          
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages                          
Ign http://archive.canonical.com natty/partner Translation-en                              
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages                    
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex 
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://extras.ubuntu.com natty/main Translation-en_US            
Ign http://security.ubuntu.com natty-security/main Translation-en_US
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://extras.ubuntu.com natty/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Fetched 133 kB in 2s (48.8 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

lspci
```

billy@wc3-LENOVO-Ideapad-U160:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
03:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


```


iwconfig
```

billy@wc3-LENOVO-Ideapad-U160:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:244
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


```

ifconfig
```

billy@wc3-LENOVO-Ideapad-U160:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr f0:de:f1:0e:e6:ee  
          inet addr:10.101.106.34  Bcast:10.101.107.255  Mask:255.255.254.0
          inet6 addr: fe80::f2de:f1ff:fe0e:e6ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8914 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:6674373 (6.6 MB)  TX bytes:2107019 (2.1 MB)
          Interrupt:41 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)



```

Figure I'd give you all something to work off of.

---

### Post by kerry_s on 2011-03-14
see this thread:
[http://ubuntuforums.org/showthread.php?t=1424280](http://ubuntuforums.org/showthread.php?t=1424280)

---

