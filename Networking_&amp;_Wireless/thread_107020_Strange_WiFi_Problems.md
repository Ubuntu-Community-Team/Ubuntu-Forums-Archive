---
title: "Strange WiFi Problems"
date: 2005-12-22
forum: Networking &amp; Wireless
---

### Post by foo-bar on 2005-12-22
Hello

I have a broadcom wireless chipset (BCM4306), and I am having some strange wireless problems.  I have ndiswrapper installed, and I am using the bcmwl5a.inf file with it (I have also tried bcmwl5.inf).  Either way, ndiswrapper -l reports that the driver was installed and the device was found.

The problem is that I am unable to connect to any outside network (although everything I have looked at indicates that the wireless network is detected and I have connected to the router and retrieved a local IP address via DHCP).

lspci -v has the following result:
```

0000:00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
        Subsystem: Compaq Computer Corporation: Unknown device 00e7
        Flags: bus master, fast devsel, latency 64, IRQ 10
        Memory at d0002000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

```

here is the output from iwconfig:

```
wlan0     IEEE 802.11g  ESSID:"default"  Nickname:"default"
          Mode:Auto  Frequency:2.437 GHz  Access Point: 00:80:C8:1D:A8:6D
          Bit Rate=11 Mb/s   Tx-Power:25 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-41 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1497   Missed beacon:0
```

any ideas?:confused: 

(PS. Sorry about any spelling errors.. it's 2:32 AM and I'm really tired :))

---

### Post by localzuk on 2005-12-22
Can you ping anything on your local network? Such as your router? If you can then it is likely that you do not have DNS/gateway settings being sent via DHCP and need to manually set them up.

---

### Post by greenway on 2005-12-22
[QUOTE=localzuk]Can you ping anything on your local network? Such as your router? If you can then it is likely that you do not have DNS/gateway settings being sent via DHCP and need to manually set them up.[/QUOTE]

Pingin' hosts on the local network wouldn't tell you much about correct DNS configuration. He shouldn trying to ping outside the local network, if this works and normal webbrowsing doesn't work, it's probably a DNS issue.

But just to check; are you sure you have received a network configuration from you DHCP server? I mean did you use ifconfig to check if your NIC has received an IP address?

Are the lights on your NIC on or blinking?

Can you give the output of this command: "sudo ifup wlan0"

---

### Post by localzuk on 2005-12-22
My question was to find out if he could receive local data. If he could then it is not a network connectivity issue/routing issue on the local machine.

If he can ping a local machine, and not an external one then he will have dns/gateway issues - as was stated in my post.

---

### Post by foo-bar on 2005-12-22
Well, this is really strange.. my wireless is working without issue now...

but anyways, here are the results of what you've asked me:

ping -c3 192.168.0.1

```

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=127 time=1.30 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=127 time=1.25 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=127 time=1.25 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 1.251/1.270/1.301/0.036 ms

```

ifconfig wlan0

```

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:4A:4A:F6
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe4a:4af6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:551720 (538.7 KiB)  TX bytes:38745 (37.8 KiB)
          Memory:d0002000-d0003fff

```

sudo ifup wlan0

```

/etc/network/interfaces:23: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"

```

well, at least it's working now, even though I have no idea why or how (I went to sleep last night with no working wlan, and now it's working)

---

