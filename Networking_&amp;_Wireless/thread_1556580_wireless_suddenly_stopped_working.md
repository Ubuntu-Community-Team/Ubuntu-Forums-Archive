---
title: "wireless suddenly stopped working"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by spd1 on 2010-08-19
hi, i'm relatively new at linux and i'm french speaking, so pardon my english
i've had Ubuntu 10.04 for about two mouths, my wireless connection was working just fine, until sunddenly, one morning I just opened my computer and there were no more internet connection and the network tray icon also disappeared. wired connection is working, but not wireless, so the problem is not my router or modem. I unsuccesfully tried all the solutions for similar problem posted on forums. nothing seems to works.

here is what **iwconfig** gives:

> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off



here is **ifconfig**:

> eth0      Link encap:Ethernet  HWaddr 00:1e:68:fe:00:00  
          inet adr:192.168.1.101  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::21e:68ff:fefe:0/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:55535 erreurs:0 :0 overruns:0 frame:0
          TX packets:39382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:73479577 (73.4 MB) Octets transmis:4191209 (4.1 MB)
          Interruption:23 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:20 erreurs:0 :0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:1312 (1.3 KB) Octets transmis:1312 (1.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:47:b3:16  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:17:c4:47:b3:16  
          inet adr:169.254.6.175  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1



here is **lshw** (i only copied network):

> *-network
             description: Wireless interface
             product: AR928X Wireless Network Adapter (PCI-Express)
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:0b:00.0
             logical name: wlan0
             version: 01
             serial: 00:17:c4:47:b3:16
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
             resources: irq:21 memory:ca400000-ca40ffff




as for network tray icon, the nm-applet command is right, notification area is present, but still nothing. 

I uninstalled bluetooth app the day before it happened, i really don't know if it has something to do with it, but i guess i'd just mention it... i tried reinstalling it and it had no effect.


if anyone can help i'd be very greatfull
thanks

---

### Post by spd1 on 2010-08-23
anyone?! :lolflag:

---

### Post by spd1 on 2010-09-02
Here's what **nm-tool** gives me:

NetworkManager Tool

State: connected


** (process:2965): WARNING **: error: failed to read connections from org.freedesktop.NetworkManagerUserSettings:
    The name org.freedesktop.NetworkManagerUserSettings was not provided by any .service files
- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:1E:68:FE:00:00

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             216.239.64.154
    DNS:             216.239.64.155


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        00:17:C4:47:B3:16

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    mysterieusesondes: Infra, 00:26:5A:D2:47:34, Freq 2437 MHz, Rate 54 Mb/s, Strength 28 WPA2
    SaidMaroc:       Infra, 00:1B:5B:AB:3E:21, Freq 2427 MHz, Rate 54 Mb/s, Strength 30 WEP
    SpeedTouchB0F018:Infra, 00:90:D0:E9:7B:81, Freq 2437 MHz, Rate 54 Mb/s, Strength 28 WEP
    belkin54g:       Infra, 00:17:3F:7F:34:C4, Freq 2462 MHz, Rate 54 Mb/s, Strength 28 WEP
    BELL181:         Infra, B0:E7:54:68:9B:B9, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WEP
    L Pelletier:     Infra, 00:1E:58:ED:9A:63, Freq 2412 MHz, Rate 54 Mb/s, Strength 31 WPA
    default:         Infra, 00:13:46:B8:04:02, Freq 2437 MHz, Rate 54 Mb/s, Strength 44
    BELL448:         Infra, B0:E7:54:6A:CE:A1, Freq 2432 MHz, Rate 54 Mb/s, Strength 32 WEP
    BELL586:         Infra, 00:25:3C:C6:8F:09, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WEP
    BELL793:         Infra, 00:24:56:3F:2C:71, Freq 2422 MHz, Rate 54 Mb/s, Strength 32 WEP
    BELL895:         Infra, 00:1D:5A:DD:23:E1, Freq 2447 MHz, Rate 54 Mb/s, Strength 35 WEP
    BELL3000:        Infra, 00:25:3C:B5:1F:B1, Freq 2417 MHz, Rate 54 Mb/s, Strength 61 WPA
    Kropotkine:      Infra, 00:25:9C:2C:5F:5D, Freq 2437 MHz, Rate 54 Mb/s, Strength 98 WPA WPA2

---

### Post by spd1 on 2010-09-02
ok, so I reinstalled network-manager-gnome

rebooted

and it finally worked...

---

### Post by AndyM3 on 2010-09-02
Don't start apps you want to be permanently running from a terminal. Use Alt+F2 or type "& disown" after the application name (so, for example, "nm-applet" turns into "nm-applet & disown").
Also, add an entry for nm-applet in "Startup Applications" (look for it in the preferences menus) if it's not already there.
Hope that helps :D

And please, don't double-, triple- or quadruple-post. It makes it less likely that you'll ever get an answer. Read [this]("http://www.catb.org/esr/faqs/smart-questions.html") before posting in any forum or mailing list.

EDIT: damn, beat me to it :mrgreen:

---

### Post by spd1 on 2010-09-02
[AUTO-SOLVED]

all I had t do was reinstall network-manager-gnome and start the nm-applet.

---

