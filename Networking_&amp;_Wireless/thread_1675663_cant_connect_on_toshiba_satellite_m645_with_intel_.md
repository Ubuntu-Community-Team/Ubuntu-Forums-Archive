---
title: "cant connect on toshiba satellite m645 with intel 802.11 a/g/n wireless LAN"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by resonador on 2011-01-25
I cant seem to understand what happens to my wifi networking, i just installed ubuntu 10.10 today (completely erasing windows) on my toshiba satellite m645. Seems like my wireless card (the specs say its intel 802.11a/g/n wireless LAN) will only randomly detect the available networks or will connect only for a few seconds just after i just turned it on, then it will disconnect. Wired works perfect. I will appreciate your ideas.

---

### Post by resonador on 2011-01-26
Still having the same problem today. I made a little n00b testing. As i  first turned my laptop on i was very close to the router, right next to  it actually and the system started and connected to the internet without  trouble, i went to the terminal and got for the "nm-tool" "sudo  iwconfig" and "sudo lshw":
                     p { margin-bottom: 0.08in; }  
  
nm-tool  
  Device: wlan0  [Auto INFINITUM2047] ------------------------------------------ 
   Type:              802.11 WiFi 
   Driver:            iwlagn 
   State:             connected 
   Default:           yes 
   HW Address:        00:23:15:84:60:38 
  
   Capabilities: 
     Speed:           54 Mb/s 
  
   Wireless Properties 
     WEP Encryption:  yes 
     WPA Encryption:  yes 
     WPA2 Encryption: yes 
  
   Wireless Access Points (* = current AP) 
     INFINITUMc9bf:   Infra, 00:25:68:C2:09:DE, Freq 2462 MHz, Rate 54 Mb/s, Strength 31 WEP 
     *INFINITUM2047:  Infra, 00:19:E4:8D:3D:49, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WEP 
 

 sudo iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 wlan0     IEEE 802.11abg  ESSID:"INFINITUM2047"   
           Mode:Managed  Frequency:2.462 GHz  Access Point: 00:19:E4:8D:3D:49    
           Bit Rate=54 Mb/s   Tx-Power=15 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off 
           Encryption key:7424-9112-39 
           Power Management:off 
           Link Quality=70/70  Signal level=-23 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 

 sudo lshw
 

  *-network 
                 description: Wireless interface 
                 product: Centrino Advanced-N + WiMAX 6250 
                 vendor: Intel Corporation 
                 physical id: 0 
                 bus info: pci@0000:06:00.0 
                 logical name: wlan0 
                 version: 5f 
                 serial: 00:23:15:84:60:38 
                 width: 64 bits 
                 clock: 33MHz 
                 capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
                 configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-22-generic firmware=9.201.4.1 build 24255 ip=192.168.1.67 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg 
                 resources: irq:47 memory:d4600000-d4601fff
 



Then  i moved farther from the router, but only around three feet, as i  expected my connection failed and started asking for the net's password,  i went to the terminal and typed the same while it was trying to  connect:


                      p { margin-bottom: 0.08in; }  

 nm-tool
  Device: wlan0  [Auto INFINITUM2047] ------------------------------------------ 
   Type:              802.11 WiFi 
   Driver:            iwlagn 
   State:             connecting (configuring) 
   Default:           no 
   HW Address:        00:23:15:84:60:38 
  
   Capabilities: 
  
   Wireless Properties 
     WEP Encryption:  yes 
     WPA Encryption:  yes 
     WPA2 Encryption: yes 
  
   Wireless Access Points  
     INFINITUM2047:   Infra, 00:19:E4:8D:3D:49, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WEP
 

 sudo iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 wlan0     IEEE 802.11abg  ESSID:off/any   
           Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated    
           Tx-Power=15 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off 
           Encryption keyoff 
           Power Management:on 
 

 sudo lshw
 *-network 
                 description: Wireless interface 
                 product: Centrino Advanced-N + WiMAX 6250 
                 vendor: Intel Corporation 
                 physical id: 0 
                 bus info: pci@0000:06:00.0 
                 logical name: wlan0 
                 version: 5f 
                 serial: 00:23:15:84:60:38 
                 width: 64 bits 
                 clock: 33MHz 
                 capabilities: pm msi pciexpress cap_list ethernet physical wireless 
                 configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-22-generic firmware=9.201.4.1 build 24255 latency=0 link=no multicast=yes wireless=IEEE 802.11abg 
                 resources: irq:47 memory:d4600000-d4601fff 
 



After a few minutes of connection trial, i got the message that i was definitely disconnected and went through the same again:


                      p { margin-bottom: 0.08in; }  nm-tool
 Device: wlan0 ---------------------------------------------------------------- 
   Type:              802.11 WiFi 
   Driver:            iwlagn 
   State:             disconnected 
   Default:           no 
   HW Address:        00:23:15:84:60:38 
  
   Capabilities: 
  
   Wireless Properties 
     WEP Encryption:  yes 
     WPA Encryption:  yes 
     WPA2 Encryption: yes 
  
   Wireless Access Points  
     INFINITUM2047:   Infra, 00:19:E4:8D:3D:49, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WEP
 

 

 sudo iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 wlan0     IEEE 802.11abg  ESSIDoff/any   
           Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated    
           Tx-Power=15 dBm    
           Retry  long limit:7   RTS throff   Fragment throff 
           Encryption keyoff 
           Power Managementon
 

 sudo lshw
 *-network 
                 description: Wireless interface 
                 product: Centrino Advanced-N + WiMAX 6250 
                 vendor: Intel Corporation 
                 physical id: 0 
                 bus info: pci@0000:06:00.0 
                 logical name: wlan0 
                 version: 5f 
                 serial: 00:23:15:84:60:38 
                 width: 64 bits 
                 clock: 33MHz 
                 capabilities: pm msi pciexpress cap_list ethernet physical wireless 
                 configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-22-generic firmware=9.201.4.1 build 24255 latency=0 link=no multicast=yes wireless=IEEE 802.11abg 
                 resources: irq:47 memory:d4600000-d4601fff




PLEASE HELP!

---

### Post by gordintoronto on 2011-01-26
Change the SSID of your router to lower case.

---

