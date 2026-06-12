---
title: "Advent 9115 wireless Issues"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by Physikx on 2011-09-17
Hey im quite new to ubuntu i dont have much exp with it but here is my problem,
i cant connect to my wifi router unless im very close but network manager says i have full signal i can get a connection on my i device anywhere in my house but i have to be sat right next to my router to connect on my laptop. this has been a problem for me for about 4 months and the laptop is close to taking a flying lesson :twisted: i have run nm-tool and this is the output


NetworkManager Tool

State: connected

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sis190
  State:             unavailable
  Default:           no
  HW Address:        00:03:0D:75:13:5C

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan1  [Auto virginmedia7106223] -------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           yes
  HW Address:        00:16:44:1D:6D:5A

  Capabilities:
    Speed:           11 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    virginmedia9921240: Infra, C4:3D:C7:42:4B:C4, Freq 2437 MHz, Rate 54 Mb/s, Strength 98 WPA WPA2
    *virginmedia7106223: Infra, 30:46:9A:7F:71:CE, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    OlenKo-Network:  Infra, 00:24:01:C5:1E:52, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Pr0f3:           Infra, 32:46:9A:7F:71:CF, Freq 2417 MHz, Rate 54 Mb/s, Strength 100
    *virginmedia7106223: Infra, 30:46:9A:7F:71:CE, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2

  


any help would be  greatly appreciated thank you :P


Edit: in case anyone is having this problem i have a solution. if you have an advent chances are you have to turn on you wifi to connect to a wifi source  if you turn on your wifi (FN+f10) while boting up it will solve this problem but you have to do it every time you boot up thanks for the help BTW ubuntu forumsxx

---

