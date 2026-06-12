---
title: "Need help deciphering what results tell me to do."
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by johnsonnoob on 2009-04-12
Hey so I installed my first version of Linux OS ever a couple of days ago, and so far I haven't gotten the networking to work to where I have internet capabilities in it :( I have Ubuntu 8.10 and am dual booting it off of Vista. (currently using vista to use the web obviously) Anyways I need help in determining my next course of action after working my way through the terminal for two days now I've decided I need help.

I think I successfully installed ndiswrapper to configure my driver for my networking card.  And...pretty much thats where I'm stuck :P heres some results of commands hopefully someone can tell me what they mean!


zach@ubuntu:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11bg  ESSID:"johnson"   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=0 dBm    
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B    
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
pan0      no wireless extensions. 



zach@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:4e:b5:db   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:221 Base address:0x4000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B) 

This one shows all the errors that are happening when network is restarted, maybe useful?

zach@ubuntu:~$ sudo /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process 
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4491 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:1b:fc:8f:65:d7 
Sending on   LPF/wlan0/00:1b:fc:8f:65:d7 
Sending on   Socket/fallback 
grep: /etc/resolv.conf: No such file or directory 
SIOCSIFFLAGS: No such file or directory 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
wmaster0: unknown hardware address type 801 
SIOCSIFFLAGS: No such file or directory 
SIOCSIFFLAGS: No such file or directory 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:1b:fc:8f:65:d7 
Sending on   LPF/wlan0/00:1b:fc:8f:65:d7 
Sending on   Socket/fallback 
receive_packet failed on wlan0: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 
send_packet: Network is down 
 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
send_packet: Network is down 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
RTNETLINK answers: Network is down 
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2 
grep: /etc/resolv.conf: No such file or directory

---

### Post by johnsonnoob on 2009-04-12
If someone could help me out, you can also pm me so that we can stay in contact...I can give u the outputs of any commands u want, it seems to me that my wlan0 is disabled, and I need to know how to enable it...otherwise my icon in the top right for networking has also disappeared :/

---

### Post by Zulu-Zeffir on 2009-04-12
What model wireless card is it?

  Try: ifup wlan0  

If you receive an address via dhcp this should get you up and running.  You are clearly trying to connect to a wireless network but if you get your ethernet up and running (ifup eth0) you will at least be able to troubleshoot your wireless while browsing from your Ubuntu Box ;)

---

### Post by johnsonnoob on 2009-04-12
yeah I've done ifup wlan0 it says that its already configured :)and yes I desperately want internet on the ubuntu box so that I don't have to go back and forth...but I can't direct plug in because the box is really far away! :(

heres some more outputs:


zach@ubuntu:~$ ndiswrapper -l 
bcmwl5 : driver installed 
	device (14E4:4318) present (alternate driver: ssb) 

(this I assume means I did the whole ndiswrapper thing right?)


zach@ubuntu:~$ lspci -v | grep Broadcom 
01:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 

(heres info on my card like you asked)

zach@ubuntu:~$ iwlist scanning 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wmaster0  Interface doesn't support scanning. 
 
wlan0     No scan results 
 
pan0      Interface doesn't support scanning. 

(this I think shows how my wlan0 totally isn't working)

zach@ubuntu:~$ sudo lshw -C Network 
  *-network                
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 9 
       bus info: pci@0000:01:09.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=32 module=ssb 
  *-network:0 DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:1b:fc:8f:65:d7 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
  *-network:1 DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: ee:9e:7c:b8:16:7e 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 

(maybe useful? looking at this I naturally seem to think that *-network 0 should be enabled? but I dunno any commands to do that...and trust me I tried a lot of them ;) )

Thanks for anyone who helps!!

---

### Post by Zulu-Zeffir on 2009-04-12
Check this out, last thread in the post. 

[http://ubuntuforums.org/showthread.php?t=935708&page=2]("http://ubuntuforums.org/showthread.php?t=935708&page=2")

---

### Post by johnsonnoob on 2009-04-13
alright...well I tried that, along with another 5 or so methods that I hadn't tried yet, and pretty much got myself deeper into a hole...so I'm currently uninstalling and going to reinstall Ubuntu, start from scratch and see what I can do..

Thanx for your help!  I'll update u on how it goes :)

---

