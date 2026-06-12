---
title: "Wireless grinds to a halt / slow (Heron - MadWifi) - FED UP! EVERYONE REPORTING SAME!"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by joelgrrr on 2009-02-21
I am not the only person to report the following symptoms on a Heron Laptop with Madwifi or Atheros wireless drivers:

My laptop with 8.04 Heron ubuntu wireless works fine at work. However, when using ubuntu at home it will grind to a halt. I have a netgear router, madwifi/atheros chipset wireless card. Of course, XP & Vista both work fine at home.

I have tried everything.

[LIST]
[*]Disabling IPV6
[*]Changing wireless channel (from 11 to 10)
[*]Using either WPA/ WPA2 / No WPA
[*]Using 11Mbs  / 54Mbs (wireless b & G)
[*]Upgrading router firmware
[/LIST]

I am now thoroughly fed up. Wireless will work for 1,2 maybe 10 minutes, and then grind to a halt. This does not appear to be a DNS issue, since pinging an IP directly is just as slow as resolving the name.

I know lots of other people have reported similar problems. I wish Ubuntu would publish some guidelines - steps to diagnose & fix. I don't that for each person reporting this the cause  will be the same, but there must be a common core set of possible causes that can be run through.

Surely the fact that so many people report the following: Ubuntu wireless works  fine when I'm at work, but not when I'm at home, and vista/xp work fine at home. There must be something to this!!! Come on UBUNTU.... GRRR! Help us help you!!!


BTW - this morning noticed the following in /var/log/messages:


```
Feb 21 10:57:33 bohr dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name
Feb 21 10:57:33 bohr dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.domain_name
Feb 21 10:57:33 bohr dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
Feb 21 10:57:33 bohr dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers
Feb 21 10:57:33 bohr dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.interface_mtu
Fe
```

Anyone know if this is important?


Here's my ifconfig

```
joel@bohr:~$ ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:21:63:cc:53:af  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12641690 (12.0 MB)  TX bytes:681902 (665.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:13:77:97:81:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:293 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75733 (73.9 KB)  TX bytes:75733 (73.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-21-63-CC-53-AF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47714 errors:0 dropped:0 overruns:0 frame:783
          TX packets:4873 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:13866498 (13.2 MB)  TX bytes:898710 (877.6 KB)
          Interrupt:19 

```


and my wlanconfig

```
joel@bohr:~$ wlanconfig ath0
[status not implemented (yet). Spawning iwconfig...]
ath0      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1B:2F:A1:A2:D6   
          Bit Rate=54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-37 dBm  Noise level=-96 dBm
          Rx invalid nwid:27392  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by joelgrrr on 2009-02-21
OK - I HAVE FIXED THIS BY USING NDISWRAPPER INSTEAD OF MADWIFI.
Although madwifi worked sometimes for me (at work) it was buggy at home - working intermittently or very slowly.
I have an atheros 5K chipset - Atheros AR5007EG, named AR5006EG in gusty, named AR242x in hardy.

So, to fix: I first un-installed madwifi:

```

# blacklist the ath_pci module (assuming you have already installed  madwifi) by appending "blacklist ath_pci" to the blacklist file
sudo echo blacklist ath_pci >>  /etc/modprobe.d/blacklist

# run this command
sudo update-initramfs -k all -u

# reboot machine
sudo shutdown -r now

# now to verify the above worked check that the output of  
lshw -C Network

``` 

Check the output of the above to ensure that the ath_pi driver is no longer registered:

> 
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:21:63:cc:53:af
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=**_ath_pci_** driverversion=1.52+,11/15/2006,5.1.1.9 ip=192.168.0.7 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


If you see the line in bold then you know that the steps to deregister madwifi did NOT work. 

If you don't see this then you can go on to the next steps. Install ndiswrapper and the windows driver for the Atheros

[LIST]
[*] install ndiswrapper & ndisgtk (System > Adminstration > Package Mngr)

[*] download the .inf from the XP driver at : [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz)

[*] unpack it using gzip & tar

[*] open a terminal and type this command : sudo ndisgtk

[*] select the net5211.inf file from the files unpacked above and press "enter"

[*] it should now work
[/LIST]

For further reference:

[LIST]
[*] ndiswrapper - [http://ubuntuforums.org/showthread.php?t=885847 ]("http://ubuntuforums.org/showthread.php?t=885847")
[*] troubleshooting ndiswrapper - [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") 
[/LIST]

---

