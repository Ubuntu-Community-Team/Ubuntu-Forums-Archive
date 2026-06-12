---
title: "Ubuntu Natty 11.04 Atheros AR5XXX Not working [UNCLAIMED]"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by Sombra on 2011-07-23
I was a happy Ubuntu Maverik user, all hardware stuff working great so far, but a week ago I upgraded my computer and decided to make a go with Natty. From first moment I upgraded the old Maverik distribution, except a few graphic driver bugs all works good enought, but once I upgraded the kernel and cleaned a few packets (mono,ruby etc) my wifi iface vanished. I think then it may be due to a removed packet (maybe a dependency not registered on the network needs) so I intalled ubuntu-desktop and rebooted. My wlan iface continues missing. I thought then the maverick distribution could be full of rubish so downloaded Natty x86_64 and maked a clean install.

To my surprise, with the system just installed, wlan iface still not showed, updated the kernel via ethernet and then I could breath, was there and could connect to a network. But today the iface vanished again, I am puzled because nothing went installed on this days. I hace spent a few hours trying to figure whats the hell is not working. Im stock so decided to ask here, I hope you could help because I think something in the newest wireless stack is broken.

Currently I have compiled and installed the last compat-wireless source from [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)

OK, lets begin:

The main problem is that my card is UNCLAIMED:

**sudo lshw -c network**
```

*-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:03:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:febf0000-febfffff

```

Note the "product" field, I have seen other info around internet all reporting things like "AR5001 Wireless Network Adapter" for example, but never a simply "Atheros Communications Inc." so I think it may be broken.

I cant remember for sure the chip my card is (and dont say nothing in any sticky on the device) but for sure is AR5XXX family so ath5k must take over the devide. But **lsmod | grep ath** shows nothing, I think add to modules the ath5k is not the solution because never need of it. If I load that module manually and check dmesg I get:

**dmesg**
```

[   13.378844] ppdev: user-space parallel port driver
[   15.069330] r8169 0000:02:00.0: eth0: link up
[   15.069703] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   15.471023] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   15.817779] EXT4-fs (sdd1): re-mounted. Opts: errors=remount-ro,commit=0
[   25.430031] eth0: no IPv6 routers present
[   67.218846] cfg80211: Calling CRDA to update world regulatory domain
[   67.245867] cfg80211: World regulatory domain updated:
[   67.245870] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   67.245873] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   67.245875] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   67.245877] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   67.245878] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   67.245880] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```

**dmesg | grep -e ath -e wlan**
```

desktop7@desktop7-desktop:~$ dmesg | grep -e ath -e wlan
[    2.090376] device-mapper: multipath: version 1.2.0 loaded
[    2.090380] device-mapper: multipath round-robin: version 1.0.0 loaded

```

It seems that the kernel does nothing with the card. But its definitely there:

**lspci**
```

..
01:05.0 VGA compatible controller: ATI Technologies Inc 760G [Radeon 3000]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:06.0 Ethernet controller: Atheros Communications Inc. Device ff16 (rev 01)
03:06.1 Serial controller: Atheros Communications Inc. Device ff96 (rev 01)

```

Its strange the system doesnt resolve the card ID, I assure with old kernels he knows exactly what card was. update-pciids is up to date (Downloaded daily snapshot dated 2011-07-14 03:15:06) :S

**modinfo ath5k | egrep 'versi|filen'**
```

filename:       /lib/modules/2.6.38-10-generic/updates/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     1416537BCAC613C038AB6EF
vermagic:       2.6.38-10-generic SMP mod_unload modversions

```

Anyway there are some traces on my system about the iface working, for example:

**cat /etc/udev/rules.d/70-persistent-net.rules**
```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:30:18:a6:62:75", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0013 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:11:bb:b2:52", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

Maybe the pci devideID has change (Im starting to believe in ghosts) or the mac or something?


Im starting to think in burn Natty down in hell and go back to Maverick, I ever update the dist several months after the release, mainly to avoid the path-storm so I get a more mature/stable system. Maybe I should report on launchpad? Please help me to find the failure, I think there is a bug to catch in the wireless stack.

Maybe I should install madwifi drivers, long time ago I used to install those ever, but I prefered to ask here before dirtify my system.

Thanks

---

### Post by chili555 on 2011-07-23
Does it start up if you manually load the module? Does the system complain if you manually load the module?```
sudo modprobe ath5k
```Are there then any informative warnings or errors?```
dmesg | grep ath
```What does this tell us?```
modifo ath5k | grep 0013 
```Thanks.

---

### Post by Sombra on 2011-07-23
@chili555 Thanks to reply

sudo modprobe ath5k goes completely clean, **lsmod | grep ath** shows

```

desktop7@desktop7-desktop:~$ lsmod | grep ath
ath5k                 149295  0 
ath                    23782  1 ath5k
mac80211              308863  1 ath5k
cfg80211              196815  3 ath5k,ath,mac80211

```

dmesg | grep ath print exactly the same output as I pointed before, even after loading the ath5k module manually, its so strange.

**modinfo ath5k | grep 0013**
```

alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*

```

Anyway, you see correct the pcID mismatch between "lspci" and "/etc/udev/rules.d/70-persistent-net.rules"? It looks suspicious to me but maybe its right


Thanks

---

### Post by chili555 on 2011-07-23
Let's have a look at:```
lspci -nn | grep 0280
rfkill list all
```> Anyway, you see correct the pcID mismatch between "lspci" and "/etc/udev/rules.d/70-persistent-net.rules"? It looks suspicious to me but maybe its right
Maybe I am missing something; I don't see a mismatch:> alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="Red"]168C[/COLOR]d0000[COLOR="Red"]0013[/COLOR]sv*sd*bc*sc*i*> # PCI device 0x[COLOR="Red"]168c[/COLOR]:0x[COLOR="Red"]0013[/COLOR] (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:11:bb:b2:52", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

---

### Post by Sombra on 2011-07-23
**lspci -nn | grep 0280** shows nothing im afraid
**rfkill list all** is empty too

```

# PCI device **0x168c:0x0013** (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:11:bb:b2:52", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0" 

```

**lspci -nn**
```

...
8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:06.0 Ethernet controller [0200]: Atheros Communications Inc. Device **[168c:ff16]** (rev 01)
03:06.1 Serial controller [0700]: Atheros Communications Inc. Device **[168c:ff96]** (rev 01)

```

That is the mismatch I was talking about, but as I said maybe its ok, just pointing it :-)

Thanks

---

### Post by chili555 on 2011-07-23
This device is a very unusual wireless device:> Ethernet controller [0200]: Atheros Communications Inc. Device [168c:ff16] (rev 01)The serial controller is not germaine to anything, except it's also manufactured by Atheros.

Looking at udev rules, I'm not sure where 168c:0013 has gone.

I found this: [http://madwifi-project.org/wiki/Compatibility/Sparklan](http://madwifi-project.org/wiki/Compatibility/Sparklan)> WMIA-166AG
Chipset:	AR5414 (802.11a/b/g)
Interface:	miniPCI
Antenna Connector:	2 x U.FL
Device Information:	[COLOR="Red"]168c:ff16[/COLOR] (rev 01)
Notes:	detected as a 5212, all standard functions and modes seem to work with latest svn pull
URL:	[http://www.sparklan.com/products_mini_pci_wmia_166ag.htm](http://www.sparklan.com/products_mini_pci_wmia_166ag.htm)I am Googling to try to work out how to get ath5k to drive it.

---

### Post by Sombra on 2011-07-23
I appreciate so much your efford.

I want to take some considerations:

[LIST=1]
[*]- This is a Dlink GWL520 card, I think is not marginal at all.
[*]- I have passed about 4 ubuntu releases with that card and never get a problem.
[*]- I remember have been driven this card with madwifi in the past, stable at most, monitor mode included, even breaking a bunch WEP keys when I was student.
[*]- It was running 12h ago, how could I get an apt-get log? just to confirm, because Im pretty sure I have not installed amything critical.
[/LIST]

As you can see, like me, there are no errors and no misconfiguration. Simply the iface was not there this morning when I plug the computer. The card still listed in pci hardware and tiling :S

Things that I have to test:
[LIST=1]
[*]- Install an old kernel, Its may be hard, you know, its easy to install new kernels on "old" distributions, but its harder to install old kernels inside "new" ones.
[*]- Get a live of Maverick and check if it works, because Natty has no wifi support during the live session, I maked sense of that.
[*]- Install madwifi-ng, start to blacklisting everithigs and such stuff. I avoided to do that because I wanted to get second opinions before make custom configs, anyway I suspect that installing madwifi's driver only will add another driver thats nos tied to my card :S
[*]- Ndiswrapper, but same considerations as with madwifi driver
[/LIST]

You think I should open a bug in launchpad?
Again, thanks so much

---

### Post by Sombra on 2011-07-23
@chili555

guess what? I have it working again, just changed the card to another PCI socket and restarted. Card worked on a Maverick live so I get mad, and tried unrelated things like that.

**lspci**
```

..
01:05.1 Audio device [0403]: ATI Technologies Inc RS780 Azalia controller [1002:960f]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:05.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)

```

**sudo lshw -c network**
```

*-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:03:05.0
       logical name: wlan0
       version: 01
       serial: 00:1b:11:bb:b2:52
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-10-generic firmware=N/A ip=192.168.1.17 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:febf0000-febfffff

```

As you can see, finally the pciIDs between **lspci** and **/etc/udev/rules.d/70-persistent-net.rules** match again, I was annoyed by that. Somehow the hardware recognition of the kernel failed and match card as other id (dont ask me how). Changing the socket solved my problem, for now. Im still thinking Natty introduce unresolved new flaws in the wireless stack that results in this kind of error.

Anyway thanks a lot for your support and time.

---

### Post by chili555 on 2011-07-23
I'm glad it's working by whatever means. Thanks for posting the solution. I hope it will help a few searchers. It helped me, I thought I had lost my skill and mojo!

---

### Post by terryit3 on 2011-07-25
Nm.

---

### Post by chili555 on 2011-07-25
You can do it with a screwdriver. What he is referring to is moving the network card physically from one PCI slot to another. Please see: [http://computer.howstuffworks.com/pci5.htm](http://computer.howstuffworks.com/pci5.htm)

If your network card is in slot two, for example, move it to slot one. Of course, the computer must be shut down and unplugged.

---

### Post by terryit3 on 2011-07-25
Ok. I am doing this on a Netbook, so I'm not sure I can physically move it.

Thanks

---

### Post by Sombra on 2011-07-25
@chili555

Thanks for explain it correctly. Unfortunatelly the 'Dell mini9' is a laptop, Im afraid terryit3 cant use this method :S

@terryit3

I think the best solution is to install a new kernel, because in the first run the card used to work (but maybe you need a slightly old kernel). I fix it the hard way, I changed the computer physic configuration, this way the kernel get forced to reconfigure all hardware configuration and my card started to work again. Maybe a kernel guru could give you a clean solution, I have been around linux exclusively a bunch of years now but my kernel skills are still somewhat limited.

Good luck!

---

