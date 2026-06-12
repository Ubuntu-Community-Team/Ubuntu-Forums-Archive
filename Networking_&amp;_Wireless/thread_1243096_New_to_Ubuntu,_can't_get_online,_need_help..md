---
title: "New to Ubuntu, can't get online, need help."
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by johnnydotexe on 2009-08-17
I ran the Ubuntu 9.04 liveCD on my IBM ThinkPad z61m to try it out, and right away it showed the local connection via cat5 crossover cable to my desktop PC that is set to share net with the laptop.  I was able to open firefox, visit pages, etc.  Because of Ubuntu automatically detecting that connection, I decided to wipe the HDD on my laptop and do a full Ubuntu install, went great.

Anyways, after the Ubuntu instal now it's not automatically seeing that connection anymore.  It still shows the auto eth0 in the connections, but it's not doing anything when the cat5 crossover cable is plugged in and internet is running on the desktop.  The laptop is still telling me there's no connection, why did it work when booting from the liveCD but not anymore now that ubuntu is installed?  On the IPv4 tab it is set to Automatic DHCP.

Here's how I get online on my windows desktop, in case the info is needed...

Alltel Blackberry Pearl 8130 connected to my desktop via USB cable, using the Alltel Axcess dial-up software to dial-up to the Alltel Axcess network, using my 10digit number as my username and no password.  The number being dialed is #777.  This desktop is set to share internet through the ethernet card to another computer, with an IP of 192.168.0.1 and a subnet mask of 255.255.255.0 and no DNS set.  The cable going from the desktop ethernet card to the laptop ethernet is a cat5 crossover cable.  I have been able to get online with an xBox using this method, and my laptop previous to this full Ubuntu install.

Anyways, I need this connection working, because when I am home I am online with my PC and use the shared internet to get online with the laptop.  Are there settings that need changed now that Ubuntu is actually installed?  Does a new connection need to be made since auto eth0 apparently isn't working?

I also need  to know how to get the Intel PRO/Wireless 3945abg working.  Ubuntu 9.04 has recognized and installed drivers for all my network adapters, I just don't know if the wifi is working.  Is there a way to check if wifi is working/enabled, if no wifi network is currently present?  I don't want to have to drive 10+ miles to the nearest McDonalds to find out.

I have successfully tethered my blackberry to the lapto via USB cable using the Berry4All software to get online.  Wasn't too hard, but this is only useful when I'm not at home and not in a wifi hotspot.  While at home I NEED that shared/LAN connection.

Thanks in advance to those who stop by to lend a hand. :)

---

### Post by johnnydotexe on 2009-08-18
BB tethering is working now, wireless and the cat5 connection arent. :confused:

---

### Post by johnnydotexe on 2009-08-18
Anyone?  Really need the ethernet/shared connection working on this thing, that was the main point in making my decision to do a full Ubuntu install on this laptop.  Without that connection working, I'm afraid I will be forced to go back to XP on this laptop. :(

---

### Post by johnnydotexe on 2009-08-18
No one here knows how to set up a local connection with ubuntu?

Can't run an OS that I can't get online with. :(

---

### Post by johnnydotexe on 2009-08-18
24 hours/100 views and still no advice? :confused:

All I want to do is establish a local area network between my windows desktop and ubuntu laptop, with the desktop sharing the net to the laptop.  That takes 30 seconds on two windows computers, is that not possible on ubuntu?  It worked when the laptop had windows on it, it worked when "trial booting" Ubuntu from the liveCD, it doesn't work after Ubuntu is actually installed...I'm sure it's something stupid/easy that needs to be set up or changed, I just don't know what.

---

### Post by johnnydotexe on 2009-08-19
Booted up the laptop not long ago and it recognized the LAN connection, currently online with it and my desktop.  An hour or two before shutting the laptop down earlier, all I did was adjust the "Route" setting on the Edit Network > Wired > Edit Auto Eth0 > IPv4, input the IP and Gateway that I set on my desktop.  I tried the net after that but it did't work, I guess a reboot was all that was needed?

I'll be honest here, this thread has kinda put a bad taste in my mouth in regards to coming here for help...over 100 views and not a single opinion or bit of advice.

---

### Post by bingo27 on 2009-08-19
hi all,
 
i have a problem with my ubuntu server. i have obtained a dns service and installed ububtu on my pc to host a web site. i have almost made every configuration to make my pc as dns server. i am unable to ping the hosted website. i am trying to make dns server using bind9. i have installed apache websever though.
 
however, i am unable to ping my website roopkumar.com configured in the server.
i have connected the server via netgear wireless router and changed the network configuration to static. i have a static ip address which is 121.243.139.121. and my server is having 192.168.1.49 ip. can anyone tell me how to host website and how to configure the server as dns? thanks in advance..

---

### Post by johnnydotexe on 2009-08-19
Uhm...you might want to make your own thread, with a title that explains your issue.  As you can see our problems weren't the same, and you'll also notice that no one replied to my issue so posting yours in here probably won't get hits.

---

### Post by johnnydotexe on 2009-08-19
Ok...after the laptop sat for several hours online and running great, I rebooted it after installing WINE.  I'm now back at the desktop, and the LAN is no longer working again.  What's the deal?

---

### Post by linux6994 on 2009-08-19
1.Best way to host a website is to install apache2 and the destination directory will be in /var.

2. Going back to XP is to step back on the evolutionary scale. In a terminal window do a ifconfig and look at the iprange that being given by your hosting PC. Then ensure that your dns and gateway under network connections actually point to it statically if need be.

---

### Post by johnnydotexe on 2009-08-19
> **linux6994 said:**
> Going back to XP is to step back on the evolutionary scale. In a terminal window do a ifconfig and look at the iprange that being given by your hosting PC. Then ensure that your dns and gateway under network connections actually point to it statically if need be.

I just turned the laptop on to try that, and the LAN is up and running, the Network Manager icon is two little screens.  Just went to a few webpages, it's working.  Why does it work sometimes, and not work other times?  Does that sound like a hardware issue?  Or maybe a driver issue?  When it isn't working, it won't allow you to connect...it loads for a few minutes, then notifies me that I lost connection.  The green light on the laptop's cat5 port stays on, the yellow light flashes when trying to connect but eventually stops.  When the connection is up and working, the yellow light flashes normally due to the flow of data.

On the laptop the connection is Auto eth0, MTU is set to auto, 802.1 security is disabled, method is set to Automatic DHCP, Route is set to IP 192.168.0.1 and Subnet Mask 255.255.255.0...those are what I have set for TCP/IP on my windows desktop.  There is no Default Gateway or DNS set in the desktop's TCP/IP properties, those fields are blank.  On the laptop in the routes edit window, Gateway and Metric are blank, and both of the little check boxes are un-checked.

> john@jr-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:71:fb:87  
          inet addr:192.168.0.163  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe71:fb87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17139 (17.1 KB)  TX bytes:11731 (11.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
> john@jr-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5752M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:16:36:71:fb:87
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5752m-v3.22 ip=192.168.0.163 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:b9:d9:34
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:13:b3:d0:fa:c1
       capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


---

