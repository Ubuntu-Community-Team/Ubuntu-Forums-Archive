---
title: "USB Wireless Adapter - Intermittent Connection"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by tmeitner on 2012-05-16
I recently bought a D-Link DWA 160 USB wireless adapter for my computer because it was supported according to the Ubuntu wifi Wiki. While it works great, the connection drops out frequently - for a few seconds, then reconnects. I've searched around and can't figure this out for the life of me. My info is below - please help! Thanks!

1. Machine: eMachines EL1358G desktop
2. Wireless brand, model, and chipset
```
Bus 001 Device 007: ID 07d1:3a09 D-Link System DWA-160 Xtreme N Dual Band USB Adapter(rev.A2) [Atheros AR9001U-(2)NG]

```
3. iwconfig output
```
wlan1     IEEE 802.11abgn  ESSID:"MeitnerHT"  
          Mode:Managed  Frequency:5.785 GHz  Access Point: 84:C9:B2:4E:34:E8   
          Bit Rate=240 Mb/s   Tx-Power=30 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:86  Invalid misc:554   Missed beacon:0

```
4. Modules
```
ath                    19387  1 carl9170

```

Ubuntu 11.10

Please let me know what other information you might need. Any help is appreciated!

---

### Post by tmeitner on 2012-05-18
On further usage, the connection is more reliable when my backup isn't running and I'm not torrenting. That's great and all, but I need to be able to do those two things or this serves no purpose. Any thoughts from anybody on this?

---

