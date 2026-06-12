---
title: "wireless network problem in 10.04"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by mefistofeles666 on 2010-07-31
Hello everybody,

I just recently updated to 10.04 and have a dual booting machine with xp sp3. The problem I have is that the network manager does not want to connect to any network, and when it does connect the connection is unstable, slow, and most of the time drops after a min of being connected. Everything works in xp so i know its not hardware related. here is some info you guys may need.

computer is toshiba satellite m45-s365

laptop:~$ sudo lshw | grep -B 1 -A 11 Wireless
           *-network      
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:05:04.0
                logical name: eth1
                version: 05
                serial: 00:13:ce:a8:7a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=128 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
                resources: irq:11 memory:b800b000-b800bfff


laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"linksys"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:14:BF:ED:EF:2D   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


any help is appreciated. thank you

---

### Post by Bladeforger on 2010-07-31
Try going to Synaptic Package Manager and search for wicd.  It's not compatible with the Gnome Network Manager and will ask to uninstall it.  That's okay.  The install process will flag your user name and ask if you can be added to make changes via wicd.  You decide.  Then, when it's executed, it really goes out and finds the wireless network.  You can select the security and set the password and go.  

I spent hours trying to get the network manager to work and cruising various forum threads.  

wicd works great.  You'll like it.

Keith

---

### Post by mefistofeles666 on 2010-08-02
I tried wicd on hardy and i was not impressed. I tried using wifi radar but that one does not connect at all.

---

