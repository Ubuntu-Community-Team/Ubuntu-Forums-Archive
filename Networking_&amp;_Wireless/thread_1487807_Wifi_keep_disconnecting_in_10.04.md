---
title: "Wifi keep disconnecting in 10.04"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by ram130 on 2010-05-19
I never had this problem with Ubuntu before and I am now confused. This is a clean install and I have not change anything about my AP so don't why this is happening. 

Every 5min or so my wifi keeps disconnecting and sometimes have problems reconnecting. I also have Windows on this machine and it does not do this at all. My AP is set to channel 9(changing it makes no difference), WPA2. Please help. Logs below

```
[   15.668746]   alloc irq_desc for 33 on node -1
[   15.668748]   alloc kstat_irqs on node -1
[   15.668768] iwlagn 0000:02:00.0: irq 33 for MSI/MSI-X
[   15.696615]   alloc irq_desc for 22 on node -1
[   15.696618]   alloc kstat_irqs on node -1
[   15.696624] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.696684] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.712761] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input9
[   15.712861] Registered led device: hp::hddprotect
[   15.712875] lis3lv02d driver loaded.
[   15.731849] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   15.781503] [drm] fb mappable at 0xC0141000
[   15.781506] [drm] vram apper at 0xC0000000
[   15.781508] [drm] size 5760000
[   15.781509] [drm] fb depth is 24
[   15.781511] [drm]    pitch is 6400
[   15.781683] fb0: radeondrmfb frame buffer device
[   15.781685] registered panic notifier
[   15.781690] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   15.783952] vga16fb: initializing
[   15.783955] vga16fb: mapped to 0xc00a0000
[   15.783958] vga16fb: not registering due to another framebuffer present
[   15.820323] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   15.841069] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   15.841217] input: HDA Intel Line Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   15.842222] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.842264] HDA Intel 0000:01:00.1: setting latency timer to 64
[   16.399352] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000
[   16.487219] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input13
[   17.133398] Console: switching to colour frame buffer device 200x56
[   17.218717] type=1505 audit(1274282243.212:5):  operation="profile_load" pid=996 name="/usr/share/gdm/guest-session/Xsession"
[   17.224028] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   17.229751] type=1505 audit(1274282243.224:6):  operation="profile_replace" pid=1001 name="/sbin/dhclient3"
[   17.230392] type=1505 audit(1274282243.224:7):  operation="profile_replace" pid=1001 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.230733] type=1505 audit(1274282243.224:8):  operation="profile_replace" pid=1001 name="/usr/lib/connman/scripts/dhclient-script"
[   17.231139] iwlagn 0000:02:00.0: loaded firmware version 8.24.2.12
[   17.240057] type=1505 audit(1274282243.236:9):  operation="profile_load" pid=1008 name="/usr/bin/evince"
[   17.250904] type=1505 audit(1274282243.244:10):  operation="profile_load" pid=1008 name="/usr/bin/evince-previewer"
[   17.258146] type=1505 audit(1274282243.252:11):  operation="profile_load" pid=1008 name="/usr/bin/evince-thumbnailer"
[   17.374652] Registered led device: iwl-phy0::radio
[   17.375125] Registered led device: iwl-phy0::assoc
[   17.375554] Registered led device: iwl-phy0::RX
[   17.375972] Registered led device: iwl-phy0::TX
[   17.392465] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.393834] r8169: eth0: link down
[   17.394018] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.531039] ppdev: user-space parallel port driver
[   17.725300] CPU0 attaching NULL sched-domain.
[   17.725304] CPU1 attaching NULL sched-domain.
[   17.748164] CPU0 attaching sched-domain:
[   17.748170]  domain 0: span 0-1 level MC
[   17.748174]   groups: 0 1
[   17.748183] CPU1 attaching sched-domain:
[   17.748186]  domain 0: span 0-1 level MC
[   17.748190]   groups: 1 0
[   18.681079] CPU0 attaching NULL sched-domain.
[   18.681084] CPU1 attaching NULL sched-domain.
[   18.704118] CPU0 attaching sched-domain:
[   18.704124]  domain 0: span 0-1 level MC
[   18.704129]   groups: 0 1
[   18.704137] CPU1 attaching sched-domain:
[   18.704141]  domain 0: span 0-1 level MC
[   18.704145]   groups: 1 0
[   19.423017] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   40.815185] wlan0: deauthenticating from 00:18:f8:f2:a4:bc by local choice (reason=3)
[   40.815235] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[   41.012059] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 2)
[   41.212048] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 3)
[   41.412047] wlan0: direct probe to AP 00:18:f8:f2:a4:bc timed out
[   54.062118] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[   54.260039] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 2)
[   54.460041] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 3)
[   54.660092] wlan0: direct probe to AP 00:18:f8:f2:a4:bc timed out
[   67.286390] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[   67.484026] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 2)
[   67.684119] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 3)
[   67.888029] wlan0: direct probe to AP 00:18:f8:f2:a4:bc timed out
[  122.494367] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[  122.497043] wlan0: direct probe responded
[  122.497050] wlan0: authenticate with AP 00:18:f8:f2:a4:bc (try 1)
[  122.499026] wlan0: authenticated
[  122.499054] wlan0: associate with AP 00:18:f8:f2:a4:bc (try 1)
[  122.501799] wlan0: RX AssocResp from 00:18:f8:f2:a4:bc (capab=0x431 status=0 aid=2)
[  122.501804] wlan0: associated
[  122.524837] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  123.559606] padlock: VIA PadLock not detected.
[  133.392088] wlan0: no IPv6 routers present
[  416.664528] No probe response from AP 00:18:f8:f2:a4:bc after 500ms, disconnecting.
[  420.048665] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[  420.051334] wlan0: direct probe responded
[  420.051340] wlan0: authenticate with AP 00:18:f8:f2:a4:bc (try 1)
[  420.053375] wlan0: authenticated
[  420.053406] wlan0: associate with AP 00:18:f8:f2:a4:bc (try 1)
[  420.056114] wlan0: RX AssocResp from 00:18:f8:f2:a4:bc (capab=0x431 status=0 aid=2)
[  420.056120] wlan0: associated
[  544.520534] No probe response from AP 00:18:f8:f2:a4:bc after 500ms, disconnecting.
[  547.923493] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[  547.926172] wlan0: direct probe responded
[  547.926178] wlan0: authenticate with AP 00:18:f8:f2:a4:bc (try 1)
[  547.928176] wlan0: authenticated
[  547.928208] wlan0: associate with AP 00:18:f8:f2:a4:bc (try 1)
[  547.930785] wlan0: RX AssocResp from 00:18:f8:f2:a4:bc (capab=0x431 status=0 aid=2)
[  547.930792] wlan0: associated
[  656.608581] No probe response from AP 00:18:f8:f2:a4:bc after 500ms, disconnecting.
[  660.031944] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[  660.228544] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 2)
[  660.428058] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 3)
[  660.628183] wlan0: direct probe to AP 00:18:f8:f2:a4:bc timed out
[  693.884429] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[  693.888532] wlan0: direct probe responded
[  693.888539] wlan0: authenticate with AP 00:18:f8:f2:a4:bc (try 1)
[  693.890297] wlan0: authenticated
[  693.890328] wlan0: associate with AP 00:18:f8:f2:a4:bc (try 1)
[  693.893062] wlan0: RX AssocResp from 00:18:f8:f2:a4:bc (capab=0x431 status=0 aid=2)
[  693.893068] wlan0: associated
[  778.632538] No probe response from AP 00:18:f8:f2:a4:bc after 500ms, disconnecting.
[  782.023479] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[  782.220533] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 2)
[  782.424666] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 3)
[  782.624043] wlan0: direct probe to AP 00:18:f8:f2:a4:bc timed out
[  807.536030] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[  807.736534] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 2)
[  807.936541] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 3)
[  808.136536] wlan0: direct probe to AP 00:18:f8:f2:a4:bc timed out
[  820.818004] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[  820.820670] wlan0: direct probe responded
[  820.820675] wlan0: authenticate with AP 00:18:f8:f2:a4:bc (try 1)
[  820.822429] wlan0: authenticated
[  820.822450] wlan0: associate with AP 00:18:f8:f2:a4:bc (try 1)
[  820.827410] wlan0: RX AssocResp from 00:18:f8:f2:a4:bc (capab=0x431 status=0 aid=2)
[  820.827415] wlan0: associated
[  978.816055] No probe response from AP 00:18:f8:f2:a4:bc after 500ms, disconnecting.
[  982.200544] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[  982.203211] wlan0: direct probe responded
[  982.203218] wlan0: authenticate with AP 00:18:f8:f2:a4:bc (try 1)
[  982.207342] wlan0: authenticated
[  982.207369] wlan0: associate with AP 00:18:f8:f2:a4:bc (try 1)
[  982.211019] wlan0: RX AssocResp from 00:18:f8:f2:a4:bc (capab=0x431 status=0 aid=2)
[  982.211025] wlan0: associated
[  990.517767] radeon 0000:01:00.0: f2052800 reserve failed for wait
[ 1276.796017] No probe response from AP 00:18:f8:f2:a4:bc after 500ms, disconnecting.
[ 1280.302358] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[ 1280.500077] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 2)
[ 1280.700546] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 3)
[ 1280.900533] wlan0: direct probe to AP 00:18:f8:f2:a4:bc timed out
[ 1322.012496] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[ 1322.214563] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 2)
[ 1322.416046] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 3)
[ 1322.616044] wlan0: direct probe to AP 00:18:f8:f2:a4:bc timed out
[ 1343.574024] wlan0: direct probe to AP 00:18:f8:f2:a4:bc (try 1)
[ 1343.576919] wlan0: direct probe responded
[ 1343.576926] wlan0: authenticate with AP 00:18:f8:f2:a4:bc (try 1)
[ 1343.579451] wlan0: authenticated
[ 1343.579484] wlan0: associate with AP 00:18:f8:f2:a4:bc (try 1)
[ 1343.582057] wlan0: RX AssocResp from 00:18:f8:f2:a4:bc (capab=0x431 status=0 aid=2)
[ 1343.582061] wlan0: associated

---

digit@digit-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"DIGIT_Network"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:18:F8:F2:A4:BC   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

digit@digit-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:9e:4d:02:cb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3255486 (3.2 MB)  TX bytes:3255486 (3.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:65:73:64:66  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:65ff:fe73:6466/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28847037 (28.8 MB)  TX bytes:4113246 (4.1 MB)


```

---

### Post by vancouverite on 2010-05-19
Hi ram,
I have a similar problem, but with less frequency.  I see the 

```
No probe response from AP <address> after 500ms, disconnecting
```

Message as well and I think this may have something to do with it.

How busy is the airspace where you are?  Only 5 other weak signals within reach here, but that my affect the frequency.

What sort of card are you using?  I have an intel 5300
```
 $sudo lshw | grep -B 1 -A 11 Wireless
*-network      
                description: Wireless interface
                product: Wireless WiFi Link 5300
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 00
                serial: 00:21:6a:33:84:b4
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.0.3 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:31 memory:f4300000-f4301fff
```

If you have problems reconnecting, I have found that either the wifi switch on my machine or restarting the network manager service with 

```
 $sudo service network-manager restart
```

gets me going again, but it is very annoying to have to use that.

Van

---

### Post by ram130 on 2010-05-21
Hey Van, 

I too have a similar wifi adapter, its Intel 5100. I guess we are the only one's with this problem?:(

---

### Post by deg12 on 2010-05-21
Same problem here. Some with solution would be nice :)

> description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 00:22:43:17:38:1e
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:16 memory:fa9f0000-fa9fffff


---

### Post by deg12 on 2010-05-21
This thread might help. Still checking now, connection seems to be stable.

[http://ubuntuforums.org/showthread.php?t=1476019](http://ubuntuforums.org/showthread.php?t=1476019)

EDIT

Doesn't seems to work... ;(

---

### Post by vancouverite on 2010-05-21
Hi guys,
Check out this bug.  

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348204?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348204?comments=all)

It sure seems like most people are relating this to network load here.  But the bug original filing is rather old.

Does it look like your problems?

I'm going to try a BIOS update and see if that helps me.

Van

---

### Post by heldal on 2010-05-24
It looks like a few issues with wifi drivers were reintroduced with one of the last kernel updates. The latest 2.6.33 or 2.6.34 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) may be a better choice. Fixed the problem for me on a laptop with a 3945 wifi chip.

---

### Post by vancouverite on 2010-05-24
Hi all,
I updated my BIOS 2 days ago and haven't had a problem since.  Appears to have solved my issue.

Again, this is on a Lenovo T400 with the Intel 5300 Wifi Link.

Best of luck.
Van

---

### Post by iceman600 on 2010-07-14
im having the same problem and its kinda annoying... esp when im downloading something. I have a HP pavilion DV5-1150us
and even my ethernet cable soent work... Getting mad on this laptop... Is there a fix for this? 
thanks... 

```
iceman@iceman-HPBUNTU:~$ sudo lshw | grep -B 1 -A 11 Wireless
[sudo] password for iceman: 
           *-network      
                description: Wireless interface
                product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: **secret**
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.0.100 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:33 memory:db600000-db601fff

```

---

### Post by The_Eddster on 2010-07-31
I started having this problem a few days ago. It was working fine until then

HP Pavilion dv9560

---

### Post by iceman600 on 2010-07-31
i switched to sabayon 5.0
now i have no hardwre problems.... its faster and more smooth than ubuntu

---

### Post by diogosales on 2010-08-29
No advance on this issue?

This also happens to me: using lucid, wifi keeps disconnecting! did not happened in older ubuntu versions. it happens when traffic is high, even a mere 200~300Kb/s of traffic load to an ftp on my home network causes wlan interface to go down. saw a couple of threads out in the forums that seem to relate to this, the solution being reverting to older ubuntu versions. is this the only option? i don't know how to check the logs and such so i can find out more about what could be the problem... 

i've grabbed this from log viewer (log: "debug"): [http://ubuntu.pastebin.com/4qCzXU9s](http://ubuntu.pastebin.com/4qCzXU9s)

can someone help? does anyone know anything about this issue?

---

### Post by mabtifro2 on 2012-12-22
did anyone ever find a solution to this problem? ive been using 10.04 for over two years now and ive never had this problem till about one week ago. its so obnoxious, it knocks me offline, then my networks disappear and i have to restart the computer every 15-20 minutes to regain a signal... thanks... btw im using an asus eeepc 1005HA

---

### Post by ram130 on 2012-12-22
Yes.. upgrading to 12.10

---

### Post by overdrank on 2012-12-22
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

