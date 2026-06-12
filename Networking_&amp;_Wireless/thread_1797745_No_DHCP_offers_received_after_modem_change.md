---
title: "No DHCP offers received after modem change"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by Feareilo on 2011-07-05
I have been using Ubuntu since Hardy Heron and I have always had trouble getting my home WiFi to work correctly. You guys have always helped me out and I am in desperate need of another lifesaving Linux guru.

I used to connect to the internet via a Linksys router using the following terminal commands (Network Manager has never worked for me on any Ubuntu install):
```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "[network name]"
sudo iwconfig wlan0 key open [64 bit WEP hex key]
sudo dhclient wlan0
```

However, I recently changed the old modem + router for a new wireless modem (a Thomson TG585v8 ).

Now, the result of that last command is this:
```

amosupremo@amosupremo:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:02:72:04:d0:04
Sending on   LPF/wlan0/00:02:72:04:d0:04
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I've tried to connect in Natty (both Ubuntu and Kubuntu) and it's not working either.

I also purged Network Manager and installed wicd and I managed to get an intermittent, slow connection.

Here are some of the common commands people post when having problems:

**1 ) Machine Brand and Model (PC/Laptop):**
No brand. I built it with the following specs:
AMD Athlon II X4 2.6GHz
2 HD: 100GB Sata (Ubuntu and XP64 install) / 80GB IDE (XP)
4GB RAM
Gigabyte Motherboard


**2 ) Wireless Brand, Model and Wireless Chipset:**
```

amosupremo@amosupremo:~$ lsusb
*Bus 002 Device 005: ID 0ace:1201 ZyDAS 802.11b*
Bus 002 Device 004: ID 049f:000e Compaq Computer Corp. Internet Keyboard
Bus 002 Device 002: ID 0ac7:0130 Panwest Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


**3 ) check interface:**
```
amosupremo@amosupremo:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:02:72:04:d0:04  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:72ff:fe04:d004/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1434 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1217660 (1.2 MB)  TX bytes:329042 (329.0 KB)

amosupremo@amosupremo:~$ iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:"INFINITUM259970"  Nickname:"zd1201"
          Mode:Managed  Channel:0  Access Point: 08:76:FF:6F:4D:8C   
          Bit Rate:11 Mb/s   
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0/128  Signal level=43/128  Noise level:0/128
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


**4 ) Check for modules:**
```
amosupremo@amosupremo:~$ lsmod | grep wlan0

```
[No output]

**5 ) Kernel boot messages**
```
amosupremo@amosupremo:~$ dmesg | grep wlan0
[   16.424539] usb 2-5: wlan0: ZD1201 USB Wireless interface
[   45.120011] wlan0: no IPv6 routers present
[  161.761282] wlan0: no IPv6 routers present
[  434.987366] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  437.368309] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  447.971274] wlan0: no IPv6 routers present

```

**6 ) Network configuration**
```
amosupremo@amosupremo:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:02:72:04:d0:04
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.68 multicast=yes wireless=IEEE 802.11b

```

**7 ) Scan for networks:**
```
amosupremo@amosupremo:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 08:76:FF:6F:4D:8C
                    ESSID:"INFINITUM259970"
                    Mode:Master
                    Channel:5
                    Bit Rates:1 Mb/s
                    Bit Rates:2 Mb/s
                    Bit Rates:5.5 Mb/s
                    Bit Rates:11 Mb/s
                    Bit Rates:9 Mb/s
                    Bit Rates:18 Mb/s
                    Bit Rates:36 Mb/s
                    Bit Rates:54 Mb/s
                    Encryption key:on
                    Quality=44/128  Signal level=-82 dBm  Noise level=-99 dBm
          Cell 02 - Address: 00:26:44:63:F2:91
                    ESSID:"INFINITUMB984E2"
                    Mode:Master
                    Channel=11
                    Bit Rates:1 Mb/s
                    Bit Rates:2 Mb/s
                    Bit Rates:5.5 Mb/s
                    Bit Rates:11 Mb/s
                    Bit Rates:18 Mb/s
                    Bit Rates:24 Mb/s
                    Bit Rates:36 Mb/s
                    Bit Rates:54 Mb/s
                    Encryption key:on
                    Quality=16/128  Signal level=-93 dBm  Noise level=-98 dBm

```

**8 ) Ubuntu Version: **
```
amosupremo@amosupremo:~$ lsb_release -d
Description:	Ubuntu 10.04.2 LTS

```

**9 ) Kernel/architecture (including 32 vs. 64 bit): **
```
amosupremo@amosupremo:~$ uname -mr
2.6.32-23-generic x86_64

```


**Additional command that may be useful**

```
amosupremo@amosupremo:~$ sudo cat /var/log/syslog | grep wlan0
Jul  4 22:29:55 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:30:03 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:30:16 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:30:24 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:30:43 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:30:55 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:31:08 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:31:21 amosupremo dhclient: receive_packet failed on wlan0: Network is down
Jul  4 22:31:21 amosupremo dhclient: Listening on LPF/wlan0/00:02:72:04:d0:04
Jul  4 22:31:21 amosupremo dhclient: Sending on   LPF/wlan0/00:02:72:04:d0:04
Jul  4 22:31:21 amosupremo dhclient: DHCPRELEASE on wlan0 to 192.168.1.254 port 67
Jul  4 22:31:21 amosupremo kernel: [  581.210496] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  4 22:31:22 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:31:24 amosupremo kernel: [  583.590024] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul  4 22:31:25 amosupremo avahi-daemon[805]: Registering new address record for fe80::202:72ff:fe04:d004 on wlan0.*.
Jul  4 22:31:31 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:31:34 amosupremo kernel: [  594.350021] wlan0: no IPv6 routers present
Jul  4 22:31:42 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:31:55 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:31:59 amosupremo dhclient: Listening on LPF/wlan0/00:02:72:04:d0:04
Jul  4 22:31:59 amosupremo dhclient: Sending on   LPF/wlan0/00:02:72:04:d0:04
Jul  4 22:31:59 amosupremo dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jul  4 22:32:04 amosupremo dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jul  4 22:32:04 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 255.255.255.255 port 67
Jul  4 22:32:04 amosupremo avahi-daemon[805]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.68.
Jul  4 22:32:04 amosupremo avahi-daemon[805]: New relevant interface wlan0.IPv4 for mDNS.
Jul  4 22:32:04 amosupremo avahi-daemon[805]: Registering new address record for 192.168.1.68 on wlan0.IPv4.
Jul  4 22:32:08 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:33:01 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:33:06 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:33:20 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:33:56 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:34:11 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:34:46 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:34:57 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:35:36 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:35:48 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:36:26 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:36:30 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:36:42 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:37:30 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:37:36 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:37:41 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:38:17 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:38:39 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:39:33 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:40:21 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:40:24 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:40:27 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:40:36 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:41:15 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:41:30 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:42:11 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:42:40 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:43:26 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:43:31 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:43:37 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:43:45 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:44:31 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:44:45 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:44:56 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:44:56 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:45:01 amosupremo avahi-daemon[805]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jul  4 22:45:01 amosupremo avahi-daemon[805]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.68.
Jul  4 22:45:01 amosupremo dhclient: receive_packet failed on wlan0: Network is down
Jul  4 22:45:01 amosupremo dhclient: receive_packet failed on wlan0: Network is down
Jul  4 22:45:01 amosupremo avahi-daemon[805]: Withdrawing address record for fe80::202:72ff:fe04:d004 on wlan0.
Jul  4 22:45:01 amosupremo avahi-daemon[805]: Withdrawing address record for 192.168.1.68 on wlan0.
Jul  4 22:45:01 amosupremo dhclient: Listening on LPF/wlan0/00:02:72:04:d0:04
Jul  4 22:45:01 amosupremo dhclient: Sending on   LPF/wlan0/00:02:72:04:d0:04
Jul  4 22:45:01 amosupremo dhclient: DHCPRELEASE on wlan0 to 192.168.1.254 port 67
Jul  4 22:45:02 amosupremo dhclient: Listening on LPF/wlan0/00:02:72:04:d0:04
Jul  4 22:45:02 amosupremo dhclient: Sending on   LPF/wlan0/00:02:72:04:d0:04
Jul  4 22:45:03 amosupremo avahi-daemon[805]: Registering new address record for fe80::202:72ff:fe04:d004 on wlan0.*.
Jul  4 22:45:06 amosupremo dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Jul  4 22:45:09 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 22:45:10 amosupremo dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jul  4 22:45:12 amosupremo kernel: [ 1411.652541] wlan0: no IPv6 routers present
Jul  4 22:45:21 amosupremo dhclient: DHCPREQUEST of 192.168.1.68 on wlan0 to 192.168.1.254 port 67
Jul  4 23:35:32 amosupremo kernel: [   16.424539] usb 2-5: wlan0: ZD1201 USB Wireless interface
Jul  4 23:35:34 amosupremo avahi-daemon[869]: Registering new address record for fe80::202:72ff:fe04:d004 on wlan0.*.
Jul  4 23:35:43 amosupremo kernel: [   45.120011] wlan0: no IPv6 routers present
Jul  4 23:36:55 amosupremo avahi-daemon[869]: Withdrawing address record for fe80::202:72ff:fe04:d004 on wlan0.
Jul  4 23:36:55 amosupremo dhclient: Listening on LPF/wlan0/00:02:72:04:d0:04
Jul  4 23:36:55 amosupremo dhclient: Sending on   LPF/wlan0/00:02:72:04:d0:04
Jul  4 23:36:55 amosupremo dhclient: DHCPRELEASE on wlan0 to 192.168.1.254 port 67
Jul  4 23:36:57 amosupremo avahi-daemon[869]: Registering new address record for fe80::202:72ff:fe04:d004 on wlan0.*.
Jul  4 23:37:03 amosupremo dhclient: Listening on LPF/wlan0/00:02:72:04:d0:04
Jul  4 23:37:03 amosupremo dhclient: Sending on   LPF/wlan0/00:02:72:04:d0:04
Jul  4 23:37:03 amosupremo dhclient: DHCPRELEASE on wlan0 to 192.168.1.254 port 67
Jul  4 23:37:04 amosupremo avahi-daemon[869]: Withdrawing address record for fe80::202:72ff:fe04:d004 on wlan0.
Jul  4 23:37:30 amosupremo dhclient: Listening on LPF/wlan0/00:02:72:04:d0:04
Jul  4 23:37:30 amosupremo dhclient: Sending on   LPF/wlan0/00:02:72:04:d0:04
Jul  4 23:37:30 amosupremo dhclient: DHCPRELEASE on wlan0 to 192.168.1.254 port 67
Jul  4 23:37:31 amosupremo avahi-daemon[869]: Registering new address record for fe80::202:72ff:fe04:d004 on wlan0.*.
Jul  4 23:37:32 amosupremo dhclient: Listening on LPF/wlan0/00:02:72:04:d0:04
Jul  4 23:37:32 amosupremo dhclient: Sending on   LPF/wlan0/00:02:72:04:d0:04
Jul  4 23:37:35 amosupremo dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jul  4 23:37:40 amosupremo kernel: [  161.761282] wlan0: no IPv6 routers present


```


I am also attaching the wicd log. It contains a session where I got the intermittent connection. I stopped that connection and restarted it (with the same results) two times.

---

### Post by chili555 on 2011-07-05
> sudo iwconfig wlan0 key open [64 bit WEP hex key]I wonder if iwconfig thinks your hex key is "open." Is the behavior improved with:```
sudo iwconfig wlan0 key [64 bit WEP hex key] open
```Or with:```
sudo iwconfig wlan0 key [64 bit WEP hex key]
```> wlan0     Scan completed :
          Cell 01 - Address: 08:76:FF:6F:4D:8C
                    ESSID:"INFINITUM259970"
                    Mode:Master
                    Channel:5
                    Bit Rates:1 Mb/s
                    Bit Rates:2 Mb/s
                    Bit Rates:5.5 Mb/s
                    Bit Rates:11 Mb/s
                    Bit Rates:9 Mb/s
                    Bit Rates:18 Mb/s
                    Bit Rates:36 Mb/s
                    Bit Rates:54 Mb/s
                    Encryption key:on
                    [COLOR="Red"]Quality=44/128[/COLOR]  Signal level=-82 dBm  Noise level=-99 dBmIs this worrisome? Is it actually quite far away?> $ lsmod | grep wlan0There is a mistake in the guide you followed. What we are looking for is the driver module; in your case it's *zd1201*. Let's see if there are any interesting messages that may aid us in troubleshooting:```
dmesg | grep zd12
```Thanks.

---

### Post by Feareilo on 2011-07-05
Wow, that was fast. Thank you very much for trying to help me!

I am at work right now so I can't try anything (yet). However, I did try:
```
sudo iwconfig wlan0 key [64 bit WEP hex key]
```

to no avail.

> I wonder if iwconfig thinks your hex key is "open."
I don't think so because I was able to connect with that command for more than a year without a single problem. I will try placing the word "open" after the hex key, though.

> Is this worrisome? Is it actually quite far away?
It's less than 3m (<10 ft)  away (unfortunately, it's far enough to require a wireless connection). Yesterday, I could connect under Windows XP (32 bit, the 64 bit version doesn't support zd1201 drivers) with good quality signal and full internet speed.

Again, thanks for helping me out! I will try the last command you mentioned and post the result when I get home.

---

### Post by Feareilo on 2011-07-05
Here is the output from the command you suggested. It looks ok to me... (and I hope this is not a bad thing!)

Any pointers from anyone else, appart from the always helpful chilli555, are also welcome.

```
amosupremo@amosupremo:~$ sudo dmesg | grep zd12
[   16.860905] usb 2-5: firmware: requesting zd1201.fw
[   17.504483] usbcore: registered new interface driver zd1201
amosupremo@amosupremo:~$ sudo cat /var/log/syslog | grep zd12
Jul  4 23:35:32 amosupremo kernel: [   15.778934] usb 2-5: firmware: requesting zd1201.fw
Jul  4 23:35:32 amosupremo kernel: [   16.424575] usbcore: registered new interface driver zd1201
Jul  5 21:46:58 amosupremo kernel: [   16.860905] usb 2-5: firmware: requesting zd1201.fw
Jul  5 21:46:59 amosupremo kernel: [   17.504483] usbcore: registered new interface driver zd1201
```

EDIT:
By the way, I also tried:
```
sudo iwconfig wlan0 key [64 bit WEP hex key] open
```
but it didn't work.

---

### Post by Feareilo on 2011-07-06
I also forgot to mention that 4 other computers (XP 32 bit, Vista 32 bit, 7 32 bit and OSX Snow Leopard) and 2 iPod Touch devices are a able to connect with good/excellent quality signal and full speed. I'd love to go back to the old modem + router solution but it's not possible because it is not a decision I can make. Unfortunately, it is my ISP (Telmex). I blame the 3rd world country monopolistic rules).

---

### Post by chili555 on 2011-07-06
> I blame the 3rd world country monopolistic rules).LOL! I don't think my country is perfect; it may just have fewer defects than many others. 

Is Network Manager and/or Wicd running on this machine? They each will interfere with manual methods. May I see:```
sudo cat /var/log/syslog | grep -i wicd
```NM *AND* Wicd is my worst nightmare, right up there with my ex-wife's lawyer!

---

### Post by Feareilo on 2011-07-06
> **chili555 said:**
> LOL! I don't think my country is perfect; it may just have fewer defects than many others. 

Is Network Manager and/or Wicd running on this machine? They each will interfere with manual methods. May I see:```
sudo cat /var/log/syslog | grep -i wicd
```NM *AND* Wicd is my worst nightmare, right up there with my ex-wife's lawyer!

Hahaha, part of being in a 3rd world country is having a gigantic supply of lawyers. Go figure...

Anyway, the commands used to work (before the modem change) with NM disabled. When I started getting no DHCP offers, I purged NM. Still, I had no luck. Then I installed WICD, and tried the commands and they failed. Finally, I deleted WICD and tried the commands and they still failed.

So, to sum up, any possible combination of NM, WICD, and commands, has been unsuccessfully tried.

Thanks for all the help. Tonight, I'll post the output of the last command you posted, anyway.

---

### Post by chili555 on 2011-07-06
I consider myself a half-way competent terminal genie and without NM or Wicd, I can connect to my doctor's 802.11***a*** network in a few moments. However, I can't do so with NM running. If you want to do things old-school, ditch Wicd and NM and populate /etc/network/interfaces and be happy.

By the way, this looks pretty well connected, no?> $ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:02:72:04:d0:04  
          inet addr:[COLOR="Red"]192.168.1.68[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:72ff:fe04:d004/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1434 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1217660 (1.2 MB)  TX bytes:329042 (329.0 KB)

---

### Post by Feareilo on 2011-07-06
That's the intermittent, weak signal I managed to get with wicd. If I don't use wicd, that field turns out blank.

---

### Post by chili555 on 2011-07-06
I suspect it's a driver issue. The only driver and firmware I can see is dated about 2005, or 900 years old in Linux years. I hate to throw cubic dollars, euros or yuan at an issue, but I wonder if it's time to pension off the old wireless device.

I'm sorry I have no other ideas.

---

### Post by Feareilo on 2011-07-06
> **chili555 said:**
> I suspect it's a driver issue. The only driver and firmware I can see is dated about 2005, or 900 years old in Linux years. I hate to throw cubic dollars, euros or yuan at an issue, but I wonder if it's time to pension off the old wireless device.

I'm sorry I have no other ideas.

I am not even close to your knowledge regarding Linux wireless issues so I am going to trust your judgement. It seems odd... because the old USB WiFi card used to work perfectly with the other modem. But I guess it is time to retire.

In a couple of hours, I'll post the output of the last command you suggested, anyway. I guess it's my last hope.

---

### Post by Feareilo on 2011-07-06
The command:
```
sudo cat /var/log/syslog | grep -i wicd
```
returns no output.

However, from the wicd log, I was able to check the commands used by wicd with which I was able to manage to get the intermittent connection.
The commands are:
```

sudo ifconfig wlan0 down
sudo iwconfig wlan0
sudo /sbin/dhclient -r wlan0
sudo ifconfig wlan0 0.0.0.0 
sudo wpa_cli -i wlan0 terminate
sudo /sbin/ip route flush dev wlan0
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
sudo wpa_supplicant -B -iwlan0 -c/var/lib/wicd/configurations/0876ff6f4d8c -Dwext
sudo iwconfig wlan0 essid INFINITUM259970
sudo iwconfig wlan0 channel 5
sudo iwconfig wlan0
sudo iwconfig wlan0 ap 08:76:FF:6F:4D:8C
sudo /sbin/dhclient wlan0

```

The output from those commands is:
```

amosupremo@amosupremo:~$ sudo ifconfig wlan0 down
amosupremo@amosupremo:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:"INFINITUM259970"  Nickname:"zd1201"
          Mode:Managed  Channel:0  Access Point: 08:76:FF:6F:4D:8C   
          Bit Rate:11 Mb/s   
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0/128  Signal level=43/128  Noise level:0/128
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

amosupremo@amosupremo:~$ sudo /sbin/dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 3750
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:02:72:04:d0:04
Sending on   LPF/wlan0/00:02:72:04:d0:04
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
amosupremo@amosupremo:~$ sudo ifconfig wlan0 0.0.0.0 
amosupremo@amosupremo:~$ sudo wpa_cli -i wlan0 terminate
OK
amosupremo@amosupremo:~$ sudo /sbin/ip route flush dev wlan0
amosupremo@amosupremo:~$ sudo iwconfig wlan0 mode managed
amosupremo@amosupremo:~$ sudo ifconfig wlan0 up
amosupremo@amosupremo:~$ sudo wpa_supplicant -B -iwlan0 -c/var/lib/wicd/configurations/0876ff6f4d8c -Dwext
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
amosupremo@amosupremo:~$ sudo iwconfig wlan0 essid INFINITUM259970
amosupremo@amosupremo:~$ sudo iwconfig wlan0 channel 5
amosupremo@amosupremo:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:"INFINITUM259970"  Nickname:"zd1201"
          Channel:5  
          Retry:off   
          Link Quality:0/128  Signal level:43/128  Noise level:0/128
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

amosupremo@amosupremo:~$ sudo iwconfig wlan0 ap 08:76:FF:6F:4D:8C
Error for wireless request "Set AP Address" (8B14) :
    SET failed on device wlan0 ; Operation not supported.
amosupremo@amosupremo:~$ sudo /sbin/dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:02:72:04:d0:04
Sending on   LPF/wlan0/00:02:72:04:d0:04
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.77 from 192.168.1.254
DHCPREQUEST of 192.168.1.77 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.77 from 192.168.1.254
bound to 192.168.1.77 -- renewal in 60 seconds.

```

Renewal in 60 seconds? That seems really weird to me...

Any clue?

EDIT:
Moreover, I **never** introduced my hex key! Does that mean that I am somehow hacking my own network? Or is the hex key included in the /var/lib/wicd/configurations/0876ff6f4d8c config file?
If it is included in the configuration file, well, that would be pretty odd. Because the output of that specific command was "ioctl[SIOCSIWENCODEEXT]: Operation not supported"

Can anyone shed light on this issue?

EDIT2:

I just tried fewer commands with the same results:
```

sudo ifconfig wlan0 down
sudo /sbin/dhclient -r wlan0
sudo ifconfig wlan0 up
sudo wpa_supplicant -B -iwlan0 -c/var/lib/wicd/configurations/0876ff6f4d8c -Dwext
sudo iwconfig wlan0 essid INFINITUM259970
sudo /sbin/dhclient wlan0

```


Edit 3:

This is getting weirder by the minute. I just tried the original commands with a slight change...

```

sudo ifconfig wlan0 down
sudo [COLOR="Red"]/sbin/[/COLOR]dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 key open [HEX KEY]
sudo iwconfig wlan0 essid INFINITUM259970
sudo [COLOR="Red"]/sbin/[/COLOR]dhclient wlan0

```

And guess what... I got the same result! Hey, faulty internet is better than no internet. But still, I'd love it if anyone could lend me a hand in here.

---

### Post by Feareilo on 2011-07-06
I hope this is my final post in this thread.

I restarted the computer and selected Ubuntu 64-bit. First thing I do when Ubuntu boots, I **quit** wicd. Then, I run the last set of commands I posted and... voilà!
I still got a renewal in 51 seconds which seems kinda odd... but I don't give a flying FRACK! [huge BSG fan] I now have uninterrupted internet again!
The problem was being caused by wicd running in the background. [Although I can't complain too much either... the wicd log tipped me off on the solution]

Before I mark this thread as solved, I'd like to test my computer for a couple of days to check whether everything is in order.
Finally, and just because I want to learn, would you know why I solved my problem by typing "/sbin/dhclient" instead of "dhclient"? I'm perplexed

---

### Post by chili555 on 2011-07-07
"I figured out how to get my old truck to start on cold mornings; I drink tea instead of coffee." That's the automotive comparison to what you just did. As far as I know, issued by sudo, in Ubuntu at least, /sbin/dhclient and dhclient are exactly the same. However, I don't fight momentum. Whenever a poster says the solution was something unlikely, I congratulate them and tell them I'm glad it's working.> The problem was being caused by wicd running in the background. So have you removed Wicd or what? You could easily configure an /etc/network/interfaces file and do all this automagically, to the extent anything is easy in a zd1201!

I wonder if the driver selection in Wicd, evidently Wext, is correct or at least optimal for zd1201.

---

### Post by Feareilo on 2011-07-07
> **chili555 said:**
> So have you removed Wicd or what?
Yesterday, I just disabled it. However, I removed it from Syanptic Package Manager before shutting down the system. I'll let you know if the commands still work after removing wicd tonight.

> **chili555 said:**
> You could easily configure an /etc/network/interfaces file and do all this automagically, to the extent anything is easy in a zd1201!
I previously tried that and it didn't work (I tried with "dhclient" instead of "/sbin/dhclient" though).

By the way, I don't type the commands manually every time I want to connect to the internet. I keep an executable text file with the commands on the desktop.

> **chili555 said:**
> I wonder if the driver selection in Wicd, evidently Wext, is correct or at least optimal for zd1201.
Maybe not. That might be the reason wicd wasn't working, right?

I like this emoticon: :guitar:

---

### Post by emiller12345 on 2011-07-07
You should also check your route when having networking problems
```
$ route -n
```make sure you have a network item in the list i.e.
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
[COLOR=Red]192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0[/COLOR]
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```and a default gateway in the list, i.e.
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
[COLOR=Red]0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0[/COLOR]

```

---

### Post by Feareilo on 2011-07-07
Yep. Confirmed 100%. I'm writing from Ubuntu using the new script (the one with [COLOR="Red"]/sbin/[/COLOR]).

Apparently /sbin/dhclient is not the same as dhclient.

I'm gonna mark this as solved.

---

