---
title: "PC as router and wireless access point"
date: 2012-09-29
forum: Networking &amp; Wireless
---

### Post by mw4jet on 2012-09-29
I have a project going on (for three weeks now!) that I have had enough success to continue. I have an older linksys WRT54Gv4 and a Netgear WNDR-3300 both with DD-WRT, my home wireless network continues to grow with four laptops, two ipads, Playstation 3, Wii, 4 smart phones.........I keep having drops when someone is watching a streamed movie, etc.
 
I have an Ubuntu server that is currently my router connected to my cable modem on eth1, I have the Linux firewall on that box, along with samba, apache web server, and ftp server. I have dyn-dns ported to Webmin, ftp, ssh, http, all on the Dell Precision dual core desktop that is doing all of this. It supplies the WNDR-3300 on eth0 which is setup as a switch and wireless access point for all my wireless clients, the ipads and cell phones are connected to the "N" band network, and the two of the laptops as well. All the rest connect on the "G" band. 
 
I want the server behind the router/firewall, if anything happens on the server, as has already happened, I loose all internet. I can set the WNDR-3300 with all the settings and keep it nearby as a replacement/stand by, but I loose the server.
 
So, my project:
I have stripped down an old toughbook CF-72 I have and it will run with out a keyboard, monitor, and takes up less room and power than another desktop would.
 
I have Ubuntu server bare bones, wireless-utils, hostapd, and some other packages as I needed, (or think I needed :p) installed of the CF-72.
 
eth0 (will be to cable modem), currently I have eth0 to the Linksys router/wap, the wan port is connected to the WNDR-3300 on a lan port acting as a network inside my network for developement purposes, I have it on a different subnet.
 
wlan0 I have a Broadcom BCM4318 "G" PCI (mini) card set up with hostapd as a wireless access point in "master mode". I currently can connect to wlan0 just like it was the Linksys or the Netgear, streams video from server and internet, working good. I have the Linksys wap also set up and I can connect to the CF-72 by ssh if I disconnect from the WAP on wlan0 and connect to the Linksys and putty in through eth0. Sounds rather convoluted but to keep by network intact and working I did it this way.
 
I have bridged eth0 to wlan0, so I "could" connect this to my modem and connect my other devices to wlan0 and access the internet, but no way to connect to an ehernet switch ....
 
I want to add an ethernet (eth1) so I can connect to a switch and connect the server, an entertainment PC, and the Wii by ethernet. This needs to be "bridged" to eth0 but I have wlan0 bridged to eth0, is it possible to bridge 3 nic's? Or bridge two-( wlan0 and eth2 ) to eth0?
 
I have also entertained thoughts of adding an "N" card with an Atheros chipset to the other PCI slot and setting up a second wireless access point which would be wlan2 and bridge that to eth0.
 
So I have
 
eth0-wlan0-br0 all good,
 
want to add eth1 and bridge to eth0
 
want to add wlan2 and bridge to eth0 also,
 
Then I will need to set up IPtables or Linux Firewall before installing but I need to get this figured out first, I think. 
 
I have a second broadcom "G" card installed in wlan2 now, I will get that up and running as second WAP before ordering the Atheros "N" mini PCI card, the card in wlan2 is a PCMCIA card for testing and set up
 
Here is iwconfig:
 
```
 
wlan2     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
lo        no wireless extensions.
br0       no wireless extensions.
eth1      no wireless extensions.
wlan0     IEEE 802.11bg  Mode:Master  Frequency:2.437 GHz  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
eth0      no wireless extensions.
mon.wlan0  IEEE 802.11bg  Mode:Monitor  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```
 
 
```
mark123@4jetrouter:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet addr:192.168.22.10  Bcast:192.168.22.255  Mask:255.255.255.0
          inet6 addr: fe80::280:45ff:fe22:84b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:313515 (313.5 KB)  TX bytes:132508 (132.5 KB)
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5611915 (5.6 MB)  TX bytes:2000504 (2.0 MB)
          Interrupt:9 Base address:0x3000
eth1      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
mon.wlan0 Link encap:UNSPEC  HWaddr 00-00-00--00-00-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:189365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:35151292 (35.1 MB)  TX bytes:0 (0.0 B)
wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet6 addr: fe80::214:a4ff:fe3b:6f9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10774 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10829 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2148881 (2.1 MB)  TX bytes:6324184 (6.3 MB)
wlan2     Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
 
eth0, wlan0, and br0 are "running" wlan2 and eth1 are not.
 
Can I modify the hostapd file to run two WAPs?
here is /etc/hostapd/hostapd.conf
```
 
interface=wlan0
driver=nl80211
# YOUR BRIDGE NAME
bridge=br0
# YOUR COUNTRY HERE
#country_code=US
#ieee80211d=1
# MODIFY YOUR SSID HERE
ssid=4JET_WAP
# CHANGE MODE HERE IF NEEDED
hw_mode=g
# CHANGE CHANNEL EVENTUALLY
channel=6
wme_enabled=0
macaddr_acl=0
auth_algs=1

# WE USE WPA2
wpa=2
# MODIFY YOUR PASSPHRASE HERE
wpa_passphrase=xxxxxxxxxxxxxx
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP


```
 
Here is /etc/network/interfaces as it is and it is working, think I made a mistake because I actually got it to work! :guitar: I have IP addresses on br0 and wlan0, they are the same, so that dosen't cause a conflict? 
 
```
 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
#auto eth0
iface eth0 inet manual
           address 192.168.22.10
           netmask 255.255.255.0
           network 192.168.22.0
           broadcast 192.168.22.255
           gateway 192.168.22.1
           dns-nameservers xxx.xx.xx.xx xxx.xx.xx.xx
           dns-search xxxxxxxx.com
#           pre-up iptables-restore < /etc/iptables.conf
 
#Wireless Setup
#auto wlan0
iface wlan0 inet dhcp
#           address 192.168.21.10
#           netmask 255.255.255.0
#           network 192.168.21.0
#           broadcast 192.168.21.255
 
#Bridge interface
auto br0
iface br0 inet static
          address 192.168.22.10
          network 192.168.22.0
          netmask 255.255.255.0
          broadcast 192.168.22.255
          gateway 192.168.22.1
          dns-nameservers xxx.xx.xx.xx, xxx.xx.xx.xx
          dns-search xxxxxxx.com
          bridge-ports eth0 wlan0
 

```
 
 
I hope I didn't make it impossible to understand, I have done alot to get this thing working!! Someone who knows of multi bridging?
 
Thanks!

---

