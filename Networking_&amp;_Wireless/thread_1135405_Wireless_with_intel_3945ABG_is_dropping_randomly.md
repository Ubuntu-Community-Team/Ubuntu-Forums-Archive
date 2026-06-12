---
title: "Wireless with intel 3945ABG is dropping randomly"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by jpjandrade on 2009-04-24
Hey guys,

since I've bought this notebook, HP Pavillion dv6875, and it came with the Intel 3945ABG wireless card, I've been having problems with wireless on Ubuntu. This time, after trying 9.04, I decided I *have* to solve it, because I can take Windows anymore.

So I ask for your help, because this problem is driving me crazy!

What happens is I connect to my home network (it's called "Marcia" for future reference in this thread. My mother's name, just for the curious ou there) and the internet works fine. But after a while, and it's not related to how long I've been connected or how much I've download from what I can tell, the connection just drops. I try to visit any website and it just can't connect. Downloads, torrents, they are all dead, and the network system monitor panel on the gnome just goes dead.

If I'm using the network-manager from gnome, I have to try to connect to some other network, and then choose mine again, and it works. Now I'm using wicd and I just disconnect and reconnect (manually, it won't do it automatically) and it works again. But as you may imagine, it's really annoying.

Oh, and the wireless works just fine in Windows, so I know it's not a problem with my card / my router.

I've also tryed yesterday the following workarounds:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)

but it didn't help. With other Ubuntu releases (8.04 I think), I had tryied using ndiswrapper, but I didn't help (I haven't tryied ndiswrapper with 9.04 because I truly believe it will just be the same).

Below are the terminal outputs that were listed in the sticked topic. If there's anything else you need, please let me know. I really could use some help here.


lspci:

```

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```


iwconfig wlan0

```
wlan0     IEEE 802.11abg  ESSID:"Marcia"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:DF:A8:63:B5   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=63/100  Signal level:-69 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


lsmod
```

iwl3945                97912  0
led_class              12036  1 iwl3945
mac80211              217208  1 iwl3945
cfg80211               38032  2 iwl3945,mac80211
```


dmesg. I just copied and pasted anything that had "iwl3945" or "wlan0" on it, so I don't know if I missed something useful.

Some of the first "wlan0" messages might be useless because I was trying to join a wireless network using the "ndiswrapper" option from wicd, and I don't have ndiswrapper installed in my system. When I switched it back to "wext", it worked "fine". Still dropping, though.


```
[   10.339082] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   10.339191] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.339205] iwl3945 0000:02:00.0: setting latency timer to 64
[   10.339321] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   10.342273] iwl3945 0000:02:00.0: irq 2297 for MSI/MSI-X
[   10.399753] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   10.399764] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.399773] nvidia 0000:01:00.0: setting latency timer to 64
[   10.399939] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels

```
```
[   20.636210] r8169: eth0: link down
[   20.636432] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.282905] Registered led device: iwl-phy0:radio
[   24.282924] Registered led device: iwl-phy0:assoc
[   24.282978] Registered led device: iwl-phy0:RX
[   24.282995] Registered led device: iwl-phy0:TX
[   24.305009] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.367446] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[   27.367463] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   27.368651] wlan0: authenticated
[   27.368654] wlan0: associate with AP 00:1c:df:a8:63:b5
[   27.368657] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[   27.564071] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   32.238799] Registered led device: iwl-phy0:radio
[   32.239781] Registered led device: iwl-phy0:assoc
[   32.239803] Registered led device: iwl-phy0:RX
[   32.239820] Registered led device: iwl-phy0:TX
[   32.260915] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.318256] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[   32.318274] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   32.321572] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[   32.321593] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   32.321599] wlan0: authenticated
[   32.321602] wlan0: associate with AP 00:1c:df:a8:63:b5
[   32.321604] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[   32.524768] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   36.389841] Registered led device: iwl-phy0:radio
[   36.389917] Registered led device: iwl-phy0:assoc
[   36.389935] Registered led device: iwl-phy0:RX
[   36.389951] Registered led device: iwl-phy0:TX
[   36.398199] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.813326] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[   36.813344] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   36.816828] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[   36.816847] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   36.816853] wlan0: authenticated
[   36.816856] wlan0: associate with AP 00:1c:df:a8:63:b5
[   36.816859] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[   37.018856] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   41.173757] Registered led device: iwl-phy0:radio
[   41.173777] Registered led device: iwl-phy0:assoc
[   41.173831] Registered led device: iwl-phy0:RX
[   41.173848] Registered led device: iwl-phy0:TX
[   41.192955] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.336051] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[   41.336070] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   41.337173] wlan0: authenticated
[   41.337177] wlan0: associate with AP 00:1c:df:a8:63:b5
[   41.337180] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[   41.536046] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   51.730024] Registered led device: iwl-phy0:radio
[   51.730299] Registered led device: iwl-phy0:assoc
[   51.737361] Registered led device: iwl-phy0:RX
[   51.737392] Registered led device: iwl-phy0:TX
[   51.746339] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   54.498295] wlan0: direct probe to AP 00:1c:df:a8:63:b5 try 1
[   54.498312] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   54.499654] wlan0 direct probe responded
[   54.499661] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[   54.500848] wlan0: authenticated
[   54.500852] wlan0: associate with AP 00:1c:df:a8:63:b5
[   54.500855] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[   54.696067] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   58.037630] Registered led device: iwl-phy0:radio
[   58.037707] Registered led device: iwl-phy0:assoc
[   58.037739] Registered led device: iwl-phy0:RX
[   58.037769] Registered led device: iwl-phy0:TX
[   58.046585] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   60.821798] mac80211-phy0: failed to set key (0, ff:ff:ff:ff:ff:ff) to hardware (-22)
[   60.822538] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[   60.825244] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[   60.825258] wlan0: authenticated
[   60.825261] wlan0: associate with AP 00:1c:df:a8:63:b5
[   60.830324] wlan0: RX AssocResp from 00:1c:df:a8:63:b5 (capab=0x411 status=0 aid=1)
[   60.830330] wlan0: associated
[   60.832074] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   71.385063] wlan0: no IPv6 routers present
[   82.000151] Clocksource tsc unstable (delta = -71775433 ns)
[ 1162.678574] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[ 1162.678586] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x0209 ser 0x0000004B
[ 1162.680573] iwl3945: Can't stop Rx DMA.
[ 1162.730361] Registered led device: iwl-phy0:radio
[ 1162.730399] Registered led device: iwl-phy0:assoc
[ 1162.730416] Registered led device: iwl-phy0:RX
[ 1162.730432] Registered led device: iwl-phy0:TX
[ 1201.061491] Registered led device: iwl-phy0:radio
[ 1201.061510] Registered led device: iwl-phy0:assoc
[ 1201.061566] Registered led device: iwl-phy0:RX
[ 1201.061582] Registered led device: iwl-phy0:TX
[ 1201.084938] mac80211-phy0: failed to set key (0, ff:ff:ff:ff:ff:ff) to hardware (-22)
[ 1201.092443] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1201.152690] r8169: eth0: link down
[ 1201.152939] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1202.186419] Registered led device: iwl-phy0:radio
[ 1202.186864] Registered led device: iwl-phy0:assoc
[ 1202.192569] Registered led device: iwl-phy0:RX
[ 1202.202533] Registered led device: iwl-phy0:TX
[ 1202.216038] mac80211-phy0: failed to set key (0, ff:ff:ff:ff:ff:ff) to hardware (-22)
[ 1202.217442] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1202.299284] r8169: eth0: link down
[ 1202.300638] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1210.630255] Registered led device: iwl-phy0:radio
[ 1210.630330] Registered led device: iwl-phy0:assoc
[ 1210.630362] Registered led device: iwl-phy0:RX
[ 1210.630393] Registered led device: iwl-phy0:TX
[ 1210.648047] mac80211-phy0: failed to set key (0, ff:ff:ff:ff:ff:ff) to hardware (-22)
[ 1210.649491] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1210.667341] wlan0: deauthenticating by local choice (reason=3)
[ 1210.829708] Registered led device: iwl-phy0:radio
[ 1210.829754] Registered led device: iwl-phy0:assoc
[ 1210.829832] Registered led device: iwl-phy0:RX
[ 1210.829863] Registered led device: iwl-phy0:TX
[ 1210.841596] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1211.987717] Registered led device: iwl-phy0:radio
[ 1211.988175] Registered led device: iwl-phy0:assoc
[ 1212.000396] Registered led device: iwl-phy0:RX
[ 1212.000452] Registered led device: iwl-phy0:TX
[ 1212.015436] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1214.782858] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[ 1214.782879] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1214.783957] wlan0: authenticated
[ 1214.783963] wlan0: associate with AP 00:1c:df:a8:63:b5
[ 1214.783968] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[ 1214.980033] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1215.361846] Registered led device: iwl-phy0:radio
[ 1215.362114] Registered led device: iwl-phy0:assoc
[ 1215.362971] Registered led device: iwl-phy0:RX
[ 1215.362996] Registered led device: iwl-phy0:TX
[ 1215.422368] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1215.492404] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[ 1215.492423] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1215.493498] wlan0: authenticated
[ 1215.493502] wlan0: associate with AP 00:1c:df:a8:63:b5
[ 1215.493504] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[ 1215.692162] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1221.302239] Registered led device: iwl-phy0:radio
[ 1221.302306] Registered led device: iwl-phy0:assoc
[ 1221.302329] Registered led device: iwl-phy0:RX
[ 1221.302351] Registered led device: iwl-phy0:TX
[ 1221.311125] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1224.098576] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[ 1224.098600] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1224.099691] wlan0: authenticated
[ 1224.099696] wlan0: associate with AP 00:1c:df:a8:63:b5
[ 1224.099701] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[ 1224.296034] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1224.638101] Registered led device: iwl-phy0:radio
[ 1224.638392] Registered led device: iwl-phy0:assoc
[ 1224.642300] Registered led device: iwl-phy0:RX
[ 1224.642351] Registered led device: iwl-phy0:TX
[ 1224.657343] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1224.744134] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[ 1224.744151] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1224.746008] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[ 1224.746022] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1224.746028] wlan0: authenticated
[ 1224.746030] wlan0: associate with AP 00:1c:df:a8:63:b5
[ 1224.746033] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[ 1224.944073] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1228.743729] Registered led device: iwl-phy0:radio
[ 1228.744445] Registered led device: iwl-phy0:assoc
[ 1228.744848] Registered led device: iwl-phy0:RX
[ 1228.748671] Registered led device: iwl-phy0:TX
[ 1228.769395] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1231.603035] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[ 1231.603059] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1231.604995] wlan0: authenticated
[ 1231.605003] wlan0: associate with AP 00:1c:df:a8:63:b5
[ 1231.605008] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[ 1231.800034] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1236.746687] Registered led device: iwl-phy0:radio
[ 1236.750266] Registered led device: iwl-phy0:assoc
[ 1236.750314] Registered led device: iwl-phy0:RX
[ 1236.750344] Registered led device: iwl-phy0:TX
[ 1236.768957] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1236.906817] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[ 1236.906841] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1236.908120] wlan0: authenticated
[ 1236.908129] wlan0: associate with AP 00:1c:df:a8:63:b5
[ 1236.908134] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[ 1236.976109] wlan0: authenticate with AP 00:1c:df:a8:63:b5
[ 1236.978779] wlan0: authenticated
[ 1236.978786] wlan0: associate with AP 00:1c:df:a8:63:b5
[ 1236.981276] wlan0: RX AssocResp from 00:1c:df:a8:63:b5 (capab=0x411 status=0 aid=1)
[ 1236.981283] wlan0: associated
[ 1236.984295] mac80211-phy0: failed to set key (0, ff:ff:ff:ff:ff:ff) to hardware (-22)
[ 1236.984584] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1247.164023] wlan0: no IPv6 routers present

```



sudo lshw -C network


```
*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:11:1b:65
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.5 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

```

iwlist scan
("Marcia" is the name of my network)
```
wlan0     Scan completed :
          Cell 01 - Address: 00:1C:DF:A8:63:B5
                    ESSID:"Marcia"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/100  Signal level:-69 dBm  Noise level=-100 dBm
                    Encryption key:on
                    IE: Unknown: 00064D6172636961
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA50050F204104A00011010440001021041000100103B0001031047001000000000000000011000001CDFA863B51021001242656C6B696E20436F72706F726174696F6E102300114E20576972656C65737320526F7574657210240007332E30312E31371042000E31323831303832333330383230391054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020004
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=0000000080d0633f
                    Extra: Last beacon: 32ms ago

```

---

### Post by jpjandrade on 2009-04-24
Any ideas? This problem is getting worser and it's getting quite frustrating.

Thanks!

---

### Post by omelette on 2009-05-03
Hi.  I have a new Jaunty install and also have Intel 3945 in a Dell laptop set up to access a home-network.  My problem is that even as I type this on the laptop, I am happily listening to streaming music via the wireless connection - so I have constant internet access - however, my signal-strength shows zero, even though I am about 2 meters from the internet-connected PC!  Signal is normally showing zero like this but will occasionally shoot up to full strength for a second or so, before vanishing.  I'd pass it off just a 'signal-strength-bug' but for the fact that whereas my max download speed on the inter-connected PC is about 350kBsec, the laptop's connection varies (wildly!) between 5-50kBsec.  But with Windows on the same PC's I was easily getting over 250kBsec on the laptop...

So, my problems aren't as serious as yours, but there is something definitely not working correctly...

---

### Post by mwolfe on 2009-05-04
I started looking at my dmesg output and did some googling. My relavant error messages were:
[   88.353138] wlan1: no IPv6 routers present
[  107.480560] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[  107.480577] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x02EF ser 0x0000004B
[  107.484369] iwl3945: Can't stop Rx DMA.


This appears to be the same (or similar) to this bugzilla report:
[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1955](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1955)

---

### Post by omelette on 2009-05-04
Just had a quick look at my dmsg log - nothing out of the usual that I can see.  What I did notice is that only after about 2 weeks, NetworkManager is creating massive log-files - Syslog is almost 40meg while Syslog.0 is a mammoth 200meg and growing, seems to be updating several times a second!  Anyone know of a way of stopping this?> NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated 
NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed 

---

### Post by mwolfe on 2009-05-05
I was thinking this may be an issue with the kernel being used, so I installed a 2.6.29 kernel (precompiled) and it didnt fix anything. shucks. Maybe if I compile from source? 

I may install ubuntu 8.10 on another partition and see if it has the same problem. I used to have 8.10 installed but that was before I got the new wireless router. With the old router I got occasional disconnects but usually it took an hour or more before that happened. With this one it happens as soon as i start downloading lots of stuff. Starting Firefox when it has a bunch of tabs to load at once will disconnect it every time.

---

### Post by bwolf1 on 2009-05-05
[jpjandrade]("http://ubuntuforums.org/member.php?u=418800"): Any luck fixing the problem. I have the exact same issue with Jaunty and the same nic, too.

thanks,

---

### Post by chili555 on 2009-05-05
> **mwolfe said:**
> I started looking at my dmesg output and did some googling. My relavant error messages were:
[   88.353138] wlan1: no IPv6 routers present
[  107.480560] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[  107.480577] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x02EF ser 0x0000004B
[  107.484369] iwl3945: Can't stop Rx DMA.


This appears to be the same (or similar) to this bugzilla report:
[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1955](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1955)What version of ucode do you have installed?```
locate ucode | grep 3945
```This command should give you:> /lib/firmware/iwlwifi-3945-1.ucode
/lib/firmware/iwlwifi-3945-2.ucode
/lib/firmware/2.6.28-11-generic/lbm-iwlwifi-3945-2.ucodeIf you don't have these, especially 3945-2.ucode, then please install *linux-backports-modules-jaunty*, if you are still running Jaunty.

---

### Post by ubuntologist on 2009-05-06
A very odd problem. I have a variation on this where, initially, no wireless routers are being found despite there being at least 3 in range.

By moving my laptop closer to the nearest wireless router, it suddenly connects and can also see other routers. Afterwards, I can move my laptop anywhere I choose without any connection issues.

I have an IBM ThinkPad R61 with 9.04 dual booting with Windows. Windows hasn't this problem and neither did 8.10 from which I recently upgraded.

Wireless details: -
network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1c:bf:d6:3f:7d
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=192.168.1.4 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

---

### Post by chili555 on 2009-05-06
> By moving my laptop closer to the nearest wireless router, it suddenly connects and can also see other routers. Afterwards, I can move my laptop anywhere I choose without any connection issues.Would you please try, before you move the laptop:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```Does that change the behavior? If so we can make it permanent. If not, the parameter will be missing on reboot.

---

### Post by enza on 2009-05-07
has the same problem as[ jpjandrade  ]("http://ubuntuforums.org/member.php?u=418800")[URL="http://ubuntuforums.org/member.php?u=418800"][COLOR=Black]the tupic maker[/COLOR]
[/URL]

---

### Post by jwwjr on 2009-06-09
> **chili555 said:**
> What version of ucode do you have installed?```
locate ucode | grep 3945
```This command should give you:If you don't have these, especially 3945-2.ucode, then please install *linux-backports-modules-jaunty*, if you are still running Jaunty.

Hello chili555,

Thanks for the helpful suggestion.  I have a Lenovo R61i with the same Intel wireless card, 3945abg - since installing Jaunty, my previously flawless wireless is not connecting with wifi hotspots.

I installed linux-backports-modules-jaunty as you recommended, but when I verify with 'locate ucode | grep 3945' I still do not see the ucode line for the 3945-2.ucode.  Is there some other way to install this, or something else I should be checking?

Thanks

jwwjr

---

### Post by omarly on 2009-08-14
i just updated the driver, this has been a problem for me a dozen times - as well as for others. 

In one of the many posts - couldn't find it now - somebody gives a link to: [http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/) 

I am sure this is the best way - tried others without real break through - because now i can use the swith to take the wifi on/off - and it comes back again! No more reboots large scale, i hope. and i have never had it like this since, i know i svear in churc now, i had ms win in my maschine.

i have tried ubuntu on my lap - on and off for the past year because of Vista, witch sucks, and even thought having win7, because of all the bugs with wifi and my usb 3g modem.

the intel 3945 is extremly buggy with the preload from ubuntu is my experience. its a shame because i think it scares a lot of ppl from converting

think i got it now!

Hope this works for others too!

---

