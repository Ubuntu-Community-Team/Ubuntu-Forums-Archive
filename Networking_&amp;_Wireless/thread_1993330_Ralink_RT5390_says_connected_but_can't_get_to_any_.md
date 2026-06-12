---
title: "Ralink RT5390 says connected but can't get to any website"
date: 2012-06-01
forum: Networking &amp; Wireless
---

### Post by joshyuCMU on 2012-06-01
Hello everyone! I have been trying to set up the wireless card (Ralink RT5390R)on my HP dv6t machine and I haven't had any luck yet. I tried these steps found in many of the thread before and they seem to work:
```

sudo make
sudo make install 
sudo modprobe -v rt5390sta (or without -v)
sudo depmod -a sudo update-initramfs -u
```

Anyway it says it's connected to the wireless point. But when I try to go to any website (or ping them), it doesn't connect. It's been very frustrating. I really hope some one can help me with this. Thanks a lot!!

---

### Post by chili555 on 2012-06-02
Let's do some diagnostics. Please run and post:```
lspci -nn | grep 0280
lsmod | grep -e rt2 -e rt5
nm-tool
dmesg | grep wlan
```Thanks.

---

### Post by slow2anger on 2012-06-03
Hi,

I have the same problem.  I.e., both wireless and wired (when I plugged in the cable) say connected according to the Network Manager.  However, there is no internet whatsoever when visiting any website.  Curiously, I can connect to my wireless router through the web browser interface fine.  I don't think it's the problem of my modem or router, as internet works fine with them on another computer.  Here are the requested output.  Please help.  Thanks!


###########################################################
hshu@magician:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)

###########################################################
hshu@magician:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Spirit] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        10:0B:A9:BE:89:AC

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HOME-0D72:       Infra, 00:1D:CF:9E:0D:70, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    ingenic:         Infra, 74:44:01:3F:4C:FE, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    Haridlink:       Infra, 5C:D9:98:63:02:60, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    totalnaporazka:  Infra, 00:26:F2:94:B3:D5, Freq 2422 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    2WIRE823:        Infra, 3C:EA:4F:D2:6F:09, Freq 2432 MHz, Rate 54 Mb/s, Strength 52 WPA
    Semaphore:       Infra, 00:25:4B:06:AB:DF, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Fabricio Sousa's Guest Network: Infra, 72:73:CB:BC:9E:60, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2
    fb3:             Infra, B8:C7:5D:06:08:6C, Freq 5180 MHz, Rate 54 Mb/s, Strength 39 WPA2
    fb3:             Infra, B8:C7:5D:06:08:6B, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA2
    *Spirit:         Infra, 00:16:01:D6:1A:51, Freq 2462 MHz, Rate 54 Mb/s, Strength 76 WPA2
    cocobread:       Infra, 70:73:CB:BC:9E:65, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    QuesoGrande:     Infra, 00:22:75:9F:71:88, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WEP
    attwifi:         Infra, F0:7D:68:16:B9:58, Freq 2412 MHz, Rate 54 Mb/s, Strength 24

  IPv4 Settings:
    Address:         192.168.11.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.11.1

    DNS:             192.168.11.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        F0:DE:F1:D8:7C:27

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

###########################################################
hshu@magician:~$ dmesg | grep wlan
[   19.429389] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.429598] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.944642] wlan0: authenticate with b8:c7:5d:06:08:6b (try 1)
[   26.947233] wlan0: authenticated
[   26.947444] wlan0: associate with b8:c7:5d:06:08:6b (try 1)
[   26.955779] wlan0: RX AssocResp from b8:c7:5d:06:08:6b (capab=0x431 status=0 aid=1)
[   26.955782] wlan0: associated
[   26.966040] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.677115] wlan0: deauthenticating from b8:c7:5d:06:08:6b by local choice (reason=3)
[   32.494352] wlan0: authenticate with 00:16:01:d6:1a:51 (try 1)
[   32.527743] wlan0: authenticated
[   32.579979] wlan0: associate with 00:16:01:d6:1a:51 (try 1)
[   32.739536] wlan0: RX AssocResp from 00:16:01:d6:1a:51 (capab=0x411 status=0 aid=3)
[   32.739546] wlan0: associated
[   43.345521] wlan0: no IPv6 routers present

---

### Post by chili555 on 2012-06-03
> **slow2anger said:**
> Hi,

I have the same problem.  I.e., both wireless and wired (when I plugged in the cable) say connected according to the Network Manager.  However, there is no internet whatsoever when visiting any website.  Curiously, I can connect to my wireless router through the web browser interface fine.  I don't think it's the problem of my modem or router, as internet works fine with them on another computer.  Here are the requested output.  Please help.  Thanks!


###########################################################
hshu@magician:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)

###########################################################
As you don't have a Ralink RT5390, the title of this thread, how about posting your own new thread. I can solve your problem in one post or you can search the forum for iwlwifi and 11n_disable.

---

### Post by slow2anger on 2012-06-03
Hello, chili555.  I have created a new post at [http://ubuntuforums.org/showthread.php?p=11994794#post11994794](http://ubuntuforums.org/showthread.php?p=11994794#post11994794)

Thank you!

---

### Post by joshyuCMU on 2012-06-25
Hello chili555 sorry it took me so long to post this. Now the router connects to my school wireless network but it still doesn't connect to my home network. Here are the results when I am using the school network. 

```


****lspci -nn | grep 0280****

0a:00.0 Network controller [0280]: Ralink corp. Device [1814:539a]

****lsmod | grep -e rt2 -e rt5****

rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci


****nm-tool****

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        08:2E:5F:74:7F:B2

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [CMU] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        08:ED:B9:1B:03:A3

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    CMU-SECURE:      Infra, 00:1A:1E:93:61:41, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA2 Enterprise
    CMU-SECURE:      Infra, 00:1A:1E:93:55:01, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA2 Enterprise
    ifab:            Infra, 00:25:9C:13:FC:DB, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    CMU-SECURE:      Infra, 00:1A:1E:8A:F6:21, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    CMU-SECURE:      Infra, 00:1A:1E:91:13:41, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise
    CMU-SECURE:      Infra, 00:1A:1E:91:12:01, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    robocut:         Infra, 20:AA:4B:1E:52:F1, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    CMU-SECURE:      Infra, 00:1A:1E:93:65:21, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    CMU-SECURE:      Infra, 00:1A:1E:93:54:C1, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    CMU-SECURE:      Infra, 00:1A:1E:82:DF:E1, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    CMU:             Infra, 00:1A:1E:93:55:00, Freq 2462 MHz, Rate 54 Mb/s, Strength 69
    CMU:             Infra, 00:1A:1E:91:13:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 45
    CMU:             Infra, 00:1A:1E:93:54:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 45
    CMU:             Infra, 00:1A:1E:8A:F6:20, Freq 2412 MHz, Rate 54 Mb/s, Strength 42
    CMU:             Infra, 00:1A:1E:91:12:00, Freq 2437 MHz, Rate 54 Mb/s, Strength 42
    AIBONET:         Infra, 00:16:B6:DB:0A:21, Freq 2437 MHz, Rate 54 Mb/s, Strength 39
    CMU:             Infra, 00:1A:1E:82:DF:E0, Freq 2412 MHz, Rate 54 Mb/s, Strength 32
    CMU:             Infra, 00:1A:1E:93:65:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 32
    CMU:             Infra, 00:1A:1E:87:37:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 29
    CMU:             Infra, 00:1A:1E:8D:6A:A0, Freq 2462 MHz, Rate 54 Mb/s, Strength 22
    *CMU:            Infra, 00:1A:1E:93:61:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 65

  IPv4 Settings:
    Address:         128.237.247.208
    Prefix:          19 (255.255.224.0)
    Gateway:         128.237.224.1

    DNS:             128.2.1.10
    DNS:             128.2.1.11

****dmesg | grep wlan****

[    8.130122] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.130768] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.248219] wlan0: authenticate with 00:1a:1e:93:61:40 (try 1)
[   11.249972] wlan0: authenticated
[   11.250690] wlan0: associate with 00:1a:1e:93:61:40 (try 1)
[   11.252722] wlan0: RX AssocResp from 00:1a:1e:93:61:40 (capab=0x21 status=17 aid=0)
[   11.252725] wlan0: 00:1a:1e:93:61:40 denied association (code=17)
[   11.255562] wlan0: deauthenticating from 00:1a:1e:93:61:40 by local choice (reason=3)
[   12.483638] wlan0: authenticate with 00:1a:1e:93:61:40 (try 1)
[   12.485363] wlan0: authenticated
[   12.486197] wlan0: associate with 00:1a:1e:93:61:40 (try 1)
[   12.489906] wlan0: RX AssocResp from 00:1a:1e:93:61:40 (capab=0x1421 status=0 aid=5)
[   12.489908] wlan0: associated
[   12.499518] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   22.521154] wlan0: no IPv6 routers present


```

Thanks a lot and I really appreciate your help!! :)

---

### Post by chili555 on 2012-06-25
I am troubled by this:> wlan0: 00:1a:1e:93:61:40 denied association (code=17)And I read this: [http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=4391](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=4391)> association status=17: "Association denied because AP is unable to handle additional associated stations."I'm not quite sure I really understand all that.

I am even more troubled by:> CMU:             Infra, 00:1A:1E:93:55:00, Freq 2462 MHz, Rate 54 Mb/s, Strength 69
    CMU:             Infra, 00:1A:1E:91:13:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 45
    CMU:             Infra, 00:1A:1E:93:54:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 45
    CMU:             Infra, 00:1A:1E:8A:F6:20, Freq 2412 MHz, Rate 54 Mb/s, Strength 42
    CMU:             Infra, 00:1A:1E:91:12:00, Freq 2437 MHz, Rate 54 Mb/s, Strength 42
    AIBONET:         Infra, 00:16:B6:DB:0A:21, Freq 2437 MHz, Rate 54 Mb/s, Strength 39
    CMU:             Infra, 00:1A:1E:82:DF:E0, Freq 2412 MHz, Rate 54 Mb/s, Strength 32
    CMU:             Infra, 00:1A:1E:93:65:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 32
    CMU:             Infra, 00:1A:1E:87:37:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 29
    CMU:             Infra, 00:1A:1E:8D:6A:A0, Freq 2462 MHz, Rate 54 Mb/s, Strength 22
    *CMU:            Infra, 00:1A:1E:93:61:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 65That's Network Manager's nightmare; 8-10 SSIDs with the same name that it wants to roam among, disconnecting, trying another, disconnecting, trying another, etc., etc. until we all go mad!

I have two suggestions. The first is a long-shot:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```The second, scarier suggestion is to remove NM and install Wicd. Let's see how the first try goes first.

---

### Post by joshyuCMU on 2012-07-28
Hello chili555!

Sorry for the late response but I am afraid that I still need your help! The logs above are from my college network and my laptop can connect to it just fine. However, I still can't connect to my home network. And after trying your two commands, my laptop can now connect to the router but has no internet connectivity (can't display websites). I have some logs (both before and after those two commands). I really appreciate your help!!:)

```

**lspci -nn | grep 0280**

0a:00.0 Network controller [0280]: Ralink corp. Device [1814:539a]

```*(Same before and after)*

```

**lsmod | grep -e rt2 -e rt5**

rt2800pci              18715  0  
rt2800lib              58925  1 rt2800pci 
crc_ccitt              12667  1 rt2800lib 
rt2x00pci              14577  1 rt2800pci 
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci 
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib 
cfg80211              205544  2 rt2x00lib,mac80211 
eeprom_93cx6           12725  1 rt2800pci 

```[I](Same before and after)

[/I]```

**nm-tool**

**BEFORE**
 
NetworkManager Tool 
 
State: connecting 
 
- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            r8169 
  State:             unavailable 
  Default:           no 
  HW Address:        08:2E:5F:74:7F:B2 
 
  Capabilities: 
    Carrier Detect:  yes 
    Speed:           100 Mb/s 
 
  Wired Properties 
    Carrier:         off 
 
 
- Device: wlan0  [Jsss] -------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            rt2800pci 
  State:             connecting (configuring) 
  Default:           no 
  HW Address:        08:ED:B9:1B:03:A3 
 
  Capabilities: 
 
  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 
 
  Wireless Access Points  
    mibo:            Infra, 98:FC:11:47:AD:15, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2 
    JWA:             Infra, 0C:D5:02:AF:02:11, Freq 2422 MHz, Rate 54 Mb/s, Strength 49 WPA2 
    linksys:         Infra, 00:23:69:4C:BF:41, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA 
    BrophyJ:         Infra, 00:23:97:DA:EC:4D, Freq 2462 MHz, Rate 54 Mb/s, Strength 9 WEP 
    myLGNet6514:     Infra, 00:40:5A:4B:65:12, Freq 2457 MHz, Rate 54 Mb/s, Strength 15 WEP 
    AnitaC8:         Infra, C0:C1:C0:D0:0F:C8, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2 
    Egypt1699:       Infra, 0C:D5:02:6D:EB:B6, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2 
    Jsss:            Infra, 00:24:01:78:55:03, Freq 2462 MHz, Rate 54 Mb/s, Strength 95 WEP 


**AFTER**

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        08:2E:5F:74:7F:B2

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Jsss] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        08:ED:B9:1B:03:A3

  Capabilities:
    Speed:           58 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    mibo:            Infra, 98:FC:11:47:AD:15, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    linksys:         Infra, 00:23:69:4C:BF:41, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA
    JWA:             Infra, 0C:D5:02:AF:02:11, Freq 2422 MHz, Rate 54 Mb/s, Strength 39 WPA2
    Egypt1699:       Infra, 0C:D5:02:6D:EB:B6, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    myLGNet6514:     Infra, 00:40:5A:4B:65:12, Freq 2457 MHz, Rate 54 Mb/s, Strength 25 WEP
    BrophyJ:         Infra, 00:23:97:DA:EC:4D, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WEP
    *Jsss:           Infra, 00:24:01:78:55:03, Freq 2462 MHz, Rate 54 Mb/s, Strength 83 WEP
    AnitaC8:         Infra, C0:C1:C0:D0:0F:C8, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    07B406056926:    Infra, 00:12:0E:79:01:42, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WEP

  IPv4 Settings:
    Address:         192.168.0.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

``````

**dmesg | grep wlan**

**BEFORE**

[   19.678492] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   19.679380] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   22.788092] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[   22.790220] wlan0: authenticated 
[   22.807858] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[   22.811111] wlan0: RX AssocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[   22.811115] wlan0: associated 
[   22.820622] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[   68.446270] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3) 
[   72.115336] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[   72.117397] wlan0: authenticated 
[   72.118124] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[   72.121374] wlan0: RX ReassocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[   72.121377] wlan0: associated 
[  117.421124] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3) 
[  121.349922] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[  121.352044] wlan0: authenticated 
[  121.352429] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[  121.355667] wlan0: RX ReassocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[  121.355674] wlan0: associated 
[  166.395753] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3) 
[  170.324893] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[  170.327006] wlan0: authenticated 
[  170.327514] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[  170.330791] wlan0: RX ReassocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[  170.330797] wlan0: associated 
[  215.374813] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3) 
[  516.151586] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[  516.153718] wlan0: authenticated 
[  516.154349] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[  516.157652] wlan0: RX ReassocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[  516.157658] wlan0: associated 
[  526.317089] wlan0: no IPv6 routers present 
[  561.193341] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3) 
[  565.122516] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[  565.124596] wlan0: authenticated 
[  565.125202] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[  565.128406] wlan0: RX ReassocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[  565.128410] wlan0: associated 
[  569.112986] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3) 
[  570.351534] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[  570.353633] wlan0: authenticated 
[  570.354145] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[  570.357419] wlan0: RX ReassocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[  570.357425] wlan0: associated 
[  571.643786] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3) 
[  572.894472] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[  572.896564] wlan0: authenticated 
[  572.897087] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[  572.900450] wlan0: RX ReassocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[  572.900457] wlan0: associated 
[  583.351770] wlan0: no IPv6 routers present 
[  618.168035] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3) 
[  622.092775] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[  622.094945] wlan0: authenticated 
[  622.095708] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[  622.099093] wlan0: RX ReassocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[  622.099101] wlan0: associated 
[  632.294690] wlan0: no IPv6 routers present 
[  667.142548] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3) 
[  671.807671] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[  671.809830] wlan0: authenticated 
[  671.810607] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[  671.813982] wlan0: RX ReassocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[  671.813989] wlan0: associated 
[  682.540846] wlan0: no IPv6 routers present 
[  717.127548] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3) 
[  721.059656] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[  721.061764] wlan0: authenticated 
[  721.062512] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[  721.065845] wlan0: RX ReassocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[  721.065851] wlan0: associated 
[  731.205756] wlan0: no IPv6 routers present 
[  766.104171] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3) 
[ 1066.886717] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[ 1066.888828] wlan0: authenticated 
[ 1066.889460] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[ 1066.892741] wlan0: RX ReassocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[ 1066.892748] wlan0: associated 
[ 1077.667883] wlan0: no IPv6 routers present 
[ 1111.926912] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3) 
[ 1115.853205] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[ 1115.855247] wlan0: authenticated 
[ 1115.855609] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[ 1115.858866] wlan0: RX ReassocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[ 1115.858869] wlan0: associated 
[ 1126.522834] wlan0: no IPv6 routers present 
[ 1160.901784] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3) 
[ 1164.832258] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[ 1164.834387] wlan0: authenticated 
[ 1164.834886] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[ 1164.838124] wlan0: RX ReassocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[ 1164.838131] wlan0: associated 
[ 1175.065912] wlan0: no IPv6 routers present 
[ 1209.876479] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3) 
[ 1213.807481] wlan0: authenticate with 00:24:01:78:55:03 (try 1) 
[ 1213.809661] wlan0: authenticated 
[ 1213.810404] wlan0: associate with 00:24:01:78:55:03 (try 1) 
[ 1213.813761] wlan0: RX ReassocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1) 
[ 1213.813768] wlan0: associated 
[ 1224.776396] wlan0: no IPv6 routers present 
[ 1258.855665] wlan0: deauthenticating from 00:24:01:78:55:03 by local choice (reason=3)


**AFTER**

[    8.413734] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.414305] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.527313] wlan0: authenticate with 00:24:01:78:55:03 (try 1)
[   11.529381] wlan0: authenticated
[   11.547529] wlan0: associate with 00:24:01:78:55:03 (try 1)
[   11.550778] wlan0: RX AssocResp from 00:24:01:78:55:03 (capab=0x431 status=0 aid=1)
[   11.550785] wlan0: associated
[   11.559980] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


```
I really appreciate your help!!:D:D

---

### Post by lfehr on 2012-11-01
This is in german but it worked for me:

[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742)

Hope it helps and it's not too late. :)

---

### Post by NikitaUbunt on 2013-01-17
0     down vote         
                           I own an HP650 which came with preinstalled SUSE Linux Enterprise Novell.
  The wireless card on this laptop is the Ralink 539a. The  driver/module for this wlan card loaded by the kernel is the rt2800pci.  The problem ofcourse is that by default they do not work or if they work  its unstable and practicly unusable. After reading many threads and  following a lot of different lines to build the  2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO the result was never  successful failing either at the build with >make returning an error  for Antenna being changed to y for yes or the driver not starting the  wlan0 interface if the Antenna switch remains n for off.
  Later I found a bug report and exchange specificly for the Ralink  539a where the solution to the problem was finallzy found. Essentially 

**1**. Download latest **Compat-Wireless** drivers from [http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.6_stable_releases](http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.6_stable_releases) 

**2. ****Unpack to a directory **

**3. ****cd to directory **

**4. sudo make **

**5. sudo make  install **

**6 reboot your computer **

**7. make sure the wireless card light/led  is on by using the wireless on/off button....**
  That did it for me. A note I also read is that any time the kernel or  drivers are updated the old rt2800pci driver/module gets unpacked and  thus the wireless gets back to not working .... So the same procedure of  make and make install to overwrite with the compat-wireless drivers  that work is to be done...
  Good luck

---

### Post by Rnunez95 on 2013-01-31
Hi guys im pretty much a complete noob at linux and i cant get linux to detect my RT5390 can someone post on how to get my drivers up and running

---

### Post by chili555 on 2013-01-31
> **Rnunez95 said:**
> Hi guys im pretty much a complete noob at linux and i cant get linux to detect my RT5390 can someone post on how to get my drivers up and runningAre you running Ubuntu 12.10? If so, please check here: [http://ubuntuforums.org/showthread.php?t=2109571](http://ubuntuforums.org/showthread.php?t=2109571)

---

### Post by varunendra on 2013-02-14
> **Rnunez95 said:**
> Hi guys im pretty much a complete noob at linux and i cant get linux to detect my RT5390 can someone post on how to get my drivers up and running

*Rnunez95*, you seem to be talking about your **backtrack installation in a VM** on Win8.

If so please see my reply on your thread here : [http://ubuntuforums.org/showthread.php?t=2111051](http://ubuntuforums.org/showthread.php?t=2111051)

In short, VMs have their own (virtualized) hardware and thus have their own drivers often supplied with them. So the solutions for normal installations (on real hardware) won't apply for them. And if the guest OS is supported, it is usually fairly easy to install its own version of drivers.

---

