---
title: "WiFi was working five days ago in 10.10... now it isn't."
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by Jguy101 on 2010-11-22
I have an old Acer Aspire 3050 laptop running Ubuntu, and my networking worked out of the box with 10.04; it continued to do so after I upgraded to 10.10, until recently.  A week ago (last Monday), I accidentally left my power adapter at a friend's place, and I didn't get it back until Saturday night.  I recharged the laptop with another friend's AC adapter on Wednesday, and WiFi was working fine, but I noticed while on battery power on Thursday that I couldn't even see my home wireless network.  I discovered over the last couple of days with the power supply back that my laptop can't find or connect to ANY wireless networks, but I can still get it online via Ethernet.  Here's my iwconfig output:
```

lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
          Retry long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```Any idea what's going on?  I'm making a 10.04 USB stick right now to make sure it's not any kind of hardware failure.  The card is an Atheros AR5001.

---

### Post by grahammechanical on 2010-11-22
It is not connected. ESSID:off/any is the give away. It should list the name of the network you are connected to. Here is the Wireless trouble shooting guide

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

If you type the command 

rfkill list

you may see that the wireless LAN is either soft or hard blocked. Soft blocked: Yes = wireless device switched of by software. Hard blocked: Yes = wireless device switched of by hardware. 

I suggest that there may be some power saving setting that was activated by the drain down of battery power that has switched off the wireless device/card.

Regards.

---

