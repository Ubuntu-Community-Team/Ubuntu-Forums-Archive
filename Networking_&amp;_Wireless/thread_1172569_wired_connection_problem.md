---
title: "wired connection problem"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by Hest on 2009-05-28
Just installed ubuntu 9.04 onto my acer

cant get wired internet to work 

tried the following advice (posted in another thread)


[http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html)

get nothing when I ping

I would idealy like it to set up automatically since I move location quite a bit

any help greatly appreciated

(there are no wirless connections showing but my windows pc is only picking up weak signals)

---

### Post by Iowan on 2009-05-28
What are results if **ifconfig -a** and **lshw -C network**?  If you're still trying via DHCP, post results of **dhclient eth0** and contents of */etc/dhcp3/dhclient.conf*.

---

### Post by Hest on 2009-05-28
Not sure how I would post this short of typing it out?

Are they any specific things I could look for?

I may be able to find a wireless connection tomorrow and see if that works

---

### Post by Iowan on 2009-05-28
> **Hest said:**
> Not sure how I would post this short of typing it out?

Are they any specific things I could look for?

I may be able to find a wireless connection tomorrow and see if that worksIn particular, see if **ifconfig -a** shows eth0 with a valid IP address. **lshw -C network** should show information about "logical name: eth0" - hopefully not "unclaimed"..  "Unclaimed" might mean a driver issue, "disabled" or "unassigned" just means "unused".  **dhclient eth0** will probably show unsuccessful attempts to get address.  If that's the case, you can check [this]("http://ubuntuforums.org/showthread.php?t=1156441") thread - or more complete information [here]("http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html").  BTW, that last site also has info on [saving terminal-output-to-file]("http://www.prash-babu.com/2009/05/how-to-save-output-of-command-entered.html").

---

### Post by Hest on 2009-05-29
(so apparently I was too tired to remeber pen drives existed lol) here is what I get for the various runs: I had already tried the suggested fix that you posted above - I have also printed out my dhclient.conf file. Cheers


**ifconfig -a:**

eth0      Link encap:Ethernet  HWaddr 00:1e:68:97:03:fc  
          inet6 addr: fe80::21e:68ff:fe97:3fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95118 (95.1 KB)  TX bytes:1494 (1.4 KB)
          Interrupt:251 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 7e:80:b8:ee:0d:a8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:68:aa:01:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-68-AA-01-4D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[B]
lshw -C network:[/B]

*-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:97:03:fc
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:68:aa:01:4d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7e:80:b8:ee:0d:a8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[B]
*/etc/dhcp3/dhclient.conf*.  :[/B]

# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

# option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}



[B]dhclient eth0:

[/B]didn't print to file but says:

wmaster0: unknown hardware address type 801
.
.
.
.
No DHCPOFFERS received.
No Working leases in persistent database - sleeping.

---

### Post by Iowan on 2009-05-29
Perhaps a bit more background information...
You are connected to a router, hub, switch or modem?  If it's a modem (sometimes, but seldom with a router), you may need to power-cycle (turn it off for several seconds, then back on) to get it to recognize the MAC address.

---

### Post by Hest on 2009-06-23
Switching the modem off and on worked, Thank you.

---

### Post by Hest on 2009-06-23
Switching the Modem off and then back on worked. Thank you.

---

