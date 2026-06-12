---
title: "rt5370sta is mapped to a wired Ehternet connection."
date: 2013-07-09
forum: Networking &amp; Wireless
---

### Post by grk9 on 2013-07-09
Hello
I am working on Beaglebone running Ubuntu 3.2.42-psp27.
I am using Ralink  RT5370 Wireless Adapter
The device is working OK with the build in driver rt2870usb. 


when I am setting an ip address to the device, it receives it. But the actual connection is done via the Ethernet device eth0. I perform several tests to ensure it. (removing the antenna and isolate it, close the wireless network, sniffing the wireless network from other device, tcpdump on the ra0 interface ). More than that I have a connection to the assigned ip address without setting any security to ra0. 

I am trying to work with a compiled rt5370sta, which I cross-compiled on other Linux machine (I compiled it on Fedora and on Ubuntu with the same results).
I blacked list all the previous installed rtxxxx drivers. 
{
blacklist rt2800usb
blacklist rt2500usb
blacklist rt2800lib
blacklist rt2x00lib
blacklist rt2x00usb
blacklist rt73usb
}
I followed all the procedures:
- modifying the config.mk
- copy the RT5370STA.dat
- install the driver
- modeprobe the driver.

in the lsmod I am receiving the following:
{
# lsmod
Module                  Size  Used by
rt5370sta             642577  1
snd_soc_tlv320aic3x    32641  0
spidev                  4700  0
ti_tscadc               5502  0
}

I set the wireless channel using.
#iwconfig ra0 channel 2

I set an ip address to the device using 

# ifconfig ra0 11.1.33.20 netmask  255.255.255.0

and the ifconfig output is
# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:18:31:e1:98:0b
          inet addr:11.1.33.5  Bcast:11.1.33.255  Mask:255.255.255.0
          inet6 addr: fe80::218:31ff:fee1:980b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2534098 (2.5 MB)  TX bytes:546691 (546.6 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ra0       Link encap:UNSPEC  HWaddr 00-0F-54-0F-65-D2-30-30-00-00-00-00-00-00-00-00
          inet addr:11.1.33.20  Bcast:11.1.33.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:54ff:fe0f:65d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21069 (21.0 KB)  TX bytes:40900 (40.9 KB)

usb0      Link encap:Ethernet  HWaddr 32:d8:13:4e:12:be
          inet addr:192.168.7.2  Bcast:192.168.7.3  Mask:255.255.255.252
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

after setting the device to monitor mode the iwconfig output is
# iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Monitor  Frequency=2.417 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


I add some printouts to the compiled driver, and they are displayed when I am configuring the device. 

Thank
Giora

---

### Post by grk9 on 2013-07-10
A short update.
I did the same using raspberry pi running debian.
The module is working.
The main difference between the two is that in the raspberry the ifconfig does not displayed the usb0. Only ra0 is displayed
Giora

---

