---
title: "Difficulty establishing wireless connection in U10.04"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by lhcpr on 2010-06-25
Hello all - have searched the forums tirelessly, but have not been able to find sufficient solution for establishing wireless connection in U10.04.

Specifications:
Wireless usb adaptor: Linksys WUSB11v4
Ubuntu - 10.04 (most recent download)
Modem/Router: Billion BiPAC 7401VGP
ADSL 2+ cnx - WPA1-PSK

Have the linksys windows drivers configured with ndiswrapper and I believe are working correctly...
```
graham@graham-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wusb11v4 : driver installed
	device (13B1:000B) present

```

lsusb ```
graham@graham-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter

```

Now I have followed the Manual Network Configuration guide written by 'Kevdog' [HTML]http://ubuntuforums.org/showthread.php?t=571188[/HTML] as follows:

1) gksu gedit /etc/wpa_supplicant.conf and then created the folowing code in that file;
2) ```

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="air-lockie"
	scan_ssid=0
	proto=WPA
	key_mgmt=WPA-PSK
	psk="MY ASCII CODE HERE"
	pairwise=TKIP
	group=TKIP
}

```
3) Output of the next step as follows
```
**graham@graham-desktop:~$ sudo ifconfig wlan0 down**

**graham@graham-desktop:~$ sudo dhclient -r wlan0**
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:0f:66:e9:5d:c3
Sending on   LPF/wlan0/00:0f:66:e9:5d:c3
Sending on   Socket/fallback

**graham@graham-desktop:~$ sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf**
ioctl[SIOCSIWPMKSA]: Invalid argument
ioctl[SIOCSIWPMKSA]: Invalid argument
Trying to associate with 00:19:db:9c:9d:de (SSID='air-lockie' freq=2412 MHz)
Association request to the driver failed
Associated with 00:00:00:00:00:00
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:19:db:9c:9d:de (SSID='air-lockie' freq=2412 MHz)
Association request to the driver failed
Associated with 00:00:00:00:00:00
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:19:db:9c:9d:de (SSID='air-lockie' freq=2412 MHz)
Association request to the driver failed
Associated with 00:19:db:9c:9d:de
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

``` and failure/disconnection continues on....and on.....

Ok so that's where I'm up to here and a little stuck as how to move on. Other outputs as follows:

ifconfig:
```
**graham@graham-desktop:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:0c:6e:65:3c:bf  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0f:66:e9:5d:c3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig
```
**graham@graham-desktop:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          RTS thr:2432 B   Fragment thr:2432 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist scan
```
**graham@graham-desktop:~$ iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:19:DB:9C:9D:DE
                    ESSID:"air-lockie"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK 

```

sudo lshw -C network
```
**graham@graham-desktop:~$ sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: 3c940 10/100/1000Base-T [Marvell]
       vendor: 3Com Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 12
       serial: 00:0c:6e:65:3c:bf
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       resources: irq:22 memory:feaf8000-feafbfff ioport:d800(size=256)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:66:e9:5d:c3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wusb11v4 driverversion=1.55+Cisco-Linksys LLC.,05/13/20 link=no multicast=yes wireless=IEEE 802.11b

```

Some help getting this up and running would be so great (I am a bit of a noob too so please excuse my stupidity in advance).

With much thanks

Graham

---

