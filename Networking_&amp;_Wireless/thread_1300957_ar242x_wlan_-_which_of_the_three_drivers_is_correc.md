---
title: "ar242x wlan - which of the three drivers is correct?"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by LuJo on 2009-10-25
After days of struggling I finally got wlan running on my Ubuntu 8.04, but it seems so weird, I'd like to have someone's opinion about it.

All three drivers are blacklisted:
cat: /etc/modprobe.d/arch: Is a directory
#blacklist ath5k
blacklist ath_hal
blacklist ath_pci
#blacklist ath5k
blacklist ath_hal
blacklist ath_pci
blacklist ath5k
And if I remove one, it turns up again after rebooting.

gksudo gedit /etc/mod gives:
fuse
lp
rtc
ath5k
#wlan_scan_sta

System>Hardare-Drivers gives 3:
none are activated, one 5xxx is being used.

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"wireless"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1D:19:FF:E4:84   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=84/100  Signal level:-48 dBm  Noise level=-102 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

birgit@birgit-laptop:~$ lsmod | grep ath
ath5k                 101376  0 
lbm_cw_mac80211       233204  1 ath5k
lbm_cw_cfg80211        36576  2 ath5k,lbm_cw_mac80211
led_class               6020  1 ath5k

At least ath_PCI is now gone.

And sudo modprobe driver(any) freezes my system completely.

What do you think? Should I leave it alone? And what do I do if Ubuntu offers me a bunch of updates that I don't understand? Never update anything?

---

