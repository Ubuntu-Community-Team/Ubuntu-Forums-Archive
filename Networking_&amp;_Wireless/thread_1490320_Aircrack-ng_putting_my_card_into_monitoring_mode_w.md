---
title: "Aircrack-ng: putting my card into monitoring mode without NetworkManager interfering"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by elreteipos on 2010-05-22
I want to use Aircrack-ng to see how vulnerable my wireless network is to attacks and after that take steps to improve its security.

When I put my card into monitor mode, this happens:
> pdedecker@betabuntu:~/wireless/ieee80211-1.2.18$ sudo airmon-ng start eth1 1


Found 3 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
14826	wpa_supplicant
15623	NetworkManager
15635	dhclient
Process with PID 15635 (dhclient) is running on interface eth1


Interface	Chipset		Driver

eth1		Intel 2200BG	ipw2200 (monitor mode enabled)


That's when NetworkManager kicks in and disables monitor mode. So then I decide to shut down these processes:
> pdedecker@betabuntu:~/wireless/ieee80211-1.2.18$ sudo service network-manager stop
network-manager stop/waiting
pdedecker@betabuntu:~/wireless/ieee80211-1.2.18$ sudo killall wpa_supplicant


Then I try to get my card into monitoring mode again:
> pdedecker@betabuntu:~$ sudo airmon-ng start eth1 1


Interface	Chipset		Driver



As you can see, my card is gone even though it's still listed in iwconfig:

> pdedecker@betabuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  Mode:Managed  Frequency=2.412 GHz  
          Access Point: Not-Associated   Bit Rate:0 kb/s   Tx-Power=20 dBm   
          Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:40   Missed beacon:0


My card is recognized by airmon-ng as soon as I restart the NetworkManager service. What's up with that? How can I activate monitoring mode without NetworkManager interfering?

---

