---
title: "RT8185L locking computer"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by lytithwyn on 2009-06-08
I recently bought a no-name rt8185 wireless card.  When I tried this card in my Mythbuntu 9.04 box, it locked it up.  As soon as X loaded, I'd get the "wait" cursor in the middle of the screen, and that'd be it.  I tried starting the computer in recovery mode and dropping to a root + net shell, but it still locked up.  Then, I rebooted and tried just a plain old root shell.  At that point, I had a usable console.  A quick lsmod revealed the following drivers loaded in relation to the card:

```

rtl8180                36864  0 
mac80211              217208  1 rtl8180
eeprom_93cx6           10240  1 rtl8180
cfg80211               38032  2 rtl8180,mac80211

```

I found that I could easily get my wired network up and running by issuing `sudo dhclient eth0`, so I also started up ssh in case my console locked up.  I figured the next step was to check out the wireless stuff, so I installed wireless-tools, and did an iwconfig.  Here's the result of that:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Ok, so I've got wireless extensions.  The trouble came when I tried to run `ifconfig wlan1 up`.  At that point, my console locked, and so did the ssh session I opened from another computer.

Any ideas?  If it helps, the device and vendor ID's for that card as output by lspci are 10ec:8185.  As far as my system goes, everything is stock 9.04.  The only lines I saw in dmesg relating to the card are as follows:

```

[   11.999966] rtl8180 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.288717] phy0: hwaddr 00:e0:70:06:00:2c, RTL8185vD + rtl8225z2

```

---

