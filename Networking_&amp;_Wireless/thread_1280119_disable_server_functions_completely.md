---
title: "disable server functions completely"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by Rainbowsix on 2009-10-01
My internet has been acting weird ever since I tried doing this:
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

I tried to roll back all the changes. I think I succeeded, but I'm not sure. I no longer want my computer to be a host, server, etc. I connect to a wireless router.

ifconfig:
> lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13728 (13.7 KB)  TX bytes:13728 (13.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:1d:93:52:07  
          inet addr:192.168.1.121  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe93:5207/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21709989 (21.7 MB)  TX bytes:3582762 (3.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-1D-93-52-07-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwconfig:
> lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Skooter"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:F0:F7:46:A1   
          Bit Rate=54 Mb/s   Tx-Power=7 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=68/100  Signal level:-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


iptables -L
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

---

### Post by dummy910 on 2009-10-01
>  I no longer want my computer to be a host, server, etc. I connect to a wireless router.
You just need to turn off a few services. My favorite tool for service management in **gnome** is called **Bum**.
```
sudo apt-get install bum
```
this will place an icon on your System>Administrator menu titled "BootUp-Manager" and from there your just a few clicks away from disabling **avahi-daemon**, **samba** and whatever other services you don't want or need running. Carefull though, one wrong move and you could cripple things ;)

---

### Post by Rainbowsix on 2009-10-02
Is there a way of flushing ifconfig?

---

### Post by dummy910 on 2009-10-02
> Is there a way of flushing ifconfig?     to shut down the [COLOR=red]eth0[/COLOR](red=network device) interface & _**release**_ the IP
*```
sudo ifconfig [COLOR=red]eth0[/COLOR] down
```*
to re-enable the [COLOR=red]eth0[/COLOR] interface & **_renew_** the IP
 *```
sudo ifconfig [COLOR=red]eth0[/COLOR] up
```*

---

