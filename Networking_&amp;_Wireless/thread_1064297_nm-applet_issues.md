---
title: "nm-applet issues"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by CorntoeGoblin on 2009-02-08
Hello I'm having troubles with the nm-applet not detecting my wired or wireless interfaces. when i click on the applet it just says "no network devices have been found" and when i click on manual configuration it doesn't open anything. when i go into the network settings i can manually set it to use dhcp with the wired network but the wireless settings don't work whatsoever. i tried to completely remove the network manager package and reinstalling but nothing happens. i'd really appreciate some help heres my interfaces file

```
auto lo
iface lo inet loopback

iface eth274 inet dhcp

iface eth275 inet dhcp

auto eth275

iface eth278 inet dhcp

auto eth278

iface eth33 inet dhcp
wireless-key s:schecter12345
wireless-essid Phreakers Beware!!!!


```

---

### Post by warp99 on 2009-02-08
Wow! You have 278 network cards listed, so that's most likely the problem. First I would edit your /etc/udev/rules.d/70-persistent-net.rules and remove **all** of the cards you have in the file. Then I would make your /etc/network/interfaces look like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

Reboot the computer and check to see if your wired connection is working. As for your wireless connection it would be listed as wlan0 or ath0 if it's an Atheros chipset. To check run the following:

```
ifconfig -a
```

Your wireless card should be listed. At that point you can set up the wireless card using the interface you obtained from ifconfig with Network Manager.

Tip: With your network SSID it's best to not have any spaces or special characters in the name, so set it up as Phreakers_Beware without the exclamation points.

---

### Post by CorntoeGoblin on 2009-02-08
ok i deleted all of the persistent names and edited my interfaces file but the applet still doesn't recognize either of the interfaces this is the ifconfig -a output

```
monski@mon-lin:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:6c:e7:0e:f6  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fee7:ef6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1799 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2005089 (1.9 MB)  TX bytes:361051 (352.5 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:3f:6a:1e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25900 (25.2 KB)  TX bytes:25900 (25.2 KB)
```

and this is the persistent names file 
```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.



# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:6c:e7:0e:f6", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4311 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1a:73:3f:6a:1e", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1" 
```

is there some kind of way to reset the applet cause the wired connection works and the drivers for the wireless are loaded its a bcom 43xx card and both adapters show up in lspci so i'm really stuck haha

---

### Post by CorntoeGoblin on 2009-02-08
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface eth1 inet dhcp
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Js


```

thats my interfaces file

help me out please i needa my wireless :P

---

### Post by warp99 on 2009-02-09
Well it looks like your wireless connection is named "eth1" which is strange because I've never seen that before. Anyway you can setup you card manually by following this format so your interfaces file should look like this:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface ath0 inet dhcp
wpa-driver wext
wpa-ssid Js
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk $your_generated_wpa_key
```

Once you edit the file and add you proper key reload the network with the following command:

```
sudo /etc/init.d/networking restart
```

You wireless should be working at this point. Once you get your wireless working I would remove network manager and install WICD instead. The program is much easier to use and just plain works. You can download it from the WICD repositories:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

