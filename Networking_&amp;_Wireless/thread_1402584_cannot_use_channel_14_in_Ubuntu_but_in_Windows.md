---
title: "cannot use channel 14 in Ubuntu but in Windows"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by utileria on 2010-02-09
My Asus 900HA can use WiFi channel 14 in Windows, but when trying to use it in Ubuntu Remix 9.10 it cannot access it (only usable channels 1-13 in Ubuntu).

I have also a desktop with a SMC wireless PCI adapter (model SMCWPCI-G2) that can access channel 14 both in Windows and in Ubuntu 9.10. 

The router is a Linksys WRT54GL with a dd-wrt firmware.

Any technical suggestion how I can fix this technical issue?

Thank you very much!

$ iwlist channel
lo        no frequency information.

eth0      no frequency information.

wmaster0  no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency=2.484 GHz (Channel 14)

tun0      no frequency information.

---

### Post by chili555 on 2010-02-09
You could try:```
sudo iwconfig wlan0 channel 14
```Or, you could reset your regulatory domain with:```
sudo iw reg set <your_region_such_as_GB>
```If one of these works, you can probably add the command, without sudo, to *rc.local*.

---

### Post by utileria on 2010-02-09
Dear chili555
None of the above proposed solutions worked with the 900HA using Ubuntu Remix. Using Windows it accesses channel 14 without any trouble. 

I used:

sudo iw reg set JP
and the result before and after applying the command above:

$iw phy
Wiphy phy0
    Band 1:
        Frequencies:
            * 2412 MHz [1] (20.0 dBm)
            * 2417 MHz [2] (20.0 dBm)
            * 2422 MHz [3] (20.0 dBm)
            * 2427 MHz [4] (20.0 dBm)
            * 2432 MHz [5] (20.0 dBm)
            * 2437 MHz [6] (20.0 dBm)
            * 2442 MHz [7] (20.0 dBm)
            * 2447 MHz [8] (20.0 dBm)
            * 2452 MHz [9] (20.0 dBm)
            * 2457 MHz [10] (20.0 dBm)
            * 2462 MHz [11] (20.0 dBm)
            * 2467 MHz [12] (20.0 dBm)
            * 2472 MHz [13] (20.0 dBm)
            * 2484 MHz [14] (20.0 dBm)
        Bitrates:
            * 1.0 Mbps
            * 2.0 Mbps (short preamble supported)
            * 5.5 Mbps (short preamble supported)
            * 11.0 Mbps (short preamble supported)
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
    max # scan SSIDs: 4
    Supported interface modes:
         * IBSS
         * managed
         * AP
         * AP/VLAN
         * monitor
         * mesh point

At the desktop computer, Ubuntu automatically accesses channel 14 without any kind of specification.

Any other suggestion?

Thank you very much!

---

### Post by chili555 on 2010-02-09
Which wireless driver does this use? *ath5k*, maybe? Please show us:```
lsmod | grep ath
```Thanks.

---

### Post by utileria on 2010-02-09
Dear chili555

$ lsmod | grep ath
ath5k                 124580  0 
mac80211              181108  1 ath5k
led_class               4096  1 ath5k
ath                     8060  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath

Thank you very much!

---

### Post by chili555 on 2010-02-09
Ah, ha! Please try:```
sudo rmmod -f ath5k
sudo modprobe ath5k all_channels=1
```Now can you see channel 14? If so, we'll need to drop this in rc.local or create an ath5k.conf file.

---

### Post by utileria on 2010-02-09
Dear chili555,

After running the commands above, 

$ iw phy
Wiphy phy1
    Band 1:
        Frequencies:
            * 2412 MHz [1] (20.0 dBm)
            * 2417 MHz [2] (20.0 dBm)
            * 2422 MHz [3] (20.0 dBm)
            * 2427 MHz [4] (20.0 dBm)
            * 2432 MHz [5] (20.0 dBm)
            * 2437 MHz [6] (20.0 dBm)
            * 2442 MHz [7] (20.0 dBm)
            * 2447 MHz [8] (20.0 dBm)
            * 2452 MHz [9] (20.0 dBm)
            * 2457 MHz [10] (20.0 dBm)
            * 2462 MHz [11] (20.0 dBm)
            * 2467 MHz [12] (20.0 dBm)
            * 2472 MHz [13] (20.0 dBm)
            * 2484 MHz [14] (20.0 dBm)
            * 2512 MHz [-498] (disabled)
            * 2532 MHz [-494] (disabled)
            * 2552 MHz [-490] (disabled)
            * 2572 MHz [-486] (disabled)
            * 2592 MHz [-482] (disabled)
            * 2612 MHz [-478] (disabled)
            * 2632 MHz [-474] (disabled)
            * 2652 MHz [-470] (disabled)
            * 2672 MHz [-466] (disabled)
            * 2692 MHz [-462] (disabled)
            * 2712 MHz [-458] (disabled)
            * 2732 MHz [-454] (disabled)
        Bitrates:
            * 1.0 Mbps
            * 2.0 Mbps (short preamble supported)
            * 5.5 Mbps (short preamble supported)
            * 11.0 Mbps (short preamble supported)
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
    max # scan SSIDs: 4
    Supported interface modes:
         * IBSS
         * managed
         * AP
         * AP/VLAN
         * monitor
         * mesh point

Please, advise me about the steps to follow.

Thank you very much!

---

### Post by utileria on 2010-02-09
Dear chili555,

It still doesn´t connect to channel 14.

---

### Post by chili555 on 2010-02-09
I am out of ideas. Sorry.

---

