---
title: "Ubuntu 9.04 Wireless stopped working"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by uo2000 on 2009-09-09
My wireless stopped working a while back. 
I can ping my router at 192.168.0.1.
As I can tell I should only have one of wlan0, wmaster0.

Hope someone can shed some light in this.

Best regards
Ulf

Here comes the results from  lshw, iwconfig, ifconfig

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:4f:e8:15
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.2 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 00
       serial: 00:16:36:e1:d2:f3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.5-1 latency=0 module=e1000e multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0a:eb:8e:6d:09:67
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Wireless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:51:EE:A6   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=74/100  Signal level:-60 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:e1:d2:f3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Minne:da000000-da020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:680 (680.0 B)  TX bytes:680 (680.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:4f:e8:15  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe4f:e815/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:353536 (353.5 KB)  TX bytes:170806 (170.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-4F-E8-15-38-31-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by chili555 on 2009-09-09
> wlan0 Link encap:Ethernet HWaddr 00:19:d2:4f:e8:15
inet addr:192.168.0.2 Bcast:192.168.0.255 Mask:255.255.255.0
[COLOR="Red"]RX bytes:353536 (353.5 KB) TX bytes:170806 (170.8 KB)[/COLOR]
Looks like its working to me! Is 192.168.0.2 a static IP address you set? Did you forget to set the DNS nameservers? May we please see the result of:```
ping -c3 74.125.45.147
ping -c3 www.google.com
cat /etc/resolv.conf
```The existence of *wmaster0* is normal and can safely be ignored.

---

### Post by uo2000 on 2009-09-10
> **chili555 said:**
> Looks like its working to me! Is 192.168.0.2 a static IP address you set? Did you forget to set the DNS nameservers? May we please see the result of:```
ping -c3 74.125.45.147
ping -c3 www.google.com
cat /etc/resolv.conf
```The existence of *wmaster0* is normal and can safely be ignored.

192.168.0.2 is from my router.
In the router DHCP is set "automatic from my ISP"
In the router DNS is set "automatic from my ISP"

The reason there was traffic on wlan0 is because I went to 192.168.0.1 (in my browser) to se the settings for my router, and this works. I am confused why it does not work on other internet addresses.
I can not reach other computer shares as well.
It works when I put in a network cable.

I tried both ping's to google without any luck.

I have not tried cat to se the nameservers

I will give the results from the ping commands and the contents from /etc/resolv.conf when I get home

Would it help if I gave the name of the wireless driver and the make of the netgear router?

A few updates ago it worked, and it works on two other computers we have.

regards
Ulf

---

### Post by chili555 on 2009-09-10
> Would it help if I gave the name of the wireless driver and the make of the netgear router?I think, for now, we have what we need, after we see */etc/resolv.conf*.> *-network
description: Wireless interface
product: PRO/Wireless 3945ABG [Golan] Network Connection
vendor: Intel Corporation
   ...
configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR] ip=192.168.0.2 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abgIt may be no surprise that I am answering this post from my Intel 3945ABG equipped laptop. Some of us tend to answer posts about gear we understand.

I'd also love to see the result of:```
sudo /etc/init.d/networking restart
```

---

### Post by chili555 on 2009-09-10
> 192.168.0.2 is from my router.
In the router DHCP is set "automatic from my ISP"
In the router DNS is set "automatic from my ISP"Sorry if I was not clear. How did 192.168.0.2 get in you *computer*? When you right-click Network Manager, select 'Edit Connection' then "Wireless' and you edit wlan0, do you have this set to manual or DHCP. If it is manual, I'd suggest DHCP. Then restart networking:```
sudo /etc/init.d/networking restart
```Are your problems fixed?

---

### Post by uo2000 on 2009-09-10
> **chili555 said:**
> Sorry if I was not clear. How did 192.168.0.2 get in you *computer*? When you right-click Network Manager, select 'Edit Connection' then "Wireless' and you edit wlan0, do you have this set to manual or DHCP. If it is manual, I'd suggest DHCP. Then restart networking:```
sudo /etc/init.d/networking restart
```Are your problems fixed?

These are the results from ping and restarting the network

ulf@ulf-laptop:~$ ping -c3 74.125.45.147
PING 74.125.45.147 (74.125.45.147) 56(84) bytes of data.

--- 74.125.45.147 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

ulf@ulf-laptop:~$ ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
ulf@ulf-laptop:~$ cat /etc/resolv.conf 
# Generated by NetworkManager
nameserver 192.168.0.1
ulf@ulf-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for ulf: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
ulf@ulf-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
ulf@ulf-laptop:~$ 


No luck as you can see.
"unknown interface wlan0=wlan0" bothers me.
I have set DHCP to automatic.
I will now try and remove the wireless setting from Network manager and reboot and try and add it and see how it goes.

...... back
FYI I can get to my router 192.168.0.1 without any wireless configured??
Tried a page, no luck. Wireless was disconnected and then automatically connected, tried again and success!!! (For how long)
Can I in some way execute some commands and try to see what the difference is or should I write it off as temporary insanity?
I am always curious why something happened and how to correct it...

Tried a reboot and it is not working anymore :-(
Perhaps reinstalling Network manager?

Do you happen to know where Network manager is storing its settings?

Some history how I got here:
I have installed 9.04 fresh, wireless is working
I have installed every patch that is recommended from Ubuntu
I tried to play with VPN without success because I missed one piece of information and then never got back to try again, deleted VPN in Network Manager.
Now I have this problem??? Was it VPN, Patching or something else?

Thank you very much for your time.

I just wish I knew the reason...

regards Ulf

---

### Post by chili555 on 2009-09-10
> I just wish I knew the reason...As the saying goes, if it ain't broke, don't fix it. Post back if it doesn't stay "fixed."

Glad it's working now!

---

### Post by uo2000 on 2009-09-10
> **chili555 said:**
> As the saying goes, if it ain't broke, don't fix it. Post back if it doesn't stay "fixed."

Glad it's working now!

Well, it worked until I rebooted.
I looked up on Google about unknown interface wla0=wlan0 and they suggest to edit /etc/network/interfaces

What does your look like?
Mine is simple 
auto lo
iface lo inet loopback

The suggestion was
Okay; start by typing these commands:
sudo ifdown wlan0
sudo iwconfig wlan0 channel [x] essid [essid] mode Managed
sudo ifup wlan0

If you get a line that says something like ignoring unknown interface wlan0=wlan0 then follow these additional steps…
sudo mousepad /etc/network/run/ifstate
Add a line that says “wlan0=wlan0&#8243; (without the quotes), and save.
sudo mousepad /etc/network/interfaces
Add a line that says “iface wlan0 inet dhcp” and save.
sudo ifdown wlan0
sudo ifup wlan0

regards
Ulf

---

### Post by uo2000 on 2009-09-12
I did a complete reset of the netgear router and now wireless is working, so I guess something was not correct in the router.

Thank you for all your help

---

