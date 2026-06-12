---
title: "Wireless Atheros AR2413 disconnects while downloading [Karmic]"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by Fueled on 2010-02-06
Hello everyone!
I've installed Ubuntu 9.10 today on a laptop which had been running Windows XP.
Wired connection works flawlessly, I can download big packages without problems. Wireless, though, doesn't work as good. I've been able to find and connect to my home network, but as soon as I start transferring files from my other PC, or if I download packages from the internet, the connection is lost.
I'm then asked two or three times for the WLAN password, and after that the network is not even available to try to connect to (in the list of wireless networks), until I reboot the PC.

I've did some research today, but I couldn't find anything that solved my problem.
Here is the information I could gather (in accordance to the forum guidelines):

1 ) Machine Brand and Model (PC/Laptop):
Toshiba Satellite M40-307

2 ) Wireless Brand, Model and Wireless Chipset:
Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)

3 ) check interface:
```
wlan0     IEEE 802.11bg  ESSID:"Dragonforce"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

4 ) Check for modules:
```
$ lsmod | grep "ath5k"
ath5k                 124260  0 
mac80211              181140  1 ath5k
led_class               4096  1 ath5k
ath                     8060  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath
```

5 ) Kernel boot messages
```
$ dmesg | grep "ath5k"
[   14.636633] ath5k 0000:02:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.636750] ath5k 0000:02:04.0: registered as 'phy0'
[   15.362037] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
```

```
$ dmesg | grep "wlan0"
[   19.403737] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2651.032979] wlan0: authenticate with AP 00:1e:58:11:31:42
[ 2651.035168] wlan0: authenticated
[ 2651.035178] wlan0: associate with AP 00:1e:58:11:31:42
[ 2651.040082] wlan0: RX AssocResp from 00:1e:58:11:31:42 (capab=0x431 status=0 aid=1)
[ 2651.040090] wlan0: associated
[ 2651.046876] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2655.173102] wlan0: disassociated (Reason: 16)
[ 2656.176157] wlan0: associate with AP 00:1e:58:11:31:42
[ 2656.178220] wlan0: RX ReassocResp from 00:1e:58:11:31:42 (capab=0x431 status=17 aid=1)
[ 2656.178230] wlan0: AP denied association (code=17)
[ 2656.376099] wlan0: associate with AP 00:1e:58:11:31:42
[ 2656.379197] wlan0: RX AssocResp from 00:1e:58:11:31:42 (capab=0x431 status=17 aid=1073)
[ 2656.379205] wlan0: AP denied association (code=17)
[ 2656.576121] wlan0: associate with AP 00:1e:58:11:31:42
[ 2656.578119] wlan0: RX AssocResp from 00:1e:58:11:31:42 (capab=0x431 status=17 aid=1073)
[ 2656.578128] wlan0: AP denied association (code=17)
[ 2656.776093] wlan0: association with AP 00:1e:58:11:31:42 timed out
[ 2657.979792] wlan0: authenticate with AP 00:1e:58:11:31:42
[ 2657.983575] wlan0: authenticated
[ 2657.983584] wlan0: associate with AP 00:1e:58:11:31:42
[ 2657.985609] wlan0: RX AssocResp from 00:1e:58:11:31:42 (capab=0x431 status=0 aid=1)
[ 2657.985616] wlan0: associated
[ 2661.660101] wlan0: no IPv6 routers present
[ 5889.648067] wlan0: no probe response from AP 00:1e:58:11:31:42 - disassociating
[ 6156.407556] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

6 ) Network configuration
```
*-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wmaster0
       version: 01
       serial: 00:11:f5:8f:83:38
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:c0200000-c020ffff
```

7 ) Scan for networks:
```
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results
```
8 ) Ubuntu Version: 
Ubuntu 9.10

9 ) Kernel/architecture (including 32 vs. 64 bit): 
2.6.31-19-generic i686

10 ) Restarting the network:
```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                       Ignoring unknown interface eth0=eth0.
```

Hopefully someone is able to help me out with this issue.
Thanks!

---

### Post by cool_penguin on 2010-02-28
I am facing a similar problem with my Acer Travelmate 2310 having the same wireless card running Ubuntu 9.10. 

I keep facing intermittent disconnection of the Internet and this is starting to get real annoying. 

I also tried to switch to WICD Network Manager but it does not seem to help. 

Wonder if NDISWrapper does the trick?

Cheers,
Harry

---

### Post by Fueled on 2010-04-05
Installing the MadWIFI drivers as explained in this thread did the trick: [http://ubuntuforums.org/showthread.php?t=1309072]("http://ubuntuforums.org/showthread.php?t=1309072").
In the last few months, updates to Ubuntu would switch back to the old way, and I wouldn't be able to connect at all via wireless. Repeating the steps explained in the above linked thread would solve the problem again. However, since 3 weeks or so, yet another update has created another problem, a different one this time.

My router's wireless network's security has always been set as WPA2-PSK(AES), and in Ubuntu I would select "WPA & WPA2 Personal", which would work fine. However now, I do not have this choice anymore in the "Wireless security" listbox of the "Wireless Network Authentication Required" dialog. I only have different variants of "WEP" and one of "LEAP".
Another thing I noticed, is that in the "Network Connections" dialog, there are now two different wireless connections, "Dragonforce" and "Auto Dragonforce", and that even if I delete the Auto one, it always comes back if I try to connect to the available connection.

Anyone knows what has changed, how to bring back the WPA security, and how to avoid having to repeat the process every time there's a change in the kernel or wherever?

---

### Post by abid_naqvi83 on 2010-12-20
I have a Lenovo Ideapad S10-3 running Ubuntu 9.10 with an Atheros A928x device. I tried the MadWifi solution given on the first page of [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072) but it did not work for me. The wifi interface completely disappeared and I got an "UNCLAIMED" network when I ran 'lshw -C network'

I was able to fix this and the original problem (stuttering wifi) using the solution (involving compat wireless drivers) on page 3 of the thread: [http://ubuntuforums.org/showthread.php?t=1309072&page=3](http://ubuntuforums.org/showthread.php?t=1309072&page=3).

If you use this technique for the first time (without trying MadWifi first) you won't need to change any of the blacklist files. 

**Note: Install the following packages from Synaptic Package Manager before installing the driver:** linux-backports-modules-karmic-generic  and  linux-backports-modules-wireless-karmic-generic

---

