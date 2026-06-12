---
title: "Madwifi installation for Atheros card"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by SonnyKing on 2010-08-23
Hi, all
I have confronted this problem for 4 days, and all methods depressed me, including the threads below.
I am so tired, is there any body can give me some suggestions? Thanks!

Now, come to my problem.
```

#uname -r
2.6.32-24-generic
``````
#lshw -C network
network UNCLAIMED
       description: Network controller
       product: AR9287 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d4100000-d410ffff
network DISABLED
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       ..........

```:
note: blacklist.conf is edited, and
```
apt-get update && apt-get upgrade
and build-essential libssl-dev, apt-get install linux-headers-`uname -r`
``````
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
```and then
note: I have "make clean", run the 2 function unload and remove the modules in ./scripts
```

#make 1>log
athstats.c: In function 'main':
athstats.c:288: warning: format not a string literal and no format arguments
athstats.c:290: warning: format not a string literal and no format arguments
athstats.c:310: warning: format not a string literal and no format arguments
athstats.c:312: warning: format not a string literal and no format arguments
athstats.c:347: warning: format not a string literal and no format arguments
80211stats.c: In function 'main':
80211stats.c:287: warning: format not a string literal and no format arguments
wlanconfig.c: In function 'list_keys':
wlanconfig.c:779: warning: ignoring return value of 'system', declared with attribute warn_unused_result
wlanconfig.c: In function 'ieee80211_status':
wlanconfig.c:895: warning: ignoring return value of 'system', declared with attribute warn_unused_result
```following, 
```

#make install
WARNING: -e needs -E or -F
```and after this, command:
```

echo ath_pci >> /ect/modules
modprobe ath_pci
reboot
```note: also, i added options.conf and the line: "options ath_pci rfkill=0"

Nevertheless, when i run "lshw -C network", or "ifconfig -a", no athx come out, just like what i showed in the top.

here is some additional info.
```

lsmod | grep ath
ath_pci               193165  0 
wlan                  222860  1 ath_pci
ath_hal               398604  1 ath_pci

``````

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any    (note: the other intel card) 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```
I commented the blacklist.conf for madwifi, and added blacklist for ath9k 
```

grep -r "madwifi" /etc/modprobe.d/
/etc/modprobe.d/blacklist-ath_pci.conf:# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
/etc/modprobe.d/blacklist-ath_pci.conf:# madwifi from loading by default. Use Jockey to select one driver

```Finally, I have tried downloaded source from "madwifi-project.org", and got madwifi-0.9.4 version(the branch one), get similar result.
In my Hardward Drivers, this is nothing except ATI graphic card, even my intel card is not there.

It's so difficult , and anyone can help me?
Thanks!

---

