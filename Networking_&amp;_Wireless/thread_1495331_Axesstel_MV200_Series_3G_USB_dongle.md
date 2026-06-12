---
title: "Axesstel MV200 Series 3G USB dongle"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by bzkd on 2010-05-28
I have an Internet 3G CDMA USB device that still does not work under Ubuntu, though it works well under Win7/Vista.
Please Help: how can I make this small usb device work under ubuntu?

I'm using Ubuntu 9.10 Karmic.
Found this error in syslog: Your CDMA modem does not support +CMEE command

---

### Post by SlidingHorn on 2010-05-28
More info needed: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by pdc on 2010-05-28
I think this device connects to a CDMA telephone system, rather than wifi

if you plug it in, and type into a terminal

> lsusb

and if you copy and paste this command 

> dmesg | grep tty

and copy and paste the results back here please

if you tell us the country and network you wish to connect to please

---

### Post by bzkd on 2010-05-29
I apologize for the lack of information.

Please find in the following lines details about my config:

[LIST][*]lsusb
[/LIST]
```

$ lsusb
Bus 001 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 002: ID 15a9:0004  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1726:1900  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
$

```

[LIST][*]dmesg | grep tty
[/LIST]
```

$ dmesg | grep tty
[    0.003017] console [[COLOR="#ff0000"]tty[/COLOR]0] enabled
[ 1214.924281] usb 2-8: GSM modem (1-port) converter now attached to [COLOR="Red"]tty[/COLOR]USB0
[ 1214.924397] usb 2-8: GSM modem (1-port) converter now attached to [COLOR="#ff0000"]tty[/COLOR]USB1
$

```

[LIST][*]lspci
[/LIST]
```

$ lspci
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation C73 [GeForce 7100 / nForce 630i] (rev a2)
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
$ 

```

[LIST][*]lspci -nn | grep 'Wireless Brand'
[/LIST]
```

$ lspci -nn | grep 'Wireless Brand'
$

```

[LIST][*]ifconfig
[/LIST]
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:68:38:80:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:28 Adresse de base:0xc000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:153 erreurs:0 :0 overruns:0 frame:0
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:32465 (32.4 KB) Octets transmis:32465 (32.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:52:d6:1a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-5F-52-D6-1A-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

$

```

[LIST][*]iwconfig
[/LIST]
```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

$

```

[LIST][*]sudo lshw -C network
[/LIST]
```

$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:22:68:38:80:cc
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:28 memory:efffd000-efffdfff ioport:f600(size=8) memory:efffc000-efffc0ff memory:efffb000-efffb00f
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:5f:52:d6:1a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
$

```

[LIST][*]lsb_release -d
[/LIST]
```

$ lsb_release -d
Description:	Ubuntu 9.10
$

```

[LIST][*]uname -mr
[/LIST]
```

$ uname -mr
2.6.31-20-generic i686
$

```

[LIST][*]tail -n 50 /var/log/syslog
[/LIST]
```

$ tail -n 50 /var/log/syslog
May 30 00:14:22 dan-desktop kernel: [ 1211.533606] VFS: busy inodes on changed media or resized disk sr1
May 30 00:14:23 dan-desktop kernel: [ 1213.102309] usb 2-8: USB disconnect, address 2
May 30 00:14:23 dan-desktop kernel: [ 1213.102934] cdrom: issuing MRW back ground format suspend
May 30 00:14:25 dan-desktop kernel: [ 1214.632930] usb 2-8: new full speed USB device using ohci_hcd and address 3
May 30 00:14:25 dan-desktop kernel: [ 1214.855217] usb 2-8: configuration #1 chosen from 1 choice
May 30 00:14:25 dan-desktop kernel: [ 1214.915742] usbcore: registered new interface driver usbserial
May 30 00:14:25 dan-desktop kernel: [ 1214.915766] USB Serial support registered for generic
May 30 00:14:25 dan-desktop kernel: [ 1214.915817] usbcore: registered new interface driver usbserial_generic
May 30 00:14:25 dan-desktop kernel: [ 1214.915820] usbserial: USB Serial Driver core
May 30 00:14:25 dan-desktop kernel: [ 1214.924093] USB Serial support registered for GSM modem (1-port)
May 30 00:14:25 dan-desktop kernel: [ 1214.924151] option 2-8:1.0: GSM modem (1-port) converter detected
May 30 00:14:25 dan-desktop kernel: [ 1214.924281] usb 2-8: GSM modem (1-port) converter now attached to ttyUSB0
May 30 00:14:25 dan-desktop kernel: [ 1214.924307] option 2-8:1.1: GSM modem (1-port) converter detected
May 30 00:14:25 dan-desktop kernel: [ 1214.924397] usb 2-8: GSM modem (1-port) converter now attached to ttyUSB1
May 30 00:14:25 dan-desktop kernel: [ 1214.924420] usbcore: registered new interface driver option
May 30 00:14:25 dan-desktop kernel: [ 1214.924423] option: v0.7.2:USB Driver for GSM modems
May 30 00:14:25 dan-desktop modem-manager: (ttyUSB0) opening serial device...
May 30 00:14:25 dan-desktop modem-manager: (ttyUSB0): probe requested by plugin 'Generic'
May 30 00:14:25 dan-desktop modem-manager: (ttyUSB1) opening serial device...
May 30 00:14:25 dan-desktop modem-manager: (ttyUSB1): probe requested by plugin 'Generic'
May 30 00:14:27 dan-desktop modem-manager: (ttyUSB0) closing serial device...
May 30 00:14:27 dan-desktop modem-manager: (Generic): CDMA modem /sys/devices/pci0000:00/0000:00:04.0/usb2/2-8 claimed port ttyUSB0
May 30 00:14:27 dan-desktop modem-manager: Added modem /sys/devices/pci0000:00/0000:00:04.0/usb2/2-8
May 30 00:14:27 dan-desktop modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:04.0/usb2/2-8 as /org/freedesktop/ModemManager/Modems/0
May 30 00:14:27 dan-desktop NetworkManager: <info>  (ttyUSB0): new CDMA device (driver: 'option1')
May 30 00:14:27 dan-desktop NetworkManager: <info>  (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/2
May 30 00:14:27 dan-desktop NetworkManager: <info>  (ttyUSB0): now managed
May 30 00:14:27 dan-desktop NetworkManager: <info>  (ttyUSB0): device state change: 1 -> 2 (reason 2)
May 30 00:14:27 dan-desktop NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 2).
May 30 00:14:27 dan-desktop NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
May 30 00:14:27 dan-desktop NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
May 30 00:14:27 dan-desktop NetworkManager: <info>  (ttyUSB0): device state change: 2 -> 3 (reason 0)
May 30 00:14:37 dan-desktop modem-manager: (ttyUSB1) closing serial device...
May 30 00:14:50 dan-desktop wpa_supplicant[1053]: CTRL-EVENT-SCAN-RESULTS 
May 30 00:15:50 dan-desktop wpa_supplicant[1053]: CTRL-EVENT-SCAN-RESULTS 
May 30 00:16:50 dan-desktop wpa_supplicant[1053]: CTRL-EVENT-SCAN-RESULTS 
May 30 00:17:01 dan-desktop CRON[4621]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 30 00:17:50 dan-desktop wpa_supplicant[1053]: CTRL-EVENT-SCAN-RESULTS 
May 30 00:18:50 dan-desktop wpa_supplicant[1053]: CTRL-EVENT-SCAN-RESULTS 
May 30 00:19:50 dan-desktop wpa_supplicant[1053]: CTRL-EVENT-SCAN-RESULTS 
May 30 00:20:04 dan-desktop kernel: [ 1553.565383] usb 1-9: reset high speed USB device using ehci_hcd and address 4
May 30 00:20:10 dan-desktop NetworkManager: <info>  Activation (ttyUSB0) starting connection 'MTN connection'
May 30 00:20:10 dan-desktop NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
May 30 00:20:10 dan-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
May 30 00:20:10 dan-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
May 30 00:20:10 dan-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
May 30 00:20:10 dan-desktop modem-manager: (ttyUSB0) opening serial device...
May 30 00:20:10 dan-desktop modem-manager: Got failure code 100: Unknown error
May 30 00:20:10 dan-desktop modem-manager: Your CDMA modem does not support +CMEE command
May 30 00:20:12 dan-desktop kernel: [ 1561.580024] usb 1-9: reset high speed USB device using ehci_hcd and address 4
$

```


I'm using a CDMA 1x EV-DO USB dongle made by Axesstel and sold by MTN.
This small USB modem connects to the internet through a CDMA network.

Please, excuse me once again for the lack of details.

I have an HP Pavilion Slimline s3721af.

Let me remind you the problem I am facing:
I have an Internet 3G CDMA USB device that still does not work under Ubuntu, though it works well under Win7/Vista.
How can I make this small usb device work under ubuntu?

I'm using Ubuntu 9.10 Karmic.
Found this error in syslog: Your CDMA modem does not support +CMEE command

---

### Post by pdc on 2010-05-30
so when the result says

> GSM modem (1-port) converter now attached to ttyUSB0

.. that SHOULD be good to dial up ...

as here ......

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

.... have you tried that?

With CDMA I believe you will need a specific user name and password, whereas on GSM the Simcard is the unique identifier

> Found this error in syslog: Your CDMA modem does not support +CMEE comm

you and I need to google on this to see if it is important

---

### Post by bzkd on 2010-05-30
> **pdc said:**
> so when the result says



.. that SHOULD be good to dial up ...

as here ......

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

.... have you tried that?

With CDMA I believe you will need a specific user name and password, whereas on GSM the Simcard is the unique identifier



you and I need to google on this to see if it is important

Thank you for your reply, pdc.

Yes! I've already tried to configure Network Manager WITH my specific username and password for the CDMA network, as I do under Win7/Vista where it works.
But It's the first time I hear about HSO module. So I'll try again and verify that HSO module is available (though I still do not know if I need this or not).

:) It's a long time since I'm googling on this ](*,)

---

### Post by pdc on 2010-05-30
> s here ......

[http://www.pharscape.org/networkmana...an-modems.html](http://www.pharscape.org/networkmana...an-modems.html)

.... have you tried that?

sorry:

I should have said: 

GO Halfway down Page:

to 

Create a mobile broadband connection 

THat's what I meant

so I was **NOT** pointing you to hso

---

### Post by claude170358 on 2010-09-06
Bonjour,

Le modem AXESSTEL MV220 fonctionne sans problème avec UBUNTU 9.04. Il suffit d'éjecter le périphérique et de modifier (login et mot de passe) la connexion CDMA qui se crée automatiquement.

Par contre je n'ai pas réussi à le faire fonctionner avec UBUNTU 9.10 ou 10.04. Si tu trouves une solution, informes moi.

---

### Post by bzkd on 2010-09-06
> **claude170358 said:**
> Bonjour,

Le modem AXESSTEL MV220 fonctionne sans problème avec UBUNTU 9.04. Il suffit d'éjecter le périphérique et de modifier (login et mot de passe) la connexion CDMA qui se crée automatiquement.

Par contre je n'ai pas réussi à le faire fonctionner avec UBUNTU 9.10 ou 10.04. Si tu trouves une solution, informes moi.

MTN delivered a solution documented inside a CDROM: ***recompile your linux kernel after tweaking some network parameters at source code level!***. After that, you'll be able to configure and use the device under Ubuntu.
This is an strange attitude 'cause if you want for instance to install the latest Ubuntu from livecd, where should you find the internet during install?

Cannot we write a sort of driver specifically for that device?

@pdc: No No, It Still Does Not work, in spite of the methods you suggested.

---

### Post by bzkd on 2010-09-06
Now tried the device on both new Ubuntu and Kubuntu Lucid 10.04; but same failures.....

---

### Post by bzkd on 2010-09-26
:( Just tried the same device on Ubuntu Maverick Pre-release; didn't work on it either..

---

### Post by andrey--k on 2011-01-28
&#1059; &#1084;&#1077;&#1085;&#1103; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1089;&#1090;&#1072;&#1074;&#1080;&#1090;&#1100; &#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1090;&#1100; &#1076;&#1072;&#1085;&#1085;&#1099;&#1081; &#1084;&#1086;&#1076;&#1077;&#1084; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1084; &#1086;&#1073;&#1088;&#1072;&#1079;&#1086;&#1084;:
&#1087;&#1088;&#1080; &#1087;&#1086;&#1076;&#1082;&#1083;&#1102;&#1095;&#1077;&#1085;&#1080;&#1080; &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072; &#1089;&#1086;&#1079;&#1076;&#1072;&#1077;&#1090;&#1089;&#1103; /dev/cdrom1, &#1084;&#1099; &#1077;&#1075;&#1086; &#1084;&#1086;&#1085;&#1090;&#1080;&#1088;&#1091;&#1077;&#1084; &#1082;&#1091;&#1076;&#1072;-&#1083;&#1080;&#1073;&#1086;, &#1086;&#1090;&#1082;&#1088;&#1099;&#1074;&#1072;&#1077;&#1084; &#1074; &#1085;&#1077;&#1084; &#1090;&#1077;&#1082;&#1089;&#1090;&#1086;&#1074;&#1080;&#1082; &#1074; &#1087;&#1072;&#1087;&#1082;&#1077; umountdrive (&#1082;&#1072;&#1082; &#1090;&#1086; &#1090;&#1072;&#1082; &#1085;&#1072;&#1079;&#1099;&#1074;&#1072;&#1083;&#1072;&#1089;&#1100;), &#1078;&#1076;&#1077;&#1084; 30-40 &#1089;&#1077;&#1082;&#1091;&#1085;&#1076;, &#1080; &#1084;&#1077;&#1085;&#1077;&#1076;&#1078;&#1077;&#1088; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1081; &#1087;&#1086;&#1076;&#1093;&#1074;&#1072;&#1090;&#1099;&#1074;&#1072;&#1077;&#1077;&#1090; &#1084;&#1086;&#1076;&#1077;&#1084;.
&#1055;&#1086;&#1089;&#1083;&#1077; &#1101;&#1090;&#1086;&#1075;&#1086; (&#1085;&#1086; &#1085;&#1077; &#1088;&#1072;&#1085;&#1100;&#1096;&#1077; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1082;&#1080; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1085;&#1080;&#1103;) &#1084;&#1086;&#1078;&#1085;&#1086; &#1086;&#1090;&#1084;&#1086;&#1085;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1090;&#1100; cdrom

Sorry for my english...
I've conected this modem next steps:
when modem conected, creates device cdrom1, I mounted it in /tmp/blabla, opened file /tmp/blabla/unmountcdrom/somename.txt (I cannt remember real name of folder), wait about minute, than connect manager esteblished conection avtomaticaly. After you can umount /tmp/blabla. do not umount before conect manager establishes connection, I've trobles in case of umounting too early.

---

