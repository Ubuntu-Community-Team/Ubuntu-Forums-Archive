---
title: "Atheros  AR9285  (lenovo g575, ubuntu 12.10)"
date: 2013-02-12
forum: Networking &amp; Wireless
---

### Post by jamie236 on 2013-02-12
Hi,

I'm having troubles with ar9285 chipset on lenovo g5757 and have no idea what to do.
* wireless card is enabled in BIOS
* no luck with lenovo energy management [[http://208.74.204.134/t5/Linux-Discussion/Ideapad-N585-wifi-AR9285-does-not-work-in-Linux/td-p/880185](http://208.74.204.134/t5/Linux-Discussion/Ideapad-N585-wifi-AR9285-does-not-work-in-Linux/td-p/880185)] (I couldn't find the magic enable wireless switch and considering rfkill list all output shows everything is unblocked, I didn't pursue wiping BIOS memory option)
* most related problems are caused by acer_wmi, I do not have it :(
* nohwcrypt=1 makes no difference.

```
lspci -nn | grep Wireless
``````

03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

``````
iwconfig wlan0
``````

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

``````
ifconfig wlan0
``````

wlan0     Link encap:Ethernet  HWaddr 44:6d:57:01:f5:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

``````
000lsmod | grep ath9
``````

ath9k                 116588  0 
mac80211              461203  2 rtl8187,ath9k
ath9k_common           13784  1 ath9k
ath9k_hw              376193  2 ath9k,ath9k_common
ath                    19188  3 ath9k,ath9k_common,ath9k_hw
cfg80211              175574  4 rtl8187,ath9k,mac80211,ath

``` ```
rfkill list all
``````

0: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: no

``````
cat /etc/modprobe.d/ath9k.conf
``````
options ath9k nohwcrypt=1
```nohwcrypt=1 makes no difference.

```
dmesg | grep ath9k
``````

[   11.584333] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   11.585936] Registered led device: ath9k-phy0

``````
lshw -C network
``````

  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 44:6d:57:01:f5:03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:90000000-9000ffff

``````
iwlist wlan0 scan
``````
wlan0     No scan results
``````
uname -mr
``````
3.5.0-23-generic i686
``````
nm-tool
``````

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        44:6D:57:01:F5:03

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```

Any help would be appreciated!

---

### Post by jamie236 on 2013-02-12
It seems like wireless card is working now, but signal is very bad.
I have to stand next to router to get a signal.

In meantime I switched to 12.04. 

```
uname -mr
3.2.0-29-generic-pae i686

```

---

### Post by kurt18947 on 2013-02-12
What version?  Can you find a wireless-backports package to download/enable?

---

### Post by jamie236 on 2013-02-12
What do you mean by what version?

I'm not very familiar with backports, but I installed
```
linux-backports-modules-cw-3.3-3.2.0-29-generic-pae
```

I switched to 12.04 32bit version in meantime, problem still persists.


Thank you for taking your time and helping me!

---

### Post by kurt18947 on 2013-02-13
Hi

Sorry to hear you're still having problems.  You answered my version inquiry with your 12.04 32 bit reply.A quick google search turned up this:

[http://askubuntu.com/questions/95875/how-do-i-make-my-atheros-ar9285-wireless-adapter-work](http://askubuntu.com/questions/95875/how-do-i-make-my-atheros-ar9285-wireless-adapter-work)

I've seen mention of compat-wireless but have no experience with it; my Atheros based adapter (AR9271 I think) is plug - n - play.  In a terminal you can run 'lsmod'.  This will list the modules loaded.  If acer-wmi is loaded,  you could follow the directions in the above link to blacklist it.  Other than that, I'm out of ideas.  Maybe someone better versed can jump in.

---

