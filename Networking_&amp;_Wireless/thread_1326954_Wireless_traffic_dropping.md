---
title: "Wireless traffic dropping"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by diogobaeder on 2009-11-14
Hi there,

Since I bought my netbook (an HP dv5-1260 with an Atheros AR928X Wireless Network Adapter) I've been having troubles trying to use the wireless network constantly. The signal is always strong, even though the network traffic falls down about once a minute - and the signal meter keeps up.

I've tried to install the latest drivers (via the compat-wireless packages at wireless.kernel.org), and it boosts my signal, but the traffic still drops from time to time to a no-communication state.

Here are my outputs:

```

$ lspci | grep -i atheros
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

```

$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"baedpint"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:0F:C5:9C:E0   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

$ lsmod | grep ath
ath9k                  97840  0 
ath9k_hw              240752  1 ath9k
mac80211              241800  1 ath9k
ath                    11424  2 ath9k,ath9k_hw
cfg80211              153448  3 ath9k,mac80211,ath
led_class               5256  2 ath9k,hp_accel

```

```

dmesg | grep -iE "(atheros|ath9k|wlan)"
[    9.813366] ath9k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.813393] ath9k 0000:08:00.0: setting latency timer to 64
[   10.386752] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.387145] Registered led device: ath9k-phy0::radio
[   10.387188] Registered led device: ath9k-phy0::assoc
[   10.387228] Registered led device: ath9k-phy0::tx
[   10.387268] Registered led device: ath9k-phy0::rx
[   10.387293] phy0: Atheros AR9280 Rev:2 mem=0xffffc90005140000, irq=17
[   20.951294] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.517086] wlan0: deauthenticating from 00:1d:0f:c5:9c:e0 by local choice (reason=3)
[   36.517444] wlan0: direct probe to AP 00:1d:0f:c5:9c:e0 (try 1)
[   36.519201] wlan0: direct probe responded
[   36.519201] wlan0: authenticate with AP 00:1d:0f:c5:9c:e0 (try 1)
[   36.520868] wlan0: authenticated
[   36.520914] wlan0: associate with AP 00:1d:0f:c5:9c:e0 (try 1)
[   36.523044] wlan0: RX AssocResp from 00:1d:0f:c5:9c:e0 (capab=0x431 status=0 aid=2)
[   36.523052] wlan0: associated
[   36.524680] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   47.021323] wlan0: no IPv6 routers present
[   49.914745] bridge-wlan0: is a Wireless Adapter
[   49.914745] bridge-wlan0: up
[   49.914745] bridge-wlan0: attached
[16403.547243] bridge-wlan0: disabling the bridge
[16403.572036] bridge-wlan0: down
[16403.572244] bridge-wlan0: detached
[16407.641265] wlan0: direct probe to AP 00:1d:0f:c5:9c:e0 (try 1)
[16407.642882] wlan0: direct probe responded
[16407.642895] wlan0: authenticate with AP 00:1d:0f:c5:9c:e0 (try 1)
[16407.646641] wlan0: authenticated
[16407.646704] wlan0: associate with AP 00:1d:0f:c5:9c:e0 (try 1)
[16407.651290] wlan0: RX ReassocResp from 00:1d:0f:c5:9c:e0 (capab=0x431 status=0 aid=1)
[16407.651290] wlan0: associated
[16407.677628] bridge-wlan0: is a Wireless Adapter
[16407.677663] bridge-wlan0: up
[16407.677697] bridge-wlan0: attached

```

```

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4e:0e:b5:1e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.31-14-generic firmware=N/A ip=192.168.1.105 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:d1100000-d110ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:25:b3:b8:dc:3a
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:2000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d102ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

```

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:0F:C5:9C:E0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"baedpint"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000104aee32c3
                    Extra: Last beacon: 56790ms ago
                    IE: Unknown: 00086261656470696E74
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 0706425220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F0101001DFF7F
                    IE: Unknown: DD0C00037F020101040002A34000
                    IE: Unknown: DD1A00037F0301000000001D0FC59CE0021D0FC59CE064002C011D08

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

```

```

$ lsb_release -d
Description:	Ubuntu 9.10

```

```

$ uname -mr
2.6.31-14-generic x86_64

```

Any ideas?

Thanks!

---

### Post by Fir3chi3f on 2009-11-14
I saw 'Atheros' as soon as I looked at your thread and almost cried myself :sad: I have an atheros card in my laptop that wasn't supported for the longest time.

Are you using 9.10? Have you tried the netbook remix as well as the regular just off a live CD?

The only other thing I can think of is trying out madwifi drivers.

---

### Post by hal10000 on 2009-11-15
After i removed the crappy network-manager and installed wicd instead, all my wireless problems are gone. Maybe this can help you too.

---

### Post by diogobaeder on 2009-11-15
> **Fir3chi3f said:**
> I saw 'Atheros' as soon as I looked at your thread and almost cried myself :sad: I have an atheros card in my laptop that wasn't supported for the longest time.

Are you using 9.10? Have you tried the netbook remix as well as the regular just off a live CD?

The only other thing I can think of is trying out madwifi drivers.

Hi,

I haven't tried any of the LiveCDs, I just upgraded from 9.04 to 9.10. Is there any difference in the drivers or network software installed comparing a LiveCD to an actual installation?

About the madwifi drivers, they recommend, for my chipset, the same driver I installed from the website I mentioned in my message. So, I've already passed this step.

But thanks for the info, anyway.

Diogo

---

### Post by diogobaeder on 2009-11-15
> **hal10000 said:**
> After i removed the crappy network-manager and installed wicd instead, all my wireless problems are gone. Maybe this can help you too.

hal,

The problems you were having were the same as mine? I just don't think it would be a good idea to move to wicd without having at least a clue that it would solve my problems, because I've tried to install it in the past, and I ended up unable to access any networks - maybe the mistake was in some procedure I did, but I want to stay in a comfortable point, nevertheless (at least I can be online part of the time, for now).

Thanks!

Diogo

---

### Post by hal10000 on 2009-11-15
> The problems you were having were the same as mine?
I have another wireless card than yours (intel PRO/wireless), but i had ramdomly network timeouts and even lost connection and installing the backported modules did'nt really solve the problem.
I noticed that in many cases network-manager was unable to reconnect, and after i installed wicd that all was gone.

> I ended up unable to access any networks - maybe the mistake was in some procedure I did
Thr setup procedure is quite the same as with network-manager.

---

### Post by diogobaeder on 2009-11-15
> **hal10000 said:**
> I have another wireless card than yours (intel PRO/wireless), but i had ramdomly network timeouts and even lost connection and installing the backported modules did'nt really solve the problem.
I noticed that in many cases network-manager was unable to reconnect, and after i installed wicd that all was gone.


Thr setup procedure is quite the same as with network-manager.

Hmmm... I'll try wicd again, then, and after some tests I'll post a feedback here...

Thanks, hal!

Diogo

---

### Post by diogobaeder on 2009-11-15
OK, tried wicd, but it can't find any connections, so now I have no network at all. (I'm writing from another computer.)

Going back to NM, then. :-(

Thanks!

Diogo

---

### Post by diogobaeder on 2009-11-22
UPDATE: I acquired a wired connection to my network, and, for my surprise, I'm having the exact same problems... :-(

Well, what do you guys suggest me to do to try to find where is the problem?

Thanks, again,

Diogo

---

### Post by diogobaeder on 2009-11-23
UPDATE: tried the LiveCD. Both wired and wireless worked flawlessly. OK, now I'm having a strong feeling I'm searching for the solution in the wrong place...

So, that's the scenario: instalation, wired and wireless with dropdowns; LiveCD, wired and wireless perfect. Any clues?

Thanks!

---

### Post by diogobaeder on 2009-11-25
UPDATE: reinstalled the system, maintaining only my home directory. The problem came back. Could it be something with a personnal config?

---

### Post by miatawnt2b on 2009-12-13
I am having the same issue with the atheros ar9280 wireless dropping. Has anyone found a solution?
-J

---

### Post by slumbergod on 2009-12-13
> **hal10000 said:**
> I have another wireless card than yours (intel PRO/wireless), but i had ramdomly network timeouts and even lost connection and installing the backported modules did'nt really solve the problem.
I noticed that in many cases network-manager was unable to reconnect, and after i installed wicd that all was gone.


Thr setup procedure is quite the same as with network-manager.

I've been having a miserable time with my wireless under Karmic too (for me, it's the normally reliable Intel PRO 3945 chipset). Been trying everything but I still haven't managed to get wireless as reliable as it was under Jaunty. I normally use wicd so that hasn't been a fix. More recently, I have taken to manually reloading the kernel wireless modules. Sometimes that works. More often, I need a reboot to reconnect.

I don't know what it is about Karmic but it is a dog for wireless. Anyone who argues otherwise is obviously one of the lucky ones.

---

### Post by Tim_nz on 2010-02-09
i am having the same problem wireless works but connection drops after a minute then starts back up again cant get consistant speeds
tried wicd,madwifi and the compat drivers none of them worked
wiced couldnt find my connection compat didnt work at all madwifi worked but didnt fix the problem.
yea and i installed backports that didnt work either.
seems to be a common problem but no fix :(

---

### Post by illuminatifire on 2010-03-16
I had little hesitation to install wicd after reading previous post because some said it caused them some disruption to their wireless services. But I finally got fed up with my signal beeing dropped. I initially thought it was only on 802.11N or 802.11G  networks but I was also being dropped at cafes with only B.  So I went on and installed wicd, using the "apt-get install wicd" command and removed network manager and now my wireless works flawlessly as it was meant to be =]  I'm using the wext driver and external backend on my Pavilion dm3 (dm3z). I had also previously installed wi but still kept loosing the signal, previous to install wicd.

Kubuntu 9.10 karmic
2.6.31-19-generic x86_64

lspci | grep -i atheros
08:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

lsmod | grep ath
ath9k                 278176  0
mac80211              210008  1 ath9k
ath                    10304  1 ath9k
cfg80211              109144  3 ath9k,mac80211,ath
led_class               5256  2 ath9k,hp_accel

---

