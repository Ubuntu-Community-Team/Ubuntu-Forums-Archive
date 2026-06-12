---
title: "network configuration failure during boot (12.10)"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by Minjae on 2012-10-19
Problem: During boot, ubuntu blocks for two minutes at the following stages, and wireless ultimately fails.

```

Waiting for network configuration
Waiting up to 60 seconds for network configuration

```

Setup: 
Ubuntu 12.10 Server, fresh install
TP-LINK TLWN722N (ath9k_htc module) connected through USB


Details:
I installed 12.10 server, and during the installation, there is autoconfiguration of wireless.  It worked like a charm for a few boots, and I started to have the above issue.  After I made another fresh install of 12.10, wireless worked for a while, then I have the same problem again.  

Modules seem to have loaded fine
```

$ lsmod | grep ath9
ath9k_htc              91402  0 
mac80211              539908  1 ath9k_htc
ath9k_common           14055  1 ath9k_htc
ath9k_hw              395218  2 ath9k_htc,ath9k_common
ath                    23827  3 ath9k_htc,ath9k_common,ath9k_hw
cfg80211              206566  3 ath9k_htc,mac80211,ath

```

The interface file looks fine
```

$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet dhcp
        wpa-ssid myssid
        wpa-psk  mypassword


```

The workaround I have is eliminate all wait time in /etc/init/failsafe.conf so that the boot does not hang for 2 min.  Then I restart the wireless connection with 

```

service networking restart

```

in /etc/rc.local.  The workaround works fine for now, but I would like to know the root cause of this.  Spending an hour and half googling gives me complaints from various people regarding similar issue, but I have not found a satisfactory solution yet.  I did not have this problem a few days ago when I used 12.04 server.  

I appreciate your help.  Thanks.

---

