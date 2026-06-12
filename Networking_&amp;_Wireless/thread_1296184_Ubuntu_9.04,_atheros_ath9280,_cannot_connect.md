---
title: "Ubuntu 9.04, atheros ath9280, cannot connect"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by fabianbadoi on 2009-10-20
Hi there, i'm Fabi, rather new to linux, i've been using ubuntu for about 8 months now on my laptop. I've allways had a problem with my wireless card. The first time i installed ubuntu on it i spent about 2 weeks trying to get it working, and i succeeded. When i upgraded to 9.04 the problem re-appeared and i had forgotten what i had done to make my card work. I spent a few days searching the net for a solution and after i cracked it i bookmarked the page (on my opera acc. so i'd have it anywhere i went).

I reinstalled 9.04 one month ago and when i tried accessing that bookmark i found out i had bookmarked to wrong page, dumb me. I haven't been able to get my wireless card to work, i've tried everything i could find but to no avail. All i remember about the last time i cracked it is that i compiled madwifi with some other "modules" or something like that, but can't find anything in their wiki about such things.

The "symptom" of my problem is:
[LIST]
[*]i can see wireless networks
[*]i can monitor wireless traffic (through aircrack-ng for example)
[*]i can see my card sending packets (through aircrack-ng) when trying to connect
[*]but my card does not seem to respond
[/LIST]
If i have the default gnome network manager, the dot corresponding to my machine turns green but the other dot stays gray.
If i use WICD it stays in the "Authetificating" part for a while and then gives up.

I think i've found out what is happening. Fedora seem to have fixed [this bug]("https://bugzilla.redhat.com/show_bug.cgi?id=498502"), which looks very similar to what i am experiencing. However i have no clue as to how to implement that fix on ubuntu, if it's posible.

I would appreciate any help i could get, i don't want to say i tried everything on these forums, but that would not be an understatement.

Here is info relating to my machine:

It's an Asus F5Z laptop

```

fabi@slacky:~$ lspci -nn | grep theros
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

```

```

fabi@slacky:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

fabi@slacky:~$ lsmod | grep th  
ath_pci               108400  0 
wlan                  232736  1 ath_pci
ath_hal               225904  1 ath_pci
ath9k                 310580  0 
mac80211              255928  1 ath9k
cfg80211               82872  2 ath9k,mac80211
led_class              13064  2 ath9k,asus_laptop

```

```

fabi@slacky:~$ dmesg | grep ath
[    4.501840] device-mapper: multipath: version 1.0.5 loaded
[    4.501843] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.521343] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.521356] ath9k 0000:02:00.0: setting latency timer to 64
[   12.988778] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.989482] Registered led device: ath9k-phy0::radio
[   12.989500] Registered led device: ath9k-phy0::assoc
[   12.989521] Registered led device: ath9k-phy0::tx
[   12.989541] Registered led device: ath9k-phy0::rx
[   13.195435] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   13.215911] ath_pci: 0.9.4

```

```

fabi@slacky:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:20:a5:92
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:54:16:8d:96
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.101 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 12:d4:90:d2:53:e5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

```

fabi@slacky:~$ lsb_release -d
Description:	Ubuntu 9.04

fabi@slacky:~$ uname -mr
2.6.28-11-generic x86_64

fabi@slacky:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

```

Thanks for reading this and a big /hug if you can help me :D

---

### Post by fabianbadoi on 2009-10-21
bumb

---

### Post by fabianbadoi on 2009-10-21
Terminal bump.

---

### Post by drpjkurian on 2009-10-21
Hi 
Please visit my thread. It might help you.
[http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)

With regards
Dr Kurian

---

### Post by fabianbadoi on 2009-10-21
> **drpjkurian said:**
> Hi 
Please visit my thread. It might help you.
[http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)

With regards
Dr Kurian
Thanks, i've tried that, but it wasn't on a fresh install, i'll try it again after i reinstall.

---

### Post by drpjkurian on 2009-10-25
Did you try after a fresh install?

Dr Kurian
> **fabianbadoi said:**
> Thanks, i've tried that, but it wasn't on a fresh install, i'll try it again after i reinstall.

---

### Post by fabianbadoi on 2009-10-25
> **drpjkurian said:**
> Did you try after a fresh install?

Dr Kurian

I gave it a shot, unfortunately i don't have a wifi router at home so i'll have to wait until tomorrow(Monday) morning.

---

### Post by fabianbadoi on 2009-10-27
Limited success. I tried connecting to an ad-hoc network and for the first time i've seen the other green dot on the network applet light up, but i still couldn't connect. That prob. means it was trying to get an IP.
Trying to connect to non-adhoc yielded the same results, although it might have been because of bad signal (referring to this time only and other laptops were able to connect).

---

### Post by Viola00 on 2009-10-29
ive always had problems with my ar928x, in 9.04 the wireless worked periodically. i then upgraded to karmic and it stopped working. i installed compat-wireless rc5 and now it works perfectly, the signal strength even works great. give it a shot

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

---

### Post by fabianbadoi on 2009-10-30
I've managed to get it working yesterday, i removed ath9k from the blacklist and reinstalled linux-backports-modules, although i haven't tried connecting to encrypted networks yet. I don't remember which builds of compat-wireless i've tried, but i know it never worked. I remember seeing some thread saying "It will automagically work" and that kind of annyoned me :P.

If i can't connect to wep/wpa i'll give compat-wireless another try.

---

### Post by fabianbadoi on 2009-11-05
compat-wireless did not work for me, and now i can't connect to any networks. I'll try reinstalling mad-wifi.

---

