---
title: "Wireless at boot time"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by God Of Atheism on 2009-02-22
Hi,

I'm trying to set up the wlan for my parents in law, and though I've managed to get it working, I haven't managed to get it to start when logging in (or earlier).
Hardware: Dell Vostro A860 with Ubuntu 8.04 preinstalled.
generic RTA 1025W wireless router. (after I discovered I had to go to 10.0.0.138 instead of 192.168.1.1 as given in the IE instructions, I could set it up)
The router can have both wired and wireless connections. Connection is via pppoe which works and continues to work, the problems are with the wireless part. I set the following on the router:
transmission mode: mixed 802.11b/g
channel: best quality
transmission rate: auto
multicast rate: auto
turbo mode: enabled

security:
wpa pre-shared key, format ascii

when setting the computer to roaming, I can connect to the network, but have to enter the key.
So in order to not have to do so and have the computer connect to the network at boot time, I tried to change /etc/network/interfaces to:
```

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid [essid]
wireless-key [key]
wireless-channel auto
wireless-mode ad-hoc

```
[essid] and [key] are as on the router.

This way, when rebooting and logging in, I get no network connection, but the network icon is as if there is a network connection (though it's displayed as a regular wired network connection, not the signal strength of the wireless). Pinging also does not lead to an immediate unknown host, but rather an eventual time-out.

What do I need to change to get it working (wireless connection upon log in)?
In addition, is there some source of all the different options (both wired and wireless, ip4 and ip6, etc) one can set in /etc/network/interfaces ? (man doesn't cut it)

Thanks

---

### Post by abyssius on 2009-02-22
> **God Of Atheism said:**
> Hi,

I'm trying to set up the wlan for my parents in law, and though I've managed to get it working, I haven't managed to get it to start when logging in (or earlier).
Hardware: Dell Vostro A860 with Ubuntu 8.04 preinstalled.
generic RTA 1025W wireless router. (after I discovered I had to go to 10.0.0.138 instead of 192.168.1.1 as given in the IE instructions, I could set it up)
The router can have both wired and wireless connections. Connection is via pppoe which works and continues to work, the problems are with the wireless part. I set the following on the router:
transmission mode: mixed 802.11b/g
channel: best quality
transmission rate: auto
multicast rate: auto
turbo mode: enabled

security:
wpa pre-shared key, format ascii

when setting the computer to roaming, I can connect to the network, but have to enter the key.
So in order to not have to do so and have the computer connect to the network at boot time, I tried to change /etc/network/interfaces to:
```

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid [essid]
wireless-key [key]
wireless-channel auto
wireless-mode ad-hoc

```
[essid] and [key] are as on the router.

This way, when rebooting and logging in, I get no network connection, but the network icon is as if there is a network connection (though it's displayed as a regular wired network connection, not the signal strength of the wireless). Pinging also does not lead to an immediate unknown host, but rather an eventual time-out.

What do I need to change to get it working (wireless connection upon log in)?
In addition, is there some source of all the different options (both wired and wireless, ip4 and ip6, etc) one can set in /etc/network/interfaces ? (man doesn't cut it)

Thanks

Is there a reason why you are using ad-hoc mode? This isn't the usual way of connecting with a router. Maybe you should try changing this parameter to 'infrastructure' and see what happens.

---

### Post by Joe2Shoe on 2009-02-22
That's right.  Change from 'ad-hoc' to 'infracstructure' and save your connection settings and that should do it.

---

### Post by God Of Atheism on 2009-02-23
Thanks, I tried this now, but it still doesn't work. (I also already tried managed mode earlier on to no avail)

Output from iwconfig:
```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"[essid]"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-100 dBm  Noise level=-100 dBm
          Rx invalid nwid:93  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
Note that ifconfig gives both ath0 (with ip6 address) and ath0:avahi (with ip4 address). Is that supposed to be so?
```

$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:17:c4:4f:ac:40  
          inet6 addr: fe80::217:c4ff:fe4f:ac40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ath0:avahi Link encap:Ethernet  HWaddr 00:17:c4:4f:ac:40  
          inet addr:169.254.6.125  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:21:70:8e:d9:ca  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1285755347 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86808 (84.7 KB)  TX bytes:86808 (84.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-17-C4-4F-AC-40-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113 errors:0 dropped:0 overruns:0 frame:18
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:195 
          RX bytes:12658 (12.3 KB)  TX bytes:6145 (6.0 KB)
          Interrupt:17 


```

---

### Post by God Of Atheism on 2009-02-23
Bump

---

### Post by abyssius on 2009-02-23
> **God Of Atheism said:**
> Bump

Are you trying to connect to the router with an ethernet cable and a wireless link at the same time? if so, try disconnecting the ethernet cable and see what happens. I also noticed your wireless adapter is not associated with an access point. You will not be able to connect wirelessly this way, You could try forcing a connection by issuing this command:

```
iwconfig ath0 ap *mac_address_of_your_router*
```

---

### Post by abyssius on 2009-02-23
Regarding IPV6, maybe you should disable IPV6 to help you to troubleshoot. This link shows you how:

[http://ubuntuforums.org/showthread.php?t=6841]("http://ubuntuforums.org/showthread.php?t=6841")

---

### Post by God Of Atheism on 2009-02-23
> **abyssius said:**
> Are you trying to connect to the router with an ethernet cable and a wireless link at the same time? if so, try disconnecting the ethernet cable and see what happens. I also noticed your wireless adapter is not associated with an access point. You will not be able to connect wirelessly this way, You could try forcing a connection by issuing this command:

```
iwconfig ath0 ap *mac_address_of_your_router*
```

No, I did not connect the ethernet while trying to connect wirelessly.

I tried the command above, but got an error:
ath0 Interface does not support MAC addresses

I then read the man page for iwconfig and tried using essid instead of ap, and now got SET failed on device ath0 ; no such device

This seemed strange, so I checked and found that typing in iwconfig showed wlan0 instead of ath0, and wmaster0 instead of wifi0

I changed /etc/network/interfaces to include wlan0 instead of ath0.

The output from ifconfig is the same as in my first post (but with ath0 replaced by wlan0, ath0:avahi replaced by wlan0:avahi, and wifi0 replace by wmaster0), except that wlan0 does not get any ip address, nor ip4, nor ip6, it only has a MAC address, wlan0:avahi still gets an ip4 address. Note that this is when not having any connection to the network.

After connecting to the wireless network, the output from iwconfig seems unchanged, but from ifconfig, wlan0:avahi disappears, and wlan0 gets both an ip4 and an ip6 address.

I'll have a look at turning of ip6, as you suggested, and see whether it helps.

Thanks

---

### Post by God Of Atheism on 2009-02-23
> **abyssius said:**
> Regarding IPV6, maybe you should disable IPV6 to help you to troubleshoot. This link shows you how:

[http://ubuntuforums.org/showthread.php?t=6841]("http://ubuntuforums.org/showthread.php?t=6841")

I tried this, and though it might help to troubleshoot, it does not by itself solve the issue.

Thanks

---

### Post by God Of Atheism on 2009-02-24
Bump

---

### Post by abyssius on 2009-02-24
> **God Of Atheism said:**
> Bump

I've been thinking about the IPV6 address issue. Ubuntu doesn't provide IP addresses. You must be getting that IP address from the DHCP server built into your router. Therefore, I'm assuming that the router must be operating in IPV6 mode. I'd try to disable this function in the router if this is possible. If you can get your set-up to operate in IPV4 only, resolving this issue will be greatly simplified. If the driver for your wireless card is valid, all you should have to do to get on the Internet is set the appropriate parameters in the interfaces file.

```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid *essid_name*
wireless-channel 6
wireless-mode managed
gateway 192.168.1.1

auto wlan0

```

This is my interfaces file. It is simple and it works perfectly. I probably don't even need the gateway line in it. This is all you should have to do to get online. I also don't have the default network-manager app or any other wifi management app installed.

---

### Post by God Of Atheism on 2009-02-26
> **abyssius said:**
> I've been thinking about the IPV6 address issue. Ubuntu doesn't provide IP addresses. You must be getting that IP address from the DHCP server built into your router. Therefore, I'm assuming that the router must be operating in IPV6 mode. I'd try to disable this function in the router if this is possible. If you can get your set-up to operate in IPV4 only, resolving this issue will be greatly simplified. If the driver for your wireless card is valid, all you should have to do to get on the Internet is set the appropriate parameters in the interfaces file.

```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid *essid_name*
wireless-channel 6
wireless-mode managed
gateway 192.168.1.1

auto wlan0

```

This is my interfaces file. It is simple and it works perfectly. I probably don't even need the gateway line in it. This is all you should have to do to get online. I also don't have the default network-manager app or any other wifi management app installed.

I returned the laptop to them with this issue unsolved, so I'll try next time I visit them whether gateway helps. Also does it matter whether you have the auto wlan0 at the beginning of the wlan0 block or at the end?

---

