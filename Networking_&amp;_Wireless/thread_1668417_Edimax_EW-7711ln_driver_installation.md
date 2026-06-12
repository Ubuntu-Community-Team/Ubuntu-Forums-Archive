---
title: "Edimax EW-7711ln driver installation"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by nashan.lam on 2011-01-16
Hi,
I'm completely new to Ubuntu and Linux.
I installed it today on my PC and ubuntu didn't recognize my wireless card (Edimax EW-7711ln PCI card).
I googled it and found that other people had the same issue.
I downloaded ralink 3562 drivers and followed instructions of one of the forums for installing it ( i can't find it right now). i found in many places that people recommend use this driver although it's not the original driver for my card.

Anyway, in the end it didn't work. I still don't have wireless network, and now there is no network symbol at all in the top right.

I have no wired network on this computer which makes the troubleshooting even harder, so please mind that.

I hope i can find the solution for this. Overall i like ubuntu, it's speed and interface, but some simple tasks are very hard to do, like installing drivers. I wish it was a bit more user friendly (even for a tech savvy like me :)

I followed instructions of this forum, here is all the info:

```
1. Intel Core i3
Gigabyte H55M-D2H

2. Edimax EW-7711ln PCI wireless card
$lspci dont list it at all

3.
doesn list the wireless card

4.
rt2800lib              31970  1 rt2800pci
rt2x00usb              11316  1 rt2800lib
rt3562sta            1008827  1 
rt2x00pci               6993  1 rt2800pci
crc_ccitt               1699  1 rt2800pci
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
snd_rawmidi            22207  1 snd_seq_midi
led_class               3393  1 rt2x00lib
mac80211              266657  3 rt2x00usb,rt2x00pci,rt2x00lib
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              170293  2 rt2x00lib,mac80211
snd                    64117  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeprom_93cx6            1789  1 rt2800pci


5.
can find anything about wireless...

6. *-network
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: ra0
       version: 00
       serial: 00:1f:1f:a6:05:44
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.0 ip=127.0.0.1 latency=32 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
       resources: irq:19 memory:fbcf0000-fbcfffff

7.lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:1B:9E:60:83:A8
                    Protocol:802.11b/g
                    ESSID:"Bezeq"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-90 dBm  Noise level:-85 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 02 - Address: 00:1B:9E:A7:A4:F6
                    Protocol:802.11b/g
                    ESSID:"Talia"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:76/100  Signal level:-60 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s

8.ubunthu 10.10

9. 
2.6.35-22-generic x86_64

10.
 * Reconfiguring network interfaces...                                                                                                    grep: /etc/resolv.conf: No such file or directory
grep: /etc/resolv.conf: No such file or directory
                                                                                                                                   [ OK ]


```

Thanks!

---

### Post by nashan.lam on 2011-01-17
Can anybody help me?

I'm stuck without internet (or you can say i'm stuck with windows - which is probably even worse) ;)

---

### Post by nashan.lam on 2011-01-17
now i noticed that the card detects the wireless networks, but it they doesn't show when i click the wireless icon. I noticed it in the log i posted before:
ra0       Scan completed :
          Cell 01 - Address: 00:1B:9E:60:83:A8
                    Protocol:802.11b/g
                    ESSID:"Bezeq"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-90 dBm  Noise level:-85 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 02 - Address: 00:1B:9E:A7:A4:F6
                    Protocol:802.11b/g
                    ESSID:"Talia"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:76/100  Signal level:-60 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s

---

### Post by MooPi on 2011-01-17
Here is my solution [http://ubuntuforums.org/showthread.php?t=1608095](http://ubuntuforums.org/showthread.php?t=1608095)
Additionally I'd look into black listing rt2800pci, rt2800usb and possibly rt2800lib. All of that is listed in the thread I linked.

---

### Post by MooPi on 2011-01-17
Here is my solution [http://ubuntuforums.org/showthread.php?t=1608095](http://ubuntuforums.org/showthread.php?t=1608095)
Additionally I'd look into black listing rt2800pci, rt2800usb and possibly rt2800lib. all of that is listed in the thread I linked.
May need new link to Ralink as the one listed doesn't work [http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D](http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D)
If you remove the card from the case as well and look at the numbers listed on the chip it should indicate if your attempting the proper driver too. I can't find a suitable photo to determine the chip on the web.

---

### Post by nashan.lam on 2011-01-17
Hi thanks for the reply

I did everything in the guide you sent +some extra tests from the thread.
I attach them, maybe they will help.
I can see that the wireless card is somehow configured, and even finds my router, but i don't can't connect to wireless in the network icon on top (there is only "wired" which is grayed out).

(commands are **bold**)

**for lspci -v**

04:01.0 Network controller: RaLink Device 3060
    Subsystem: Edimax Computer Co. Device 7711
    Flags: bus master, slow devsel, latency 32, IRQ 19
    Memory at fbcf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2860
    Kernel modules: rt3562sta, rt2800pci

[B]
iwconfig[/B]

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[B]
iwlist scanning[/B]

ra0       Scan completed :
          Cell 01 - Address: 00:1B:9E:60:83:A8
                    Protocol:802.11b/g
                    ESSID:"Bezeq"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:60/100  Signal level:-66 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s

**$ sudo ifdown ra0**
grep: /etc/resolv.conf: No such file or directory

**$ sudo ifup ra0**
grep: /etc/resolv.conf: No such file or directory

---

### Post by MooPi on 2011-01-17
Can you give me the contents of ??```
/etc/modprode.d/blacklist.conf
```

---

### Post by nashan.lam on 2011-01-18
here you go.
I also get this msg when i start the computer: 
modprobe: FATAL: Could not load /lib/modules/2.6.35-22/modules.dep
modprobe: FATAL: Could not load /lib/modules/2.6.35-22/modules.dep

---

### Post by nashan.lam on 2011-01-18
WoW. At last... :popcorn:
I reintalled ubuntu and installed the drivers and now it works.
I have to say that this was a bit too complicated, i hope i'll find ubuntu to be more user friendly in the future.

Thanks a lot

---

