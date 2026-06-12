---
title: "Wireless Problem - Atheros 5212 chipset [DWL-G630 v.C2]"
date: 2006-01-25
forum: Networking &amp; Wireless
---

### Post by chris4amd on 2006-01-25
I am trying to get the D-Link DWL-G630 v.C2 PCMCIA wireless card working with my IBM Thinkpad A21M and Xubuntu (Ubuntu 5.10).  My problem is that I cannot connect to either of the two available unencrypted, completely open wireless networks around me.

I have been through all the options I know of and many forum posts and I am stumped. 

Here is my dmesg output for this card:
> 
[4298082.298000] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
[4298082.298000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4298082.891000] Build date: Nov 22 2005
[4298082.891000] Debugging version (IEEE80211)
[4298082.891000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4298082.891000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4298082.891000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4298082.891000] ath0: mac 7.8 phy 4.5 radio 5.6
[4298082.891000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4298082.891000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4298082.891000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4298082.891000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4298082.891000] ath0: Use hw queue 8 for CAB traffic
[4298082.891000] ath0: Use hw queue 9 for beacons
[4298082.891000] Debugging version (ATH)
[4298082.891000] ath0: Atheros 5212: mem=0x8c00000, irq=11


Here is my lsmod output:
> 
root@nemo:~# lsmod | egrep ath
ath_pci                78908  0
ath_rate_sample        17000  1 ath_pci
wlan                  141692  3 ath_pci,ath_rate_sample
ath_hal               148432  3 ath_pci,ath_rate_sample


Here is my iwconfig output:
> 
ath0      IEEE 802.11  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:0 kb/s   Tx-Power:20 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Here is some more helpful (???) information:
> 
root@nemo:~# iwlist ath0 scan
ath0      Interface doesn't support scanning : Network is down

root@nemo:~# ifconfig ath0 up *[At this point the lights on the card begin flashing alternately.]*
root@nemo:~# iwlist ath0 scan
ath0      Failed to read scan data : Resource temporarily unavailable


I tried "[installing the latest madwifi-ng drivers from subversion]("http://ubuntuforums.org/showthread.php?t=105437")", but didn't have any luck there and ended up removing it with 'make uninstall.'

Any help would be appreciated.   I have no idea where to go from here.

PS - I wanted to use the native madwifi-ng drivers instead of ndiswrapper because everything I have read says that this card / chipset is fully supported.

---

### Post by Lambert on 2006-01-25
Post the output of 

```
dpkg -s wireless-tools
``` and


I would also consider purging this package and re-installing it to see if that helps.

I'm running dapper with -ng currently so i'm not sure if it's different but my module wlan also has the depend wlan_scan_sta loaded.

You can also turn on debugging with these commands and check syslog for output

```

athdebug 0xffffffff
``` ```
802110 xffffffff
```

---

