---
title: "[NEED HELP] internet stops working until reboot [NEED HELP]"
date: 2013-07-02
forum: Networking &amp; Wireless
---

### Post by ismaeel96 on 2013-07-02
hi :D
when i turn my pc on the internet works fine but its a bit slow. after 5-13 minutes the inter net stops but i can still ping my router but not other websites. i have to reboot for it to work for another 10-13 minutes.

how can i fix this?

im a newb to linux so dont know much commands so if u need something done in terminal please the me the command :)

ik i missed alot of information but if u need anythiung just ask and ill try to get it.

i have a linksys ae1200 broadcom BCM43235
i already changed the ip4v dns server to 8.8.8.8 8.8.4.4

---

### Post by varunendra on 2013-07-03
Hello ismaeel96, and Welcome to the forums !

Please follow the "Wireless Script" link in my signature and download the script as mentioned in the "Method 2 (no internet)" of the linked post.

When the internet seems to stop working, run the script (as per Method 2 in the post) and post back the "wireless-info.txt" file it creates (or better, its pastebin link).

Let's hope it is something that can be easily fixed :)

---

### Post by ismaeel96 on 2013-07-07
here, i did what u asked here is the pastebin [http://pastebin.com/Qh1ePRBg](http://pastebin.com/Qh1ePRBg)

---

### Post by varunendra on 2013-07-07
Please change the encryption type from WPA/WPA2 mixed mode to pure WPA2-PSK with AES (not TKIP) in your router.

Also, it seems that you have not added the 8.8.8.8 and 8.8.4.4 as DNS, but "search domain".

Make sure to set IPv4 "Method" in Network Manager settings to "Automatic (DHCP) address only", then enter these DNS servers in the "DNS Servers" field, separated by comma (8.8.8.8, 8.8.4.4). Save and close NM settings after this.

Once done, reconnect the wifi, run "nm-tool" command and post back its output. Also let us know if the performance improved.

---

### Post by ismaeel96 on 2013-07-07
alright, i did what u said. but what is the nm-tool command?

---

### Post by varunendra on 2013-07-08
It is just a reporting tool for Network Manager, doesn't change anything. Run it and see for yourself.

---

### Post by ismaeel96 on 2013-07-09
Lol u said it was a command, what is the vommand that i have to write in terminal. Sorryz im somewhat of a newb to linux :L

---

### Post by varunendra on 2013-07-09
> **ismaeel96 said:**
> Lol u said it was a command, what is the vommand that i have to write in terminal. Sorryz im somewhat of a newb to linux :L

Oh, got it, lol !

"nm-tool" itself is the command that you have to type in the terminal. Exactly - 
```
nm-tool
```

---

### Post by ismaeel96 on 2013-07-18
sorry for delay :L but i just tried it and it seems to work. if any problems i will report them :D but here is the out put
```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [HOME-4E83] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        C0:C1:C0:6C:1A:7E

  Capabilities:
    Speed:           117 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *HOME-4E83:      Infra, 00:1D:D5:8E:4E:80, Freq 2462 MHz, Rate 54 Mb/s, Strength 81 WPA2
    dlink:           Infra, 1C:AF:F7:D4:35:E5, Freq 2442 MHz, Rate 54 Mb/s, Strength 50 WPA

  IPv4 Settings:
    Address:         10.0.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        50:E5:49:D5:EE:D1

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

edit:
it stopped working again.
also usually when i try to download java it stops right away (idk if that helps u or not :L)

also i dont have to reboot pc to get internet again. all i have to do is take out the adapter and put it back in (i just relised that :P)

after it stopped
```

NetworkManager Tool

State: connected (global)

- Device: wlan0  [HOME-4E83] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        C0:C1:C0:6C:1A:7E

  Capabilities:
    Speed:           117 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *HOME-4E83:      Infra, 00:1D:D5:8E:4E:80, Freq 2462 MHz, Rate 54 Mb/s, Strength 82 WPA2
    dlink:           Infra, 1C:AF:F7:D4:35:E5, Freq 2442 MHz, Rate 54 Mb/s, Strength 49 WPA

  IPv4 Settings:
    Address:         10.0.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        50:E5:49:D5:EE:D1

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

---

