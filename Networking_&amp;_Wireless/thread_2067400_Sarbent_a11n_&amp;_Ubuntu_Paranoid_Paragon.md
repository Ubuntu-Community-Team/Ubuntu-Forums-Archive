---
title: "Sarbent a11n &amp; Ubuntu Paranoid Paragon"
date: 2012-10-06
forum: Networking &amp; Wireless
---

### Post by ohgodwhy on 2012-10-06
Hey there, first, let me say thanks for reviewing my question.

I've been tackling trying to get this Ubuntu 12.04 precise pangolin machine connected via wifi for the better part of a week. Let me preface the next paragraph by noting that I am by no means an expert in linux.

I unfortunately do not possess the ability to connect directly to my router with a wired connection; this has compounded my issue. I've tried connecting to my network with several different wifi cards before finally reviewing a list of supported devices out of the box. 

I went down to my local store and picked up a Sarbent a11n which said it was supported (Ralink chipset of some sort? rtl8192cu?). 

Anyway, I came home and plugged'er in. Right out of the box it worked and found my network. I attempted to connect to it and it and it attempts, then says disconnected. It does this quite a few times before it no longer attempts a connection.

I've done sudo cat /var/log/syslog | grep -e ipw -e firmware -e wpa -e wlan -e etork | tail n-55 and see that it continually faces a warning:

ggtr-server networkmanager[626]: <warn> Actvation (wlan1) failed for access point (belkin.2ca), which is prefaced by:

ggtr-server networkmanager[626]: <warn> Activation (wlan1/wireless): association took too long, failing activation.

Here's the output from the requested commands to be included when posting for help (Sorry if mispelled in some areas, had to type it out by hand)

```
Machine Brand / Model -- Dell Dimension 4600 Mini Tower
```

```
Wireless Brand / Model -- Bus 001 Device : ID 0bda:8176 RTL8188CUS 802.11n WLAN
```

```
ifconfig:

wlan1 
    
    Link encap:Ethernet HWaddr 00:09:c9:19:a2:5e
    inet6 addr: fe80::209:c9ff:fe19:a25e/64 scope:Link
    UP BROADCAST MJULTICAST MTU:1500 Metric:1
    RX packets:0 errors:0 dropped:0 overruns:0 frame:0
    TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000
    rx bytes:0 (0.0 b) TX bytes:6988 (6.9 KB)
```

```
iwconfig:

wlan1

    IEEE 802.11bgn ESSID:off/any
    Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
    Try long limit:7  RTS thr=2347 B Fragment thr:off
    Power Management:off
```

```
lsmod | grep "wlan" produced no matching results.
```

```
sudo lshw -C network

    *-network
        description: Wirelesst Interface
        physical id: 1
        bus info: usb@1:3
        logical name: wlan1
        serial: 00:09:c9:19:a2:5e
        capabilites: ethernet physical wireless
        configuration: brodcast=yes driver=rtl8192cu driverversion=2.3.0-29-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
```

```
sudo iwlist scan wlan1:

    wlan1 No scan results
```

```
lsb_release -d
  
    Description:    Ubuntu 12.0.1 LTS
```

```
uname -r

    3.2.0-29-generic-pae i686
```

```
sudo /etc/init.d/networking restart

    (some message about deprecation)
    * Reconfiguring Network interfaces.... [ OK ]  
```

Any thoughts would be greatly appreciated.

---

### Post by ohgodwhy on 2012-10-06
Anyone? Please. I've been at my wit's end for quite some time and I'm running out of possibilities. I am having difficulties trying to compile from the source against my kernel.

Any documentation or links would be helpful as a week's worth of googling and reinstalling and trying everything known-to-me has been in vain.

Thank you.

---

### Post by ohgodwhy on 2012-10-06
Apparently the distance from the router was too great. I was about 20 feet away, I've since moved the machine into a room that's a bit closer and low-and-behold it connected instantly with NO issues what so ever.

It sucks that I made this post and it will likely not be relevant for users in the future.

Maybe a mod can delete it.

Thank you anyway.

---

