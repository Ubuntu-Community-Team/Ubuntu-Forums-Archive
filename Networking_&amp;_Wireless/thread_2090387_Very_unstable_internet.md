---
title: "Very unstable internet"
date: 2012-12-02
forum: Networking &amp; Wireless
---

### Post by MjmConway on 2012-12-02
Hi, this is my first post,but this problem needs to be solved! I recently upgraded my PC from *lubuntu* to *xubuntu*. This is because I was fed up with basic features. Don't worry, my PC can handle xubuntu, it is working as fast as it did with lubuntu.

It keeps asking for my authentication key, then it will try to connect for 2 mins then it pops up again. Occasionaly, it says it connects, but then it disconnects 2 seconds later. This is **UNBEARABLE**.

Here are my wireless properties, I ran nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        76:15:64:EA:0F:00

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             disconnected
  Default:           no
  HW Address:        7C:DD:90:13:CC:B7

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    WiFi-TalkTalk-Conway@Conway: Infra, 00:22:B0:DC:E5:AA, Freq 2452 MHz, Rate 54 Mb/s, Strength 55 WPA

---

### Post by Merrattic on 2012-12-02
Title really needs to be about wireless connection, not internet.

Can you connect with a wire? Does this behave itself?

How far away are you from the router/access point ? Did you have good connection before on same machine with lubuntu?

When you say updated to xubuntu, do you mean fresh install or installed xubuntu-desktop? Which release ?

Report back with output from ifconfig / iwconfig.

---

