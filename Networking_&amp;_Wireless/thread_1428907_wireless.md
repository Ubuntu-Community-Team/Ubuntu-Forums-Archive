---
title: "wireless"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by ankscorek on 2010-03-13
hi i am using ubuntu 8.10 and

orinoco wireless card and of course two machines

i have configured both the cards in ad-hoc mode by doing this

# echo "options ath_pci autocreate=adhoc" > /etc/modprobe.d/madwifi
# echo "ath_pci autocreate=adhoc" >> /etc/modules


#!/bin/sh
/sbin/ifconfig eth1 down
/sbin/iwconfig eth1 mode ad-hoc
/sbin/iwconfig eth1 channel 3
/sbin/iwconfig eth1 enc off
/sbin/iwconfig eth1 essid kite_ad-hoc
/sbin/ifconfig eth1 169.254.114.100 netmask 255.255.0.0



both are in ad-hoc mode as u can see form this

machine2@ddd-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"UbuntuAdhoc"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.422 GHz  Cell: 02:20:A6:57:58:EA   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
          Rx invalid nwid:42  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


similiarly for the other machine

However when i click on the nm applet i am unable to connect these two machines

can some one give me a hint please

ps: both machines have their IP address and are able to ping their own IP address

However they are unable to ping each other

---

