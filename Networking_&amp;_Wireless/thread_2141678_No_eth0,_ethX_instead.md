---
title: "No eth0, ethX instead"
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by Martin123 on 2013-05-03
Hello,

My eth0 interface always changes its interface name after restart. It can be for example eth3, eth7, eth5,... . Sometimes it's also eth0. And its MAC Address also changes.
Everything else works fine with networking. The only problem is that the Matlab license remembers the MAC Address of the eth0 interface. And since there is non, I always have to activate Matlab when I restart my computer.

ifconfig:

```
eth7      Link encap:Ethernet  Hardware Adresse 00:00:73:ae:ff:bf  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:5
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:0 (0.0 B)  TX-Bytes:0 (0.0 B)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:65536  Metrik:1
          RX packets:6581 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6581 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:598100 (598.1 KB)  TX-Bytes:598100 (598.1 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 1c:4b:d6:91:52:2c  
          inet Adresse:10.0.0.8  Bcast:10.0.0.255  Maske:255.255.255.0
          inet6-Adresse: fe80::1e4b:d6ff:fe91:522c/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:122494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77985 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:133169591 (133.1 MB)  TX-Bytes:10235240 (10.2 MB)
```

---

### Post by Cheesehead on 2013-05-03
Attach your /var/log/dmesg showing your last boot. This will show when and/or why your interfaces are being renamed.

Also look in /etc/udev/rules.d/ , find the file "##-persistent-net-rules", and attach that too. Common reasons for interface renaming are a name collision and a udev rule...sometimes both.

---

### Post by Martin123 on 2013-05-04
I observed that there are several interfaces defined in "persistent.net.rules" and there is always one more added at reboot. I deleted them except eth0 and it started over again adding eth1 and then eth2.

[ATTACH]242165[/ATTACH]
[ATTACH]242168[/ATTACH]

---

### Post by Cheesehead on 2013-05-04
Each line of the rules file tells your system to assign eth0, wlan0, eth1, and eth2 to a specific MAC address. None of those ethX MAC addresses seems to be the one you are actually using.

For example, 
> # PCI device 0x1969:/sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", [COLOR="#FF0000"]**ATTR{address}=="00:00:6e:ea:45:ca"**[/COLOR], ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", **[COLOR="#FF0000"]NAME="eth0"[/COLOR]**


> [COLOR="#FF0000"]**eth7**[/COLOR]      Link encap:Ethernet  [COLOR="#FF0000"]**Hardware Adresse 00:00:73:ae:ff:bf**[/COLOR]  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:5
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:0 (0.0 B)  TX-Bytes:0 (0.0 B)

Your rules file says to assign eth0 to MAC Address 00:00:6e:ea:45:ca,
but your ifconfig says you are actually using Hardware Adresse 00:00:73:ae:ff:bf
See the difference in MAC addresses?

One way to solve the problem:

1) Make a backup copy of your /etc/udev/rules.d/70-persistent-net-rules.

2) In file /etc/udev/rules.d/70-persistent-net-rules,
on the eth0 line,
change the ATTR{address} field 
from ATTR{address}=="00:00:6e:ea:45:ca"
to ATTR{address}=="00:00:73:ae:ff:bf"

3) Reboot to test the change

If this change does not work after a reboot, change it back and let us know.

That dmesg includes only the first 17 seconds after POST, and does not include any renaming or eth adding activity. If changing the rules file does not fix the problem, then please attach dmesg for the entire boot.

---

### Post by Martin123 on 2013-05-04
Didn't work.

These are all dmesg files I found in this folder. I hope there is everything included.

[ATTACH]242177[/ATTACH]
[ATTACH]242178[/ATTACH]
[ATTACH]242179[/ATTACH]
[ATTACH]242180[/ATTACH]
[ATTACH]242181[/ATTACH]

---

### Post by Cheesehead on 2013-05-04
What kind of ethernet device is it? USB? PCI?
Please run the command 'lshw > /tmp/lshw.output', then attach the file /tmp/lshw.output

Does ifconfig look the same? What ethX is it assigned to now?

---

### Post by Martin123 on 2013-05-06
It's a PCI device.
There was no file "/tmp/lshw.output", so I copied the output from the terminal 
[ATTACH]242274[/ATTACH]

Ifconfig didn't change. It's eth3.

I also had made a fresh Install of the new Ubuntu version and I still had this Problem like on the old version.

---

