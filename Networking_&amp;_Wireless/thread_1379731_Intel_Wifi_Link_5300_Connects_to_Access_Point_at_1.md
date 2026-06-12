---
title: "Intel Wifi Link 5300 Connects to Access Point at 1MB/s"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by dmfrey on 2010-01-12
I have built a Mythbuntu frontend on a Zotac Ion (ZOTAC IONITX-F-E Intel Atom 330 (1.6GHz, dual-core) NVIDIA ION Mini ITX Motherboard/CPU Combo)

I replaced the mini-pcie Atheros wireless n card with an Intel Wifi Link 5300.

This card sees a 100% signal from my router.  Encryption is turned of.  It is a concurrent dual band wireless n router from TrendNET.

The card connects to the access point, however, it connects at only 1MB/s.  I cannot ping the router or any device on the network.

Below is the relevant information that I have seen in other posts.  The difference here with this issue is that actually sees the ap and connects to it.  It just can't do anything after that.

uname -rm
```

2.6.31-17-generic-pae i686

```

lspci -n
```

$ lspci -nn
00:00.0 Host bridge [0600]: nVidia Corporation MCP79 Host Bridge [10de:0a82] (rev b1)
00:00.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a88] (rev b1)
00:03.0 ISA bridge [0601]: nVidia Corporation MCP79 LPC Bridge [10de:0aad] (rev b2)
00:03.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0aa4] (rev b1)
00:03.2 SMBus [0c05]: nVidia Corporation MCP79 SMBus [10de:0aa2] (rev b1)
00:03.3 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a89] (rev b1)
00:03.5 Co-processor [0b40]: nVidia Corporation MCP79 Co-processor [10de:0aa3] (rev b1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa5] (rev b1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa6] (rev b1)
00:06.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa7] (rev b1)
00:06.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa9] (rev b1)
00:08.0 Audio device [0403]: nVidia Corporation MCP79 High Definition Audio [10de:0ac0] (rev b1)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Bridge [10de:0aab] (rev b1)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
00:0b.0 IDE interface [0101]: nVidia Corporation MCP79 SATA Controller [10de:0ab4] (rev b1)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac4] (rev b1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0aa0] (rev b1)
00:15.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac6] (rev b1)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
00:17.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
00:18.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
03:00.0 VGA compatible controller [0300]: nVidia Corporation ION VGA [10de:087d] (rev b1)
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection [8086:4235]

```

lshw -C Network
```

  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:01:2e:27:b7:21
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.10.104 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:21 memory:fae7c000-fae7cfff ioport:d080(size=8) memory:fae7e400-fae7e4ff memory:fae7e000-fae7e00f
  *-network
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:6a:6d:44:58
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:febfe000-febfffff

```

lsmod |grep iwlagn
```

iwlagn                109468  0 
iwlcore               113212  1 iwlagn
mac80211              181108  2 iwlagn,iwlcore
cfg80211               93052  3 iwlagn,iwlcore,mac80211

```

dmesg |grep -e wlan -e iwl
```

[    4.560748] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    4.560760] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    4.561891] iwlagn 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
[    4.561904] iwlagn 0000:04:00.0: setting latency timer to 64
[    4.561956] iwlagn 0000:04:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[    4.599712] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    4.599820] iwlagn 0000:04:00.0: irq 30 for MSI/MSI-X
[    4.680455] phy0: Selected rate control algorithm 'iwl-agn-rs'
[    6.253811] iwlagn 0000:04:00.0: firmware: requesting iwlwifi-5000-2.ucode
[    6.270272] iwlagn 0000:04:00.0: loaded firmware version 8.24.2.12
[    6.462894] Registered led device: iwl-phy0::radio
[    6.462955] Registered led device: iwl-phy0::assoc
[    6.463013] Registered led device: iwl-phy0::RX
[    6.463072] Registered led device: iwl-phy0::TX
[    6.491968] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.340811] Registered led device: iwl-phy0::radio
[   14.340853] Registered led device: iwl-phy0::assoc
[   14.340891] Registered led device: iwl-phy0::RX
[   14.340928] Registered led device: iwl-phy0::TX
[   14.361933] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

I have read a number of threads on this forum.  This issue is similar, but not quite the same as the other threads I have seen.

Any help would be greatly appreciated.

---

### Post by adam814 on 2010-01-12
sudo iwconfig wlan0 rate 54M

---

### Post by dmfrey on 2010-01-13
> **adam814 said:**
> sudo iwconfig wlan0 rate 54M

Thank you.

When I do this, it gives me connectivity for a brief time, but it is still very slow.  There still seems to be something going on here.  Also, this is not maintained between reboots.

I might be getting ahead of myself, but this card supports wireless n speeds.  Do you know if those connections are supported? Or am I going to be limited to 54M?

---

### Post by adam814 on 2010-01-13
I don't know, I have an Intel Wifi Link 5100 myself, but I've never bothered with it since I only have a wireless G router anyway.

If you're running Karmic you should have a fairly updated firmware for it.  With Intrepid and Jaunty I had to compile the driver from source (wireless.kernel.org) to get decent performance.  Maybe that would work for you too.

---

### Post by dmfrey on 2010-01-13
Can you describe your experience with the 5100.  When I bought it, I was thinking about the future and the initial research I did indicated it would be fully supported under linux.

After this didn't work, I considered getting a 5100 because it seemed to be more supported.

Thanks.

---

### Post by adam814 on 2010-01-13
Initially I dual-booted Vista and Ubuntu 8.10 on this laptop.  The wifi was (mostly) supported out of the box.  My main complaint was the occasional disconnect and some spam to the system logs since the driver didn't disassociate properly on shutdown.

I ended up installing developer's versions of the driver, which I found ironically to be more stable with my hardware than the version Ubuntu shipped with Jaunty.

I upgraded to Karmic and found the version included stable enough for my needs and haven't bothered with it since.

I haven't tried to use the wireless N features.  In addition to the usual b/g connections the driver also supports monitor mode, packet injection, and lorcon to some extent.  I haven't been able to get it into AP mode, but I haven't really tried that hard.

I've liked it.  I've certainly had less issues than I did with the Atheros chipset in my old laptop (although it had more features, I actually used it as an AP at one point).

I wouldn't jump ship on the 5300 just yet.  Maybe the development drivers from the compat-wireless package will work for you.

---

### Post by dmfrey on 2010-01-13
I have started down the path of compiling the compat driver.

The driver fails to compile on this system and it might be due to the pae version of the linux kernel it is using to be able to address all 4gb of memory I have in there.

I will have to do some more research on why this is failing to compile.  It is funny...for the intel 5000 driver, it throws a warning for a class cast exception, which is the driver that I need.  I will take a look at the code to see if I can fix it.

It isn't the driver that breaks compiling, however.  It is later in the compile process on a different driver that fails.  I should check and see if I can target the make to only do the intel drivers that I required.

---

### Post by adam814 on 2010-01-13
Hmm....there's usually something useful in the error messages.  I think there most likely is a way to target just one driver (you should only need iwlagn after all).

If it doesn't work out for you post your compilation output here and I'll take a look at it.  It shouldn't matter that you're using a PAE kernel since you're building the module on your own machine for that kernel.  What might cause problems is if you don't have the headers for your kernel installed.  Make sure they are with "sudo apt-get install linux-headers-generic-pae"

---

### Post by dmfrey on 2010-01-13
Thanks.

I will make sure the headers are loaded.  I am pretty sure they are, but I will double check.  I don't think I would have gotten as far as I would have if they weren't loaded.  I will check tonight when I get home.

Thanks for your help.

---

### Post by dmfrey on 2010-01-13
Instead of compiling the whole package, I was able to select only the intel driver.

```

./scripts/driver-select iwlwifi

```

This didn't have the compile errors that compiling the whole driver had.

I installed the driver with sudo make install.  Then unloaded the iwlagn with sudo make unload.  I then rebooted.

The same issue still exists: I can see all the available networks around.  I can connect to my access point. I can pull an IP Address.  Afterwards, I can't ping anything on the network.

I ran sudo iwconfig wlan0 rate 54M and disconnected and reconnected.  iwconfig wlan reported 54mb/s, however, I still couldn't ping anything on the network.

Thanks for all your help.

---

### Post by adam814 on 2010-01-13
Hmm...this is puzzling.  Try posting the output of "route -n".

---

### Post by dmfrey on 2010-01-13
Here it is.  Looks ok.

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 wlan0

```

---

### Post by adam814 on 2010-01-13
Yeah, that looks about as good as it gets.  Can you ping your gateway at least?

I suppose it's possible it might not respond to pings on the LAN port, but that would be weird.  If that's the case you might be able to try something like "nslookup google.com 192.168.10.1" to see if it serves DNS.

---

### Post by dmfrey on 2010-01-14
I did a nslookup command and tried to ping the router and other computers on my network.  All of these failed.

Do you know of a version of ubuntu that works with this card.  Or another distro that works.  I want to rule out that it is a hardware issue of some sort.

---

### Post by adam814 on 2010-01-14
I'd think 9.10 would be your best bet as far as Ubuntu goes.  You could always try out a few other distro LiveCDs too, but since it's an in-kernel driver your mileage may vary (since they'll have a very similar kernel).  Maybe you could try out the newest mainline kernel to see if it works there?

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.3/")

Those are missing some of the ubuntu patches (for example AppArmor and nfs-kernel-server won't work with them) and they're more server-optimized than desktop, but it's worth a shot to see if it supports your hardware any better.

Of course whether it works in Windows has always been the de facto hardware failure test.  Short of that there aren't that many free OS that aren't Linux-based that use LiveCDs (I think Dragonfly BSD does).

---

### Post by dmfrey on 2010-01-14
I previously tried a 9.04 livecd with no luck.

I believe I read that 8.10 had support for the chipset, so I downloaded a livecd.  I also downloaded fedora 12 and freebsd.

Tonight, when I get home, I will try to boot them and see what happens.

One question for you about compiling the latest driver.  When I ran the driver select program and if you run it with no driver it gives you a list of supported drivers and driver groups.  I noticed there were two listed with iwlagn.  I selected the second option (iwlwifi), but I am wondering if I should have selected the first option.  What is your opinion on which version of iwlagn I should be using?

---

### Post by adam814 on 2010-01-14
As for which one you should select when compiling the drivers:
I don't think it would matter, as long as iwlagn is getting built.  When I built it I built the entire package of drivers.

As an alternative, I believe you can install the linux-backports-modules-<release> (i.e. linux-backports-modules-intrepid) package and it's supposed to contain a fairly updated set of backported drivers.

---

### Post by dmfrey on 2010-01-14
I tried fedora 12 and had the same result.  FreeBSD wasn't what i was expecting...never really looked at bsd before.

I tried an ubuntu 8.10 live cd and it connected.  iwconfig showed it was connected at 60 mb/s.  However, I still couldn't ping anything on my network.

I am not sure what else to try.  Can you think of any other ideas?

---

### Post by adam814 on 2010-01-14
Yeah, I don't think FreeBSD has a LiveCD or anything like that.  All the BSDs are pretty good for server use, not so great as desktops IMHO.

No luck with the linux-backports-modules-intrepid package?

The last thing I was going to suggest was installing the linux-firmware package from a newer version of Ubuntu, but if it won't work in Fedora 12 I doubt that would help you either (it's probably the same firmware).

I'm down to about 3 possibilities here:
1) firewall gone insane (post your "iptables -L" output, I kinda doubt it's the problem, but worth a shot).
2) Not quite supported by Linux just yet.  Doesn't make a lot of sense since it loads a driver for it and connects, but I guess it's possible.
3) Hardware problem (either facing a LOT of interference, getting weak signal, or outright broken).

Unless someone knows more about it than me I don't know what else to say other than good luck.

---

### Post by changingstate on 2010-01-14
Apologies for the interruption, but I have a slightly crazy idea based on this :
[FONT=monospace]
[/FONT]> [    4.599712] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channelsIn the US, you're only supposed to be able to use 1-11, aren't you?

This stuff is set by the regulatory domain, which is supposed to be set by the AP. 

I'm probably wrong, but it my be worth looking at : [http://linuxwireless.org/en/developers/Regulatory/CRDA](http://linuxwireless.org/en/developers/Regulatory/CRDA)

---

### Post by adam814 on 2010-01-14
Well, that's not stopping it from working in any case.  I get the same message.

---

### Post by changingstate on 2010-01-14
I also saw something very similar when one of the routers in my WDS system blew a gasket and ended up on a different channel, today. 1Mb/s throughput reported and the client couldn't get traffic anywhere, even though it showed as connected. 

I'm probably wrong, as I admit.

---

### Post by adam814 on 2010-01-14
How's your signal strength?  You should be able to check it with "iwconfig wlan0".  For example I'm in the same room as my router and I have a link quality of 70/70 and a signal level of -32dbm.

The reason I ask is if I move to some far away corner the rate usually swaps down to 36MB/s or even 24MB/s.  I suppose if I was really far away it might drop to 1MB/s (the lower the bandwidth the more error tolerant).

---

### Post by dmfrey on 2010-01-15
Here is the output of iptables -L

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

It is the same as on my desktop.

I pulled down the crda package from the repo and set it to US.  I didn't notice any change, however.

I also now just noticed something wrong in the output below.  It appears the firmware is not getting loaded correctly.  It seems to indicate that it is dropping back to lbm-iwlwifi-5000-1.ucode when it wants to be using lbm-iwlwifi-5000-2.ucode. lbm-iwlwifi-5000-2.ucode doesn't exist in /lib/firmware/{kernel}/. It seems to me like this may be part of my problem. 

dmesg |grep -e wlan -e iwl
```

[    4.448758] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    4.448788] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    4.450414] iwlagn 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
[    4.450451] iwlagn 0000:04:00.0: setting latency timer to 64
[    4.450510] iwlagn 0000:04:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[    4.491786] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    4.491900] iwlagn 0000:04:00.0: irq 30 for MSI/MSI-X
[    4.602093] phy0: Selected rate control algorithm 'iwl-agn-rs'
[    4.741261] iwlagn 0000:04:00.0: firmware: requesting lbm-iwlwifi-5000-2.ucode
[    4.756233] iwlagn 0000:04:00.0: lbm-iwlwifi-5000-2.ucode firmware file req failed: -2
[    4.756250] iwlagn 0000:04:00.0: firmware: requesting lbm-iwlwifi-5000-1.ucode
[    4.774467] iwlagn 0000:04:00.0: Loaded firmware lbm-iwlwifi-5000-1.ucode, which is deprecated. Please use API v2 instead.
[    4.774486] iwlagn 0000:04:00.0: loaded firmware version 8.24.2.12
[    4.980901] Registered led device: iwl-phy0::radio
[    4.980962] Registered led device: iwl-phy0::assoc
[    4.981043] Registered led device: iwl-phy0::RX
[    4.981099] Registered led device: iwl-phy0::TX
[    5.018213] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.484095] wlan0: direct probe to AP 00:14:d1:c5:50:c0 (try 1)
[   16.484125] wlan0: deauthenticating from 00:14:d1:c5:50:c0 by local choice (reason=3)
[   16.484408] wlan0: direct probe to AP 00:14:d1:c5:50:c0 (try 1)
[   16.487792] wlan0: direct probe responded
[   16.487805] wlan0: authenticate with AP 00:14:d1:c5:50:c0 (try 1)
[   16.494103] wlan0: authenticated
[   16.494145] wlan0: associate with AP 00:14:d1:c5:50:c0 (try 1)
[   16.497956] wlan0: RX AssocResp from 00:14:d1:c5:50:c0 (capab=0x1 status=0 aid=3)
[   16.497963] wlan0: associated
[   16.499974] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.000017] wlan0: no IPv6 routers present
[30987.544602] wlan0: deauthenticating from 00:14:d1:c5:50:c0 by local choice (reason=3)
[30987.544762] wlan0: deauthenticating from 00:14:d1:c5:50:c0 by local choice (reason=3)
[30987.907810] Registered led device: iwl-phy0::radio
[30987.907856] Registered led device: iwl-phy0::assoc
[30987.907896] Registered led device: iwl-phy0::RX
[30987.907935] Registered led device: iwl-phy0::TX
[30987.928991] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[30991.118676] wlan0: deauthenticating from 00:14:d1:c5:50:c0 by local choice (reason=3)
[30991.132105] wlan0: direct probe to AP 00:14:d1:c5:50:c0 (try 1)
[30991.135821] wlan0: direct probe responded
[30991.135829] wlan0: authenticate with AP 00:14:d1:c5:50:c0 (try 1)
[30991.139930] wlan0: authenticated
[30991.139968] wlan0: associate with AP 00:14:d1:c5:50:c0 (try 1)
[30991.143517] wlan0: RX AssocResp from 00:14:d1:c5:50:c0 (capab=0x1 status=0 aid=3)
[30991.143525] wlan0: associated
[30991.146112] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[31002.048018] wlan0: no IPv6 routers present

```

---

### Post by changingstate on 2010-01-15
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1837686.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1837686.html)

---

### Post by dmfrey on 2010-01-15
thanks, i will give that a shot when i get home tonight.

---

### Post by changingstate on 2010-01-15
If anyone deserves thanks here, it's adam814, not a google jockey like me :)

---

### Post by dmfrey on 2010-01-19
Thanks again for all your help.

Here is what I did.  I pulled the Intel 5300 card out and replaced it with the original Atheros card that came with the zotac board.

I then built the wireless-compat bleeding edge drivers and installed the ath9k driver.  This worked...somewhat.

My wireless router is in my basement.  If I start this box up down there, I can connect to the access point and actually stream HD content from my mythtv to it with no lag.

If I move one floor up, i can't connect to it at all.

So this is where I am at...I don't want to use the Atheros card as it is not really rated for HD content delivery.  I can pick up an Intel 5100 card as that seems to be more supported, but I am afraid I am gonna run into similar issues.

I am also considering a hardware solution.  My Trendnet Router supports WDS and they also make a device that can be a WDS Access Point and a wireless Bridge.  I am thinking this might be the better option.

I also want to state that i don't seem to have trouble accessing wifi in the rest of my house on other devices.  My wife's netbook, for one, has no trouble connection from the locations I have tried.

Any thoughts on these options?

---

