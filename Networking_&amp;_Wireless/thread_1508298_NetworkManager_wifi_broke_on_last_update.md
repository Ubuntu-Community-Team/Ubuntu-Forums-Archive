---
title: "NetworkManager wifi broke on last update"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by DavidFourer on 2010-06-12
A few days ago, 10.04 had a slew of updates, and NetworkManager applet broke.  I have a wired connection, but wifi won't work.  NetworkManager applet now asks me for my wep key and then crashes.  Systems > preferences > network connections also crashes.  This is not urgent because it's not a portable computer.

> david@david-desktop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             unavailable
  Default:           no
  HW Address:        00:22:5F:C0:A8:07

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points


I have an HP Pavilion p6100z,AMD Athlon LE-1660 with Lucid.  Everything was great until two days ago.

Can I go into synaptic pkg mgr and return to an earlier version?  How do I determine what package was updated?  I am looking in dpkg.log.  gnome-panel and gnome-keyring are affected by the update,  but I don't think NetworkManager.

Thanks


Solution: go to admin>login screen.  unlock and de-select the option to login automatically.  This was always buggy.  It also fixed a crash in UbuntuOne.  Maybe has to do with the keyring.

---

