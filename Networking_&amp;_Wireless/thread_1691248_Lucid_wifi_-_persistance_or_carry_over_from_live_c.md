---
title: "Lucid wifi - persistance or carry over from live cd session?"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by keithpeter on 2011-02-19
Hello All

Yesterday, I did a clean install of Lucid on a T42 thinkpad, with wireless card as identified by lshw below. I did the installation from within a live CD session, with wifi enabled.

```
description: Wireless interface
product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
vendor: Intel Corporation
```

On reboot into the fresh system and update I had the issues that others have seen with network manager not connecting, repeatedly asking for password and so on. Oddly enough, using a Netgear usb wifi dongle worked perfectly, so I thought there might be a driver issue. Updates did not help. The network manager icon would not appear in the notification area at all when attempting to connect to wifi in a cafe locally.

Today, I did a fresh re-install from the same CD with the home wifi switched off and no internet connection on the laptop. No issues. Wifi is working perfectly at present. I had to make the home connection available to all users to stop the keyring password request (I use autologin). I'll be trying to connect at local cafes tomorrow (one has no security, one uses an ascii wep password, and a third has a WPA encryption)

**Is it possible that the settings from the live session are carried over in some way and interfering with network manager in some way**?

(*[SIZE="1"]This all started because my minimal install (see signature) reached a state where it would not show the network manager icon when attempting to connect to wifis in cafes and colleges, which I need to do. I decided to reinstall to return to a known state. I may try a minimal installation and manual wifi connection from the command line next...[/SIZE]*)

---

### Post by keithpeter on 2011-02-21
Hello

I'm bumping this one from an Arts centre with public wifi (no encryption). nm-applet working fine, just updated the kernel on this 10.04 install.

sudo iwlist scan gives (among other stuff)


```
          Cell 02 - Address: Hex stuff
                    ESSID:"mac-public"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:16  Signal level:0  Noise level:0
                    Extra: Last beacon: 13776ms ago

```

This wan't working on the last install when I had wifi enabled during the install.

Added later: after an enjoyable holiday afternoon being a tourist in my own city, I can say networking appears solid on this T42 with 10.04 installed. I've connected to unencrypted, WEP and WPA/WPA2 wifi spots without issue and have restarted & suspended and resumed perfectly. The scientific method suggests that I should now re-install from a live session with wifi running and see what happens. I think I'll just monitor the situation...

---

