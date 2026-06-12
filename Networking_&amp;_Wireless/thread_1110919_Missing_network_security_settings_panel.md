---
title: "Missing network security settings panel"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by gewitty on 2009-03-30
**SOLVED**

I just installed a couple of dLAN ethernet-over-mains adapters. It took a while to get them installed and configured but I got there in the end. I can now run a configuration program that allows me to talk to both adapters (local and remote) and set up passwords on them, so I know that they are working and talking to one-another. However, my Hardy installation cannot connect.  

I have the wired connection setting in Network Manager set to use Automatic DHCP. I have both the units' MAC addresses loaded in the router's MAC address filter, so as far as I know, there is no problem at that end.

The bit that is defeating me is that I know the dLAN units use encryption. When I first started to install them, Network Manager popped up a window that asked for various things, such as a user name and password for the Ethernet connection, but since that one occasion that panel has never re-appeared and I can't find it anywhere. I'm pretty sure that this is the cause of the problem, because the passwords have not been set correctly.

A couple of other clues (in case the password idea is a red herring):

When Firestarter tries to run, it fails and reports that device eth0 is not ready.

ifconfig output is as follows:

dave@dave-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:3a:a1:01  
          inet6 addr: fe80::20c:76ff:fe3a:a101/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:18 txqueuelen:1000 
          RX bytes:10035 (9.7 KB)  TX bytes:91135 (88.9 KB)
          Interrupt:17 Base address:0x8e00 

eth0:avahi Link encap:Ethernet  HWaddr 00:0c:76:3a:a1:01  
          inet addr:169.254.4.48  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x8e00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:264845 (258.6 KB)  TX bytes:264845 (258.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:30:bd:64:82:ae  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fe64:82ae/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:1968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1624325 (1.5 MB)  TX bytes:397206 (387.8 KB)



**UPDATE**

I finally found the security panel. It appears when I switch the connection to Roaming Mode. What I get is a pop-up window that's headed, 'Connect to a 802.1X protected wired network'. This has my router SSID showing as the network name and has a number of fields for EAP Method, Phase2 Type, Identity, Password, Anonymous Identity, Client Certificate File, CA Certificate File, Private Key File, and Private Key Password.

I've tried just about every combination using the security I.D's and passwords assigned to the two dLAN HomePlugs, but so far with no success.

Anyone got any experience with this, or any ideas about where I'm going wrong?

---

