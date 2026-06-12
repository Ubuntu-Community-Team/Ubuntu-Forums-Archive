---
title: "Final steps for DWA 125 with 10.04"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by Lastmerlin on 2011-02-24
Hi to all,

I am trying to get wireless network with Dlink DWA 125 working unter Kubuntu 10.04 (kernel 2.6.32-23, 32-bit).
I already carried out all the hacks for replacing the rt28** modules by rt3070, which seems a rather common issue. What I did is described here:
[http://forum.ubuntuusers.de/topic/ubuntu-10-04-lucid-lynx-64-bit-d-link-dwa-125/#post-2482091](http://forum.ubuntuusers.de/topic/ubuntu-10-04-lucid-lynx-64-bit-d-link-dwa-125/#post-2482091)

Now output of usb-devices is:
```

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=07d1 ProdID=3c16 Rev=01.01
S:  Manufacturer=Ralink
S:  Product=11n Adapter
S:  SerialNumber=1.0
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=450mA
I:  If#= 0 Alt= 0 #EPs= 7 Cls=ff(vend.) Sub=ff Prot=ff Driver=rt2870

```I have no Idea why is still displays rt2870, lsmod | grep rt gives:
```

agpgart                31724  2 fglrx,intel_agp
parport                32635  2 ppdev,lp
rt3070sta             567126  1 

```Output of iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 88:25:2C:B0:7A:99   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XX   Security mode:restricted
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```This is already after executing...
iwconfig ra0 ap 88:25:2C:B0:7A:99 key restricted XXXXXXXXXX
...which was an attempt to configure the device via shell.

Output of: iwlist ra0 scanning
```

          Cell 02 - Address: 88:25:2C:B0:7A:99
                    Protocol:802.11b/g/n
                    ESSID:"EasyBox-B07A35"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=99/100  Signal level=-51 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0E0050F204104A0001101044000102

```To sum it up: AS far as I can tell, the device has its correct driver (no errors on mesg either) and my EasyBox was detected with excellent signal quality. The main issue is, that I have no internet as soon as I unplug the ethernet cable...

I also tried the gui way (and I would strongly prefer such a solution for the last step):
- opened network manager
- selected wireless tab and "add button"
- clicked Scan, it found my EasyBox instantly (among half a dozen other)
- entered WPA key
- clicked ok

...and what happened was - nothing. The list of wireless connections stayed empty. No error message. 
An extract of /var/log/deamon.log:
cat /var/log/daemon.log | egrep 'ra0|usb'
```

Feb 23 21:55:56 kalypso NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/net/ra0, iface: ra0)
Feb 23 21:55:56 kalypso NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/net/ra0, iface: ra0): no ifupdown configuration found.
Feb 23 21:55:56 kalypso NetworkManager: <info>  (ra0): driver does not support SSID scans (scan_capa 0x00).
Feb 23 21:55:56 kalypso NetworkManager: <info>  (ra0): new 802.11 WiFi device (driver: 'usb')
Feb 23 21:55:56 kalypso NetworkManager: <info>  (ra0): exported as /org/freedesktop/NetworkManager/Devices/1
Feb 23 21:55:56 kalypso NetworkManager: <info>  (ra0): now managed
Feb 23 21:55:56 kalypso NetworkManager: <info>  (ra0): device state change: 1 -> 2 (reason 2)
Feb 23 21:55:56 kalypso NetworkManager: <info>  (ra0): bringing up device.
Feb 23 21:55:57 kalypso NetworkManager: <info>  (ra0): preparing device.
Feb 23 21:55:57 kalypso NetworkManager: <info>  (ra0): deactivating device (reason: 2).
Feb 23 21:55:57 kalypso NetworkManager: <info>  (ra0): supplicant interface state:  starting -> ready
Feb 23 21:55:57 kalypso NetworkManager: <info>  (ra0): device state change: 2 -> 3 (reason 42)
Feb 23 21:55:58 kalypso avahi-daemon[891]: Registering new address record for fe80::f27d:68ff:fe14:36cf on ra0.*.
Feb 23 22:04:45 kalypso NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/net/ra0, iface: ra0)
Feb 23 22:04:45 kalypso NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/net/ra0, iface: ra0): no ifupdown configuration found.
Feb 23 22:04:45 kalypso NetworkManager: <info>  (ra0): driver does not support SSID scans (scan_capa 0x00).
Feb 23 22:04:45 kalypso NetworkManager: <info>  (ra0): new 802.11 WiFi device (driver: 'usb')
Feb 23 22:04:45 kalypso NetworkManager: <info>  (ra0): exported as /org/freedesktop/NetworkManager/Devices/0
Feb 23 22:04:45 kalypso NetworkManager: <info>  (ra0): now managed
Feb 23 22:04:45 kalypso NetworkManager: <info>  (ra0): device state change: 1 -> 2 (reason 2)
Feb 23 22:04:45 kalypso NetworkManager: <info>  (ra0): bringing up device.
Feb 23 22:04:46 kalypso avahi-daemon[831]: Registering new address record for fe80::f27d:68ff:fe14:36cf on ra0.*.
Feb 23 22:04:46 kalypso NetworkManager: <info>  (ra0): preparing device.
Feb 23 22:04:46 kalypso NetworkManager: <info>  (ra0): deactivating device (reason: 2).
Feb 23 22:04:46 kalypso NetworkManager: <info>  (ra0): supplicant manager state:  down -> idle
Feb 23 22:04:46 kalypso NetworkManager: <info>  (ra0): device state change: 2 -> 3 (reason 0)
Feb 23 22:04:46 kalypso NetworkManager: <info>  (ra0): supplicant interface state:  starting -> ready
Feb 23 23:00:14 kalypso dhclient: Listening on LPF/ra0/f0:7d:68:14:36:cf
Feb 23 23:00:14 kalypso dhclient: Sending on   LPF/ra0/f0:7d:68:14:36:cf
Feb 23 23:00:15 kalypso dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
Feb 23 23:00:19 kalypso dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
Feb 23 23:00:30 kalypso dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
Feb 23 23:00:41 kalypso dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
Feb 23 23:00:56 kalypso dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
Feb 23 23:01:09 kalypso dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
Feb 24 08:58:44 kalypso NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/net/ra0, iface: ra0)
Feb 24 08:58:44 kalypso NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/net/ra0, iface: ra0): no ifupdown configuration found.
Feb 24 08:58:45 kalypso NetworkManager: <info>  (ra0): driver does not support SSID scans (scan_capa 0x00).
Feb 24 08:58:45 kalypso NetworkManager: <info>  (ra0): new 802.11 WiFi device (driver: 'usb')
Feb 24 08:58:45 kalypso NetworkManager: <info>  (ra0): exported as /org/freedesktop/NetworkManager/Devices/0
Feb 24 08:58:45 kalypso NetworkManager: <info>  (ra0): now managed
Feb 24 08:58:45 kalypso NetworkManager: <info>  (ra0): device state change: 1 -> 2 (reason 2)
Feb 24 08:58:45 kalypso NetworkManager: <info>  (ra0): bringing up device.
Feb 24 08:58:46 kalypso NetworkManager: <info>  (ra0): preparing device.
Feb 24 08:58:46 kalypso NetworkManager: <info>  (ra0): deactivating device (reason: 2).
Feb 24 08:58:46 kalypso NetworkManager: <info>  (ra0): supplicant manager state:  down -> idle
Feb 24 08:58:46 kalypso NetworkManager: <info>  (ra0): device state change: 2 -> 3 (reason 0)
Feb 24 08:58:46 kalypso NetworkManager: <info>  (ra0): supplicant interface state:  starting -> ready
Feb 24 08:58:47 kalypso avahi-daemon[804]: Registering new address record for fe80::f27d:68ff:fe14:36cf on ra0.*.
Feb 24 21:17:31 kalypso NetworkManager: <info>  (ra0): device state change: 3 -> 2 (reason 0)
Feb 24 21:17:31 kalypso NetworkManager: <info>  (ra0): deactivating device (reason: 0).
Feb 24 21:17:31 kalypso NetworkManager: <info>  (ra0): taking down device.
Feb 24 21:17:31 kalypso avahi-daemon[804]: Withdrawing address record for fe80::f27d:68ff:fe14:36cf on ra0.
Feb 24 21:17:33 kalypso NetworkManager: <info>  (ra0): bringing up device.
Feb 24 21:17:34 kalypso NetworkManager: <info>  (ra0): supplicant interface state:  starting -> ready
Feb 24 21:17:34 kalypso NetworkManager: <info>  (ra0): device state change: 2 -> 3 (reason 42)
Feb 24 21:17:36 kalypso avahi-daemon[804]: Registering new address record for fe80::f27d:68ff:fe14:36cf on ra0.*.
Feb 24 21:18:21 kalypso dhclient: Listening on LPF/ra0/f0:7d:68:14:36:cf
Feb 24 21:18:21 kalypso dhclient: Sending on   LPF/ra0/f0:7d:68:14:36:cf
Feb 24 21:18:21 kalypso avahi-daemon[804]: Withdrawing address record for fe80::f27d:68ff:fe14:36cf on ra0.
Feb 24 21:18:23 kalypso avahi-daemon[804]: Registering new address record for fe80::f27d:68ff:fe14:36cf on ra0.*.
Feb 24 21:18:23 kalypso dhclient: Listening on LPF/ra0/f0:7d:68:14:36:cf
Feb 24 21:18:23 kalypso dhclient: Sending on   LPF/ra0/f0:7d:68:14:36:cf
Feb 24 21:18:24 kalypso avahi-daemon[804]: Withdrawing address record for fe80::f27d:68ff:fe14:36cf on ra0.
Feb 24 21:18:26 kalypso avahi-daemon[804]: Registering new address record for fe80::f27d:68ff:fe14:36cf on ra0.*.

```This is where I hit a dead end, because none of the key phrases gave any really useful results at google x(

One rather silly question (excuse me, never used wireless before): Is the WPA key the 10 digit hex-number labeled "network key" on my hardware ? At least I entered this one under Windows and it worked instantly x( . Even if something is wrong here, I expected some error messages.

I feel I got pretty close, but I still need some help for the last few steps. Please give me a tip what might help or how to get some useful error information.

Thanks in advance.

---

### Post by bkratz on 2011-02-24
here is a though thread on your card, perhaps something useful there. About the 10 hex number label, this sounds more like a WEP key than a WPA key (see below copied from about.com)

WEP stands for Wired Equivalent Privacy, a standard for WiFi wireless network security. But what exactly are WEP keys?
Answer: A WEP key is a security code used on some Wi-Fi networks. WEP keys allow a group of devices on a local network (such as a home network) to exchange encoded messages with each other while hiding the contents of the messages from easy viewing by outsiders.
A WEP key is a sequence of hexadecimal digits. These digits include the numbers 0-9 and the letters A-F. Some examples of WEP keys are:

1A648C9FE2
99D767BAC38EA23B0C0176D15
WEP keys are chosen by a network administrator. WEP keys are set on Wi-Fi routers, adapters and other wireless network devices. Matching WEP keys must be set on each device for them to communicate with each other.

The length of a WEP key depends on the type of WEP security (called "encryption") utilized:

40- / 64-bit WEP: 10 digit key
104- / 128-bit WEP: 26 digit key
256-bit WEP: 58 digit key


Sorry, forgot the promised link!

[http://art.ubuntuforums.org/showthread.php?t=1434630](http://art.ubuntuforums.org/showthread.php?t=1434630)

---

### Post by Lastmerlin on 2011-02-25
Thank you for your post and for the link. However, I believe, that I already got around all the issues described there. I do not know, if I exactly used this thread, but the commands proposed there look very familiar to me. The issue essentially was, that the original rt28** and 2870 drivers are bugged and must be replaced by the 3070 (with blacklisting the broken ones). In addition the new driver also had a bug that must be fixed by changing some lines in the source.

Thats why I posted the output of lsmod to show, that I have the 3070 module running. I believe that the driver finally works, at least I can not see any errors in the outputs of usb-devices, dmesg, iwconfig. Of course I will also post the output if you propose another command that might reveal the problem. 

As, for instance, detection of different access points works, I bet that the device cant be completely malfunctioning. However, configuration both via networkmanager and via shell failed and (thats what really annoys me) did not yield any useful error messages.

---

