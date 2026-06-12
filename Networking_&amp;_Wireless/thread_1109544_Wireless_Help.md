---
title: "Wireless Help"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by bsta520 on 2009-03-28
i have ubuntu 8.10 and i dont see where i can "scan" wireless networks, only where i can manually enter the information about it.  the walk through that ubuntu provides isnt correct unless im not seeing something cuz it says to click on network ... but the only thing is network settings or another word for settings i cant remember... but if someone could explain a better walk through id appreciate it... if i have to enter the information from my network do i obtain that information from typing [http://196.168.1.1](http://196.168.1.1) in a web browser???    

also anothing thing when ubuntu is loading the bar stops and i have to press and hold a key whether it be space bar or esc... both work ... for it to continue loading... do i need to reinstall or what cuz this is a pain if i just want to turn on the computer and leave it.. i have to wait and hold a key while it loads..

Thanks a lot and sorry if any of these were posted already i couldnt find the exact answers

---

### Post by mikewhatever on 2009-03-28
You should be able to see the available wireless networks by clicking on the network manager icon on the top panel. Network settings are managed by right clicking on the same icon and selecting 'Edit Connections...'.

192.168.1.1 could be your router's gateway or default rout, but it depends on the router. In my case, it's a different address. Entering the default rout address into the address bar should get you access to the router, but if that's what you mean by obtaining your network info. On the second thought, don't you already know it?

---

### Post by pytheas22 on 2009-03-28
I'm guessing your wireless card is not configured correctly.  Please post the output of these commands so we can see what's going on:
```

sudo iwlist scan
lshw -C Network
lspci -nn
lsusb
uname -rm
```

---

### Post by bsta520 on 2009-03-29
can i still use this information if i swapped out ubuntu for kubuntu??  if not i will switch it back. not a big deal... i went to kubuntu to see if i could scan for networks on there.

---

### Post by pytheas22 on 2009-03-29
Yes, the information will be the same in both Ubuntu and Kubuntu.  Please post the output of those commands.

---

### Post by bsta520 on 2009-03-29
i did those commands in the terminal and nothing came up it was like an error or something...so i put ubuntu back on and this is what it said:::

**_Sudo iwlist scan:_**

lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
pan0      Interface doesn't support scanning. 


**_Lshw -C network: _**

 *-network                
       description: Ethernet interface 
       product: MCP67 Ethernet 
       vendor: nVidia Corporation 
       physical id: a 
       bus info: pci@0000:00:0a.0 
       logical name: eth0 
       version: a2 
       serial: 00:1e:68:26:a8:bc 
       width: 32 bits 
       clock: 66MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=0 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: f2:be:d5:7e:f3:db 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 

**_lspci -nn:_**

00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2) 
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2) 
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2) 
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2) 
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2) 
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2) 
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2) 
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2) 
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2) 
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1) 
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1) 
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2) 
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2) 
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2) 
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2) 
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2) 
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7150M [10de:0531] (rev a2) 
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100] 
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101] 
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102] 
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103] 
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) 
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) 
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12) 
02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12) 
02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff) 
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01) 

lsusb:

Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module] 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

***uname -rm:***

2.6.27-7-generic i686


i have no idea what this stuff means

---

### Post by pytheas22 on 2009-03-29
There's no driver installed for your wireless card, hence the inability to see networks.  Please connect to the Internet via the wire, then run these commands, which should install a driver for your card (they will also update your system in case it's not already):
```

sudo apt-get update
sudo apt-get install linux-backports-modules-interpid
sudo apt-get upgrade
echo ath5k | sudo tee -a /etc/modules
echo atk9k | sudo tee -a /etc/modules
```

When they're done, reboot and see if your wireless works.  If it still doesn't, please post the output of these commands:
```

sudo iwlist scan
dmesg | grep -e wlan -e ath
lsmod | grep ath
```

The directions above are the same on both Ubuntu and Kubuntu.

---

### Post by bsta520 on 2009-03-30
I did everything and unless im missing the part where you SCAN for networks I dont know whats going on... but I ran in to some problems as followed::

when I entered the following this is what I got:

_**sudo apt-get install linux-backports-modules-interpid**_


Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
E: Couldn't find package linux-backports-modules-interpid 

[B][U]echo atk5k | sudo tee -a /etc/modules
and
echo atk9k | sudo tee -a /etc/modules[/U][/B]

after I pressed enter on those two commands it just said atk5k and then atk9k nothing else ... wasnt sure if it was supposed to do that

I restarted did updates and restarted again and still I cant wireless connect, when I plug it in it connects automatically though so I dont know whats going on.


these were the outputs of the commands you ask me to do::

branden@branden-laptop:~$ _**sudo iwlist scan**_
[sudo] password for branden: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

branden@branden-laptop:~$ _**dmesg | grep -e wlan -e ath**_
[   16.843264] ath_hal: module license 'Proprietary' taints kernel.
[   16.851160] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   16.899956] wlan: 0.9.4
[   16.906086] ath_pci: 0.9.4
[   16.921444] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   16.921454] ath_pci 0000:03:00.0: setting latency timer to 64
[   16.949919] ath_pci 0000:03:00.0: PCI INT A disabled
branden@branden-laptop:~$ _**lsmod | grep ath**_
ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci

---

### Post by Mr A Mouse on 2009-03-30
> **bsta520 said:**
> I did everything and unless im missing the part where you SCAN for networks I dont know whats going on... but I ran in to some problems as followed::

when I entered the following this is what I got:

_**sudo apt-get install linux-backports-modules-interpid**_

That should be:

sudo apt-get install linux-backports-modules-intrepid

The last word ("intrepid") was misspelled.

---

### Post by bsta520 on 2009-03-30
i redid that terminal command and when i restarted a thing popped up and said something to the fact that the 802 wireless driver was installed and active...but now what do i do to connect to a wireless network..where do i go to scan for networks?

---

### Post by Mr A Mouse on 2009-03-30
> **bsta520 said:**
> i redid that terminal command and when i restarted a thing popped up and said something to the fact that the 802 wireless driver was installed and active...but now what do i do to connect to a wireless network..where do i go to scan for networks?

Make sure you have "Network Monitor" installed on your panel. In the default Ubuntu installation, the panel is at the top of the screen, on the right side of the bar. Click on Network Monitor with your left mouse button: if there are any wireless networks in range, they will show in a drop-down list.

---

### Post by bsta520 on 2009-03-30
still nothing...this is pissing me off

---

### Post by pytheas22 on 2009-03-30
If the computer told you the wireless driver was installed and active, it's probably working.  Are you sure you're clicking in the right place to scan for networks?  As the poster above explained, you need to *left*-click on the Network Manager applet, which should be in the system tray in the top-right corner of your screen, near the clock.  By default, the icon should look like two computer monitors.  When you left-click on that icon, what do you see (even if the wireless card isn't installed, you should see something)?

Note that there's no button to press to initiate a scan as in Windows; the system automatically keeps track of which networks are in range, and shows you a list when you click on the Network Manager icon--no need to tell it explicitly to do a scan.

Please also post the output of these commands again, now that the driver is installed (when you last posted them, the driver still hadn't been installed):

```
dmesg | grep -e ath -e wlan
sudo iwlist scan
lsmod | grep ath
lshw -C Network
```

---

### Post by bsta520 on 2009-03-30
when i left click it it shows 
Wired Network witch is gray 
Auto eth0
VPN Configurations

these are the commands you requested:

branden@branden-laptop:~$ dmesg | grep -e ath -e wlan
[   17.070795] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   17.083225] wlan: 0.9.4
[   17.089551] ath_pci: 0.9.4
[   17.090030] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   17.090039] ath_pci 0000:03:00.0: setting latency timer to 64
[   17.118525] ath_pci 0000:03:00.0: PCI INT A disabled
[   17.378821] ath5k 0000:03:00.0: enabling device (0000 -> 0002)
[   17.378832] ath5k 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   17.378843] ath5k 0000:03:00.0: setting latency timer to 64
[   17.378881] ath5k 0000:03:00.0: registered as 'phy0'
[   17.388841] ath5k phy0: failed to wakeup the MAC Chip
[   17.388865] ath5k 0000:03:00.0: PCI INT A disabled
[   17.388872] ath5k: probe of 0000:03:00.0 failed with error -5
branden@branden-laptop:~$ sudo iwlist scan
[sudo] password for branden: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

branden@branden-laptop:~$ lsmod | grep ath
ath5k                 116612  0 
lbm_cw_mac80211       215856  1 ath5k
lbm_cw_cfg80211        46744  2 ath5k,lbm_cw_mac80211
led_class              12164  1 ath5k
ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci
branden@branden-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:26:a8:bc
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:57:c2:8f:c3:cf
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by pytheas22 on 2009-03-30
Sorry it's still not working, but fortunately I have a better idea what the problem is now (it's related to the line in dmesg that reads '[ 17.388841] ath5k phy0: failed to wakeup the MAC Chip').

To solve this problem, please run these commands:
```

echo 'blacklist ath_pci' | sudo tee -a /etc/modules
echo 'blacklist ath_hal' | sudo tee -a /etc/modules
```

Then reboot.  Your wireless should work now.  If it still doesn't, please post again the output of:
```

dmesg | grep -e ath -e wlan
lsmod | grep ath
```

---

### Post by bsta520 on 2009-03-31
still not working, does everyone have this problem when installing ubuntu for first time?  and again thank you for helping....

first commands:

branden@branden-laptop:~$ echo 'blacklist ath_pci' | sudo tee -a /etc/modules

[sudo] password for branden: 

blacklist ath_pci

branden@branden-laptop:~$ echo 'blacklist ath_hal' | sudo tee -a /etc/modules

blacklist ath_hal



restarted and still no wireless networks shown.

next commands:

branden@branden-laptop:~$ dmesg | grep -e ath -e wlan 
[   15.930208] ath_hal: module license 'Proprietary' taints kernel. 
[   15.944600] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413) 
[   15.957083] wlan: 0.9.4 
[   15.972779] ath_pci: 0.9.4 
[   16.009434] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19 
[   16.009443] ath_pci 0000:03:00.0: setting latency timer to 64 
[   16.038232] ath_pci 0000:03:00.0: PCI INT A disabled 
[   17.222823] ath5k 0000:03:00.0: enabling device (0000 -> 0002) 
[   17.222834] ath5k 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19 
[   17.222845] ath5k 0000:03:00.0: setting latency timer to 64 
[   17.222882] ath5k 0000:03:00.0: registered as 'phy0' 
[   17.232834] ath5k phy0: failed to wakeup the MAC Chip 
[   17.232860] ath5k 0000:03:00.0: PCI INT A disabled 
[   17.232868] ath5k: probe of 0000:03:00.0 failed with error -5 
branden@branden-laptop:~$ lsmod | grep ath 
ath5k                 116612  0  
lbm_cw_mac80211       215856  1 ath5k 
lbm_cw_cfg80211        46744  2 ath5k,lbm_cw_mac80211 
led_class              12164  1 ath5k 
ath_pci                99096  0  
wlan                  211952  1 ath_pci 
ath_hal               198864  1 ath_pci

---

### Post by pytheas22 on 2009-04-01
Sorry for taking so long to get back to you.  The problem appears to be that the ath_pci and ath_hal modules are still loading, even though they're on the blacklist.  Please try running these commands to remove them permanently (you have no need for them):
```

sudo rm -r /lib/linux-restricted-modules/$(uname -r)/ath_pci
sudo rm -r /lib/linux-restricted-modules/$(uname -r)/ath_hal
```

Then reboot.  Does the wireless work now?  If not, what's the output of:
```

lsmod | grep ath
dmesg | grep -e ath -e wlan
```

---

### Post by rodneymillerpca on 2009-04-01
If I may squeeze in. I had similar trouble with my lap top. This tut [http://www.hp2133guide.com/forums/viewtopic.php?p=10230](http://www.hp2133guide.com/forums/viewtopic.php?p=10230) helped me in just a few minutes. I could not find any trace of the linux-backports-modules-intrepid. I used linux-backport-modules-hardy-generic.

---

### Post by bsta520 on 2009-04-01
you are a genius pytheas22 thank you so much..its working!!  how do i add you to friends if i ever have problems?

thank you again!!!!

now if i have any problems on other computers with wireless and ubuntu can i just do what we have done throughout this forum??

---

### Post by pytheas22 on 2009-04-01
I'm glad it's working.
> 
now if i have any problems on other computers with wireless and ubuntu can i just do what we have done throughout this forum?? 

It depends on what kind of wireless cards are in those computers.  What we did in this thread only applies to certain kinds of devices; others require different steps.  In general, your best bet is to run the command 'lshw -C Network', which will tell you which kind of card you have, e.g. (from my computer):
```

 *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: **AR2413 802.11bg NIC**
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:01:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
```

Then google the name of the device (in the example above, 'AR2413') and ubuntu and see if you can find instructions for making it work.  Or start a forum thread...
> 
how do i add you to friends if i ever have problems?

If you click someone's name, a menu appears that includes an option for adding that person as a friend.

---

