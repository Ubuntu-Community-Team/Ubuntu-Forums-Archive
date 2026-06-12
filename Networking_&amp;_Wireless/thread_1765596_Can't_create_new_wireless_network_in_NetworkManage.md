---
title: "Can't create new wireless network in NetworkManager Applet 0.8"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by moondog62 on 2011-05-23
When I left click the applet and select "Create New Wireless Network" the "Create" button is grayed out.
If I right click the applet, select "Edit Connections", then "Wireless" tab, then "Add" button, the "Apply" button is grayed out in the resulting dialog box.

If I open a terminal and enter "nm-tool" I get

[QUOTE
NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        00:18:DE:2D:74:88

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Janet -O_Wireless_C990BB: Infra, 00:22:75:C9:90:BB, Freq 2437 MHz, Rate 54 Mb/s, Strength 34


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tulip
  State:             connected
  Default:           yes
  HW Address:        00:04:5A:A8:76:D5

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         64.77.253.186
    Prefix:          23 (255.255.254.0)
    Gateway:         64.77.252.1

    DNS:             198.6.1.122
    DNS:             198.6.1.3
/QUOTE]

Any ideas would be greatly appreciated.

Bill

---

### Post by moondog62 on 2011-05-23
I guess NetworkManager has to be able to deal with dummies like me. Turns out that I have to fill out all the required fields with the minimum required number of characters before the "Create" or "Apply" buttons become active.

---

