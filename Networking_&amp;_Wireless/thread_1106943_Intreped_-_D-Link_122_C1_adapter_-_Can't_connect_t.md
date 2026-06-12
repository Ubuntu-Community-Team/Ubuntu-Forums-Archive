---
title: "Intreped - D-Link 122 C1 adapter - Can't connect to Wireless Network"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by jmeryden on 2009-03-26
Ubuntu 8.10 Desktop -  D-Link G122  Version C1 Adapter &#8211;  Wireless Network not working

As a senior & newbie to Ubuntu & Linux Wireless Networking I am in need of assistance to get connected to the Internet.

Ubuntu 8.10 has been installed on my Desktop ( Mainboard 7S5A motherboard) & from the Synaptic Package Managed I have installed the rt73 driver required by the D-Link G122 version C1  usb wireless adapter.  The wireless router is a D-Link G604T model, currently serves another computer with Windows OS & is working ok.

As I was unable to connect to the internet through the Networking Manager I removed  it & have now installed WICD networking. I can get onto the internet via the wired connection, but am still unable to connect onto the wireless network. When I am eventually connected to the internet I want to have a static IP address & using WEP encryption.

I would appreciate if someone could look at my iwconfig & ifconfig files to see if the problem could be found, or give me some simple step by step advice to help me get connected to the  wireless network.


jmerriden@jmerriden-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"G604T_WIRELESS"  
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: Not-Associated   
          Tx-Power=8 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=72/100  Signal level:-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

jmerriden@jmerriden-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:4f:25:94:55  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2590 errors:5 dropped:0 overruns:0 frame:0
          TX packets:1927 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3109995 (3.1 MB)  TX bytes:238933 (238.9 KB)
          Interrupt:11 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1408 (1.4 KB)  TX bytes:1408 (1.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:5b:78:3a:96  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:11499 (11.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-5B-78-3A-96-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

jmerriden@jmerriden-desktop:~$

---

