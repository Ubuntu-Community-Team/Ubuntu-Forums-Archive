---
title: "Intel Centrinio Wireless-n-1000 problem"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by Mikyll on 2013-09-03
would use linux more if not for issues i keep having. One in particular  is a real pain. I am in college, so I use linux a few times a week for  school projects. I have actually managed to currupt the system, not  install enough memory on the partition, and things like that which  require a reinstall every single time. I am on an HP-dv6t qe edition  laptop with the intel centrino wireless-n-1000 network card so every  time i have to reinstall, I have to go through the proceess of fixing  the wireless functionallity. I have just built a new computer, however,  and lost the solution that I was using. 

I searched around and found your post that I thought i was using:

[http://ubuntuforums.org/showthread.php?t=205690](http://ubuntuforums.org/showthread.php?t=205690)

where you say use sudo modprobe -r iwlwifi; sudo modprobe iwlwifi 11n_disable=1;
This works temporarily after saving it to the  /etc/modprobe.d/iwlwifi.conf file, but after about 2 minutes the  connection loads forever. No "not connected", but no connection either.

I still get this from iwconfig:
```
iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"mynetwork"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:6B:62:B5:A2   
          Bit Rate=39 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:43   Missed beacon:0


```

also from nm-tool:
```
nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [mynetwork] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        8C:A9:82:AF:A8:8A

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Mojito:          Infra, E8:89:2C:72:7A:E0, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    Wireless:        Infra, 74:44:01:05:2F:53, Freq 2442 MHz, Rate 54 Mb/s, Strength 65 WPA2
    Home Network:    Infra, E0:46:9A:4B:75:AA, Freq 2427 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    KAE:             Infra, E0:46:9A:44:55:8A, Freq 2417 MHz, Rate 54 Mb/s, Strength 49 WPA2
    Tsquared:        Infra, 00:25:9C:D3:FC:D8, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    GoodApple:       Infra, 00:25:BC:8C:A4:8B, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    NavyGirl (2.4GHz): Infra, C4:3D:C7:97:E6:0D, Freq 2427 MHz, Rate 54 Mb/s, Strength 39 WPA2
    taniwha:         Infra, 68:7F:74:B8:53:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Aries:           Infra, B8:9B:C9:5F:5A:A8, Freq 2457 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    DevineSuite:     Infra, 28:C6:8E:8E:FA:48, Freq 2442 MHz, Rate 54 Mb/s, Strength 24 WPA2
    amitom:          Infra, C4:39:3A:11:6E:48, Freq 2432 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Douang's Wi-Fi Network: Infra, 00:1E:52:7A:58:B7, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    *mynetwork:     Infra, 00:22:6B:62:B5:A2, Freq 2462 MHz, Rate 54 Mb/s, Strength 77 WPA
    HOME-4002:       Infra, 00:1D:D6:43:40:00, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    SeedFactory:     Infra, DC:45:17:C8:99:90, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    shakerhawsawi:   Infra, 20:10:7A:74:4E:AD, Freq 2457 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    MonieLuv:        Infra, 00:1B:2F:02:1E:16, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2
    VERTSYS:         Infra, 7C:BF:B1:39:BC:80, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Diamond:         Infra, E0:91:F5:AF:91:A4, Freq 2422 MHz, Rate 54 Mb/s, Strength 19 WEP

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76

  IPv6 Settings:
    Address:         2002:1862:c0e8:0:3c2a:f04a:9826:53a0
    Prefix:          64
    Gateway:         fe80::222:6bff:fe62:b5a0

    Address:         2002:1862:c0e8:0:8ea9:82ff:feaf:a88a
    Prefix:          64
    Gateway:         fe80::222:6bff:fe62:b5a0

    Address:         fe80::8ea9:82ff:feaf:a88a
    Prefix:          64
    Gateway:         fe80::222:6bff:fe62:b5a0



- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        10:1F:74:0D:BA:69

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76

  IPv6 Settings:
    Address:         2002:1862:c0e8:0:5160:a801:78ed:9772
    Prefix:          64
    Gateway:         fe80::222:6bff:fe62:b5a0

    Address:         2002:1862:c0e8:0:121f:74ff:fe0d:ba69
    Prefix:          64
    Gateway:         fe80::222:6bff:fe62:b5a0

    Address:         fe80::121f:74ff:fe0d:ba69
    Prefix:          64
    Gateway:         fe80::222:6bff:fe62:b5a0




```

Running on Ubuntu 12.04.3
```
cat /etc/modprobe.d/iwlwifi.conf
options iwlwifi 11n_disable=1


```

I am currently having to post this on a wired network.

If you could offer me some help, I would greatly appreciate it.

Thank you very much.

---

### Post by chili555 on 2013-09-03
You seem to have both a wired and wireless connection. Please detach the ethernet and run:```
iwconfig > mikyll.txt
ping -c3 192.168.1.1 >> mikyll.txt
ping -c3 www.google.com >> mikyll.txt
dmesg | grep iwl >> mikyll.txt
```Now click the Network Manager icon and disconnect the wireless. Connect the ethernet, find the file mikyll.txt in your user directory and attach it as an attachment to your reply using the paperclip tool at the top of the reply box.

I notice you have an IPv6 address. Some hardware and driver combinations work well with IPv6 and some do not. I suggest, as an experiment, that you disable it in Network manager as attached.

---

### Post by Mikyll on 2013-09-03
Disconnected ethernet and ran commands. Also before running disableed IPV6.

```
wlan0     IEEE 802.11bgn  ESSID:"mynetwork"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:6B:62:B5:A2   
          Bit Rate=65 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:83  Invalid misc:425   Missed beacon:0

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.100 icmp_seq=1 Destination Host Unreachable
From 192.168.1.100 icmp_seq=2 Destination Host Unreachable
From 192.168.1.100 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2007ms
pipe 2
[   14.689200] iwlwifi 0000:0d:00.0: irq 55 for MSI/MSI-X
[   15.013679] iwlwifi 0000:0d:00.0: loaded firmware version 39.31.5.1 build 35138
[   15.950999] iwlwifi 0000:0d:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   15.951004] iwlwifi 0000:0d:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   15.951006] iwlwifi 0000:0d:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   15.951009] iwlwifi 0000:0d:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   15.951011] iwlwifi 0000:0d:00.0: CONFIG_IWLWIFI_P2P disabled
[   15.951014] iwlwifi 0000:0d:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   15.951089] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S
[   16.093931] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   20.125176] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S
[   20.132556] iwlwifi 0000:0d:00.0: Radio type=0x0-0x0-0x3
[   20.272183] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S
[   20.279538] iwlwifi 0000:0d:00.0: Radio type=0x0-0x0-0x3
[  255.156539] iwlwifi 0000:0d:00.0: RF_KILL bit toggled to disable radio.
[  255.157172] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  255.157276] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  255.190598] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  255.190618] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  255.190636] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  255.190653] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  255.190689] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  255.190702] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  255.190836] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  255.202517] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  756.059348] iwlwifi 0000:0d:00.0: RF_KILL bit toggled to enable radio.
[  756.275881] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S
[  756.283259] iwlwifi 0000:0d:00.0: Radio type=0x0-0x0-0x3
[  882.546071] iwlwifi 0000:0d:00.0: RF_KILL bit toggled to disable radio.
[  882.546791] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  882.546919] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  882.562783] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  882.562805] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  882.562825] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  882.562845] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  882.562882] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  882.562893] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  882.563153] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  882.570679] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  905.260057] iwlwifi 0000:0d:00.0: RF_KILL bit toggled to enable radio.
[  905.471697] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S
[  905.479077] iwlwifi 0000:0d:00.0: Radio type=0x0-0x0-0x3
```

Also from ping -c3 [www.google.com](www.google.com)

ping: unknown host [www.google.com](www.google.com)

---

### Post by chili555 on 2013-09-03
> [  882.562893] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  882.563153] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  882.570679] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[  905.260057] iwlwifi 0000:0d:00.0: RF_KILL bit toggled to enable radio.Hmmm. Weird. What does this tell us now?```
rfkill list all
```One wonders how you got an IP address previously when:> RF_KILL bit toggled to disable radio.Did you fill in the IP address, gateway, etc. in Network Manager or...??

EDIT: I am starting my 12.04 live CD to help troubleshoot.

---

### Post by Mikyll on 2013-09-03
rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


No I did not.

---

### Post by chili555 on 2013-09-03
Please leave the wireless switch or key combination as is and reboot without the ethernet cable and run and post:```
nm-tool
```Your iwconfig looks solid. Your ping looks awful. My favorite kind of problem; everything looks great except it doesn't work!!!

---

### Post by Mikyll on 2013-09-03
It works now, so maybe I just needed to restart after saving the iwlwifi file.

But just in case here is nm-tool: 

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Stewart434] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        8C:A9:82:AF:A8:8A

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    belkin.db4:      Infra, 08:86:3B:9B:9D:B4, Freq 2417 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    Mojito:          Infra, E8:89:2C:72:7A:E0, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    Home Network:    Infra, E0:46:9A:4B:75:AA, Freq 2427 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    Wireless:        Infra, 74:44:01:05:2F:53, Freq 2442 MHz, Rate 54 Mb/s, Strength 59 WPA2
    taniwha:         Infra, 68:7F:74:B8:53:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    GoodApple:       Infra, 00:25:BC:8C:A4:8B, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    KAE:             Infra, E0:46:9A:44:55:8A, Freq 2417 MHz, Rate 54 Mb/s, Strength 40 WPA2
    Douang's Wi-Fi Network: Infra, 00:1E:52:7A:58:B7, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    MonieLuv:        Infra, 00:1B:2F:02:1E:16, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Tsquared:        Infra, 00:25:9C:D3:FC:D8, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    NavyGirl (2.4GHz): Infra, C4:3D:C7:97:E6:0D, Freq 2427 MHz, Rate 54 Mb/s, Strength 32 WPA2
    HOME-4002:       Infra, 00:1D:D6:43:40:00, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Aries:           Infra, B8:9B:C9:5F:5A:A8, Freq 2457 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Boat Drinks:     Infra, 30:46:9A:8F:81:D6, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    DevineSuite:     Infra, 28:C6:8E:8E:FA:48, Freq 2442 MHz, Rate 54 Mb/s, Strength 22 WPA2
    SeedFactory:     Infra, DC:45:17:C8:99:90, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    *mynetwork:     Infra, 00:22:6B:62:B5:A2, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA
    Diamond:         Infra, E0:91:F5:AF:91:A4, Freq 2422 MHz, Rate 54 Mb/s, Strength 22 WEP

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        10:1F:74:0D:BA:69

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

---

### Post by chili555 on 2013-09-03
> maybe I just needed to restart after saving the iwlwifi file.I'm pretty sure that's the case. Please post back if you have more trouble.

---

### Post by Mikyll on 2013-09-03
Also thank you for all the help that you do on these forums.

---

### Post by chili555 on 2013-09-03
Thank you for your kind words. There are many others here who make great contributions to help make this a true community. 

This is like my college years. I am still learning, I have been here for eight years, I'm not done yet and I haven't offended enough people to get expelled...yet.

---

