---
title: "Wireless problem on 11.04"
date: 2012-05-08
forum: Networking &amp; Wireless
---

### Post by Govas on 2012-05-08
[B]Can't install wireless drivers.Please help!
[/B]

---

### Post by chili555 on 2012-05-08
Can't help without more information! [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Govas on 2012-05-08
laptop Turbo X
Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express

Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3776 (3.7 KB)  TX bytes:3776 (3.7 KB)

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

PCI (sysfs)  
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 48:5d:60:c2:22:bc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-15-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f1900000-f190ffff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: e0:69:95:10:be:f4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.55 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:f1800000-f183ffff ioport:c000(size=128)

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

uname -mr
2.6.38-15-generic x86_64

---

### Post by iMurshaq on 2012-05-08
Have you tried "sudo apt-get update"? I know it's simple but that command has fixed so many problems for me.

---

### Post by Govas on 2012-05-08
the output 

sudo apt-get update
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty InRelease
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates InRelease   
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty Release.gpg             
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates Release.gpg     
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty Release                 
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates Release                                                        
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                                                   
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/main Sources                                                           
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/restricted Sources                              
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/universe Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/multiverse Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/main amd64 Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/restricted amd64 Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/universe amd64 Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/multiverse amd64 Packages
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/main TranslationIndex                       
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/multiverse TranslationIndex                 
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/restricted TranslationIndex
&#934;&#941;&#961;&#949;:1 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]                   
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/universe TranslationIndex                   
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/main Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/restricted Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/universe Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/multiverse Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/main amd64 Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/restricted amd64 Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/universe amd64 Packages
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/multiverse amd64 Packages
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/main TranslationIndex
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/restricted TranslationIndex
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/universe TranslationIndex
&#934;&#941;&#961;&#949;:2 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/main Translation-el [64,1 kB]                
&#934;&#941;&#961;&#949;:3 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [39,8 kB]                     
&#934;&#941;&#961;&#949;:4 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/multiverse Translation-el [21,8 kB]    
&#934;&#941;&#961;&#949;:5 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/restricted Translation-el [2743 B]
&#934;&#941;&#961;&#949;:6 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/universe Translation-el [4630 B]
&#934;&#941;&#961;&#949;:7 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [95,9 kB]                                   
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/main Translation-el_GR         
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/main Translation-en            
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/multiverse Translation-el_GR
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/multiverse Translation-en
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/restricted Translation-el_GR
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/restricted Translation-en         
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/universe Translation-el_GR        
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty/universe Translation-en           
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/main Translation-el_GR
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/main Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/main Translation-en       
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/multiverse Translation-el_GR
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/multiverse Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/multiverse Translation-en
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/restricted Translation-el_GR
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/restricted Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/restricted Translation-en
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/universe Translation-el_GR                                
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/universe Translation-el                                   
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) natty-updates/universe Translation-en                                   
&#934;&#941;&#961;&#949;:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [1292 B]                                 
&#934;&#941;&#961;&#949;:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [25,1 kB]
&#934;&#941;&#961;&#949;:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [1638 B]
&#934;&#941;&#961;&#949;:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages [306 kB]
&#934;&#941;&#961;&#949;:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages [4790 B]
&#934;&#941;&#961;&#949;:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages [82,4 kB]
&#934;&#941;&#961;&#949;:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages [3554 B]
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-el_GR
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-el_GR
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-el_GR
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-el_GR
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
&#924;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#974;&#952;&#951;&#954;&#945;&#957; 654 kB &#963;&#949; 5s (124 kB/s)
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... completed

---

### Post by chili555 on 2012-05-08
May I see:```
rfkill list all
```Thanks.

---

### Post by Govas on 2012-05-08
rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by chili555 on 2012-05-08
> 1: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]This strongly suggests the wireless switch is set to OFF. Can you switch it on? What kind and model computer is it?

---

### Post by Govas on 2012-05-08
wifi led on modem is switched to on

wifi led on my com is switched to off

---

### Post by chili555 on 2012-05-08
> **Govas said:**
> wifi led on modem is switched to on

wifi led on my com is switched to offWhat kind and model computer is it?

---

### Post by Govas on 2012-05-08
Turbo-X laptop windows 7 intel pentium

---

### Post by Govas on 2012-05-08
Turbo-X laptop intel pentium windows 7

---

### Post by chili555 on 2012-05-08
Isn't there a wireless switch or key combination that switches the wireless on and off? For instance, on my Lenovo, there are both a switch on the side and also the key combination Fn+F5. Do you have something like that?

---

### Post by Govas on 2012-05-08
OK MAN THANKS SO MUCH Fn + F2!;)

---

### Post by mörgæs on 2012-05-09
If it works, please mark the thread 'solved'.

Also, double-posting is not welcome. I have closed your other thread.

---

