---
title: "Wireless doesn't work in awesome wm"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by Holyaxe on 2009-09-07
I decided to install awesome on my laptop (Acer Aspire 5520), which is running Xubuntu 9.04. Wireless works without any problems in xfce, but when I use awesome, it doesn't. It seems to detect the network, but I don't know  how  to connect to it. This is what iwconfig says, if it helps:

[I]lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"WLAN-AP"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
[/I]
I am using ath5k driver, which works fine in xfce.

---

### Post by Holyaxe on 2009-09-07
I tried

[I]iwconfig wlan0 channel X ap XX:XX:XX:XX:XX:XX

[/I](with the right channel and ap address of course) but it just doesn't work. No matter what I do, it says that access point is non-associated.

Could anyone help, please?

EDIT: I managed to configure the network using wicd. No more help needed.

---

### Post by koushik.ms on 2010-08-10
Always wanted to switch to awesome but couldn't get wireless up. Tried wicd but no luck. Even uninstalled nm (apt-get remove network-manager network-manager-gnome) and rebooted the machine since post-install wicd-daemon complained wicd monitor couldn't load. Finally verified wicd daemon, monitor all are OK and started wicd-gtk but couldn't connect to wireless network. In my situation (strangely) the essid of the network I want to connect to appears at least twice (sometimes 5-6 times) in the network list, some instance claiming it is WEP and others that it is WPA. I know it is WPA and so I gave the WPA passphrase and tried to connect any of the instance - but all failed.

Finally my solution was to remove wicd and reinstall network-manager* and to invoke nm-applet from within awesome with the following command.

```
nm-applet --sm-disable

```

---

