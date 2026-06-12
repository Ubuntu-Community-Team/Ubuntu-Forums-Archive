---
title: "No longer connecting to router"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by startling on 2010-10-27
When I start Ubuntu at work it automatically connects to the router every time. At home the router signal is quite weak but manually connecting via NetworkManager Applet 0.8 was successful for a week or so. In the past week, however, although the router appears in the list in Network Manager, it has stopped working and is unable to connect. Nothing has changed with the router or hardware in that time.

This is a new laptop which had Windows 7 pre-installed. Windows 7 connects to the home router successfully every time. I really don't want to use Windows 7 but until I can get this fixed I have no choice.

I don't know if it's relevant, but once I tried deleting the AUTO Home connection from Network Manager and was then able to connect on the next attempt, but this has not worked since.

---

### Post by startling on 2010-11-02
Are there any log files or places I can look to diagnose the problem?

---

### Post by startling on 2010-11-09
Any advice on where to start looking for a solution? I'd be grateful for any pointers. (I really hate logging into Windows 7!)

---

### Post by grahammechanical on 2010-11-09
May I advise that you are not giving enough clues? We have to assume that you are wanting to use a wireless connection but we do not know this for sure. Type in a terminal nm-tool

Look for something that says Device wlan0 and see if the state is listed as connected or disconnected.

Also you can right click the icon and uncheck Enable wireless and then re-check Enable wireless. This might start things up again. If you know all about this then please forgive me. As I say, you do not give enough clues as to where to begin.

regards.

---

### Post by startling on 2010-11-10
Thanks for your reply grahammechanical - it's helpful to know where to start!

Sorry if I haven't posted enough information. Yes, it is a wireless connection I'm attempting to use. The router has a weak signal.

It's safe to assume that I have no knowledge of these things, so any instructions or pointers are most helpful and gratefully received.

When I get home tonight I will try the suggestions you've kindly given and post back with the results.

---

### Post by startling on 2010-11-15
Hi grahammechanical - for a few days recently I have typed nm-tool in a terminal as you suggested. On one day, Ubuntu actually managed to connect, but only once out of the past five days, despite several attempts. Here is the output of nm-tool for two failed attempts and the one successful attempt: 

```
NetworkManager Tool output

========== 13 Nov 2010==========
State: connected

- Device: wlan0  [NETGEAR] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xSE
  State:             connected
  Default:           no
  HW Address:        E0:91:53:19:F6:CA

  Capabilities:
    Speed:           12 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *NETGEAR:        Ad-Hoc, 8A:E6:2C:E2:77:EF, Freq 2457 MHz, Rate 12 Mb/s, Strength 50
    NETGEAR:         Infra, 00:18:4D:F4:EC:D8, Freq 2462 MHz, Rate 54 Mb/s, Strength 62

  IPv4 Settings:
    Address:         10.42.43.1
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0


========== 12 Nov 2010 ==========

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xSE
  State:             disconnected
  Default:           no
  HW Address:        E0:91:53:19:F6:CA

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NETGEAR:         Infra, 00:18:4D:F4:EC:D8, Freq 2462 MHz, Rate 54 Mb/s, Strength 47

===== 11 Nov 2010 ====

Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xSE
  State:             disconnected
  Default:           no
  HW Address:        E0:91:53:19:F6:CA

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NETGEAR:         Infra, 00:18:4D:F4:EC:D8, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
```


Is there anything else I should look at and post to help diagnose this?

Thanks

---

