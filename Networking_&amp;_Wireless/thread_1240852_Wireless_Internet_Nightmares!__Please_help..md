---
title: "Wireless Internet Nightmares!  Please help."
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by Lost!?! on 2009-08-15
I just bought a netbook and it came with Ubuntu 8.10.  I've never used any Linux operating system before but felt it would be worth a shot as I've heard great things about it.

It took me over three hours to initially connect to the internet as Network Manager kept changing the WEP/WPA password I would enter (and I tried connecting from 3 different places).  

When my patience finally won the day by some miracle, I downloaded the updates (most worked and some failed).  I then restarted my Netbook and was surprised to discover that the Enable Wireless option under Network Manager had totally disappeared and that I simply can't connect to the internet.  I went into Help and followed the Troubleshooting directions using Terminal but to no avail (the "results" were mostly Chinese to me and the Troubleshooting didn't seem to state how to resolve anything).

Can someone help?  I'd really appreciate it as I honestly want to give Ubuntu a try (and am more than willing to learn).  But a netbook that can't connect to the internet because of Ubuntu sort of defeats the purpose!

---

### Post by superprash2003 on 2009-08-15
post output of the following commands ( copy paste ) from the terminal(Applications->Accessories->Terminal)
1)lshw -C network
2)iwconfig

---

### Post by Lost!?! on 2009-08-15
Thanks for replying, I really appreciate your willingness to help!

Here they are (I would like to point out that after the updates the Netbook button that would usually get enable/disable the wireless isn't working either):

   lshw -C network
  WARNING: you should run this program as super-user.
  
    *-network               
  
         description: Ethernet interface
  
         product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
  
         vendor: Realtek Semiconductor Co., Ltd.
  
         physical id: 0
  
         bus info: pci@0000:01:00.0
  
         logical name: eth0
  
         version: 02
  
         serial: 00:24:25:00:34:df
  
         width: 64 bits
  
         clock: 33MHz
  
         capabilities: bus_master cap_list ethernet physical
  
         configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  
    *-network DISABLED
  
         description: Ethernet interface
  
         physical id: 2
  
         logical name: pan0
  
         serial: b2:90:0c:35:19:77
  
         capabilities: ethernet physical
  
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  
   
  jazz@pov:~$ iwconfig
  
  lo        no wireless extensions.
  
   
   
  eth0      no wireless extensions.
  
   
   
  [FONT=&quot]pan0      no wireless extensions.[/FONT]

---

### Post by Lost!?! on 2009-08-17
I reinstalled the wireless drivers and now theoretically have wireless internet (the Netbook button is working again and the Enable Wireless option under Network Manager has come back).

The only problem (which is driving me crazy) is that I still have problems when I enter a WEP or WPA security password.

The password automatically gets changed and I end up re-inputting the correct password only to have it randomly get changed again and the annoying cycle continues.  So obviously I can't connect.

What's going wrong and how can I resolve this?

---

