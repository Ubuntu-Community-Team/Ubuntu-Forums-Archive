---
title: "Jaunty, nidiswrapper, and network manager"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by FreudianSlap on 2009-04-26
Hi,

I installed Jaunty on my old Toshiba laptop yesterday - all went well with the install.  I have a Belkin wireless PCMCIA card (Model F5D7010) for which I installed ndiswrapper and the windows drivers (blkwgnv7.inf, .sys, and .cat).  I then opened Network Manager, and connected to my wireless network without a problem.  I did a few random searches on google to make sure it was connected to the internet - it worked fine.

Since I restarted the computer, network manager will not connect to my network.  When my network card is connected to a network, a small green LED on the card will come on permanently.  When I try to connect to my network this LED is coming on for about 5 seconds, then going off for 15 or so, coming back on for 5, and so on...  The network manager icon at this point just 'spins', and every so often, network manager will ask for my WPA key.  I do not appear to get any connection at all to my network.

Network manager will detect other peoples networks around me, so the card is obviously doing something.  The card is not faulty as I tried it in windows, and I know that it worked flawlessly after its initial install.

Can anyone help with this... I am not completely new to Ubuntu but I'm no expert either.

Many thanks!

Freud.

---

### Post by gopalsingh on 2009-04-26
On your router try turning your wireless encryption to WEP, or try disabling all encryption (open wifi network) and see if it works connecting then?

Myself and a few others are experiencing problems connecting to WPA networks in Jaunty, but WEP and open networks work fine, we havn't figured out why yet.

---

### Post by FreudianSlap on 2009-04-26
I took the encryption off entirely and it has connected without a problem, in fact I am writing this message over the connection now.  (Although I can't leave the network unsecured like this!!!) Is there a specific thread you can point me to where the encryption problem is being discussed in more detail?

Thanks!

Freud.

PS It seems strange how the encryption wasn't a problem before I restarted the computer, but that is obviously what is causing the problem.

---

### Post by siddharth_moghe on 2009-04-26
hi,

i have a very stupid looking problem, the network manager wouldn't detect the wireless networks that is there at home. Also the icon shows up with a red cross even when there is proper Ethernet connectivity on it.

When i first loaded Jaunty, i was seeing two wireless networks as expected and i connected through pppoe as i usually do on windows, but on subsequent reloads - the network manager stopped detecting the wireless networks at home.

how do i see the networks with the help of network manager

Here is the output of some of the commands that could help



 siddharth@novice:~$sudo lshw -C network
  *-network              
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 11
       serial: 00:15:60:b1:43:5b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5751m-v3.29a ip=192.168.1.3 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s


 siddharth@novice:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:1B:57:C4:BB:C9
                    ESSID:"Moghe"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=93/100  Signal level=-19 dBm 
                    Extra: Last beacon: 2060ms ago

siddharth@novice:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 5103
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:16:6f:32:17:4d
Sending on   LPF/eth1/00:16:6f:32:17:4d
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 35053 seconds.


now that its connected thru iwconfig, it doesnt get connected to pppoe nor do they show up on network manager ( it still shows a red crozz )

---

### Post by gopalsingh on 2009-04-26
> **FreudianSlap said:**
> I took the encryption off entirely and it has connected without a problem, in fact I am writing this message over the connection now.  (Although I can't leave the network unsecured like this!!!) Is there a specific thread you can point me to where the encryption problem is being discussed in more detail.

Thanks!

Freud.

PS It seems strange how the encryption wasn't a problem before I restarted the computer, but that is obviously what is causing the problem.

Here is the thread:
[http://ubuntuforums.org/showthread.php?t=1134948](http://ubuntuforums.org/showthread.php?t=1134948)

I am pretty sure that for me, my wireless also initially connected to my WPA network, but then after restarting it wouldn't connect to any WPA networks again, and I hadn't touched any wireless settings at all.

I got mine to work with WPA networks again by using a different driver with ndiswrapper. This new driver works with WPA, but now doesnt work with WEP! There is more details in that thread.

---

### Post by gopalsingh on 2009-04-26
> **siddharth_moghe said:**
> hi,

i have a very stupid looking problem, the network manager wouldn't detect the wireless networks that is there at home. Also the icon shows up with a red cross even when there is proper Ethernet connectivity on it.

When i first loaded Jaunty, i was seeing two wireless networks as expected and i connected through pppoe as i usually do on windows, but on subsequent reloads - the network manager stopped detecting the wireless networks at home.

how do i see the networks with the help of network manager

Here is the output of some of the commands that could help

(snip)

I would open a seperate thread as your problem is very different.

I would try booting from the Ubuntu 9.04 install CD under "Live" mode to see if everything works fine on a fresh Jaunty install.

Also, you could try installing WICD instead of the default NetworkManager that comes with Ubuntu and see if that works instead.

---

