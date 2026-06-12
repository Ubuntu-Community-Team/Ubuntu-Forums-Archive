---
title: "No wireless, atheros AR5212"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by vikpaul on 2009-02-07
Hi,

The details of my problem are:
*Laptop: IBM Lenovo thinkpad R60
*OS: Ubuntu 8.04
The wired connection works fine - I get internet.
But I dont get internet with wireless.
Some other details:
The wireless card is Atheros AR5212 802.11abg NIC.
I can see the wireless networks both in the Network manager
and on the main screen (when I click on the network icon).
However, in the Network manager I see 2 networks labeled
"Linksys" with different strengths. Linksys is the network
I am trying to connect to. In Network manager I select "Roaming
mode enabled" so that everything is grey. Then on the main
screen by clicking on the network icon I can see Linksys and
after selecting it I can see the bars showing signal strength,
but the internet doesnot work!

The driver is ath_pci (as given by "lshw" command). ath_pci shows
up in "lsmod" command like this:
ath_pci 101024 0
There are 2 more  entries:
ath_hal 192592 4 ath_rate_sample,ath_pci
wlan 207728 4 wlan_scan_sta,ath_rate_sample,ath_pci

"iwconfig" shows entry for ath0. The details of this output
shows Access Point = Not Associated

"sudo iwlist ath0 scan" shows a lot of output with ESSID="linksys"; Mode:Master etc

Thanks for your help

---

### Post by mykelmykel on 2010-02-19
bump....same issue here and I'm on 9.10

---

