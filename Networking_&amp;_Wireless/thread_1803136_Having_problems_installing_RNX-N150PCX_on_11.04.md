---
title: "Having problems installing RNX-N150PCX on 11.04"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by initialx on 2011-07-12
Hey everyone!!! I'm a noob to Ubuntu so my apologies in the possible headaches and thank you in advance for any help.
I bought a Rosewill RNX-N150PCx on online because I saw reviews saying that it woks on Ubuntu and I'm having problems installing it.  I've spent about a week working on it, but no luck.  So far, I've tried doing what this thread says: 
[http://ubuntuforums.org/showthread.php?t=1608095&highlight=rnx-n150pcx](http://ubuntuforums.org/showthread.php?t=1608095&highlight=rnx-n150pcx)
got a little confused on how to install it so i went to this thread to see how others are installing it: 
[http://ubuntuforums.org/showthread.php?t=1801363](http://ubuntuforums.org/showthread.php?t=1801363)
Now im at a complete loss and in NEED of help.  
Here are some info i can supply right now
Im running 11.04 with a Rosewill RNX-N150PCx
the tower is a Dell Dimension E521
lshw -C network
```
 richard@Richard:~$ sudo lshw -C network
sudo password for richard: 
PCI (sysfs)  
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:84:30:fd
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:19 memory:fdbfe000-fdbfffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 9
       bus info: pci@0000:04:09.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=2 maxlatency=4 mingnt=2
       resources: memory:fdbe0000-fdbeffff
richard@Richard:~$ 
```lspci
```
richard@Richard:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
04:09.0 Network controller: Ralink corp. Device 3060
```iwconfig
```
richard@Richard:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```ifconfig
```

richard@Richard:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8b:84:30:fd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2016 (2.0 KB)  TX bytes:2016 (2.0 KB)

richard@Richard:~$ 
```and my "enable wireless" button on the top right corner isn't there anymore if its worth anything.  Thanks again to anyone who is willing to help!!!

---

### Post by chili555 on 2011-07-13
Let's see where you are so far. Please open a terminal and run and post:```
modinfo rt3562sta
lsmod | grep rt3
```If there is no listing after the second command, then do:```
sudo modprobe rt3563sta
```Now is your wireless working? Are there any error or warning messages when you do any of those commands?

---

### Post by initialx on 2011-07-13
no luck so far but here's the script you asked for...
```
richard@Richard:~$ modinfo rt3562sta
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt3562sta.ko
version:        2.4.1.1
srcversion:     4D386FD1EDC7B95F07E2F57
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)
richard@Richard:~$ lsmod | grep rt3
richard@Richard:~$ sudo modprobe rt3563sta
[sudo] password for richard: 
FATAL: Module rt3563sta not found.
richard@Richard:~$ 
```

---

### Post by chili555 on 2011-07-13
> richard@Richard:~$ sudo modprobe rt356[COLOR="Red"]3[/COLOR]sta
[sudo] password for richard: 
FATAL: Module rt3563sta not found.Please try as I meant, not as I said! I'm sorry about that:```
sudo modprobe rt356[COLOR="Red"]2[/COLOR]sta
iwconfig
```Now I'm going to clean my old, bent trifocals...

---

### Post by initialx on 2011-07-13
I think its up and running now but i can't seem to get a list of connections nor my "enable wireless" button on the top right corner to work... ```
 richard@Richard:~$ modinfo rt3562sta 
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt3562sta.ko 
version:        2.4.1.1 
srcversion:     4D386FD1EDC7B95F07E2F57 
alias:          pci:v00001432d00007722sv*sd*bc*sc*i* 
alias:          pci:v00001432d00007711sv*sd*bc*sc*i* 
alias:          pci:v00001814d00003592sv*sd*bc*sc*i* 
alias:          pci:v00001814d00003060sv*sd*bc*sc*i* 
alias:          pci:v00001814d00003562sv*sd*bc*sc*i* 
alias:          pci:v00001814d00003062sv*sd*bc*sc*i* 
alias:          pci:v00001432d00007768sv*sd*bc*sc*i* 
alias:          pci:v00001432d00007748sv*sd*bc*sc*i* 
alias:          pci:v00001432d00007738sv*sd*bc*sc*i* 
alias:          pci:v00001432d00007727sv*sd*bc*sc*i* 
alias:          pci:v00001432d00007758sv*sd*bc*sc*i* 
alias:          pci:v00001432d00007728sv*sd*bc*sc*i* 
alias:          pci:v00001432d00007708sv*sd*bc*sc*i* 
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i* 
alias:          pci:v00001814d00000781sv*sd*bc*sc*i* 
alias:          pci:v00001814d00000701sv*sd*bc*sc*i* 
alias:          pci:v00001814d00000681sv*sd*bc*sc*i* 
alias:          pci:v00001814d00000601sv*sd*bc*sc*i* 
depends:         
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686  
parm:           mac:rt28xx: wireless mac addr (charp) 
richard@Richard:~$ lsmod | grep rt3 
richard@Richard:~$ sudo modprobe rt3562sta 
[sudo] password for richard:  
richard@Richard:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
ra0       Ralink STA   
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0 
 
richard@Richard:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:18:8b:84:30:fd   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:19  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:2016 (2.0 KB)  TX bytes:2016 (2.0 KB) 
 
richard@Richard:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA" 
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s    
          RTS thr:off   Fragment thr:off 
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
richard@Richard:~$ iwlist scan 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
ra0       Scan completed : 
          Cell 01 - Address: 00:26:50:F1:CF:A9 
                    Protocol:802.11b/g 
                    ESSID:"2WIRE021" 
                    Mode:Managed 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality:5/100  Signal level:-88 dBm  Noise level:-83 dBm 
                    Encryption key:on 
                    Bit Rates:54 Mb/s 
 
richard@Richard:~$  

```

---

### Post by chili555 on 2011-07-14
It scans and sees a network, presumably yours, although I am troubled by this:> ra0       Scan completed : 
          Cell 01 - Address: 00:26:50:F1:CF:A9 
                    Protocol:802.11b/g 
                    ESSID:"2WIRE021" 
                    Mode:Managed 
                    Frequency:2.437 GHz (Channel 6) 
                    [COLOR="Red"]Quality:5/100[/COLOR]  Signal level:-88 dBm  Noise level:-83 dBm 
                    Encryption key: on 
                    Bit Rates:54 Mb/s I'm not sure that's at all accurate because if it was only 5% as strong as possible, I doubt scanning would even see it at all. Let's take steps to load rt3562sta automatically on boot:```
sudo su
echo rt3562sta >> /etc/modules
exit
```Now reboot and let's see what happens on boot in the message logs:```
dmesg | grep -e ra0 -e rt3
```Thanks.

---

### Post by initialx on 2011-07-14
here's the results of the boot 
```
richard@Richard:~$ dmesg | grep -e ra0 -e rt3 
[   10.607562] rt3562sta: module license 'unspecified' taints kernel. 
[   10.644936] The name of the new ra interface is ra0... 
richard@Richard:~$ 
``` 
sorry if it takes me a while to respond and thanks for the help!!!

---

### Post by chili555 on 2011-07-14
Now when you click the Network Manager icon, do you see your network 2WIRE021? Can you click it and try to connect? Are you asked for the encryption key? Does it try?

---

### Post by initialx on 2011-07-14
it doesn't show up... I also tried connecting to it manually but that didn't work either...
[http://i130.photobucket.com/albums/p242/xxplosivedrummer/Screenshot-1.png](http://i130.photobucket.com/albums/p242/xxplosivedrummer/Screenshot-1.png)

---

### Post by chili555 on 2011-07-15
Let's do some deep exploratory surgery. We are going to create a text document, zip it and post it as as an attachment to your reply. Please reboot and do:```
dmesg > init.txt
lspci -nn | grep 0280 >> init.txt
lsmod >> init.txt
sudo cat /var/log/syslog | grep -e rt2 -e rt3 -e ra0 >> init.txt
zip init.zip init.txt
```The file init.zip will be found in your user directory. Please attach it to your reply using the paperclip tool at the top of the reply box. Thanks.

---

### Post by initialx on 2011-07-15
[ATTACH]197529[/ATTACH]
here you go...

---

### Post by chili555 on 2011-07-15
I am a little concerned about this is syslog:> <warn> /sys/devices/virtual/net/ra0: couldn't determine device driver; ignoring...I'm not completely sure what it means, but it sounds ugly. Open the folder that was created when you extracted the downloaded tar.gz and look in os > linux and open the file config.mk with a text editor. Please confirm that you set:```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=[COLOR="Red"]y[/COLOR]

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="Red"]y[/COLOR]
```If either or both of these are =n, we need to change them and rebuild the module:```
cd Desktop/DPO_RT3562
```Press Tab and the remainder will fill in automatically. Substitute the location of your file, if it's not on your desktop. Now we rebuild:```
sudo su
make clean
make
make install
rmmod -f rt3562sta
modprobe rt3562sta
exit
```Any improvement?

---

### Post by initialx on 2011-07-15
got the connection up... THANK YOU!!! you the man chili

---

### Post by chili555 on 2011-07-15
Awesome! Glad it's working.

---

