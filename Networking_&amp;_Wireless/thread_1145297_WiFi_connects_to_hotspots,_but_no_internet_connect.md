---
title: "WiFi connects to hotspots, but no internet connection"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by CA_Warren on 2009-05-01
Upgraded to 9.04 yesterday, and everything worked great. Wireless networking included.

Today, though I could connect to any of a dozen of local wifi networks, I had no internet access through them (the new plasmoid says I'm connected, but Firefox and the update manager can't connect to anything on the interwebs). I installed knetworkmanager, since I know the new plasmoid has some glitches, but am having the same problem. Wired networking works just fine. Rebooting didn't help.

Looked through the forums, and every other time this has happened it's been a firewall issue - but I haven't installed any, nor activated ufw. 

Specs:
Lenovo Thinkpad R61i
Kubuntu 9.04
Wireless Card: Intel PRO/Wireless 3945ABG [Golan]

Any thoughts/ideas would very much be appreciated. I wasn't able to make anything out of the following output, but maybe someone else will be able to:

Output for ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1c:25:93:a0:42                                                        
          UP BROADCAST MULTICAST  MTU:1500  Metric:1                                                           
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0                                                   
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                                                 
          collisions:0 txqueuelen:1000                                                                         
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)                                                               
          Interrupt:18                                                                                         

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:720 errors:0 dropped:0 overruns:0 frame:0
          TX packets:720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:53256 (53.2 KB)  TX bytes:53256 (53.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:91:b3:76
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe91:b376/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31684 (31.6 KB)  TX bytes:63080 (63.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-91-B3-76-33-37-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Output for 'ping [www.google.com](www.google.com)' (same as output for 'ping -c3 [www.google.com'):](www.google.com'):)
```
ping: unknown host www.google.com
```

Output for 'nslookup [www.google.com':](www.google.com':)
```
;; connection timed out; no servers could be reached
```

Output for 'ping 192.168.1.1' (the router):
```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=5.47 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=10.2 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=3.83 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=8.24 ms
[etc.]
--- 192.168.1.1 ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 11017ms
rtt min/avg/max/mdev = 2.824/4.927/10.271/2.220 ms
```

Output from iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"NETGEAR"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:2A:75:6F:E0
          Bit Rate=24 Mb/s   Tx-Power=14 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality=40/100  Signal level:-85 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

Output from 'dmesg | tail' right after connecting to a network and trying to load a web page:
```
[ 3272.687205] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3282.560565] wlan0: disassociating by local choice (reason=3)
[ 3283.112020] wlan0: no IPv6 routers present
[ 3284.368510] wlan0: deauthenticated
[ 3284.372886] wlan0: authenticate with AP 00:1e:2a:75:6f:e0
[ 3284.376166] wlan0: authenticate with AP 00:1e:2a:75:6f:e0
[ 3284.376193] wlan0: authenticated
[ 3284.376201] wlan0: associate with AP 00:1e:2a:75:6f:e0
[ 3284.381205] wlan0: RX AssocResp from 00:1e:2a:75:6f:e0 (capab=0x401 status=0 aid=1)
[ 3284.381211] wlan0: associated

```


Any and all help is very much welcome.

---

### Post by chili555 on 2009-05-01
Open a terminal and do:```
sudo mv /etc/resolv.conf /etc/resolv.conf.bak
echo "nameserver 192.168.1.1" | sudo tee /etc/resolv.conf
```Now can you surf?

---

### Post by CA_Warren on 2009-05-01
Thanks for the quick response, chili555. That didn't fix the issue, unfortunately. 

I checked the iptables too, and they don't seem to be doing anything. Starting apps with root access also doesn't fix it, so it can't be a permissions issue...

Any other thoughts on what could cause this? Is there any way to trace the request to see if it gets to the router (to check if the problem's outbound or inbound)?

---

### Post by CA_Warren on 2009-05-01
New Info:

I reinstalled Kubuntu 9.04, wiping the old / partition, and the problem continues.

Either the problem is with the initial setup (unlikely; everyone has this chipset), *or* the problem is on the /home partition.

This should narrow possibilities. Any new thoughts/ideas?

---

### Post by chili555 on 2009-05-01
> everyone has this chipsetIncluding me. Do other internet protocols work? For instance, can you:```
sudo apt-get update
```Have you tried Pidgin? How about:```
wget www.google.com
```In Firefox -> Edit -> Preferences -> Advanced -> Network how does it say Firefox connects to the internet? Can you get a web page by IP address, such as [http://74.125.65.147](http://74.125.65.147) manually typed into the address bar of Firefox?

By the way, I am running low on ammo.

---

### Post by abn91c on 2009-05-01
are you using the new network plasmoid? had same issue, that resolved it for me

---

