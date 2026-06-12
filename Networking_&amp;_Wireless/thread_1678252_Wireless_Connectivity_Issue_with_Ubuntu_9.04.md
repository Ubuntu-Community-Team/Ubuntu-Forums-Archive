---
title: "Wireless Connectivity Issue with Ubuntu 9.04"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by Dave1024 on 2011-01-30
Hi,
 
I am writting this for solve one of the issue faced after the installation of ubuntu 9.04
 
I am using Acer Aspire 5745 Laptop. I have broadcom 802.11n wireless network adapter.
 
I have beetel router.
 
I know the Name,SSID Encryption Type, Encryption Method, Key and MAC address.
 
But i am unable to connect to the router.
 
Please give a guidance for connect my router to ubuntu 
 
;)
 
Dave

---

### Post by Dave1024 on 2011-01-30
When i search my hardware driver list there is nothing relate to 802.11 wireless network card[Acer Nplify 802.11 b/g/n]. So is this probelm comes due to the driver issue?
 
Which ubuntu version will give the proper driver?
 
;)
Dave

---

### Post by grahammechanical on 2011-01-30
Linux is a modular operating system. The installation will install modules specific to the hardware of your machine. This will only happen if the required modules have been developed. Ubuntu 9.04 is almost two years old. Were are expecting 11.04 soon. It is possible that a driver module for your wireless device has been developed for your machine since 9.04 was released. But then again, may be not.

Of course, the correct drivers may already be available for your machine and you are not doing what you need to do to activate the wireless adapter.

You do not give us enough information. The installation comes with a Help program. If I remember 9.04 correctly there should be an icon on the top panel. Have you read the directions for setting up Internet and Networks that are in the help files?

Do you have a network icon in the top panel? What information does the machine give to tell you that you are not connected?

Regards.

---

### Post by Dave1024 on 2011-01-30
The issue presently faced is i cann't connect to my beetel 450TC1 ADSL 2+ Router from my ubuntu 9.04
The following steps i tried from my limited knowledge in ubuntu 9.04
1. Mozilla Firefox un check the box for work offline
2. from wireless icon from my machine panel.
 
 There is 2 options 1. no network device availabe[Disable] 2. VPN connections
    
 I choose VPN connections - > Configure VPN/Disconnect VPN
 Configure VPN-> wireless->connection name 
       ->ssID 
       ->MTU : Automatic 
       ->Mode : Infrastructure 
 Configure VPN->wireless security None
 Configure VPN->IPV4 Settings ->DHCP
         ->DHCP Client ID : None 
3. System->Administrations->Network Tools
      Device , Ping, Netsat, Traceroot, Port Scan, Look Up, Finger, Whois
      
I don't know how can configure to these tabs.

---

### Post by Dave1024 on 2011-01-30
Hi,
 
Please see the output of different trouble shooting commands in Ubuntu with my laptops present setup.
 
[FONT=Batang][SIZE=3]Output After the Command for wireless trouble shooting from the ubuntu forum[/SIZE][/FONT]
***_[SIZE=3][FONT=Batang]sudo lshw -c network[/FONT][/SIZE]_***
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang] *-network UNCLAIMED     [/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       description: Ethernet controller[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       product: Attansic Technology Corp.[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       vendor: Attansic Technology Corp.[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       physical id: 0[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       bus info: pci@0000:01:00.0[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       version: c0[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       width: 64 bits[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       clock: 33MHz[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       capabilities: pm msi pciexpress vpd bus_master cap_list[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       configuration: latency=0[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]  *-network UNCLAIMED[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       description: Network controller[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       product: Broadcom Corporation[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       vendor: Broadcom Corporation[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       physical id: 0[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       bus info: pci@0000:02:00.0[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       version: 01[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       width: 64 bits[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       clock: 33MHz[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       capabilities: pm msi pciexpress bus_master cap_list[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       configuration: latency=0[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]  *-network DISABLED[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       description: Ethernet interface[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       physical id: 2[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       logical name: pan0[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       serial: aa:97:8e:18:d6:7c[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       capabilities: ethernet physical[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
***_[SIZE=3][FONT=Batang]sudo lsmod[/FONT][/SIZE]_***
***_[FONT=Batang][SIZE=3] [/SIZE][/FONT]_***
[FONT=Batang][SIZE=3]bridge                 56340  0 [/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
***_[SIZE=3][FONT=Batang]sudo iwconfig[/FONT][/SIZE]_***
***_[FONT=Batang][SIZE=3][/SIZE][/FONT]_***
***_[FONT=Batang][SIZE=3] [/SIZE][/FONT]_***
[FONT=Batang][SIZE=3]lo        no wireless extensions.[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3]pan0      no wireless extensions.[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
***_[SIZE=3][FONT=Batang]sudo iwlist scan[/FONT][/SIZE]_***
***_[FONT=Batang][SIZE=3][/SIZE][/FONT]_***
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]lo        Interface doesn't support scanning.[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3]pan0      Interface doesn't support scanning.[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
***_[SIZE=3][FONT=Batang]ping -c 4 192.168.0.1[/FONT][/SIZE]_***
***_[FONT=Batang][SIZE=3][/SIZE][/FONT]_***
[FONT=Batang][SIZE=3]connect: Network is unreachable[/SIZE][/FONT]

 
 
Please help me to solve the issue
;)
Dave

---

### Post by grahammechanical on 2011-01-30
If there is an icon for networking in the top panel, then that indicates that Ubuntu has recognized your wireless adapter. This is my opinion. 

If when you left click on the icon you see a message no network device available, then I would guess that the wireless adapter is switched off. This is why you are getting Network Unclaimed in the listing from lshw -c network.

You are using a laptop. Could it be that there is a key combination that you have to press to switch on the wireless adapter, such as fn-f10? Or something like that. My sister has a laptop and this is what she has to do to get a wireless connection to her modem/router.

Allow a some seconds to pass for the machine to power up the wireless adapter and then see if the network icon shows any indication that it is scanning for nearby wireless networks. You may now see some available networks in the list. One of which could be your wireless network. Select it, enter the wireless key and network manager will do the rest.

Regards.

---

