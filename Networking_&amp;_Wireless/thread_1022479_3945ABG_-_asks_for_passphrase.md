---
title: "3945ABG - asks for passphrase"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by tzvi on 2008-12-26
Hi -

I've been researching this problem for the last 6 weeks with no luck. I haven't found a post matching my exact problem.

I connect to my neighbor's encrypted wireless network with no problem (he gave me the password and I entered it into Network Manager.)  However when I try to connect to an open network at the coffee shop I get a dialog box asking for the password.  This happens 80% of the time, but there are times when I can connect.  I think the coffee shop uses a Linksys router (I do not have access to it).  It should not ask for a password if it is an open network- they do not encrypt for a short time, or require that you get a token, etc., - this is a one man shop and he said he doesn't even know how to encrypt his network.  Other patrons use it without problems.

I started using Ubuntu in August, and I love it.  I am a beginner but can use the terminal.  Below is some info on my system plus the output of some commands suggested (while connected to the encrypted network).  Thank you for any help.


Dell Inspiron 1525 laptop
Intel PRO/Wireless 3945ABG Network Connection (rev 02)
Driver: iwl3945
Ubuntu 8.04.1
Use Network Manager
2.6.24-22-generic i686

Installed:
sudo apt-get install linux-backports-modules-hardy-generic



ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:58:79:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:09:58:79:48  
          inet addr:169.254.4.132  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:129400 (126.3 KB)  TX bytes:129400 (126.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:a1:c1:6b  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fea1:c16b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:88257870 (84.1 MB)  TX bytes:5506877 (5.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-A1-C1-6B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"VHLL3"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:01:F3:E2:00   
          Bit Rate=5.5 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality=42/100  Signal level:-84 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.



sudo lshw -C network
 *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:a1:c1:6b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.2 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

---

### Post by tzvi on 2009-01-28
I talked with a Linux guy here where I live and we tried wicd and that solved this problem. 
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
Add the repository then install the package. It will automatically uninstall Network Manager.

---

