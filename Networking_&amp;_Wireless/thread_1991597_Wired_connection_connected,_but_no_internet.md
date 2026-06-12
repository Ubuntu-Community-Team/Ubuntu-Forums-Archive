---
title: "Wired connection connected, but no internet"
date: 2012-05-30
forum: Networking &amp; Wireless
---

### Post by ping128 on 2012-05-30
Hi, I'm using Ubuntu 12.04. My wireless is working fine. The wired cable are connected in the top right menu, but there is no internet through wired connection. I'm using internet through wireless.

I also don't find eth0, as I saw when the wired connection is working

---

### Post by ping128 on 2012-05-30
```
ping128@admin:$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

``````
ping128@admin:$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        B8:AC:6F:6E:34:7F

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         128.208.117.144
    Prefix:          24 (255.255.255.0)
    Gateway:         128.208.117.100



- Device: wlan0  [thehousejew] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           no
  HW Address:        70:F1:A1:BA:B4:40

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *thehousejew:    Infra, 58:6D:8F:01:58:B4, Freq 2462 MHz, Rate 54 Mb/s, Strength 78 WPA2
    BronzeSpruce:    Infra, 68:7F:74:C9:67:BD, Freq 2462 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    Cisco87328:      Infra, 68:7F:74:3A:A0:D2, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    Black Mesa:      Infra, 00:13:10:C7:91:F9, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    LHC:             Infra, 00:23:69:C9:F7:FE, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA2
    Miley 570:       Infra, 5C:D9:98:5A:6A:6C, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA
    ShyTiger:        Infra, 58:6D:8F:50:15:70, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    Skynet:          Infra, 98:FC:11:8F:16:02, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA2
    juliakayla:      Infra, 00:25:9C:D4:5A:5E, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    pAnTy Dr0pPa$:   Infra, 00:14:6C:79:5F:A4, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA
    ILikeTurtles:    Infra, 08:86:3B:2F:B1:8C, Freq 2422 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    FireHazard:      Infra, 00:1C:10:99:45:64, Freq 2422 MHz, Rate 54 Mb/s, Strength 45 WPA
    belkin.45f:      Infra, 08:86:3B:54:54:5F, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    U+Net2DF3:       Infra, 00:40:5A:62:2D:F1, Freq 2452 MHz, Rate 54 Mb/s, Strength 44 WPA2
    What did you say?: Infra, 1C:AF:F7:CA:7F:BF, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    jmorgan:         Infra, 94:44:52:FA:48:02, Freq 2427 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    McCarty567:      Infra, 08:86:3B:3F:3F:36, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    JadeCat20:       Infra, 58:6D:8F:35:60:1C, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    KarliMitzel:     Infra, E0:46:9A:8D:73:5E, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    McCarty 684:     Infra, 00:21:91:F7:98:3F, Freq 2417 MHz, Rate 54 Mb/s, Strength 29 WPA2
    356:             Infra, 08:86:3B:3B:3E:92, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Ryan Gutierrez's Network: Infra, 00:1B:63:23:F7:FD, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    SAKNIB:          Infra, 00:1D:7E:6C:AD:0D, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    SpiroTheHero:    Infra, 4C:E6:76:64:4C:92, Freq 2447 MHz, Rate 54 Mb/s, Strength 70 WEP
    Mr.Leaf:         Infra, 00:90:4C:7E:00:10, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WEP
    Thompson-Lazo:   Infra, 00:21:91:EF:7C:AA, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WEP
    BronzeSpruce-guest: Infra, 68:7F:74:C9:67:BE, Freq 2462 MHz, Rate 54 Mb/s, Strength 79
    Connectify-jyk:  Ad-Hoc, 22:06:BD:2E:17:9F, Freq 2462 MHz, Rate 11 Mb/s, Strength 77
    Xindi's MacBook Pro: Infra, 28:CF:DA:E6:48:90, Freq 2462 MHz, Rate 54 Mb/s, Strength 60
    ShyTiger-guest:  Infra, 58:6D:8F:50:15:72, Freq 2412 MHz, Rate 54 Mb/s, Strength 57
    HPD110a.57449F:  Ad-Hoc, 02:23:33:D4:7A:D3, Freq 2437 MHz, Rate 54 Mb/s, Strength 55
    hpsetup:         Ad-Hoc, 2E:25:B3:88:97:BE, Freq 2437 MHz, Rate 11 Mb/s, Strength 39
    JadeCat20-guest: Infra, 58:6D:8F:35:60:1E, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    Swagnificent:    Infra, 20:4E:7F:38:EA:62, Freq 2417 MHz, Rate 54 Mb/s, Strength 35 WPA2
    Skynet2029:      Infra, 00:1B:11:72:D6:00, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2
    Buho:            Infra, 08:86:3B:2A:94:D6, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    GetYourDawgOffMyLAN: Infra, 08:86:3B:39:F9:D4, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Bert:            Infra, C0:C1:C0:C4:9E:F5, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    NCJB:            Infra, 08:86:3B:49:41:9E, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Sullivan569:     Infra, 14:D6:4D:2E:81:AC, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    H518:            Infra, E0:46:9A:88:97:D8, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2
    WE CAN HEAR YOU JERKING OFF: Infra, 74:44:01:2F:BB:97, Freq 2442 MHz, Rate 54 Mb/s, Strength 24 WPA2
    NETGEAR20:       Infra, 20:4E:7F:98:EF:54, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    Bill Nye the WiFi Guy: Infra, 00:09:5B:6E:5F:26, Freq 2462 MHz, Rate 11 Mb/s, Strength 47 WEP
    Puzzles:         Infra, 08:86:3B:89:29:D4, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    H214:            Infra, 08:86:3B:5E:6B:00, Freq 2447 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Mine:            Infra, 00:22:75:53:03:72, Freq 2452 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2

  IPv4 Settings:
    Address:         128.208.117.36
    Prefix:          24 (255.255.255.0)
    Gateway:         128.208.117.100

    DNS:             140.142.17.18
    DNS:             140.142.15.27


ping128@admin:$ 

```

```

ping128@admin:$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"thehousejew"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 58:6D:8F:01:58:B4   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:43   Missed beacon:0

eth0      no wireless extensions.

```

---

### Post by bhishan on 2012-05-30
Could you post the results of $ ifconfig

---

### Post by ping128 on 2012-05-30
yes, sure

```
ping128@admin:$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:6e:34:7f  
          inet addr:128.208.117.144  Bcast:128.208.117.255  Mask:255.255.255.0
          inet6 addr: fe80::baac:6fff:fe6e:347f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15081 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6473 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:6323721 (6.3 MB)  TX bytes:1000100 (1.0 MB)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:126914 (126.9 KB)  TX bytes:126914 (126.9 KB)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:ba:b4:40  
          inet addr:128.208.117.36  Bcast:128.208.117.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:feba:b440/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2228048 (2.2 MB)  TX bytes:11309 (11.3 KB)


```

---

### Post by bhishan on 2012-05-30
On line 6 of the results I see carrier: 4
I am not that sure, but I think it should be 0. I need to do a little more research. Sorry.

---

### Post by bhishan on 2012-05-30
also, did you use the $ ifconfig while connected to wireless? If so, could you try disconnecting wireless and use $ ifconfig, and see if anything changes.

---

### Post by ping128 on 2012-05-30
Yes, I didn't 

This is what I got without wireless connection.

```
ping128@admin:$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:6e:34:7f  
          inet addr:128.208.117.144  Bcast:128.208.117.255  Mask:255.255.255.0
          inet6 addr: fe80::baac:6fff:fe6e:347f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17923 errors:0 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:20501320 (20.5 MB)  TX bytes:3250148 (3.2 MB)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:793482 (793.4 KB)  TX bytes:793482 (793.4 KB)

```

---

### Post by ping128 on 2012-05-31
I just figure it out. I don't even know why it works. As I remember, I changed the IPv4 settings Method: "Automatic (DHCP) addresses only" to "Automatic (DHCP)" and the wired connection has Internet access!

---

