---
title: "Cant connect to my network anymore"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by WinterMadness on 2011-11-22
I was on my network(wireless) today watching a video and suddenly, i noticed im not online anymore. I have to stress, **i did not at any time change any setting or feature before this happened**

Also, wired connections are fine 

so anyway, this is what happens when I try to connect to my network after it stopped working:
**remember, I absolutely did not change anything, this includes passwords**

1) I look in my network manager(kubuntu's), see my network, and click connect
2) spends about a minute configuring interface
3) get message "waiting for authorization"
4) it gives up





I can tether on my phone, which also uses wpa2-psk
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
**02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)**
03:00.0 USB Controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 04)
04:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)

```


```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [AndroidAP] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        40:25:C2:51:AD:24

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    11FX05180266:    Infra, 0C:D5:02:B2:0C:76, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WEP
    Herodotus2:      Infra, 00:12:0E:72:A6:C2, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WEP                                                                                                     
    NetGear:         Infra, C0:3F:0E:26:D9:20, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2                                                                                                
    *AndroidAP:      Infra, 02:1A:11:FE:40:45, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2                                                                                                   
   
    yellow cheetah:  Infra, 00:1E:2A:54:69:72, Freq 2442 MHz, Rate 54 Mb/s, Strength 27 WEP
    09FX01039149:    Infra, 00:23:97:1E:0C:A4, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WEP
   
    Carol's Network: Infra, 00:25:9C:68:49:AF, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA
**    linuxcbl:        Infra, E0:91:F5:FD:1F:8E, Freq 2437 MHz, Rate 54 Mb/s, Strength 92 WPA2**

  IPv4 Settings:
    Address:         192.168.43.17
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.43.1

    DNS:             192.168.43.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        14:DA:E9:4F:4F:A0

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



```

androidap = my phone
linuxcbl = my network

---

### Post by WinterMadness on 2011-11-23
```
joe@joe-U46:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: asus-wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: asus-wimax: WiMAX
        Soft blocked: yes
        Hard blocked: no

joe@joe-U46:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"AndroidAP"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 02:1A:11:F0:9E:73   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:98   Missed beacon:0

joe@joe-U46:~$ dmesg | grep iwl
[    9.306350] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    9.306353] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[    9.306405] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.306415] iwlagn 0000:02:00.0: setting latency timer to 64
[    9.306447] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[    9.317854] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
[    9.317858] iwlagn 0000:02:00.0: Device SKU: 0X9
[    9.317860] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[    9.318208] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[    9.318303] iwlagn 0000:02:00.0: irq 42 for MSI/MSI-X
[    9.449382] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[    9.452078] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
joe@joe-U46:~$ 

```

what does soft blocked mean(near top)?

---

### Post by tiffany98122 on 2011-11-23
Same thing is happening to me on the latest Kubuntu on a Lenovo x201 with an Intel Wireless N 6300. Worked fine in Gnome though, so maybe the Gnome network manager just handles WPA differently?

ETA: I had the same problem with the latest openSUSE KDE, which is why I decided to try Kubuntu in the first place.

---

### Post by tiffany98122 on 2011-11-23
I installed Gnome, and now it works just fine with both Gnome and KDE.

---

### Post by WinterMadness on 2011-11-24
ill try installing the gnome network manager later, but i seriously doubt thats the root of the problem because other networking managers are failing as well (wicd)

this is more than likely a driver issue

---

### Post by inobe on 2011-11-24
go into network manager> manage connections> wireless> remove all> log out> log back in> reconnect.

---

### Post by WinterMadness on 2011-11-24
> **inobe said:**
> go into network manager> manage connections> wireless> remove all> log out> log back in> reconnect.

unfortunately this is a driver issue, not a networking manager issue. I wish it were that simple.

---

### Post by pastalavista on 2011-11-24
Try this ```
sudo rfkill unblock wimax

--or--

sudo rfkill unblock asus-wimax

--or--

sudo rfkill unblock all
```

---

### Post by WinterMadness on 2011-11-25
unfortunately that didnt do anything.

Is there any way that I can figure out what glitch/problem/whatever is happening in order to troubleshoot? Right now were kind of shooting in the dark, and if I could see whats actually happening when I try to connect, I suspect a good solution would come forth

---

### Post by WinterMadness on 2011-11-25
also my connection works fine if i turn off security, but i wont keep it that way. im not leaving my network unsecured

---

### Post by inobe on 2011-11-25
how is your router configured, did you reboot the router and modem yet?

---

### Post by WinterMadness on 2011-11-26
> **inobe said:**
> how is your router configured, did you reboot the router and modem yet?
I use WPA2-PSK security, nothing else, no mac filtering etc

I didnt restart my router but I guess I could try that, but ive never had trouble connecting to it, in fact my old linux laptop connects to it just fine, my desktop does fine, and so does my phone

my driver is iwlagn as well

---

### Post by WinterMadness on 2011-11-27
if i change my network to a g network, my wireless connects fine but my wireless card was able to recognize the N network before, and it was able to connect to it at one time.

also, on windows it connects to the n network

---

