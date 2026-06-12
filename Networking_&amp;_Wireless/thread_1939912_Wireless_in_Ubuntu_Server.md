---
title: "Wireless in Ubuntu Server?"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by apple_head on 2012-03-12
Hey Everyone

Is there anyway I can connect my desktop PC (which will run Ubuntu server) through wireless without having to connect to the internet...

In other words can I install a wireless card from the Ubuntu CD and adapter driver CD's?? as the router is downstairs and not near the desktop?

---

### Post by chili555 on 2012-03-12
You certainly can. We may or may not need any other drivers. We may or may not need firmware. We probably do not want the adapter driver CD. Let's see what kind of device you have. On the server, if it's a USB device, run and post the relevant part of:```
lsusb
```If it's PCI, then:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by apple_head on 2012-03-13
Realtek semiconductor corp RTL8188CUS 802.11n WLAN

how do i go about setting it up??

---

### Post by chili555 on 2012-03-13
We need the pci.id that you omitted. It will be in the form of 1234:abcd or similar. It will also be helpful to know which Ubuntu version you've installed:```
lsb_release -rc
```I believe, if it's the device I think it is, that the driver is installed by default in 11.10; not so in earlier versions. Firmware may be an issue.

If you have an earlier version and we need to compile the driver from source code, we have a long, fun task before us.

---

### Post by apple_head on 2012-03-14
I've installed server 11.10 and its detected my wireless adapter after doing some searching on google, so its definatley installed correct.

I just want to know how to connect to my wireless network?

---

### Post by chili555 on 2012-03-14
I suggest you do:```
sudo vim /etc/network/interfaces
```Use any other text editor if you are not familiar with vim. Set up the file like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.1
    wpa-ssid mynetwork
    wpa-psk mykey

```Substitute your details as needed. Be sure to use an IP address outside the range assigned by the DHCP server in the router. Next do:```
sudo vim /etc/resolv.conf
```Add a DNS nameserver; the router's address will be fine or you could use Google:```
nameserver 8.8.8.8
```In both cases, save and close.

Now get the system to read and use the files:```
sudo ifdown wlan0 && sudo ifup wlan0
```Did you connect?```
ifconfig
```Can you reach the internet?```
ping -c3 www.google.com
```Post back any problems, errors, etc.

---

### Post by apple_head on 2012-03-15
Keep getting Unknown host for google and host unreachable for router when trying to ping??

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.65
netmask 255.255.255.0
gateway 192.168.1.254 (hub address)
    wpa-ssid BTHomeHub2-NG4K
    wpa-psk **********
```

```
nameserver 192.168.1.254 (hub address)
```

---

### Post by apple_head on 2012-03-15
checked ifconfig and have a broadcast address of 0.0.0.0??

Is this normal??

---

### Post by chili555 on 2012-03-15
Are you sure your wireless is working correctly? Let's see:```
iwconfig wlan0
sudo iwlist wlan0 scan
```You don't have to post all the scan results; just tell us if it scans and, if not, any error messages.> checked ifconfig and have a broadcast address of 0.0.0.0??It can be; here are my perfectly working details:> wlan0     Link encap:Ethernet  HWaddr 99:19:d2:c2:11:88  
          inet addr:192.168.1.108  [COLOR="Red"]Bcast:0.0.0.0[/COLOR]  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fec2:1b8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:2621786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1757379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3484977685 (3.4 GB)  TX bytes:234358233 (234.3 MB)

---

### Post by apple_head on 2012-03-15
Yes it scans and picks up every network in the area :P

---

### Post by apple_head on 2012-03-15
ok i take that back it says "no scan results"

---

### Post by chili555 on 2012-03-15
Let's have a look at:```
ping -c3 192.168.1.254
ping -c3 74.125.45.106
cat /etc/resolv.conf
```Thanks.

---

### Post by chili555 on 2012-03-15
> **apple_head said:**
> ok i take that back it says "no scan results"Let's have a look at:```
dmesg | grep 819
```

---

