---
title: "wifi issue in Server 12.04 on WPA2"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by benwayj on 2013-02-09
This is a newly installed version of Ubuntu server 12.04 without a desktop running on an itx system with a intel 1000 centrino-n wireless mini pcie card.

I've been following some different tutorials to get this working but they seem pretty inconsistant and nothing has worked for me so far.  Anyways here is what I've got so far.

I've edited my /etc/wpa_supplicant.conf file to read:
```
ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="<mySSID>"
	psk="<myWPA2pass>"
	key_mgmt=WPA-PSK
	proto=RSN WPA
	pairwise=CCMP TKIP
	group=CCMP TKIP
}
```

first ```
sudo ifconfig wlan0 up
```

then ```
sudo wpa_supplicant -B -dd -D wext -i wlan0 -c /etc/wpa_supplicant.conf
```

I captured the output from that in a log file here:
```

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=6):
     53 6b 79 6e 65 74                                 Skynet          
PSK (ASCII passphrase) - hexdump_ascii(len=9): [REMOVED]
key_mgmt: 0x2
proto: 0x3
pairwise: 0x18
group: 0x18
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Skynet'
WEXT: cfg80211-based driver detected
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
netlink: Operstate: linkmode=1, operstate=5
Own MAC address: e0:94:67:07:23:d4
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=4 set_tx=0 seq_len=0 key_len=0
Driver did not support SIOCSIWENCODEEXT
wpa_driver_wext_set_key: alg=0 key_idx=5 set_tx=0 seq_len=0 key_len=0
Driver did not support SIOCSIWENCODEEXT
wpa_driver_wext_set_countermeasures
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): bd 7e 51 55 5d b1 5f 19 8d 72 98 35 27 d1 bc 46
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: Supplicant port status: Unauthorized
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: Supplicant port status: Unauthorized
EAPOL: Supplicant port status: Unauthorized
Using existing control interface directory.
ctrl_iface bind(PF_UNIX) failed: Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

Failed to add interface wlan0
No keys have been configured - skip key clearing
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portValid=0
EAPOL: Supplicant port status: Unauthorized
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
netlink: Operstate: linkmode=0, operstate=6
```

last I run: ```
sudo dhclient wlan0
``` and get this read out:
```
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
```

when I use ifconfig to look at my devices, wlan0 has the ip that my router is set to give to its hardware address but there seems to be no connectivity.

Any ubunutu/debian vets out there with an idea for me?  I'm stuck!

---

### Post by chili555 on 2013-02-09
That seems like the long way around. I suggest you edit /etc/network/interfaces to something like:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-essid <mySSID>
wpa-psk <myWPA2pass>
dns-nameservers 192.168.1.1 8.8.8.8
```Then restart the interface:```
sudo ifdown wlan0 && sudo ifup wlan0
```See if you are connected:```
ping -c3 www.google.com
```Actually, I'd set a proper static IP in preference to address reservations in the router. But hey, I'm old skool!

---

### Post by benwayj on 2013-02-09
I've already tried that, I don't think its going to be that simple.   It's my understanding that I'll need wpa_supplicant since its wpa2.  I  did what you asked, no connectivity but here is what ifconfig prints:
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3968 (3.9 KB)  TX bytes:3968 (3.9 KB)

wlan0     Link encap:Ethernet  HWaddr e0:94:67:07:23:d4  
          inet addr:10.10.99.132  Bcast:10.10.99.255  Mask:255.255.255.0
          inet6 addr: fe80::e294:67ff:fe07:23d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69282 (69.2 KB)  TX bytes:20369 (20.3 KB)

```

---

### Post by chili555 on 2013-02-09
> I've already tried that, I don't think its going to be that simple.Really? It seems to be that simple on my machine right here and right now.> wlan0     Link encap:Ethernet  HWaddr e0:94:67:07:23:d4  
          inet addr:10.10.99.132  Bcast:10.10.99.255  Mask:255.255.255.0
          inet6 addr: fe80::e294:67ff:fe07:23d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69282 (69.2 KB)  TX bytes:20369 (20.3 KB)Looks perfect to me. What does ping tell you?```
ping -c3 www.google.com
```Obviously, your dns-nameservers will be something more like:```
dns-nameservers 10.10.99.1 [COLOR="Red"]<--or whatever your gateway is[/COLOR] 8.8.8.8
```If you didn't connect, where did the address come from? The router, yes??

---

### Post by benwayj on 2013-02-09
Exactly why I'm confused.  Its clearly working well enough to get its ip from my router but there isn't normal connectivity.

ping -c3 [www.google.com](www.google.com) returns:
```
ping: unknown host www.google.com
```

---

### Post by chili555 on 2013-02-09
Using your method or my method? If yours, where and how are DNS nameservers declared?

---

### Post by benwayj on 2013-02-10
As far as I can tell both methods yield the same result.  It works well enough to get an IP, but doesn't display any connectivity.

I declared my nameservers like this
```
dns-nameservers 10.10.99.1 8.8.8.8
```
10.10.99.1 is the ip for my router

---

### Post by chili555 on 2013-02-10
May we see:```
route -n
```Can you ping the router?```
ping -c3 10.10.99.1
```And how about Google's DNS nameserver?```
ping -c3 8.8.8.8
```Where does the router get its DNS nameservers? From your ISP? Or...?

What is the similar information on another computer on the same network? ifconfig /a is it??

---

### Post by benwayj on 2013-02-10
route -n output:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.99.1      0.0.0.0         UG    100    0        0 wlan0
10.10.99.0      0.0.0.0         255.255.255.0   U     0      0        0 wlan0
```

ping -c3 10.10.99.1 results in zero packets received, same for pinging 8.8.8.8

The router does get its nds from my ISP.  First dns is set to 192.168.0.1 (modem) and the second one is 205.171.3.25 (century link)

Here is the output from ifconfig -a on a different machines, same network:
```
eth0      Link encap:Ethernet  HWaddr 50:e5:49:3f:fe:b5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25962 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2536793 (2.5 MB)  TX bytes:2536793 (2.5 MB)

wlan0     Link encap:Ethernet  HWaddr f8:d1:11:cd:86:9a  
          inet addr:10.10.99.100  Bcast:10.10.99.255  Mask:255.255.255.0
          inet6 addr: fe80::fad1:11ff:fecd:869a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2623857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1484485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3675415276 (3.6 GB)  TX bytes:152774992 (152.7 MB)

```

Thank you so much for your assistance and patience thus far.

---

### Post by benwayj on 2013-02-10
Any thoughts team?  I'm still lost!

---

### Post by chili555 on 2013-02-10
Please let me see:```
cat /etc/network/interfaces
cat /etc/resolv.conf
```Thanks.

---

### Post by varanasi on 2013-02-11
Please keep trying to get this solved and posting here!

I, too, am interested in how this gets solved.  There are literally dozens of posts concerning this issue -- many without solutions.  I haven't been able to get wpa2 working despite trying many different things.

---

### Post by chili555 on 2013-02-11
> **varanasi said:**
> Please keep trying to get this solved and posting here!

I, too, am interested in how this gets solved.  There are literally dozens of posts concerning this issue -- many without solutions.  I haven't been able to get wpa2 working despite trying many different things.Including my proposal in post #2? Can you verify your card actually does WPA2?```
sudo iwlist wlan0 auth
```...assuming your wireless interface is wlan0; verify:```
iwconfig
```

---

### Post by benwayj on 2013-02-11
I've done as you've asked.  Here is my /etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Intel 1000 Centrino Wireless-N
auto wlan0
iface wlan0 inet dhcp
wpa-essid <nameofmyssid>
wpa-psk <mypassword>
dns-nameservers 10.10.99.1 8.8.8.8
```

And here is my resolv.conf file:
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 10.10.99.1
nameserver 8.8.8.8
```

Any thoughts?

---

### Post by chili555 on 2013-02-11
Please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
sudo ifdown wlan0 && sudo ifup wlan0
ping -c3 8.8.8.8
```Thanks.

---

### Post by benwayj on 2013-02-11
Works!  that did the trick!  Only issue is it didn't last of course.

For sake of documentation, I fixed it permently by creating a new file:
```
sudo vi /etc/modprobe.d/iwlwifi.conf
```

and using the vi editor I wrote the line:
```
options iwlwifi 11n_disable=1
```

then saved and rebooted.

Thank you so much chili555!  You and those like you are the guys that make this the best OS in the world.  What does this option even do?

---

### Post by chili555 on 2013-02-12
> **benwayj said:**
> What does this option even do?As it implies, it disables 802.11N capability; only A, B and G will work now. Working G is faster than not-working N anyway.

Sorry I didn't realize it earlier. I didn't connect server on a laptop, although they sometimes are!

---

