---
title: "IPv6 with miredo: &quot;connect: Cannot assign requested address&quot;"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by Calimo on 2010-12-18
Hello,

I have Lucid (10.04.1) connected to a wireless LAN behind NAT. My ISP doesn't provide IPv6 (and my router probably doesn't support it anyway) so I installed miredo to get IPv6 connectivity.

Unfortunately it doesn't work. When I try to ping6  ipv6.google.com:
```
socket/connect: Cannot assign requested address
```

```
xavier@ubuntu:/etc/miredo$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:a9:c2:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15585 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3491320 (3.4 MB)  TX bytes:3491320 (3.4 MB)

teredo    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1280  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:0b:24:9c  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:752192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1138889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:107678548 (107.6 MB)  TX bytes:1625885090 (1.6 GB)

```eth0 isn't plugged. It looks like teredo has no IP address assigned. However if I sudo /etc/init.d/miredo restart I get no error message on the console; in syslog I can read:```
Dec 18 14:17:50 ubuntu miredo[4230]: Exiting on signal 15 (Terminated)
Dec 18 14:17:50 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/teredo, iface: teredo)
Dec 18 14:17:50 ubuntu miredo[4230]: Child 4231 exited (code: 0)
Dec 18 14:17:50 ubuntu miredo[4230]: Terminated with no error.
Dec 18 14:17:51 ubuntu miredo[4574]: Starting...
Dec 18 14:17:51 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/teredo, iface: teredo)
Dec 18 14:17:51 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/teredo, iface: teredo): no ifupdown configuration found.
Dec 18 14:17:51 ubuntu kernel: [23993.731686] teredo: Disabled Privacy Extensions
Dec 18 14:17:52 ubuntu miredo[4576]: New Teredo address/MTU
Dec 18 14:17:52 ubuntu miredo[4576]: Teredo pseudo-tunnel started
Dec 18 14:17:52 ubuntu miredo[4576]:  (address: 2001:0:53aa:64c:206a:471e:aafd:40b1, MTU: 1280)
```There is this "no ifupdown configuration found" message, but I don't know what it means…

What's wrong and what should I do to fix it?

Thanks,
Calimo

---

### Post by lemming465 on 2010-12-19
The "*socket/connect: Cannot assign requested address*" error suggests that the inet6 protocol family isn't loaded.  Maybe try:```

sudo modprobe ipv6
sudo /etc/init.d/miredo restart
```
Normally on v6-enabled systems the interfaces such as wlan0 would show an IPv6 link-local address starting with FE80::/64.

---

### Post by Calimo on 2010-12-19
Thanks for your help.
I tried that (got a "WARNING: All config files need .conf: /etc/modprobe.d/blacklist.local, it will be ignored in a future release."), but I still don't see an address in the teredo interface and I still get the same message upon ping6.

Any other idea?

---

### Post by lemming465 on 2010-12-20
What is in /etc/modprobe.d/blacklist.local?  Key things to watch for would be *alias ipv6* or *alias net-pf-10* lines anywhere in /etc/modprobe.conf or /etc/modprobe.d/*, particularly if they blacklisted those to "/bin/true" or "off".

---

### Post by Calimo on 2010-12-26
Thanks for your help and sorry for the delay.
The "blacklist ipv6" in blacklist.local is commented out (line starts with #). I found no line starting with "alias" (maybe I should look elsewhere?)

```
xavier@ubuntu:/etc/modprobe.d$ grep ipv6 *
blacklist.local:#blacklist ipv6
xavier@ubuntu:/etc/modprobe.d$ grep "net-pf" *
xavier@ubuntu:/etc/modprobe.d$ grep ^alias *

```

Here is the full content of blacklist.conf if it can help:
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

Any other idea?

---

