---
title: "Wireless connection seems to work, but no internet connection"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by tschill on 2012-10-20
My internet connection, which was working fine, stopped working from one day to the other. Imho I did not change any settings, other computers can access the internet via the wireless router and when I run Ubuntu from a USB stick, the affected Ubuntu computer can access the internet. For my amateur eyes it looks like the WLAN connection is established and working, nonetheless no program (firefox, thunderbird, chrome, dropbox) can access the internet.

I post at the end the output of lshw -c network, iwconfig, ifconfig and ping. Any idea what I should check additionally is appreciated, since I do not have much experience in troubleshooting Ubuntu. Thank you.

```
sudo lshw -c network
  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:26:5d:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-32-generic-pae firmware=8.83.5.1 build 33692 ip=192.168.1.66 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:d1500000-d1501fff
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 13
       serial: 00:1d:ba:1b:c4:e6
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:d0120000-d0123fff ioport:2000(size=256) memory:d0100000-d011ffff

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"O2wireless6492B5"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 58:98:35:64:92:B5   
          Bit Rate=58.5 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:297  Invalid misc:286   Missed beacon:0

eth0      no wireless extensions

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:ba:1b:c4:e6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:667 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69207 (69.2 KB)  TX bytes:69207 (69.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:26:5d:18  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:eaff:fe26:5d18/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1101332 (1.1 MB)  TX bytes:309408 (309.4 KB)


ping -c3 85.190.27.2
PING 85.190.27.2 (85.190.27.2) 56(84) bytes of data.

--- 85.190.27.2 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

```

---

### Post by chili555 on 2012-10-20
As a temporary measure, please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Any improvement?

---

### Post by tschill on 2012-10-20
Just checking - the "11n_disable" starts with eleven, not double LL, yes?

If so, then there is no change afterwards. Ping and firefox, both don't work.

---

### Post by chili555 on 2012-10-20
Correct; as is 'eleven N.' Let's have a look at:```
nm-tool
```The plot thickens.

---

### Post by tschill on 2012-10-20
Thank you so much for your help, Chili. I am sorry, that I wasted your time in a way. 
In the last hour we had a power outage here in our building (lovely London, it is). This turned off  everything including the router. After we had our electricity back, the problem did not exist anymore. It  is somewhat embarrasing that I didn't try to restart the router. But then again - why didn't the other computers have the same problem? I don't get it, why the problem is solved now. 

Is there anything to be learned from this? Maybe. First, a power cut is unpleasant, but it can solve problems (I won't tell you that another computer now has a different problem due to this unforeseen shutdown.) Second, always stick with the IT CROWD: "Did you try to turn it off and on again?" Next time it might be better, not to use the main switch. 
Thanks again for your help. You are very precise in your instructions and they are understandable even for non-experts like me. Keep up the good work.

---

### Post by chili555 on 2012-10-20
I am happy it is working by whatever means. We all learn a bit more every day!

---

### Post by tschill on 2012-10-28
Argh, unfortunately I have to re-open this thread. :(

The problem re-appeared after a day - a normal wifi signal, but  no internet connection. It was now not difficult to guess that a reboot of the router will solve the problem - and it did. But I have to do this every day now. If I turn off the computer and restart it after 10 minutes - no problem with the internet connection. But if I restart the computer the next day I must reboot the router. Pretty annoying, I would be glad for any hint. 

As for the readout of the suggested nm-tool, here we go (but these values have now been generated with no internet problem - maybe I should repeat this, when the connection problem is present?)


```
NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:1D:BA:1B:C4:E6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [O2wireless6492B5] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:16:EA:26:5D:18

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    SKYE1D5D:        Infra, 7C:03:4C:AE:1D:5E, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    TALKTALK-4FD374: Infra, 88:53:D4:4F:D3:76, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    Gatehouse:       Infra, 00:04:ED:93:59:C0, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA
    BTHub3-NTTZ:     Infra, 00:01:3B:AE:25:82, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    SKY2C49A:        Infra, 7C:03:4C:72:C4:9B, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    BrightBox-yh7pwp:Infra, 1C:C6:3C:29:D1:C9, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    BTHub3-44W7:     Infra, 00:FE:F4:23:87:50, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    arseholes:       Infra, 00:26:44:F1:42:1D, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Ellison Lee:     Infra, 00:24:36:AB:2D:FD, Freq 2432 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    London Media Press: Infra, 00:1B:2F:3D:3E:F4, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA
    LJNetwork:       Infra, 30:46:9A:49:B6:EA, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    PlusnetWireless: Infra, 00:26:44:2C:D9:83, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    DOT:             Infra, 00:26:44:EC:ED:85, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    banuedaa:        Infra, 00:26:F2:5F:4B:72, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA
    virginmedia9594253: Infra, C4:3D:C7:43:6E:88, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    PENKOM2:         Infra, 00:50:7F:E9:50:C9, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2
    junky styling :  Infra, 00:1B:9E:81:E2:EC, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA
    4AB-PHS:         Infra, 00:50:7F:A2:0B:38, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    ZyXEL2513vql:    Infra, CC:5D:4E:BC:0F:28, Freq 2452 MHz, Rate 54 Mb/s, Strength 30 WPA
    ab:              Infra, 4C:17:EB:9A:9B:3A, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    raven:           Infra, 20:AA:4B:C5:77:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA
    PENKOM1:         Infra, 00:50:7F:E9:50:C8, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WEP
    PENKOM3:         Infra, 00:50:7F:E9:50:CA, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WEP
    Burma@Access:    Infra, 00:1F:33:0C:A2:90, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WEP
    BTBusinessHub-975: Infra, 00:26:50:E8:9A:89, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WEP
    BTWiFi:          Infra, 02:01:3B:AE:25:82, Freq 2437 MHz, Rate 54 Mb/s, Strength 39
    BTWiFi-with-FON: Infra, 12:01:3B:AE:25:82, Freq 2437 MHz, Rate 54 Mb/s, Strength 34
    BTOpenzone:      Infra, 00:26:50:E8:9A:8C, Freq 2452 MHz, Rate 54 Mb/s, Strength 27
    4AB-TNY:         Infra, 00:50:7F:A2:0B:39, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    (((linguascope))): Infra, 00:24:A5:34:90:1F, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    BTHub3-HPRW:     Infra, 00:AC:54:EB:B4:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    slodesh40:       Infra, 00:24:17:30:DE:E1, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA
    Sell! Sell!:     Infra, 00:1C:B3:AE:D5:BD, Freq 2442 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Baby Splice:     Infra, B8:C7:5D:03:4F:19, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA2
    virginmedia1071873: Infra, 2C:B0:5D:D6:F9:C5, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Pino:            Infra, 00:13:64:37:98:C1, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    *O2wireless6492B5: Infra, 58:98:35:64:92:B5, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    TALKTALK-52960E: Infra, 14:D6:4D:52:96:0E, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    ThemDesignLtd:   Infra, 00:50:7F:77:82:A0, Freq 2472 MHz, Rate 54 Mb/s, Strength 24 WPA
    BTWiFi:          Infra, 02:AC:54:E5:3D:AA, Freq 2462 MHz, Rate 54 Mb/s, Strength 22
    BTOpenzone-B:    Infra, 12:AC:54:E5:3D:AA, Freq 2462 MHz, Rate 54 Mb/s, Strength 22
    SKY81465:        Infra, F0:7D:68:6A:3C:04, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Air K:           Infra, 00:19:E3:FB:33:3C, Freq 2422 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    BeBox:           Infra, 00:26:44:07:9B:61, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    bkeo:            Infra, C8:60:00:94:BB:E6, Freq 2472 MHz, Rate 54 Mb/s, Strength 27 WPA2

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

```

---

### Post by chili555 on 2012-10-28
As an experiment, and we can easily reverse it if it isn't helpful, please do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Add one line:```
options iwlwifi 11n_disable=1
```Proofread, save and close gedit. Reboot.

Now does the problem persist?

---

### Post by tschill on 2012-10-28
Problem is - an immediate reboot or a restart after 10 minutes doesn't disconnected me before. So I can tell you only tomorrow, if the problem reoccured. 

I did what you suggested. The file was empty. Is this to be expected?

Just out of interest - is it difficult to explain, what we are doing at the moment?

---

### Post by chili555 on 2012-10-28
> So I can tell you only tomorrow, if the problem reoccured.
I will await your report.>  what we are doing at the moment? We are trying to overcome a well-known and long-standing bug in the driver iwlwifi with N-speeds. I notice in your nm-tool:> Speed:           65 Mb/sN for sure.

I have never heard of the issue being at the router, but, then again, I learn something new and often astounding, every day. Perhaps the router and the wireless card will speak N together for a while and then die out. Perhaps a re-negotiation (a.k.a. reboot) between the router and the wireless card gets them both back on sync.

I have an Intel wireless card but no N router, so I can't find out except through you.

---

### Post by tschill on 2012-10-30
Good news. Today the reconnection was without any problems, maybe your idea solved the problem. :)

I will keep you informed, if the connection problem re-appears. Let's hope for the best. Thanks again for your invaluable help.

---

### Post by tschill on 2012-10-30
Just as an additional information - I find it very strange that this problem appeared out of the blue. The router - wifi combination worked before without any problem. Imho some kind of Ubuntu update created this problem.

---

### Post by tschill on 2012-10-30
Sigh. No, unfortunately the connection problem still exists.

This is the output of nm-tools shortly before I rebooted the router

```
NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:1D:BA:1B:C4:E6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [O2wireless6492B5] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:16:EA:26:5D:18

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    virginmedia9594253: Infra, C4:3D:C7:43:6E:88, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    BTHub3-NTTZ:     Infra, 00:01:3B:AE:25:82, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    ab:              Infra, 4C:17:EB:9A:9B:3A, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    arseholes:       Infra, 00:26:44:F1:42:1D, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    BTHub3-HPRW:     Infra, 00:AC:54:EB:B4:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    SKYE1D5D:        Infra, 7C:03:4C:AE:1D:5E, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    PlusnetWireless: Infra, 00:26:44:2C:D9:83, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    BrightBox-yh7pwp:Infra, 1C:C6:3C:29:D1:C9, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    Pino:            Infra, 00:13:64:37:98:C1, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    SKY81465:        Infra, F0:7D:68:6A:3C:04, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    raven:           Infra, 20:AA:4B:C5:77:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA
    BTHub3-44W7:     Infra, 00:FE:F4:23:87:50, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Gatehouse:       Infra, 00:04:ED:93:59:C0, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA
    TALKTALK-52960E: Infra, 14:D6:4D:52:96:0E, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    SKY2C49A:        Infra, 7C:03:4C:72:C4:9B, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    virginmedia1071873: Infra, 2C:B0:5D:D6:F9:C5, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    bkeo:            Infra, C8:60:00:94:BB:E6, Freq 2472 MHz, Rate 54 Mb/s, Strength 45 WPA2
    TALKTALK-042121: Infra, BC:F6:85:04:21:21, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    banuedaa:        Infra, 00:26:F2:5F:4B:72, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA
    TALKTALK-4FD374: Infra, 88:53:D4:4F:D3:76, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    LJNetwork:       Infra, 30:46:9A:49:B6:EA, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    London Media Press: Infra, 00:1B:2F:3D:3E:F4, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA
    Hagz Wifi:       Infra, 00:26:44:ED:3F:6D, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    PENKOM2:         Infra, 00:50:7F:E9:50:C9, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    virginmedia3090213: Infra, 74:44:01:61:FC:05, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    junky styling :  Infra, 00:1B:9E:81:E2:EC, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA
    Burma@Access:    Infra, 00:1F:33:0C:A2:90, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WEP
    O2wireless485407:Infra, 00:1F:9F:15:05:95, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WEP
    BTWiFi-with-FON: Infra, 12:01:3B:AE:25:82, Freq 2437 MHz, Rate 54 Mb/s, Strength 90
    BTWiFi:          Infra, 02:01:3B:AE:25:82, Freq 2437 MHz, Rate 54 Mb/s, Strength 84
    *O2wireless6492B5: Infra, 58:98:35:64:92:B5, Freq 2412 MHz, Rate 54 Mb/s, Strength 56 WPA WPA2
    BTHub3-WFPG:     Infra, 00:AC:54:C6:20:F2, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    BTOpenzone-B:    Infra, 12:AC:54:C6:20:F2, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    BTWiFi:          Infra, 02:AC:54:C6:20:F2, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    BTWiFi-with-FON: Infra, 12:FE:F4:47:5C:10, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    O2wireless190D95:Infra, 58:98:35:19:0D:95, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    PENKOM3:         Infra, 00:50:7F:E9:50:CA, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WEP
    iPhone:          Infra, AA:53:95:5C:4F:29, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA2
    BTHub3-FHPC:     Infra, 00:FE:F4:47:5C:10, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Campaign Wireless: Infra, 00:1F:F3:C2:3D:23, Freq 2472 MHz, Rate 54 Mb/s, Strength 30 WPA2
    PENKOM1:         Infra, 00:50:7F:E9:50:C8, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    BTWiFi:          Infra, 42:96:A0:39:C2:8D, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    BrightBox-r4b7q5:Infra, 1C:C6:3C:B1:69:67, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    O2wireless428591:Infra, 00:24:17:B4:CB:EB, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP

  IPv4 Settings:
    Address:         192.168.1.65
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

```

and this shortly after I rebooted the router:

```
NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:1D:BA:1B:C4:E6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [O2wireless6492B5] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:16:EA:26:5D:18

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    virginmedia9594253: Infra, C4:3D:C7:43:6E:88, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    BTHub3-NTTZ:     Infra, 00:01:3B:AE:25:82, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    ab:              Infra, 4C:17:EB:9A:9B:3A, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    arseholes:       Infra, 00:26:44:F1:42:1D, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    BTHub3-HPRW:     Infra, 00:AC:54:EB:B4:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    SKYE1D5D:        Infra, 7C:03:4C:AE:1D:5E, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    PlusnetWireless: Infra, 00:26:44:2C:D9:83, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    BrightBox-yh7pwp:Infra, 1C:C6:3C:29:D1:C9, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    Pino:            Infra, 00:13:64:37:98:C1, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    SKY81465:        Infra, F0:7D:68:6A:3C:04, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    raven:           Infra, 20:AA:4B:C5:77:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA
    BTHub3-44W7:     Infra, 00:FE:F4:23:87:50, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Gatehouse:       Infra, 00:04:ED:93:59:C0, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA
    TALKTALK-52960E: Infra, 14:D6:4D:52:96:0E, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    SKY2C49A:        Infra, 7C:03:4C:72:C4:9B, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    virginmedia1071873: Infra, 2C:B0:5D:D6:F9:C5, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    bkeo:            Infra, C8:60:00:94:BB:E6, Freq 2472 MHz, Rate 54 Mb/s, Strength 50 WPA2
    TALKTALK-042121: Infra, BC:F6:85:04:21:21, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    banuedaa:        Infra, 00:26:F2:5F:4B:72, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA
    TALKTALK-4FD374: Infra, 88:53:D4:4F:D3:76, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    London Media Press: Infra, 00:1B:2F:3D:3E:F4, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA
    Hagz Wifi:       Infra, 00:26:44:ED:3F:6D, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    PENKOM2:         Infra, 00:50:7F:E9:50:C9, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    virginmedia3090213: Infra, 74:44:01:61:FC:05, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    junky styling :  Infra, 00:1B:9E:81:E2:EC, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA
    Burma@Access:    Infra, 00:1F:33:0C:A2:90, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WEP
    O2wireless485407:Infra, 00:1F:9F:15:05:95, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WEP
    BTWiFi-with-FON: Infra, 12:01:3B:AE:25:82, Freq 2437 MHz, Rate 54 Mb/s, Strength 90
    BTWiFi:          Infra, 02:01:3B:AE:25:82, Freq 2437 MHz, Rate 54 Mb/s, Strength 84
    BTHub3-WFPG:     Infra, 00:AC:54:C6:20:F2, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    BTOpenzone-B:    Infra, 12:AC:54:C6:20:F2, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    BTWiFi:          Infra, 02:AC:54:C6:20:F2, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    BTWiFi-with-FON: Infra, 12:FE:F4:47:5C:10, Freq 2437 MHz, Rate 54 Mb/s, Strength 27
    O2wireless190D95:Infra, 58:98:35:19:0D:95, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    PENKOM3:         Infra, 00:50:7F:E9:50:CA, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    iPhone:          Infra, AA:53:95:5C:4F:29, Freq 2417 MHz, Rate 54 Mb/s, Strength 40 WPA2
    BTHub3-FHPC:     Infra, 00:FE:F4:47:5C:10, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Campaign Wireless: Infra, 00:1F:F3:C2:3D:23, Freq 2472 MHz, Rate 54 Mb/s, Strength 29 WPA2
    PENKOM1:         Infra, 00:50:7F:E9:50:C8, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WEP
    BTWiFi:          Infra, 42:96:A0:39:C2:8D, Freq 2437 MHz, Rate 54 Mb/s, Strength 25
    O2wireless428591:Infra, 00:24:17:B4:CB:EB, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    BTHub3-W67G:     Infra, CC:96:A0:39:C2:8C, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    *O2wireless6492B5: Infra, 58:98:35:64:92:B5, Freq 2412 MHz, Rate 54 Mb/s, Strength 53 WPA WPA2
    BTWiFi-with-FON: Infra, 42:96:A0:39:C2:8E, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    Thomson9445B9:   Infra, 00:26:44:23:99:1F, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

```

I don't know if this is helpful, but I thought a direct comparison before and after might be a good idea.

---

