---
title: "Wireless repeatedly drops after 10.10 upgrade (Broadcom 4309) - full documentation"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by SilentSeven on 2010-10-23
**Summary**:  My wireless connection ran without issue when I ran Ubuntu 9.x on a windows dual boot loader.  Liking Ubuntu, I wiped the system and installed a 10.10 with no dual boot.  After the upgrade, my wireless connection is no longer reliable.

**Drop summary**:  Wireless seems to stay connected when traffic volumes are low.  As soon as any significant traffic is generated such as a download, torrent or video stream, the network disconnects.  Disabling and re-enabling the connection at the GUI recovers the connection.  Disconnect can be generated on demand.

Appreciate if anyone has any suggestions or if I can somehow roll back to the 9.x network setup I was running.  Unclear to me (n00b) if the windows dual boot was impacting that setup or not.  

**1 ) Machine Brand and Model (PC/Laptop)**:
```
Dell Latitude D400, 1GB ram
```**2 ) Wireless Brand, Model and Wireless Chipset:**

```
jeff@D400:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
01:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
01:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
01:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
``````

jeff@D400:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jeff@D400:~$ 
```**3 ) check interface:**

```
jeff@D400:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:90:96:aa:2c:f2  
          inet addr:172.31.0.105  Bcast:172.31.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:feaa:2cf2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:374169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:286323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:308884084 (308.8 MB)  TX bytes:28572961 (28.5 MB)
``````
jeff@D400:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"1342"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:3F:64:B0   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```** 4) Check for modules:**

```

jeff@D400:~$ lsmod
Module                  Size  Used by
snd_seq_dummy           1350  0 
binfmt_misc             6599  1 
snd_intel8x0           25632  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
arc4                    1165  2 
pcmcia                 35973  0 
snd_seq_device          5744  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
b43                   168681  0 
mac80211              231541  1 b43
yenta_socket           21518  0 
joydev                  8735  0 
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  291004  2 
pcmcia_rsrc            10566  1 yenta_socket
cfg80211              144470  2 b43,mac80211
drm_kms_helper         30200  1 i915
soundcore                880  1 snd
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   168054  2 i915,drm_kms_helper
ppdev                   5556  0 
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
parport_pc             26058  1 
led_class               2633  1 b43
intel_agp              26360  2 i915
lp                      7342  0 
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
psmouse                59033  0 
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
shpchp                 29886  0 
serio_raw               4022  0 
dcdbas                  5402  0 
parport                31492  3 ppdev,parport_pc,lp
firewire_ohci          21106  0 
tg3                   123310  0 
ssb                    39288  1 b43
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
```**5 ) Kernel boot messages**

```
jeff@D400:~$ dmesg | grep wlan0
[   26.321244] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.797895] wlan0: authenticate with 00:13:46:3f:64:b0 (try 1)
[   38.800322] wlan0: authenticated
[   38.800466] wlan0: associate with 00:13:46:3f:64:b0 (try 1)
[   38.802344] wlan0: RX AssocResp from 00:13:46:3f:64:b0 (capab=0x31 status=0 aid=3)
[   38.802351] wlan0: associated
[   38.803458] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   49.776051] wlan0: no IPv6 routers present
[ 1910.729014] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1913.348758] wlan0: authenticate with 00:13:46:3f:64:b0 (try 1)
[ 1913.362903] wlan0: authenticated
[ 1913.362954] wlan0: associate with 00:13:46:3f:64:b0 (try 1)
[ 1913.364881] wlan0: RX AssocResp from 00:13:46:3f:64:b0 (capab=0x31 status=0 aid=3)
[ 1913.364893] wlan0: associated
[ 1913.367035] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1924.048136] wlan0: no IPv6 routers present
[ 4240.592841] wlan0: deauthenticating from 00:13:46:3f:64:b0 by local choice (reason=3)
[ 4248.232929] wlan0: authenticate with 00:14:bf:17:9c:d4 (try 1)
[ 4248.432074] wlan0: authenticate with 00:14:bf:17:9c:d4 (try 2)
[ 4248.632089] wlan0: authenticate with 00:14:bf:17:9c:d4 (try 3)
[ 4248.832085] wlan0: authentication with 00:14:bf:17:9c:d4 timed out
[ 4305.553644] wlan0: authenticate with 00:13:46:3f:64:b0 (try 1)
[ 4305.555296] wlan0: authenticated
[ 4305.555624] wlan0: associate with 00:13:46:3f:64:b0 (try 1)
[ 4305.557495] wlan0: RX AssocResp from 00:13:46:3f:64:b0 (capab=0x31 status=0 aid=3)
[ 4305.557501] wlan0: associated
[31051.311195] wlan0: deauthenticating from 00:13:46:3f:64:b0 by local choice (reason=3)
[31064.552601] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[31076.858080] wlan0: authenticate with 00:13:46:3f:64:b0 (try 1)
[31076.860293] wlan0: authenticated
[31076.860433] wlan0: associate with 00:13:46:3f:64:b0 (try 1)
[31076.863581] wlan0: RX AssocResp from 00:13:46:3f:64:b0 (capab=0x31 status=0 aid=4)
[31076.863588] wlan0: associated
[31076.864669] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[31087.664042] wlan0: no IPv6 routers present
[31567.577496] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[31570.192563] wlan0: authenticate with 00:13:46:3f:64:b0 (try 1)
[31570.207469] wlan0: authenticated
[31570.207522] wlan0: associate with 00:13:46:3f:64:b0 (try 1)
[31570.210510] wlan0: RX AssocResp from 00:13:46:3f:64:b0 (capab=0x31 status=0 aid=4)
[31570.210520] wlan0: associated
[31570.214352] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[31580.984044] wlan0: no IPv6 routers present
[32537.765138] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[32540.936851] wlan0: authenticate with 00:13:46:3f:64:b0 (try 1)
[32540.949996] wlan0: authenticated
[32540.950032] wlan0: associate with 00:13:46:3f:64:b0 (try 1)
[32540.952761] wlan0: RX AssocResp from 00:13:46:3f:64:b0 (capab=0x31 status=0 aid=4)
[32540.952772] wlan0: associated
[32540.954920] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[32551.200026] wlan0: no IPv6 routers present
[32940.998354] wlan0: deauthenticating from 00:13:46:3f:64:b0 by local choice (reason=3)
[32948.604531] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[32951.248738] wlan0: authenticate with 00:13:46:3f:64:b0 (try 1)
[32951.250187] wlan0: authenticated
[32951.250554] wlan0: associate with 00:13:46:3f:64:b0 (try 1)
[32951.252600] wlan0: RX AssocResp from 00:13:46:3f:64:b0 (capab=0x31 status=0 aid=4)
[32951.252607] wlan0: associated
[32951.254089] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[32961.472254] wlan0: no IPv6 routers present
[33270.585420] wlan0: deauthenticating from 00:13:46:3f:64:b0 by local choice (reason=3)
[33281.421212] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[33297.364909] wlan0: authenticate with 00:13:46:3f:64:b0 (try 1)
[33297.366417] wlan0: authenticated
[33297.366782] wlan0: associate with 00:13:46:3f:64:b0 (try 1)
[33297.368865] wlan0: RX AssocResp from 00:13:46:3f:64:b0 (capab=0x31 status=0 aid=4)
[33297.368876] wlan0: associated
[33297.370927] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[33307.488251] wlan0: no IPv6 routers present
[33370.701409] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[33373.756556] wlan0: authenticate with 00:13:46:3f:64:b0 (try 1)
[33373.758287] wlan0: authenticated
[33373.758455] wlan0: associate with 00:13:46:3f:64:b0 (try 1)
[33373.760526] wlan0: RX AssocResp from 00:13:46:3f:64:b0 (capab=0x31 status=0 aid=4)
[33373.760534] wlan0: associated
[33373.769025] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[33384.672249] wlan0: no IPv6 routers present
[33509.025212] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[33512.148576] wlan0: authenticate with 00:13:46:3f:64:b0 (try 1)
[33512.150057] wlan0: authenticated
[33512.150439] wlan0: associate with 00:13:46:3f:64:b0 (try 1)
[33512.152677] wlan0: RX AssocResp from 00:13:46:3f:64:b0 (capab=0x31 status=0 aid=4)
[33512.152688] wlan0: associated
[33512.154669] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[33522.416071] wlan0: no IPv6 routers present
[33629.177204] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[33631.804765] wlan0: authenticate with 00:13:46:3f:64:b0 (try 1)
[33631.806648] wlan0: authenticated
[33631.806830] wlan0: associate with 00:13:46:3f:64:b0 (try 1)
[33631.811763] wlan0: RX AssocResp from 00:13:46:3f:64:b0 (capab=0x31 status=0 aid=4)
[33631.811774] wlan0: associated
[33631.813859] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[33642.272045] wlan0: no IPv6 routers present
[33906.241815] wlan0: deauthenticating from 00:13:46:3f:64:b0 by local choice (reason=3)
[33909.500567] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[33912.148636] wlan0: authenticate with 00:13:46:3f:64:b0 (try 1)
[33912.150345] wlan0: authenticated
[33912.150515] wlan0: associate with 00:13:46:3f:64:b0 (try 1)
[33912.152407] wlan0: RX AssocResp from 00:13:46:3f:64:b0 (capab=0x31 status=0 aid=4)
[33912.152418] wlan0: associated
[33912.159252] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[33922.256268] wlan0: no IPv6 routers present
[38317.877050] wlan0: authenticate with 00:13:46:3f:64:b0 (try 1)
[38317.878503] wlan0: authenticated
[38317.878881] wlan0: associate with 00:13:46:3f:64:b0 (try 1)
[38317.880751] wlan0: RX AssocResp from 00:13:46:3f:64:b0 (capab=0x31 status=0 aid=4)
[38317.880763] wlan0: associated
```[B]6 ) Network configuration
[/B]```
jeff@D400:~$ sudo lshw -C network
[sudo] password for jeff: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:aa:7b:c6
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=5705-v3.11 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:11 memory:fcff0000-fcffffff memory:fd000000-fd00ffff
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fcfec000-fcfedfff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:96:aa:2c:f2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A ip=172.31.0.105 link=yes multicast=yes wireless=IEEE 802.11bg
```[B]7 ) Scan for networks

[/B]```
jeff@D400:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:3F:64:B0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"1342"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d0742053f
                    Extra: Last beacon: 18104ms ago
                    IE: Unknown: 000431333432
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: DD0600032F010001
                    IE: Unknown: 2A0105
                    IE: Unknown: 32041224606C
```[B]8 ) Ubuntu Version: 

[/B]```
jeff@D400:~$  lsb_release -d
Description:    Ubuntu 10.10
```[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 

[/B]```
jeff@D400:~$ uname -mr
2.6.35-22-generic i686
```

---

### Post by msm120 on 2010-10-23
Don't know if this is related, but the WiFi drops were enough for me to revert to 9.10. Check out [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658747](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658747) ...

> "Natty" kernel 2.6.36-020636-generic #201010210905 ... resolved a problem where the normal b43 wireless would not stay connected for more than a minute or two ...

---

### Post by maclenin on 2010-10-24
...though I can't share a solution - yet - your wireless issue seems very similar to mine (in both 10.04 and LiveUSB of 10.10) - perhaps you'll find some buried leads in [my thread]("http://ubuntuforums.org/showthread.php?t=1579095")....

---

### Post by oak3 on 2010-10-24
Same problem for me with 10.04. I thought 10.10 will solve it but if not maybe I delay update...

---

### Post by SilentSeven on 2010-10-24
Thanks for the starts.

mclenin:  does your wireless drop or just get slow?  forgive me if I missed that when I surfed your thread.  early here, still working on my coffee.  mine drops and i have to reconnect.  when working, my speed seems ok but as soon as a put any load on it outside of simple page loads, it drops.

I wish i knew what driver/firmware combo I was running last setup.  While quite a n00b to all this, i seem to have distilled the following:

- my 4309 card is 'unsupported' in the both the b43 and sta drivers (yet worked fine before)
- there are two drivers?  b43 and STA and i'm running b43, right?  maybe i should try STA.
- there are two versions of firmware - b43 and b43legacy.  i'm assuming i'm running b43.  maybe i should try the legacy?

Any suggestions on firmware/driver swaps would be helpful.

Generally, I'm a bit amazed that wireless could be such apparent trainwreck in the 10.x version.  All sorts of posts in the forums with connect problems.  Was it this bad when the 9.x versions came out?  I'm just playing with ubuntu and would like to swap over some day; do real work on a windows 7 box.

---

### Post by maclenin on 2010-10-24
**SilentSeven:** No worries - I can appreciate the early am pre-coffee coma. My connection does both (slowing and/or dropping) at the "significant traffic" junctures you describe. However, my connection is at all times slower than it had been in pre-10 ubuntu releases. When I first started with ubuntu I had to tinker with wireless to get it working - but at that time (edgy) ndiswrapper turned out to be the perfect solution.

Currently:

*I can no longer use google maps | way too slow
*I can no longer watch web-based videos | chronic freezing and dropping
*I can no longer send files via skype | prohibitively SLOW - 174KB files take at least 20 minutes (I terminate the transfers before they complete)

I really don't have any specific suggestion re: solution - but feel free to troll [my thread]("http://ubuntuforums.org/showthread.php?t=1579095") for ideas. I am currently using ndiswrapper (having tried b43 and sta, as well) but am posting this latest message via MAC because - you know why.... Other than this VERY LARGE ISSUE, I consider myself a linux zealot as this is, essentially, the ONLY issue I have not (YET) been able to resolve (with reasonable effort) over the course of my 4 year dance with ubuntu....

**NB:** Perhaps the very recently posted "[Sef sticky]("http://ubuntuforums.org/showthread.php?t=1604868")" presents a solution?

---

### Post by oak3 on 2010-10-30
Like I mentioned I have exactly same problem. My computer is Dell Latitude E5500 with Broadcom BCM4322. OS is Kubuntu 10.04 updated from 910 (which did not have this issue). Under low traffic everything is OK, but if you start some heavy downloads (for example torrents) connection is dropped and I have to disable/enable wireless in network manager. Now I've noticed some messages in /var/log/messages. Maybe some of you could also look what do you have in this file - if its similar to mine that means it is related and we could try to look for some help based on that :)
My /var/log/messages after connection drop:
```

Oct 31 00:28:45 dell kernel: [  160.229204] key[0] alg=TKIP key_set=1 tx_pn=000000000729 rx_pn=000000000680 replays=5 icv_errors=0 local_mic_failures=1
Oct 31 00:28:45 dell kernel: [  160.229208] : TKIP stats from module: Ucast
Oct 31 00:28:45 dell kernel: [  160.243917] key[0] alg=TKIP key_set=1 tx_pn=000000000729 rx_pn=000000000680 replays=5 icv_errors=0 local_mic_failures=2
Oct 31 00:28:45 dell kernel: [  160.243921] : TKIP stats from module: Ucast
Oct 31 00:29:45 dell kernel: [  220.258243] wpa_supplicant[945]: segfault at 2000095 ip 0809bb34 sp bff84400 error 4 in wpa_supplicant[8048000+7d000]

```BTW I have tried to move to older version of bcmwl-kernel-source as suggested in this post ([http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx](http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx)). I though that if bcmwl-kernel-source newer version is buggy maybe it also causes my connection drops and I should try version from 9.10 where I did not have such problems. Unfortunately it didn't help to me :(

---

### Post by inspired on 2010-10-31
Just a note to say I am having the same issue on a friend's computer. Trying to get him set up with Ubuntu and away from Vista which was (yet again) heavily compromised by malware.

In testing his computer with Ubuntu Live 10.10 the only issue in our way to ditching windows is that the wifi drops as soon as any activity goes through it like installing drivers from the repositories, etc. 

The Wifi is a USB one. Cisco Linksys WUSB54GC ver. 3

When I plug in lspci the controller is referred to as Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)

I see here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB)

... that on earlier versions of Ubuntu it was reported to NOT work out of the box. It has actually worked out of the box, but it drops the connection, and looking at this thread this may not be anything to do specifically with the USB Wifi we have, but a more general issue.

I may create a new thread to search for an option.

WIth thanks,

Jonathan

---

### Post by oak3 on 2010-10-31
Could you check /var/log/messages and then start some heavy activity to drop connection and see if you have any new messages in that log file?

---

### Post by inspired on 2010-10-31
> **oak3 said:**
> Could you check /var/log/messages and then start some heavy activity to drop connection and see if you have any new messages in that log file?

I am not convinced I have exactly the same issue. After more time watching it I can see that it does NOT appear to be related to how much the connection is being used. It just so happened I was doing a lot of downloading of drivers etc. when I got this going, so there appeared to be a correlation. I also don't think this Wifi controller has a broadcom chipset.

So I will start a new thread.

---

### Post by oak3 on 2010-11-09
Changing router settings to WPA2 solved my problem!

---

### Post by y_farkash on 2010-11-11
I have the same issue with a Dell Latitude D400.

My router is set to WPA2 and I can connect briefly but it will drop the connection soon after. Disabling and enabling the wireless connection via the connection manager allows it to connect again, but only to drop the connection a few minutes later again.

Please help with a solution. I don't want to go back to the XP I used to have on this machine, but as it stands, the machine is not very usable.

Cheer.

---

### Post by don pepito on 2010-11-19
Same issue here with wifi. Also happens with a nokia 5800 gsm connection via USB or bluetooth

---

### Post by aquascrotum on 2010-12-05
I have the same issue - Dell laptop running Maverick with Broadcom wifi modem.  Wifi connection drops out particularly when under heavy load (update or torrent download).

Connection generally reestablishes after a restart.  Disabling networking, removing the saved connection point and restarting network sometimes does the trick.

Have tried this with and without the Broadcom drivers enabled.

---

### Post by SilentSeven on 2010-12-26
Somethings seems to have changed with one of the updates - all my problems seem to be gone.  Anyone else having better luck?

---

### Post by Med(B) on 2011-01-18
I was having the same problem.  I upgraded to 10.10 and would get a couple minutes of use on my wireless before the connection dropped.  I installed broadcom-sta-common from synaptic, switched to the STA driver, then did a complete restart (shut down, not just restart) and it seems to have fixed my problem.  I've been playing with Ubuntu for about a year now so I'm far (far, far, far) from an expert, but this helped me.  Hope it helps!

---

### Post by acarlstein on 2011-03-30
> **Med(B) said:**
> I was having the same problem.  I upgraded to 10.10 and would get a couple minutes of use on my wireless before the connection dropped.  I installed broadcom-sta-common from synaptic, switched to the STA driver, then did a complete restart (shut down, not just restart) and it seems to have fixed my problem.  I've been playing with Ubuntu for about a year now so I'm far (far, far, far) from an expert, but this helped me.  Hope it helps!

1. I followed your steps and did not resolve my problems.

2. I tried to remove nm-applet and network manager and install wcid (executing wicd-client). Failed too.

3. I never had weird problems up to Ubuntu 8.10

In Ubuntu 9.04 is when all kind of problems began: my hibernation mode was failing.

Then Ubuntu 10.04 showed up! WORSE

Now with Ubuntu 10.10 I cannot have a signal working more than a minute.

IF IT IS WORKING DON'T FIX IT DAMMIT!!!
:mad::mad:

---

### Post by kyalpani on 2011-05-11
this worked for me on my sony vaio:

$sudo rmmod iwl3945
$sudo modprobe iwl3945

Remember that iwl3945 is the module (driver) that is specific for wireless on this laptop. On your machine it could be something else.

---

