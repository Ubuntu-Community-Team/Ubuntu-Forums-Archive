---
title: "Wireless not working after update"
date: 2013-06-02
forum: Networking &amp; Wireless
---

### Post by Azpedey on 2013-06-02
I used Update Manager yesterday (since message said there were updates) and now I am unable to get the wireless to work.  Ethernet is ok.
The one thing that was changed during the update was the kernal version as listed below.  If I boot to the previous kernal, everything works fine.  Hopefully I have most of what is needed from following the "Howto post a wireless issue".

```
Computer:  HP Pavillion Model s5730y Desktop
 O.S:  Ubuntu 10.04.4
 Processor:  AMD Phenom II 511
  
 **Conditions prior to update via Update Manager (wireless working normally):**
 kernal: 2.6.32-38-generic x86_64  

 azpedey@HPPavillion:~$ lspci  
 02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe  
 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)  
 
  azpedey@HPPavillion:~$ lspci -nn | grep RaLink  
 02:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]  
 
  azpedey@HPPavillion:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 64:31:50:32:9b:f9   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:26 Base address:0xe000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)  
 
  ra0       Link encap:Ethernet  HWaddr 1c:65:9d:a7:ef:38   
           inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::1e65:9dff:fea7:ef38/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:25121 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:3521 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:6461532 (6.4 MB)  TX bytes:422091 (422.0 KB)  
           Interrupt:18  
  
 azpedey@HPPavillion:~$ iwconfig  
 lo        no wireless extensions.  
  
 eth0      no wireless extensions.  
  
 ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"  
           Mode:Managed  Frequency=2.437 GHz  Access Point: 00:14:BF:7C:24:A6    
           Bit Rate=54 Mb/s    
           RTS thrff   Fragment thrff  
           Link Quality=100/100  Signal level:-31 dBm  Noise level:-63 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 azpedey@HPPavillion:~$ sudo lshw -C network  
 [sudo] password for azpedey:  
   *-network                
        description: Wireless interface  
        product: RT3090 Wireless 802.11n 1T/1R PCIe  
        vendor: RaLink  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: ra0  
        version: 00  
        serial: 1c:65:9d:a7:ef:38  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.1.3 ip=192.168.1.102 latency=0 multicast=yes wireless=Ralink STA  
        resources: irq:18 memory:feaf0000-feafffff  
   *-network  
        description: Ethernet interface  
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logical name: eth0  
        version: 05  
        serial: 64:31:50:32:9b:f9  
        size: 10MB/s  
        capacity: 100MB/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s  
        resources: irq:26 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff(prefetchable)  
 
  azpedey@HPPavillion:~$ lsb_release -d  
 Description:    Ubuntu 10.04.4 LTS  
 
  azpedey@HPPavillion:~$ uname -mr  
 2.6.32-38-generic x86_64  
 azpedey@HPPavillion:~$ sudo /etc/init.d/networking restart  
  * Reconfiguring network interfaces...                                          Ignoring unknown interface ra0=ra0.  
                                                                          [ OK ]  
 
  azpedey@HPPavillion:~$ sudo iwlist scan 
 [sudo] password for azpedey:  
 lo        Interface doesn't support scanning.  
 
  eth0      Interface doesn't support scanning.  
 
  ra0       Scan completed :  
           Cell 01 - Address: 00:14:BF:7C:24:A6  
                     Protocol:802.11b/g  
                     ESSID:"xxxxxxxx" 
                     Mode:Managed  
                     Frequency:2.437 GHz (Channel 6)  
                     Quality:100/100  Signal level:-31 dBm  Noise level:-92 dBm  
                     Encryption keyn  
                     Bit Rates:54 Mb/s  
                     IE: WPA Version 1  
                         Group Cipher : TKIP  
                         Pairwise Ciphers (1) : TKIP  
                         Authentication Suites (1) : PSK  
           Cell 02 - Address: 98:FC:11:90:7D:B8  
                     Protocol:802.11b/g/n  
                     ESSID:"grannyof9" 
                     Mode:Managed  
                     Frequency:2.412 GHz (Channel 1)  
                     Quality:42/100  Signal level:-73 dBm  Noise level:-68 dBm  
                     Encryption keyn  
                     Bit Rates:144 Mb/s  
                     IE: WPA Version 1  
                         Group Cipher : TKIP  
                         Pairwise Ciphers (2) : CCMP TKIP  
                         Authentication Suites (1) : PSK  
                     IE: IEEE 802.11i/WPA2 Version 1  
                         Group Cipher : TKIP  
                         Pairwise Ciphers (2) : CCMP TKIP  
                         Authentication Suites (1) : PSK  
                     IE: Unknown: DD0E0050F204104A0001101044000102  
 
  **Conditions post-update (wireless not functioning):**
 
  kernal:  2.6.32-47-generic x86_64  
  
 azpedey@HPPavillion:~$ lspci  
 02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe  
 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)  
 azpedey@HPPavillion:~$ lspci -nn | grep RaLink  
 02:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]  
 
  azpedey@HPPavillion:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 64:31:50:32:9b:f9   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:26 Base address:0x6000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:16 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:16 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:1104 (1.1 KB)  TX bytes:1104 (1.1 KB)  
 
  azpedey@HPPavillion:~$ iwconfig  
 lo        no wireless extensions.  
 
  eth0      no wireless extensions.  
 
  azpedey@HPPavillion:~$ sudo lshw -C network  
 [sudo] password for azpedey:  
   *-network UNCLAIMED      
        description: Network controller  
        product: RT3090 Wireless 802.11n 1T/1R PCIe  
        vendor: RaLink  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        version: 00  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list  
        configuration: latency=0  
        resources: memory:feaf0000-feafffff  
   *-network  
        description: Ethernet interface  
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logical name: eth0  
        version: 05  
        serial: 64:31:50:32:9b:f9  
        size: 10MB/s  
        capacity: 100MB/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s  
        resources: irq:26 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff(prefetchable)  
 
  azpedey@HPPavillion:~$ lsb_release -d  
 Description:    Ubuntu 10.04.4 LTS  
 
  azpedey@HPPavillion:~$ uname -mr  
 2.6.32-47-generic x86_64  
 
  azpedey@HPPavillion:~$ sudo /etc/init.d/networking restart  
  * Reconfiguring network interfaces...                                   [ OK ]  
 
  azpedey@HPPavillion:~$ sudo iwlist scan 
 lo        Interface doesn't support scanning.  
 
  eth0      Interface doesn't support scanning.  
 
  I have tried the following from the forum:
 
  quote:
as root (or sudo before each line):
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart
 
  No change.
 
  Per chili555 on forum:   
  
 azpedey@HPPavillion:~$ rfkill list all 
 azpedey@HPPavillion:~$ rfkill unblock all 
 azpedey@HPPavillion:~$ rfkill list all 
  
 azpedey@HPPavillion:~$ dmesg | grep -i RT3 
 [    9.863148] rt3090sta: disagrees about version of symbol module_layout 
 azpedey@HPPavillion:~$ dmesg | grep -i RT2 
 
  From same forum, tried following:

  azpedey@HPPavillion:~$ ls /etc/Wireless/RT2860STA 
 RT2860STA.dat 
 azpedey@HPPavillion:~$ ls /etc/Wireless 
 RT2860STA

```

I have tried to provide what has been asked for on other posts.  I'm not great using Terminal but will sure try to get anything else that you need.  Thanks

---

### Post by chili555 on 2013-06-02
Did you compile the driver from source? When a newer kernel version is installed, you must recompile:```
cd Desktop/RT3090file  [COLOR="#FF0000"]<--or wherever you have the files[/COLOR]
sudo su
make clean
make
make install
exit
```Reboot and it should be working.

---

### Post by Azpedey on 2013-06-02
Thanks for the fast response.  No, I did not compile the driver.  I downloaded and installed "rt3090-dkms_2.3.1.3-OubuntuO~ppa0_all.deb" prior to the last update.  That download is still on the computer.  I haven't done anything with it so I would need guidance as to what to do; I presume extract the files and then use the information you sent to get a particular file(s) compiled.

---

### Post by chili555 on 2013-06-02
I would simply try to install it; either it will install as expected or a hopefully informative error will be thrown:```
cd Desktop [COLOR="#FF0000"]<--or wherever the deb is located[/COLOR]
sudo dpkg -i rt3090*.deb
```If there is an error, post it here and we'll try to fix it.

---

### Post by ajgreeny on 2013-06-02
I presume you are aware that 10.04 is no longer supported, so any updates etc etc will now not be available in the normal way. I am not sure if this is the reason for your problem, but nevertheless I feel you should be made aware of the situation.

---

### Post by Azpedey on 2013-06-02
chili555 - That took care of the problem.  Thanks so much.  Based on your first reply, am I to assume that this same procedure will have to be performed each time Update Manager installs an updated kernal?

ajgreeny - Thanks, I was not aware of that.  The computer I am working on is for my sister, and she prefers the look and action of the 10.04 desktop compared to newer versions.  Personally, I use 12.04 and have not had too many issues, even though at 70+ I'm not as quick as I was years ago.

---

### Post by chili555 on 2013-06-02
> **Azpedey said:**
> chili555 - That took care of the problem.  Thanks so much.  Based on your first reply, am I to assume that this same procedure will have to be performed each time Update Manager installs an updated kernal?

A deb file installed along with dkms should not require re-installation at each new kernel update. However, things don't always go as expected. Glad it's working!

Please mark the thread Solved: 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

