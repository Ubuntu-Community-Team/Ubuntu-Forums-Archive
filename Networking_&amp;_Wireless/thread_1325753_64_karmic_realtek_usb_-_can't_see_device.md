---
title: "64 karmic realtek usb - can't see device"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by duckling9 on 2009-11-13
Hello
I've upgraded from hardy to karmic, basically to get my usb wireless working... so far to no avail. But I'm not sure what I'm meant to be doing, although some uses seem to be reporting this working 'straight out the box' it may be because my previous attempts to get things working have clouded the situation, so help would be much appreciated.

The 'wireless network drivers' tool gives me a message "unable to see if hardware is present". I have installed the windows driver using this. 

I'm on a Dell E520 AMD64
Ubuntu 9.10
2.6.31-14-generic x86_64
---
lsusb
Bus 001 Device 014: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

(NB: Windows (where it works) thinks its a RTL8187B)
---
ifconfig gives:

wlan0     Link encap:Ethernet  HWaddr 00:11:3b:13:74:3f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:11:3b:13:74:3f  
          inet addr:169.254.3.204  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-11-3B-13-74-3F-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
---

iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
---

lsmod  gives:

rtl8187                53604  0 
mac80211              210104  1 rtl8187
led_class               5256  1 rtl8187
eeprom_93cx6            2528  1 rtl8187
cfg80211              109144  2 rtl8187,mac80211

----
dmesg | grep rtl
[14041.434294] rtl8187: inconsistency between id with OEM info!
[14041.483429] phy0: hwaddr 00:11:3b:13:74:3f, RTL8187BvB(early) V0 + rtl8225z2
[14041.547664] rtl8187: Customer ID is 0xFF
[14041.547765] Registered led device: rtl8187-phy0::tx
[14041.547805] Registered led device: rtl8187-phy0::rx
[14041.547857] usbcore: registered new interface driver rtl8187

---
lshw -C network

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:3b:13:74:3f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


---
iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:17:97:A3:69
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"O2wireless302424"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000631febd47
                    Extra: Last beacon: 2100ms ago
                    IE: Unknown: 00104F32776972656C657373333032343234
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

----
/etc/init.d/networking restart
 * Reconfiguring network interfaces...                                             There is already a pid file /var/run/dhclient.eth0.pid with pid 2487
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:18:8b:88:55:ba
Sending on   LPF/eth0/00:18:8b:88:55:ba
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4107
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:11:3b:13:74:3f
Sending on   LPF/wlan0/00:11:3b:13:74:3f
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:11:3b:13:74:3f
Sending on   LPF/wlan0/00:11:3b:13:74:3f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---
thanks in advance for any pointers... i really hope i didn't go through the upgrade pain for one purpose that still doesn't work....
d

---

