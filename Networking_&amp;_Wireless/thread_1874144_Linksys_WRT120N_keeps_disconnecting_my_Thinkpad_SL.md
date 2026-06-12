---
title: "Linksys WRT120N keeps disconnecting my Thinkpad SL510 (Ubuntu 11.10)"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by Trolle on 2011-11-02
Hi.

I have no idea what to do, so I will try to share any details I find relevant.

**My setup**
I have a Linksys WRT120N wireless router hooked up to the internet socket in the wall (DSL of some kind). Firmware is v1.0.06. I switched to manual The only change I have made is changing the SSID and set a password.
I have three units:

[LIST]
[*]A MacBook Pro running MacOS.
[*]A HTC phone with Android.
and
[*]A Lenovo Thinkpad SL510 running Ubuntu 11.10 (Oneiric Ocelot).
[/LIST]
**Symptoms**
The MacBook and the phone can be online at the same time - no issues. As soon as the Ubuntu machine connects to the wifi, all units are disconnect within 15-20 seconds. After that the router needs to be switched off and on again to work.
If the Ubuntu machine is connected through cable to the router, everything is fine.

**What I've tried**
I used to run Ubuntu 11.04. I formated my disk and made a fresh install of Ubuntu 11.10.
The router used to run firmware v1.0.01. I updated it to v1.0.06.
I tried to change the Network Mode to Wireless-N technology. It didn't help, so I switched it back to Mixed.
I tried to change the MTU, but switched it back to Auto.

**My guesses**
ISP:
Everything worked fine at my previous flat. The only change since I moved is the ISP. A friend told me that the router should use NAT, and not Bridge (so that the units don't have a public IP). All units have a 192.168.1.* IP address, which should mean that the router should be set up correctly.
If the ISP somehow disables several units, how can the Mac and phone be online at the same time, but the Thinkpad can't?

Driver:
lspci -v gives me:

    ```
05:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at f2200000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn
```According to [http://www.thinkwiki.org/wiki/Intel_Centrino_Wireless-N_1000](http://www.thinkwiki.org/wiki/Intel_Centrino_Wireless-N_1000) there is an issue with the my network card and linux. I tried running
```
modprobe -r iwlagn
modprobe iwlagn

```but it didn't help.
If the driver is the problem it would explain why I also have issues with my Ubuntu machine at my schools wifi. But it does not explain why everything worked flawlessly at my previous flat.

I hope you understand what I tried to explain, and that you can help me.

/Troels

---

### Post by SilvaRizla on 2011-11-02
Are you downloading or something on the Ubuntu machine?  A lot of routers seem to struggle with a lot of connections being made wirelessly to a single machine

---

### Post by Trolle on 2011-11-02
> **SilvaRizla said:**
> Are you downloading or something on the Ubuntu machine?  A lot of routers seem to struggle with a lot of connections being made wirelessly to a single machine
Not that I know of. It's a fresh install of Ubuntu.
The only things I've added are Eclipse, gnome-tweak-tool, Chromium and restricted-extras, but the issue has been there from the beginning.

---

### Post by SilvaRizla on 2011-11-03
I seem to remember back in the Intrepid days at some point I had to set up a small script that pinged my router with 2 packets every 10 seconds and leave that running to stay connected wirelessly, you could try that?

---

### Post by Trolle on 2011-11-03
> **SilvaRizla said:**
> I seem to remember back in the Intrepid days at some point I had to set up a small script that pinged my router with 2 packets every 10 seconds and leave that running to stay connected wirelessly, you could try that?
I tried the following script
```
#!/bin/bash
while [ true ]; do
	ping -c 2 192.168.1.1
done

```
but, with no luck.
Output
```
...

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.617/2.634/2.652/0.054 ms
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=44 time=2.53 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=44 time=41.0 ms

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.531/21.778/41.026/19.248 ms
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=44 time=10.6 ms

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 1 received, 50% packet loss, time 1001ms
rtt min/avg/max/mdev = 10.658/10.658/10.658/0.000 ms
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1008ms

[11 more]

2 packets transmitted, 0 received, 100% packet loss, time 999ms

connect: Network is unreachable
```
I tried in both Firefox and Chromíum.

---

### Post by Trolle on 2011-11-11
I give up.
I have downgraded to 10.04 LTS.

---

### Post by praseodym on 2011-11-11
Hi,

there is a bug with the N-mode in kernel 3. The N-mode needs to be shut off:

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
```
In 10.04 with kernel 2.6.32 it works.

---

### Post by Trolle on 2011-11-16
> **praseodym said:**
> Hi,

there is a bug with the N-mode in kernel 3. The N-mode needs to be shut off:

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
```In 10.04 with kernel 2.6.32 it works.

Thank you.

---

