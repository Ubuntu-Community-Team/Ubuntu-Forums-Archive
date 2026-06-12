---
title: "USB Wireless Help"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by Franks&amp;Beans on 2006-07-11
Have 6.06 working perfectly on my laptop wirelessly via an X-Micro PCMCIA card out of the box. Very impressed. Unfortunately not the same for my desktop using a Repotec RP-WU1700 USB Adaptor. Ubuntu picks it up straight away and installs the driver automatically. Appears in Network Manager - I can configure it - detects ESSID fine - wireless network strengh bar appears.

But no internet or even network connection to router. Don't know what I'm doing wrong. I'm am a total Linux newbie so would appreciate some help in trouble shooting this device to pin down where the problem might be.

From lshw:
 *-usb
                   description: Generic USB device
                   product: USB2.0 WLAN
                   vendor: ZyDAS
                   physical id: 1
                   bus info: usb@3:1
                   version: 43.30
                   capabilities: usb-2.00
                   configuration: driver=zd1211 maxpower=500mA speed=480.0MB/s

From iwconfig:

wlan0     802.11b/g NIC  ESSID:"MAXI"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:80:1E:30:18:C0
          Bit Rate:11 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=68/92  Signal level=56/154  Noise level=161/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any ideas?  Thanks.

---

### Post by OpsVentus on 2006-07-11
Ok, steps to take when internet fails om wireless network.
1: iwlist (see if it finds the network)
2: iwconfig (see if it is connected to the network)
3: ifconfig (see if you got an ip-address)
4: route (see if your gateway is set ok)
5: check dns-servers (in network-manager)
6: ping router
7: ping internet-address (like 209.202.229.100)
8: ping dns-internet-address (like [www.hotbot.com](www.hotbot.com))

If you need further help go into terminal(looking at iwconfig, I think you know how) type "ifconfig" and "route" and post what is says.

Cheers,
Bart.

---

### Post by Franks&amp;Beans on 2006-07-11
Here is ifconfig and route info: Still can't even log into router. Although wireless router lists the USB mac address on the wireless client list. Can't get it to assign IP via DHCP so have set it to static.

wlan0     Link encap:Ethernet  HWaddr 00:11:A3:02:47:5F
          inet addr:10.1.1.24  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:293518 (286.6 KiB)  TX bytes:53687 (52.4 KiB)

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.0.0.0       U     0      0        0 wlan0
10.0.0.0        *               255.0.0.0       U     0      0        0 eth0
default         10.1.1.1        0.0.0.0         UG    0      0        0 eth0


Any further ideas?

Thanks.

---

### Post by OpsVentus on 2006-07-11
route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
10.0.0.0 * 255.0.0.0 U 0 0 0 wlan0
10.0.0.0 * 255.0.0.0 U 0 0 0 eth0
default 10.1.1.1 0.0.0.0 UG 0 0 0 eth0

Here you see that wlan0 and eth0 both are in the same network "10.0.0.0 255.0.0.0" and the default(gateway) is 10.1.1.1 on eth0.

So your wireless network card connects to the router.
You set your ip-adres, but your computer dosn't know it has to use wlan0 for adresses on the internet.

Try to get an ip from the DHCP-server, this will set the gateway for you.
In terminal go:
#dhclient wlan0
This should work, if it fails try to set the gateway by hand:
In terminal go:
#route del default
#route add default gw 10.1.1.1 wlan0 (not completely sure about the syntacs of this line, I'm at the office now, can check tonight)

Then go trough step 1 to 8 again. ;)

---

