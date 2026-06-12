---
title: "Too many torrent connections &gt; internet disconnects"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by MisterM on 2009-04-28
Hi,

I'm having exactly the same problem as Tampio in the thread [*Too many torrent connections -> internet disconnects*]("/showthread.php?t=570545").
> **Tampio said:**
> Torrents work otherwise just fine, but if there are a couple of those running at full speed, then the internet connection disconnects after a while. It stays on if I set the global connection limit in KTorrent to 30, any more and it will eventually disconnect. Needless to say that makes downloading really slow. Rebooting my ADSL modem gets the connection back up. Same thing happens in Deluge and uTorrent under wine. I don't have any connection problems with BitComet on Windows XP, even if I'm running it on VirtualBox. Any idea what's causing this?

I tried posting there, but the thread appears to be locked. Someone said there that this is due to traffic shaping. I don't think this is the case, since the problem only happens in Ubuntu and not in Windows. If I'm mistaken, could someone please elaborate on how traffic shaping can be the cause of this problem?

I too am running uTorrent under wine and the disconnects seem to be more frequent when I have many torrents downloading at the same time (i.e. many connections). This is really annoying, since uTorrent needs a long time to pick up speed again after a disconnect/reconnect.

Any help would be greatly appreciated.

Thanks!

---

### Post by euphemus on 2009-04-28
I too have just updated to Jaundiced Jack and Transmission for the first time is closing down after 8 seconds - am trying to cut-back my simultaneous connections (8 secs at a time!) Otherwise JJ is really really good (this is the only prob and I've seen a real pick-up in pace)

---

### Post by Bios Element on 2009-04-28
Wouldn't surprise me of your ISP is killing the connection after it hits a certain level.

---

### Post by MisterM on 2009-04-28
> **Bios Element said:**
> Wouldn't surprise me of your ISP is killing the connection after it hits a certain level.

As I mentioned in my first post, this only happens in Ubuntu, never in Windows, therefore I don't think the ISP has anything to do with it.

Also, I forgot to mention that I'm (still) running Intrepid.

---

### Post by kabloink on 2009-04-28
Have you tried Deluge or some other native Linux app to eliminate wine as being part of the problem? 

I use to have a similar problem, but in my case the connections were killing my linksys router.

---

### Post by MisterM on 2009-04-28
> **kabloink said:**
> Have you tried Deluge or some other native Linux app to eliminate wine as being part of the problem?

I haven't tried it, no. But according to Tampio, it's the same.

> **kabloink said:**
> I use to have a similar problem, but in my case the connections were killing my linksys router.

I use my Ubuntu box (the one where uTorrent is running) as a router as well. So, I don't use an external router.

---

### Post by _Narcisse_ on 2009-08-31
Bump ?

I have the same situation here, on both Transmission and Deluge.

---

### Post by Bugs318 on 2009-12-07
This problem is still ongoing in Karmic (64) whether using Ktorrent, deluge, utorrent (on wine), or transmission (or presumably any other torrent software).

Help please!

---

### Post by Bugs318 on 2009-12-15
bump

---

### Post by ApEkV2 on 2009-12-15
I've never torrented in windows, but in linux i do it all the time.
The only time i have had this happen to me was when i maxed out my connection (3mb/640kb) with over 60 peers.

I've read about this in the past and one of the problems was old or cheap routers.
Some problem about them disconnecting the internet for a couple minutes during a heavy torrent.

My guess is some routers have some sort of anti-dos programming that trips after a certain number of connections at a certain bandwidth.

---

### Post by MisterM on 2009-12-16
> **ApEkV2 said:**
> I've never torrented in windows, but in linux i do it all the time.
The only time i have had this happen to me was when i maxed out my connection (3mb/640kb) with over 60 peers.
Indeed, this does not happen when there is a low number of peers connected. However, I frequently have 100+ peer connections active.

> **ApEkV2 said:**
> I've read about this in the past and one of the problems was old or cheap routers.
Some problem about them disconnecting the internet for a couple minutes during a heavy torrent.

My guess is some routers have some sort of anti-dos programming that trips after a certain number of connections at a certain bandwidth.

> **MisterM said:**
> I use my Ubuntu box (the one where uTorrent is running) as a router as well. So, I don't use an external router.

---

### Post by solitaire on 2009-12-16
I've found most "home" Routers can only handle a limtied number of concurrent connections at a time. My router dies if I have over 256 connections (i.e. if i have 3 torrents running with 85 connections each the router can freeze or drop connection).

Think you might have to invest in a better Router/Modem or limit the number of torrents you have running at any one time...

*Note my ISP does NOT do traffic shaping or limit my download speed...

---

### Post by MisterM on 2009-12-16
> **solitaire said:**
> I've found most "home" Routers can only handle a limtied number of concurrent connections at a time. My router dies if I have over 256 connections (i.e. if i have 3 torrents running with 85 connections each the router can freeze or drop connection).

Think you might have to invest in a better Router/Modem or limit the number of torrents you have running at any one time...

*Note my ISP does NOT do traffic shaping or limit my download speed...

I really don't see how I can make myself any more clear. **I do not use an external router**. All my home routing is done through **iptables**, installed on my Ubuntu server. This is the same server that runs uTorrent, and it is also the same server that connects to the internet through PPPoE.

---

### Post by solitaire on 2009-12-16
Sorry I mis-read your posts.....

Are you on Cable or DSL?

What make of card are you using to connect?

It might be a problem/bug with the linux drivers, if the problem is only happening in Linux..

---

### Post by MisterM on 2009-12-16
> **solitaire said:**
> Are you on Cable or DSL?
ADSL

> **solitaire said:**
> What make of card are you using to connect?

It might be a problem/bug with the linux drivers, if the problem is only happening in Linux..

I'm not sure, what make the network card is. I actually have 3 network cards installed in the server. I there an easy way to check this in Ubuntu (intrepid desktop edition)?

---

### Post by solitaire on 2009-12-16
The command ```
lshw
``` or ```
lspci
``` should list all the hardware in your server, look for ones marked "Network controler" 

I'm not sure how ADSL card will be listed...

---

### Post by Linuxforall on 2009-12-16
Windows had a connection limit till Vista which has been removed in 7, OTOH, Linux never had any connection limits and has a super stable and strong TCP base, in my Windows machine, after heavy torrenting and downloading, net would always slow down, never felt that in Linux. I use Transmission and even with multiple connections, I have no slowdowns. I do have logging turned off in my router though.

---

### Post by MisterM on 2009-12-16
This is the card that is connected to the modem:
```
*-network:0
    description: Ethernet interface
    product: NC100 Network Everywhere Fast Ethernet 10/100
    **vendor: ADMtek**
    physical id: 1
    bus info: pci@0000:01:01.0
    logical name: eth1
    version: 11
    serial: 00:c0:26:c3:cb:39
    width: 32 bits
    clock: 33MHz
    capabilities: pm bus_master cap_list ethernet physical
    configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=10.0.2.40 latency=64 maxlatency=128 mingnt=64 module=tulip multicast=yes
```

> **solitaire said:**
> I'm not sure how ADSL card will be listed...
There is no "ADSL card". The connection is made through [PPPoE]("http://en.wikipedia.org/wiki/PPPoE") using an ADSL modem.

---

### Post by MisterM on 2009-12-16
> **Linuxforall said:**
> Windows had a connection limit till Vista which has been removed in 7, OTOH, Linux never had any connection limits and has a super stable and strong TCP base, in my Windows machine, after heavy torrenting and downloading, net would always slow down, never felt that in Linux. I use Transmission and even with multiple connections, I have no slowdowns. I do have logging turned off in my router though.

I'm not completely sure, but I think I had that limit removed when I was still using Windows, or there is no limit to start with in Windows 2003.

I am definitely seeing slowdowns in Linux, when torrent is downloading. I don't know, maybe I *should* try an external router. Maybe the problem is in iptables' routing.

---

### Post by mryanmarkryan on 2009-12-19
I'm having the same symptoms and I'm not using a DSL connection. I use a wireless modem connected to a Time Warner line. I recently bought a new laptop (an HP DV7 model) and put Ubuntu 9.10 on it. When I have Deluge running, I lose my connection periodically and instead of auto re-connecting, I have to manually connect. 

description: Wireless interface
product: AR9285 Wireless Network Adapter (PCI-Express)
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath9k ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11bgn

This is being reported elsewhere for this release of Ubuntu and I'm still searching for a solution..

---

### Post by Bugs318 on 2009-12-23
The disconnect is not a router disconnect - it is the gnome wireless network manager that disconnects from the network (while the router and other computers remain connected).

Then to reconnect requires a reboot as it fails to reconnect to the network until that is done.

Just clarifying.  This is a noted bug that occurs whenever there are two torrents downloading at once.  I am just hoping someone discovers w workaround or that it is fixed in 10.04

---

### Post by Mars73 on 2009-12-26
It happens here as well on my wireless Belkin USB card.
As I googled on this issue (disconnects with heavy network load) it seems the problem was introduced in kernel 2.6.29 and has not gone away.
That explains why it works for me in Windows and also on older Ubuntu images (I believe 8.10 still works).
I have the problem when streaming video to my media center...absolutely no problem with Ubuntu < 8.10, major problem => 9.04.
It's no problem when doing some surfing, mail reading or the occasional MB download, it becomes a problem with heavy or long downloads (or streaming in my case). It's a major pain in the (you know).

---

### Post by Micheal Luttrull on 2009-12-31
> **Bugs318 said:**
> The disconnect is not a router disconnect - it is the gnome wireless network manager that disconnects from the network (while the router and other computers remain connected).

Then to reconnect requires a reboot as it fails to reconnect to the network until that is done.

Just clarifying.  This is a noted bug that occurs whenever there are two torrents downloading at once.  I am just hoping someone discovers w workaround or that it is fixed in 10.04

This is my exact problem and current work around... sad, but until there's a fix I just limit what I'm downloading and reboot when I forget, heh.

---

### Post by jjcobm on 2010-01-03
I have had the same problem, a bug was filed in may 09...

[https://bugs.launchpad.net/bugs/374650](https://bugs.launchpad.net/bugs/374650)

---

### Post by zaphod777 on 2010-01-03
> **jjcobm said:**
> I have had the same problem, a bug was filed in may 09...

[https://bugs.launchpad.net/bugs/374650](https://bugs.launchpad.net/bugs/374650)

If everyone comments on this bug and clicks the link that says it effects them we will most likely get a fix in the next release as it says right now the bug is not assigned to anyone.

---

### Post by MisterM on 2010-01-03
I would just like to point out that my original post in this thread has nothing to do with wireless whatsoever. In my case it is the ADSL connection that gets disconnected. The computer in question doesn't even have a wireless card.

It might be that the two problems are somehow related, but I just wanted to point that out.

---

### Post by adenewton on 2010-01-04
It's worth as many people doing the logs as possible, as outlined in the bug, theyare more likely to make note of the bug log than forum postings.

For me I have bodged a fix by using wicd and limited my torrent download speed to 350k and upload speed to 70k.

This seems to prevent network drops, but it's obviously not the desired fix. Drops still happen for me when i use wicd and torrents at max speed. They also still drop when using network-manager with the speed limits I have imposed on my client (vuze)

I am also going to start contacting some blog sites about the problem and see if I can get a response. At least this way the people that are memebers of 'the planet' etc might start to notice the bug which may bring more help and attention to getting a fix sorted if other people from the community can get involved.

---

### Post by stinger30au on 2010-01-04
do u have a decent router that will handle the traffic, eg a billion 7402LM router will do torrents on its head

---

### Post by zaphod777 on 2010-01-04
> **stinger30au said:**
> do u have a decent router that will handle the traffic, eg a billion 7402LM router will do torrents on its head

Don't have any trouble when I swap my HDD with the one running Win7.

---

### Post by adenewton on 2010-01-04
> **stinger30au said:**
> do u have a decent router that will handle the traffic, eg a billion 7402LM router will do torrents on its head

Other computers in the house including a xubuntu laptop and a Vista laptop all manage to stay connected. Running torrents through the Vista machine has no issues what so ever.

---

### Post by zaphod777 on 2010-01-04
I have even had it disconnect when only running a couple (2) torrents.

---

### Post by zaphod777 on 2010-01-06
Downloading 2 torrents right now and wireless disconected and I had to reboot to get network to reconnect.

Blow is my log from the event

> Jan  6 18:03:03 zaphod kernel: [276466.402554] wlan0: deauthenticated from 00:1d:73:8e:de:98 (Reason: 6)
Jan  6 18:03:05 zaphod kernel: [276468.350266] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 1)
Jan  6 18:03:06 zaphod kernel: [276468.542718] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 2)
Jan  6 18:03:06 zaphod kernel: [276468.740187] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 3)
Jan  6 18:03:06 zaphod kernel: [276468.940174] wlan0: direct probe to AP 00:1d:73:8e:de:98 timed out
Jan  6 18:03:16 zaphod kernel: [276479.309777] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 1)
Jan  6 18:03:17 zaphod kernel: [276479.502548] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 2)
Jan  6 18:03:17 zaphod dhclient: There is already a pid file /var/run/dhclient.pid with pid 21157
Jan  6 18:03:17 zaphod dhclient: killed old client process, removed PID file
Jan  6 18:03:17 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:03:17 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:03:17 zaphod dhclient: All rights reserved.
Jan  6 18:03:17 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:03:17 zaphod dhclient: 
Jan  6 18:03:17 zaphod kernel: [276479.702578] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 3)
Jan  6 18:03:17 zaphod dhclient: Listening on LPF/eth0/00:15:c5:82:50:cc
Jan  6 18:03:17 zaphod dhclient: Sending on   LPF/eth0/00:15:c5:82:50:cc
Jan  6 18:03:17 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:03:17 zaphod dhclient: DHCPRELEASE on eth0 to 192.168.11.1 port 67
Jan  6 18:03:17 zaphod kernel: [276479.902644] wlan0: direct probe to AP 00:1d:73:8e:de:98 timed out
Jan  6 18:03:18 zaphod kernel: [276480.440229] sky2 eth0: disabling interface
Jan  6 18:03:18 zaphod kernel: [276480.452813] sky2 eth0: enabling interface
Jan  6 18:03:18 zaphod kernel: [276480.453885] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  6 18:03:18 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:03:18 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:03:18 zaphod dhclient: All rights reserved.
Jan  6 18:03:18 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:03:18 zaphod dhclient: 
Jan  6 18:03:18 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:03:18 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:03:18 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:03:18 zaphod avahi-daemon[919]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  6 18:03:18 zaphod avahi-daemon[919]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.11.100.
Jan  6 18:03:18 zaphod avahi-daemon[919]: Withdrawing address record for fe80::21d:e0ff:fe35:481d on wlan0.
Jan  6 18:03:18 zaphod avahi-daemon[919]: Withdrawing address record for 192.168.11.100 on wlan0.
Jan  6 18:03:18 zaphod dhclient: DHCPRELEASE on wlan0 to 192.168.11.1 port 67
Jan  6 18:03:18 zaphod dhclient: send_packet: Network is unreachable
Jan  6 18:03:18 zaphod dhclient: send_packet: please consult README file regarding broadcast address.
Jan  6 18:03:18 zaphod kernel: [276481.218378] Registered led device: iwl-phy0::radio
Jan  6 18:03:18 zaphod kernel: [276481.218424] Registered led device: iwl-phy0::assoc
Jan  6 18:03:18 zaphod kernel: [276481.218468] Registered led device: iwl-phy0::RX
Jan  6 18:03:18 zaphod kernel: [276481.218506] Registered led device: iwl-phy0::TX
Jan  6 18:03:18 zaphod kernel: [276481.308667] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  6 18:03:18 zaphod kernel: [276481.373162] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 1)
Jan  6 18:03:19 zaphod kernel: [276481.570180] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 2)
Jan  6 18:03:19 zaphod kernel: [276481.657978] wlan0: direct probe responded
Jan  6 18:03:19 zaphod kernel: [276481.657989] wlan0: authenticate with AP 00:1d:73:8e:de:98 (try 1)
Jan  6 18:03:19 zaphod kernel: [276481.716577] wlan0: authenticated
Jan  6 18:03:19 zaphod kernel: [276481.716631] wlan0: associate with AP 00:1d:73:8e:de:98 (try 1)
Jan  6 18:03:19 zaphod kernel: [276481.774477] wlan0: RX ReassocResp from 00:1d:73:8e:de:98 (capab=0x431 status=0 aid=1)
Jan  6 18:03:19 zaphod kernel: [276481.774486] wlan0: associated
Jan  6 18:03:19 zaphod kernel: [276481.880227] wlan0: deauthenticating from 00:1d:73:8e:de:98 by local choice (reason=3)
Jan  6 18:03:19 zaphod kernel: [276481.880364] wlan0: deauthenticating from 00:1d:73:8e:de:98 by local choice (reason=3)
Jan  6 18:03:19 zaphod kernel: [276481.880427] ------------[ cut here ]------------
Jan  6 18:03:19 zaphod kernel: [276481.880476] WARNING: at /build/buildd/linux-backports-modules-2.6.31-2.6.31/debian/build/build-generic/compat-wireless-2.6/net/wireless/mlme.c:96 cfg80211_send_rx_assoc+0x190/0x250 [cfg80211]()
Jan  6 18:03:19 zaphod kernel: [276481.880485] Hardware name: XPS M1530                       
Jan  6 18:03:19 zaphod kernel: [276481.880490] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage cbc cryptd aes_x86_64 aes_generic binfmt_misc ppdev bridge stp bnep vboxnetadp vboxnetflt vboxdrv dm_crypt joydev snd_hda_codec_idt arc4 ecb iwlagn iwlcore mac80211 lp parport sdhci_pci sdhci led_class snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss iptable_filter uvcvideo videodev v4l1_compat v4l2_compat_ioctl32 ip_tables x_tables dell_wmi snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device btusb nvidia(P) dell_laptop dcdbas psmouse serio_raw cfg80211 snd soundcore snd_page_alloc usbhid dm_raid45 xor ohci1394 sky2 ieee1394 video output intel_agp
Jan  6 18:03:19 zaphod kernel: [276481.880610] Pid: 834, comm: phy0 Tainted: P   M    W  2.6.31-16-generic #53-Ubuntu
Jan  6 18:03:19 zaphod kernel: [276481.880616] Call Trace:
Jan  6 18:03:19 zaphod kernel: [276481.880634]  [<ffffffff8105e788>] warn_slowpath_common+0x78/0xb0
Jan  6 18:03:19 zaphod kernel: [276481.880644]  [<ffffffff8105e7cf>] warn_slowpath_null+0xf/0x20
Jan  6 18:03:19 zaphod kernel: [276481.880669]  [<ffffffffa00b43a0>] cfg80211_send_rx_assoc+0x190/0x250 [cfg80211]
Jan  6 18:03:19 zaphod kernel: [276481.880766]  [<ffffffffa0c21cd9>] ieee80211_sta_work+0x329/0x10e0 [mac80211]
Jan  6 18:03:19 zaphod kernel: [276481.880777]  [<ffffffff8101062b>] ? __switch_to+0xcb/0x370
Jan  6 18:03:19 zaphod kernel: [276481.880785]  [<ffffffff8104f135>] ? finish_task_switch+0x65/0x120
Jan  6 18:03:19 zaphod kernel: [276481.880814]  [<ffffffffa0c219b0>] ? ieee80211_sta_work+0x0/0x10e0 [mac80211]
Jan  6 18:03:19 zaphod kernel: [276481.880825]  [<ffffffff810737a5>] run_workqueue+0x95/0x170
Jan  6 18:03:19 zaphod kernel: [276481.880834]  [<ffffffff81073924>] worker_thread+0xa4/0x120
Jan  6 18:03:19 zaphod kernel: [276481.880843]  [<ffffffff81078b30>] ? autoremove_wake_function+0x0/0x40
Jan  6 18:03:19 zaphod kernel: [276481.880851]  [<ffffffff81073880>] ? worker_thread+0x0/0x120
Jan  6 18:03:19 zaphod kernel: [276481.880859]  [<ffffffff81078746>] kthread+0xa6/0xb0
Jan  6 18:03:19 zaphod kernel: [276481.880868]  [<ffffffff810130ea>] child_rip+0xa/0x20
Jan  6 18:03:19 zaphod kernel: [276481.880876]  [<ffffffff810786a0>] ? kthread+0x0/0xb0
Jan  6 18:03:19 zaphod kernel: [276481.880883]  [<ffffffff810130e0>] ? child_rip+0x0/0x20
Jan  6 18:03:19 zaphod kernel: [276481.880889] ---[ end trace 9feee2fc4ed2868e ]---
Jan  6 18:03:19 zaphod kernel: [276481.880933] ------------[ cut here ]------------
Jan  6 18:03:19 zaphod kernel: [276481.880959] WARNING: at /build/buildd/linux-backports-modules-2.6.31-2.6.31/debian/build/build-generic/compat-wireless-2.6/net/wireless/sme.c:417 __cfg80211_connect_result+0x350/0x3c0 [cfg80211]()
Jan  6 18:03:19 zaphod kernel: [276481.880966] Hardware name: XPS M1530                       
Jan  6 18:03:19 zaphod kernel: [276481.880970] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage cbc cryptd aes_x86_64 aes_generic binfmt_misc ppdev bridge stp bnep vboxnetadp vboxnetflt vboxdrv dm_crypt joydev snd_hda_codec_idt arc4 ecb iwlagn iwlcore mac80211 lp parport sdhci_pci sdhci led_class snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss iptable_filter uvcvideo videodev v4l1_compat v4l2_compat_ioctl32 ip_tables x_tables dell_wmi snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device btusb nvidia(P) dell_laptop dcdbas psmouse serio_raw cfg80211 snd soundcore snd_page_alloc usbhid dm_raid45 xor ohci1394 sky2 ieee1394 video output intel_agp
Jan  6 18:03:19 zaphod kernel: [276481.881085] Pid: 834, comm: phy0 Tainted: P   M    W  2.6.31-16-generic #53-Ubuntu
Jan  6 18:03:19 zaphod kernel: [276481.881090] Call Trace:
Jan  6 18:03:19 zaphod kernel: [276481.881101]  [<ffffffff8105e788>] warn_slowpath_common+0x78/0xb0
Jan  6 18:03:19 zaphod kernel: [276481.881110]  [<ffffffff8105e7cf>] warn_slowpath_null+0xf/0x20
Jan  6 18:03:19 zaphod kernel: [276481.881134]  [<ffffffffa00b6eb0>] __cfg80211_connect_result+0x350/0x3c0 [cfg80211]
Jan  6 18:03:19 zaphod kernel: [276481.881143]  [<ffffffff810160d0>] ? show_trace+0x10/0x20
Jan  6 18:03:19 zaphod kernel: [276481.881168]  [<ffffffffa00b440d>] cfg80211_send_rx_assoc+0x1fd/0x250 [cfg80211]
Jan  6 18:03:19 zaphod kernel: [276481.881197]  [<ffffffffa0c21cd9>] ieee80211_sta_work+0x329/0x10e0 [mac80211]
Jan  6 18:03:19 zaphod kernel: [276481.881207]  [<ffffffff8101062b>] ? __switch_to+0xcb/0x370
Jan  6 18:03:19 zaphod kernel: [276481.881215]  [<ffffffff8104f135>] ? finish_task_switch+0x65/0x120
Jan  6 18:03:19 zaphod kernel: [276481.881243]  [<ffffffffa0c219b0>] ? ieee80211_sta_work+0x0/0x10e0 [mac80211]
Jan  6 18:03:19 zaphod kernel: [276481.881253]  [<ffffffff810737a5>] run_workqueue+0x95/0x170
Jan  6 18:03:19 zaphod kernel: [276481.881262]  [<ffffffff81073924>] worker_thread+0xa4/0x120
Jan  6 18:03:19 zaphod kernel: [276481.881270]  [<ffffffff81078b30>] ? autoremove_wake_function+0x0/0x40
Jan  6 18:03:19 zaphod kernel: [276481.881279]  [<ffffffff81073880>] ? worker_thread+0x0/0x120
Jan  6 18:03:19 zaphod kernel: [276481.881286]  [<ffffffff81078746>] kthread+0xa6/0xb0
Jan  6 18:03:19 zaphod kernel: [276481.881294]  [<ffffffff810130ea>] child_rip+0xa/0x20
Jan  6 18:03:19 zaphod kernel: [276481.881302]  [<ffffffff810786a0>] ? kthread+0x0/0xb0
Jan  6 18:03:19 zaphod kernel: [276481.881308]  [<ffffffff810130e0>] ? child_rip+0x0/0x20
Jan  6 18:03:19 zaphod kernel: [276481.881314] ---[ end trace 9feee2fc4ed2868f ]---
Jan  6 18:03:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:03:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:03:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4585)
Jan  6 18:03:55 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:03:55 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:03:55 zaphod dhclient: All rights reserved.
Jan  6 18:03:55 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:03:55 zaphod dhclient: 
Jan  6 18:03:55 zaphod kernel: [276517.976872] Registered led device: iwl-phy0::radio
Jan  6 18:03:55 zaphod kernel: [276517.976920] Registered led device: iwl-phy0::assoc
Jan  6 18:03:55 zaphod kernel: [276517.976962] Registered led device: iwl-phy0::RX
Jan  6 18:03:55 zaphod kernel: [276517.977002] Registered led device: iwl-phy0::TX
Jan  6 18:03:55 zaphod kernel: [276518.048517] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  6 18:03:56 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:03:56 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:03:56 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:03:59 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jan  6 18:04:04 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jan  6 18:04:13 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Jan  6 18:04:27 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jan  6 18:04:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:04:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:04:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4586)
Jan  6 18:04:42 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jan  6 18:04:50 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Jan  6 18:05:00 zaphod dhclient: No DHCPOFFERS received.
Jan  6 18:05:00 zaphod dhclient: No working leases in persistent database - sleeping.
Jan  6 18:05:00 zaphod avahi-autoipd(wlan0)[9817]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jan  6 18:05:00 zaphod avahi-autoipd(wlan0)[9817]: Successfully called chroot().
Jan  6 18:05:00 zaphod avahi-autoipd(wlan0)[9817]: Successfully dropped root privileges.
Jan  6 18:05:00 zaphod avahi-autoipd(wlan0)[9817]: Starting with address 169.254.5.46
Jan  6 18:05:05 zaphod avahi-autoipd(wlan0)[9817]: Callout BIND, address 169.254.5.46 on interface wlan0
Jan  6 18:05:06 zaphod avahi-daemon[919]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.5.46.
Jan  6 18:05:06 zaphod avahi-daemon[919]: New relevant interface wlan0.IPv4 for mDNS.
Jan  6 18:05:06 zaphod avahi-daemon[919]: Registering new address record for 169.254.5.46 on wlan0.IPv4.
Jan  6 18:05:09 zaphod avahi-autoipd(wlan0)[9817]: Successfully claimed IP address 169.254.5.46
Jan  6 18:05:16 zaphod dhclient: There is already a pid file /var/run/dhclient.pid with pid 9838
Jan  6 18:05:16 zaphod dhclient: killed old client process, removed PID file
Jan  6 18:05:16 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:05:16 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:05:16 zaphod dhclient: All rights reserved.
Jan  6 18:05:16 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:05:16 zaphod dhclient: 
Jan  6 18:05:16 zaphod dhclient: Listening on LPF/eth0/00:15:c5:82:50:cc
Jan  6 18:05:16 zaphod dhclient: Sending on   LPF/eth0/00:15:c5:82:50:cc
Jan  6 18:05:16 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:05:16 zaphod dhclient: DHCPRELEASE on eth0 to 192.168.11.1 port 67
Jan  6 18:05:16 zaphod dhclient: send_packet: Network is unreachable
Jan  6 18:05:16 zaphod dhclient: send_packet: please consult README file regarding broadcast address.
Jan  6 18:05:16 zaphod kernel: [276598.710112] sky2 eth0: disabling interface
Jan  6 18:05:16 zaphod kernel: [276598.722658] sky2 eth0: enabling interface
Jan  6 18:05:16 zaphod kernel: [276598.723066] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  6 18:05:16 zaphod avahi-autoipd(wlan0)[9817]: SIOCSIFFLAGS failed: Permission denied
Jan  6 18:05:16 zaphod avahi-autoipd(wlan0)[9817]: Callout STOP, address 169.254.5.46 on interface wlan0
Jan  6 18:05:16 zaphod avahi-daemon[919]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  6 18:05:16 zaphod avahi-daemon[919]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.5.46.
Jan  6 18:05:16 zaphod avahi-daemon[919]: Withdrawing address record for 169.254.5.46 on wlan0.
Jan  6 18:05:16 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:05:16 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:05:16 zaphod dhclient: All rights reserved.
Jan  6 18:05:16 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:05:16 zaphod dhclient: 
Jan  6 18:05:16 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:05:16 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:05:16 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:05:16 zaphod dhclient: DHCPRELEASE on wlan0 to 192.168.11.1 port 67
Jan  6 18:05:16 zaphod dhclient: send_packet: Network is unreachable
Jan  6 18:05:16 zaphod dhclient: send_packet: please consult README file regarding broadcast address.
Jan  6 18:05:16 zaphod kernel: [276599.299095] Registered led device: iwl-phy0::radio
Jan  6 18:05:16 zaphod kernel: [276599.299140] Registered led device: iwl-phy0::assoc
Jan  6 18:05:16 zaphod kernel: [276599.299185] Registered led device: iwl-phy0::RX
Jan  6 18:05:16 zaphod kernel: [276599.299225] Registered led device: iwl-phy0::TX
Jan  6 18:05:16 zaphod kernel: [276599.371516] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  6 18:05:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:05:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:05:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4587)
Jan  6 18:05:52 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:05:52 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:05:52 zaphod dhclient: All rights reserved.
Jan  6 18:05:52 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:05:52 zaphod dhclient: 
Jan  6 18:05:52 zaphod kernel: [276635.209363] Registered led device: iwl-phy0::radio
Jan  6 18:05:52 zaphod kernel: [276635.209408] Registered led device: iwl-phy0::assoc
Jan  6 18:05:52 zaphod kernel: [276635.209454] Registered led device: iwl-phy0::RX
Jan  6 18:05:52 zaphod kernel: [276635.209505] Registered led device: iwl-phy0::TX
Jan  6 18:05:52 zaphod kernel: [276635.268462] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  6 18:05:53 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:05:53 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:05:53 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:05:56 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jan  6 18:06:04 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Jan  6 18:06:15 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Jan  6 18:06:31 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Jan  6 18:06:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:06:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:06:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4588)
Jan  6 18:06:41 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jan  6 18:06:48 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jan  6 18:06:56 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
Jan  6 18:06:57 zaphod dhclient: No DHCPOFFERS received.
Jan  6 18:06:57 zaphod dhclient: No working leases in persistent database - sleeping.
Jan  6 18:06:57 zaphod avahi-autoipd(wlan0)[10195]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jan  6 18:06:57 zaphod avahi-autoipd(wlan0)[10195]: Successfully called chroot().
Jan  6 18:06:57 zaphod avahi-autoipd(wlan0)[10195]: Successfully dropped root privileges.
Jan  6 18:06:57 zaphod avahi-autoipd(wlan0)[10195]: Starting with address 169.254.5.46
Jan  6 18:07:03 zaphod avahi-autoipd(wlan0)[10195]: Callout BIND, address 169.254.5.46 on interface wlan0
Jan  6 18:07:03 zaphod avahi-daemon[919]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.5.46.
Jan  6 18:07:03 zaphod avahi-daemon[919]: New relevant interface wlan0.IPv4 for mDNS.
Jan  6 18:07:03 zaphod avahi-daemon[919]: Registering new address record for 169.254.5.46 on wlan0.IPv4.
Jan  6 18:07:07 zaphod avahi-autoipd(wlan0)[10195]: Successfully claimed IP address 169.254.5.46
Jan  6 18:07:10 zaphod dhclient: There is already a pid file /var/run/dhclient.pid with pid 10217
Jan  6 18:07:10 zaphod dhclient: killed old client process, removed PID file
Jan  6 18:07:10 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:07:10 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:07:10 zaphod dhclient: All rights reserved.
Jan  6 18:07:10 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:07:10 zaphod dhclient: 
Jan  6 18:07:10 zaphod dhclient: Listening on LPF/eth0/00:15:c5:82:50:cc
Jan  6 18:07:10 zaphod dhclient: Sending on   LPF/eth0/00:15:c5:82:50:cc
Jan  6 18:07:10 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:07:10 zaphod dhclient: DHCPRELEASE on eth0 to 192.168.11.1 port 67
Jan  6 18:07:10 zaphod dhclient: send_packet: Network is unreachable
Jan  6 18:07:10 zaphod dhclient: send_packet: please consult README file regarding broadcast address.
Jan  6 18:07:10 zaphod kernel: [276712.672714] sky2 eth0: disabling interface
Jan  6 18:07:10 zaphod kernel: [276712.685279] sky2 eth0: enabling interface
Jan  6 18:07:10 zaphod kernel: [276712.686362] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  6 18:07:10 zaphod avahi-daemon[919]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  6 18:07:10 zaphod avahi-daemon[919]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.5.46.
Jan  6 18:07:10 zaphod avahi-daemon[919]: Withdrawing address record for 169.254.5.46 on wlan0.
Jan  6 18:07:10 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:07:10 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:07:10 zaphod dhclient: All rights reserved.
Jan  6 18:07:10 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:07:10 zaphod dhclient: 
Jan  6 18:07:10 zaphod avahi-autoipd(wlan0)[10195]: SIOCSIFFLAGS failed: Permission denied
Jan  6 18:07:10 zaphod avahi-autoipd(wlan0)[10195]: Callout STOP, address 169.254.5.46 on interface wlan0
Jan  6 18:07:10 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:07:10 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:07:10 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:07:10 zaphod dhclient: DHCPRELEASE on wlan0 to 192.168.11.1 port 67
Jan  6 18:07:10 zaphod dhclient: send_packet: Network is unreachable
Jan  6 18:07:10 zaphod dhclient: send_packet: please consult README file regarding broadcast address.
Jan  6 18:07:10 zaphod kernel: [276713.246639] Registered led device: iwl-phy0::radio
Jan  6 18:07:10 zaphod kernel: [276713.246684] Registered led device: iwl-phy0::assoc
Jan  6 18:07:10 zaphod kernel: [276713.246727] Registered led device: iwl-phy0::RX
Jan  6 18:07:10 zaphod kernel: [276713.246766] Registered led device: iwl-phy0::TX
Jan  6 18:07:10 zaphod kernel: [276713.318465] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  6 18:07:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:07:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:07:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4589)
Jan  6 18:07:46 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:07:46 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:07:46 zaphod dhclient: All rights reserved.
Jan  6 18:07:46 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:07:46 zaphod dhclient: 
Jan  6 18:07:46 zaphod kernel: [276749.207567] Registered led device: iwl-phy0::radio
Jan  6 18:07:46 zaphod kernel: [276749.207610] Registered led device: iwl-phy0::assoc
Jan  6 18:07:46 zaphod kernel: [276749.207652] Registered led device: iwl-phy0::RX
Jan  6 18:07:46 zaphod kernel: [276749.207691] Registered led device: iwl-phy0::TX
Jan  6 18:07:46 zaphod kernel: [276749.268517] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  6 18:07:47 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:07:47 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:07:47 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:07:49 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jan  6 18:07:54 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Jan  6 18:08:04 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jan  6 18:08:17 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jan  6 18:08:32 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Jan  6 18:08:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:08:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:08:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4590)
Jan  6 18:08:49 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
Jan  6 18:08:50 zaphod dhclient: No DHCPOFFERS received.
Jan  6 18:08:50 zaphod dhclient: No working leases in persistent database - sleeping.
Jan  6 18:08:50 zaphod avahi-autoipd(wlan0)[10569]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jan  6 18:08:50 zaphod avahi-autoipd(wlan0)[10569]: Successfully called chroot().
Jan  6 18:08:50 zaphod avahi-autoipd(wlan0)[10569]: Successfully dropped root privileges.
Jan  6 18:08:50 zaphod avahi-autoipd(wlan0)[10569]: Starting with address 169.254.5.46
Jan  6 18:08:55 zaphod avahi-autoipd(wlan0)[10569]: Callout BIND, address 169.254.5.46 on interface wlan0
Jan  6 18:08:55 zaphod avahi-daemon[919]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.5.46.
Jan  6 18:08:55 zaphod avahi-daemon[919]: New relevant interface wlan0.IPv4 for mDNS.
Jan  6 18:08:55 zaphod avahi-daemon[919]: Registering new address record for 169.254.5.46 on wlan0.IPv4.
Jan  6 18:08:59 zaphod avahi-autoipd(wlan0)[10569]: Successfully claimed IP address 169.254.5.46
Jan  6 18:09:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:09:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:09:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4591)
Jan  6 18:10:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:10:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:10:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4592)
Jan  6 18:11:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:11:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:11:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4593)
Jan  6 18:12:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:12:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:12:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4594)
Jan  6 18:13:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:13:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:13:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4595)
Jan  6 18:13:43 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jan  6 18:13:48 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jan  6 18:13:53 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Jan  6 18:13:59 zaphod dhclient: There is already a pid file /var/run/dhclient.pid with pid 10589
Jan  6 18:13:59 zaphod dhclient: killed old client process, removed PID file
Jan  6 18:13:59 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:13:59 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:13:59 zaphod dhclient: All rights reserved.
Jan  6 18:13:59 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:13:59 zaphod dhclient: 
Jan  6 18:13:59 zaphod dhclient: Listening on LPF/eth0/00:15:c5:82:50:cc
Jan  6 18:13:59 zaphod dhclient: Sending on   LPF/eth0/00:15:c5:82:50:cc
Jan  6 18:13:59 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:13:59 zaphod dhclient: DHCPRELEASE on eth0 to 192.168.11.1 port 67
Jan  6 18:13:59 zaphod dhclient: send_packet: Network is unreachable
Jan  6 18:13:59 zaphod dhclient: send_packet: please consult README file regarding broadcast address.
Jan  6 18:13:59 zaphod kernel: [277121.750197] sky2 eth0: disabling interface
Jan  6 18:13:59 zaphod kernel: [277121.762707] sky2 eth0: enabling interface
Jan  6 18:13:59 zaphod kernel: [277121.763778] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  6 18:13:59 zaphod avahi-autoipd(wlan0)[10569]: SIOCSIFFLAGS failed: Permission denied
Jan  6 18:13:59 zaphod avahi-autoipd(wlan0)[10569]: Callout STOP, address 169.254.5.46 on interface wlan0
Jan  6 18:13:59 zaphod avahi-daemon[919]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  6 18:13:59 zaphod avahi-daemon[919]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.5.46.
Jan  6 18:13:59 zaphod avahi-daemon[919]: Withdrawing address record for 169.254.5.46 on wlan0.
Jan  6 18:13:59 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:13:59 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:13:59 zaphod dhclient: All rights reserved.
Jan  6 18:13:59 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:13:59 zaphod dhclient: 
Jan  6 18:13:59 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:13:59 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:13:59 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:13:59 zaphod dhclient: DHCPRELEASE on wlan0 to 192.168.11.1 port 67
Jan  6 18:13:59 zaphod dhclient: send_packet: Network is unreachable
Jan  6 18:13:59 zaphod dhclient: send_packet: please consult README file regarding broadcast address.
Jan  6 18:13:59 zaphod kernel: [277122.376658] Registered led device: iwl-phy0::radio
Jan  6 18:13:59 zaphod kernel: [277122.376703] Registered led device: iwl-phy0::assoc
Jan  6 18:13:59 zaphod kernel: [277122.376746] Registered led device: iwl-phy0::RX
Jan  6 18:13:59 zaphod kernel: [277122.376787] Registered led device: iwl-phy0::TX
Jan  6 18:14:00 zaphod kernel: [277122.450078] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  6 18:14:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:14:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:14:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4596)
Jan  6 18:14:35 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:14:35 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:14:35 zaphod dhclient: All rights reserved.
Jan  6 18:14:35 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:14:35 zaphod dhclient: 
Jan  6 18:14:35 zaphod kernel: [277158.316877] Registered led device: iwl-phy0::radio
Jan  6 18:14:35 zaphod kernel: [277158.316906] Registered led device: iwl-phy0::assoc
Jan  6 18:14:35 zaphod kernel: [277158.316933] Registered led device: iwl-phy0::RX
Jan  6 18:14:35 zaphod kernel: [277158.316957] Registered led device: iwl-phy0::TX
Jan  6 18:14:35 zaphod kernel: [277158.368463] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  6 18:14:36 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:14:36 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:14:36 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:14:39 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jan  6 18:14:44 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jan  6 18:14:53 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jan  6 18:15:02 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jan  6 18:15:15 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Jan  6 18:15:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:15:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:15:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4597)
Jan  6 18:15:35 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jan  6 18:15:40 zaphod dhclient: No DHCPOFFERS received.
Jan  6 18:15:40 zaphod dhclient: No working leases in persistent database - sleeping.
Jan  6 18:15:40 zaphod avahi-autoipd(wlan0)[11598]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jan  6 18:15:40 zaphod avahi-autoipd(wlan0)[11598]: Successfully called chroot().
Jan  6 18:15:40 zaphod avahi-autoipd(wlan0)[11598]: Successfully dropped root privileges.
Jan  6 18:15:40 zaphod avahi-autoipd(wlan0)[11598]: Starting with address 169.254.5.46
Jan  6 18:15:45 zaphod avahi-autoipd(wlan0)[11598]: Callout BIND, address 169.254.5.46 on interface wlan0
Jan  6 18:15:45 zaphod avahi-daemon[919]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.5.46.
Jan  6 18:15:45 zaphod avahi-daemon[919]: New relevant interface wlan0.IPv4 for mDNS.
Jan  6 18:15:45 zaphod avahi-daemon[919]: Registering new address record for 169.254.5.46 on wlan0.IPv4.
Jan  6 18:15:49 zaphod avahi-autoipd(wlan0)[11598]: Successfully claimed IP address 169.254.5.46
Jan  6 18:16:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:16:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:16:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4598)
Jan  6 18:17:02 zaphod CRON[11782]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  6 18:17:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:17:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:17:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4599)
Jan  6 18:18:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:18:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:18:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4600)
Jan  6 18:19:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:19:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:19:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4601)
Jan  6 18:19:39 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jan  6 18:19:47 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jan  6 18:20:02 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Jan  6 18:20:13 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jan  6 18:20:26 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Jan  6 18:20:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:20:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:20:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4602)
Jan  6 18:20:40 zaphod dhclient: No DHCPOFFERS received.
Jan  6 18:20:40 zaphod dhclient: No working leases in persistent database - sleeping.
Jan  6 18:20:48 zaphod dhclient: There is already a pid file /var/run/dhclient.pid with pid 11618
Jan  6 18:20:48 zaphod dhclient: killed old client process, removed PID file
Jan  6 18:20:48 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:20:48 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:20:48 zaphod dhclient: All rights reserved.
Jan  6 18:20:48 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:20:48 zaphod dhclient: 
Jan  6 18:20:48 zaphod dhclient: Listening on LPF/eth0/00:15:c5:82:50:cc
Jan  6 18:20:48 zaphod dhclient: Sending on   LPF/eth0/00:15:c5:82:50:cc
Jan  6 18:20:48 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:20:48 zaphod dhclient: DHCPRELEASE on eth0 to 192.168.11.1 port 67
Jan  6 18:20:48 zaphod dhclient: send_packet: Network is unreachable
Jan  6 18:20:48 zaphod dhclient: send_packet: please consult README file regarding broadcast address.
Jan  6 18:20:48 zaphod kernel: [277530.692714] sky2 eth0: disabling interface
Jan  6 18:20:48 zaphod kernel: [277530.714436] sky2 eth0: enabling interface
Jan  6 18:20:48 zaphod kernel: [277530.715511] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  6 18:20:48 zaphod avahi-autoipd(wlan0)[11598]: SIOCSIFFLAGS failed: Permission denied
Jan  6 18:20:48 zaphod avahi-autoipd(wlan0)[11598]: Callout STOP, address 169.254.5.46 on interface wlan0
Jan  6 18:20:48 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:20:48 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:20:48 zaphod dhclient: All rights reserved.
Jan  6 18:20:48 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:20:48 zaphod dhclient: 
Jan  6 18:20:48 zaphod avahi-daemon[919]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  6 18:20:48 zaphod avahi-daemon[919]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.5.46.
Jan  6 18:20:48 zaphod avahi-daemon[919]: Withdrawing address record for 169.254.5.46 on wlan0.
Jan  6 18:20:48 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:20:48 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:20:48 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:20:48 zaphod dhclient: DHCPRELEASE on wlan0 to 192.168.11.1 port 67
Jan  6 18:20:48 zaphod dhclient: send_packet: Network is unreachable
Jan  6 18:20:48 zaphod dhclient: send_packet: please consult README file regarding broadcast address.
Jan  6 18:20:48 zaphod kernel: [277531.364770] Registered led device: iwl-phy0::radio
Jan  6 18:20:48 zaphod kernel: [277531.364814] Registered led device: iwl-phy0::assoc
Jan  6 18:20:48 zaphod kernel: [277531.364856] Registered led device: iwl-phy0::RX
Jan  6 18:20:48 zaphod kernel: [277531.364896] Registered led device: iwl-phy0::TX
Jan  6 18:20:49 zaphod kernel: [277531.438350] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  6 18:21:24 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:21:24 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:21:24 zaphod dhclient: All rights reserved.
Jan  6 18:21:24 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:21:24 zaphod dhclient: 
Jan  6 18:21:24 zaphod kernel: [277567.256331] Registered led device: iwl-phy0::radio
Jan  6 18:21:24 zaphod kernel: [277567.256375] Registered led device: iwl-phy0::assoc
Jan  6 18:21:24 zaphod kernel: [277567.256415] Registered led device: iwl-phy0::RX
Jan  6 18:21:24 zaphod kernel: [277567.256453] Registered led device: iwl-phy0::TX
Jan  6 18:21:24 zaphod kernel: [277567.320932] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  6 18:21:25 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:21:25 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:21:25 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:21:27 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Jan  6 18:21:31 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Jan  6 18:21:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:21:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:21:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4603)
Jan  6 18:21:35 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jan  6 18:21:41 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Jan  6 18:21:51 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Jan  6 18:22:07 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jan  6 18:22:14 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Jan  6 18:22:28 zaphod dhclient: No DHCPOFFERS received.
Jan  6 18:22:28 zaphod dhclient: No working leases in persistent database - sleeping.
Jan  6 18:22:28 zaphod avahi-autoipd(wlan0)[12652]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jan  6 18:22:28 zaphod avahi-autoipd(wlan0)[12652]: Successfully called chroot().
Jan  6 18:22:28 zaphod avahi-autoipd(wlan0)[12652]: Successfully dropped root privileges.
Jan  6 18:22:28 zaphod avahi-autoipd(wlan0)[12652]: Starting with address 169.254.5.46
Jan  6 18:22:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:22:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:22:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4604)
Jan  6 18:22:34 zaphod avahi-autoipd(wlan0)[12652]: Callout BIND, address 169.254.5.46 on interface wlan0
Jan  6 18:22:34 zaphod avahi-daemon[919]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.5.46.
Jan  6 18:22:34 zaphod avahi-daemon[919]: New relevant interface wlan0.IPv4 for mDNS.
Jan  6 18:22:34 zaphod avahi-daemon[919]: Registering new address record for 169.254.5.46 on wlan0.IPv4.
Jan  6 18:22:38 zaphod avahi-autoipd(wlan0)[12652]: Successfully claimed IP address 169.254.5.46
Jan  6 18:23:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:23:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:23:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4605)
Jan  6 18:24:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:24:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:24:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4606)
Jan  6 18:25:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:25:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:25:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4607)
Jan  6 18:25:47 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jan  6 18:25:54 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jan  6 18:26:01 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Jan  6 18:26:11 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jan  6 18:26:26 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Jan  6 18:26:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:26:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:26:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4608)
Jan  6 18:26:47 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
Jan  6 18:26:48 zaphod dhclient: No DHCPOFFERS received.
Jan  6 18:26:48 zaphod dhclient: No working leases in persistent database - sleeping.
Jan  6 18:27:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:27:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:27:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4609)
Jan  6 18:27:37 zaphod dhclient: There is already a pid file /var/run/dhclient.pid with pid 12675
Jan  6 18:27:37 zaphod dhclient: killed old client process, removed PID file
Jan  6 18:27:37 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:27:37 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:27:37 zaphod dhclient: All rights reserved.
Jan  6 18:27:37 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:27:37 zaphod dhclient: 
Jan  6 18:27:37 zaphod dhclient: Listening on LPF/eth0/00:15:c5:82:50:cc
Jan  6 18:27:37 zaphod dhclient: Sending on   LPF/eth0/00:15:c5:82:50:cc
Jan  6 18:27:37 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:27:37 zaphod dhclient: DHCPRELEASE on eth0 to 192.168.11.1 port 67
Jan  6 18:27:37 zaphod dhclient: send_packet: Network is unreachable
Jan  6 18:27:37 zaphod dhclient: send_packet: please consult README file regarding broadcast address.
Jan  6 18:27:37 zaphod kernel: [277939.852716] sky2 eth0: disabling interface
Jan  6 18:27:37 zaphod kernel: [277939.865286] sky2 eth0: enabling interface
Jan  6 18:27:37 zaphod kernel: [277939.866354] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  6 18:27:37 zaphod avahi-autoipd(wlan0)[12652]: SIOCSIFFLAGS failed: Permission denied
Jan  6 18:27:37 zaphod avahi-autoipd(wlan0)[12652]: Callout STOP, address 169.254.5.46 on interface wlan0
Jan  6 18:27:37 zaphod avahi-daemon[919]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  6 18:27:37 zaphod avahi-daemon[919]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.5.46.
Jan  6 18:27:37 zaphod avahi-daemon[919]: Withdrawing address record for 169.254.5.46 on wlan0.
Jan  6 18:27:37 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:27:37 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:27:37 zaphod dhclient: All rights reserved.
Jan  6 18:27:37 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:27:37 zaphod dhclient: 
Jan  6 18:27:37 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:27:37 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:27:37 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:27:37 zaphod dhclient: DHCPRELEASE on wlan0 to 192.168.11.1 port 67
Jan  6 18:27:37 zaphod dhclient: send_packet: Network is unreachable
Jan  6 18:27:37 zaphod dhclient: send_packet: please consult README file regarding broadcast address.
Jan  6 18:27:38 zaphod kernel: [277940.458830] Registered led device: iwl-phy0::radio
Jan  6 18:27:38 zaphod kernel: [277940.458860] Registered led device: iwl-phy0::assoc
Jan  6 18:27:38 zaphod kernel: [277940.458888] Registered led device: iwl-phy0::RX
Jan  6 18:27:38 zaphod kernel: [277940.458913] Registered led device: iwl-phy0::TX
Jan  6 18:27:38 zaphod kernel: [277940.530490] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  6 18:28:13 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  6 18:28:13 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  6 18:28:13 zaphod dhclient: All rights reserved.
Jan  6 18:28:13 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  6 18:28:13 zaphod dhclient: 
Jan  6 18:28:13 zaphod kernel: [277976.416185] Registered led device: iwl-phy0::radio
Jan  6 18:28:13 zaphod kernel: [277976.416216] Registered led device: iwl-phy0::assoc
Jan  6 18:28:13 zaphod kernel: [277976.416242] Registered led device: iwl-phy0::RX
Jan  6 18:28:13 zaphod kernel: [277976.416267] Registered led device: iwl-phy0::TX
Jan  6 18:28:14 zaphod kernel: [277976.488496] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  6 18:28:15 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:28:15 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan  6 18:28:15 zaphod dhclient: Sending on   Socket/fallback
Jan  6 18:28:16 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan  6 18:28:25 zaphod dhclient: last message repeated 2 times
Jan  6 18:28:25 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jan  6 18:28:31 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jan  6 18:28:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:28:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:28:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4610)
Jan  6 18:28:44 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jan  6 18:28:59 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jan  6 18:29:14 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan  6 18:29:17 zaphod dhclient: No DHCPOFFERS received.
Jan  6 18:29:17 zaphod dhclient: No working leases in persistent database - sleeping.
Jan  6 18:29:17 zaphod avahi-autoipd(wlan0)[13724]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jan  6 18:29:17 zaphod avahi-autoipd(wlan0)[13724]: Successfully called chroot().
Jan  6 18:29:17 zaphod avahi-autoipd(wlan0)[13724]: Successfully dropped root privileges.
Jan  6 18:29:17 zaphod avahi-autoipd(wlan0)[13724]: Starting with address 169.254.5.46
Jan  6 18:29:22 zaphod avahi-autoipd(wlan0)[13724]: Callout BIND, address 169.254.5.46 on interface wlan0
Jan  6 18:29:22 zaphod avahi-daemon[919]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.5.46.
Jan  6 18:29:22 zaphod avahi-daemon[919]: New relevant interface wlan0.IPv4 for mDNS.
Jan  6 18:29:22 zaphod avahi-daemon[919]: Registering new address record for 169.254.5.46 on wlan0.IPv4.
Jan  6 18:29:26 zaphod avahi-autoipd(wlan0)[13724]: Successfully claimed IP address 169.254.5.46
Jan  6 18:29:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:29:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:29:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4611)
Jan  6 18:30:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:30:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:30:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4612)
Jan  6 18:31:33 zaphod INADYN[1279]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  6 18:31:33 zaphod INADYN[1279]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  6 18:31:33 zaphod INADYN[1279]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 4613)

---

### Post by Bugs318 on 2010-01-18
I have now had things act a bit differently.  I have periodically downloaded 4 or 5 torrents at a time, kicking into very high speeds without any disconnects (making me think the problem was fixed), but at other times even a single torrent limited to 12 KiBs has caused repetitive disconnects every few minutes when there were no other torrents being downloaded and no high speeds.

Just to reiterate, the disconnect is not a router disconnect - the network remains connected - but gnome network manager on the computer in question disconnects and will not pick up any wireless signal again until the system is rebooted.

Any help or fix for this known bug would be hugely appreciated as this is an annoying pain!

---

### Post by zaphod777 on 2010-01-19
> **Bugs318 said:**
> I have now had things act a bit differently.  I have periodically downloaded 4 or 5 torrents at a time, kicking into very high speeds without any disconnects (making me think the problem was fixed), but at other times even a single torrent limited to 12 KiBs has caused repetitive disconnects every few minutes when there were no other torrents being downloaded and no high speeds.

Just to reiterate, the disconnect is not a router disconnect - the network remains connected - but gnome network manager on the computer in question disconnects and will not pick up any wireless signal again until the system is rebooted.

Any help or fix for this known bug would be hugely appreciated as this is an annoying pain!

I have noticed the same thing it can be quite random really. I think this is an issue in the Kernel I am tempted to try the latest beta/Alpha and see if the issue is fixed in a later kernel.

---

### Post by evatw001 on 2010-01-19
this only happens to me when I do far too many connections. Getting up over 3 to 4 hundred.

---

### Post by zaphod777 on 2010-01-19
I have my max connections set to 200.

---

### Post by ant080808 on 2010-01-19
I have a similar problem except mine happens mostly while streaming media to my PS3. It is really annoying. It also happens if I try and load more than one website at a time or download more than one file.

---

### Post by herbig on 2010-03-05
Have there been any updates to this recently?  I'm having the same exact problem and am wondering if anyone has discovered a workaround yet...

---

### Post by zaphod777 on 2010-03-05
I fixed this by installing 9.04 and upgrading to 9.10. 

Although we just got a new kernel pushed out today. Maybe that will fix it for you.

---

### Post by adenewton on 2010-03-06
> **zaphod777 said:**
> I fixed this by installing 9.04 and upgrading to 9.10. 

Although we just got a new kernel pushed out today. Maybe that will fix it for you.

Odd, as the problem started in 9.04 for the majority of us.

Another, but more expensive fix, is to buy an ethernet wireless bridge, that turns your ethernet port into a wireless adapter. That way your then using your ethernet port directly rather than the iffy driver the kernel is providing for your wireless adapter.

---

### Post by zaphod777 on 2010-03-06
Not sure if this makes a difference but I used EXT3 instead of EXT4 and didn't use home drive encryption this time where as before I was. Maybe something to do with the new FS causing some errors? I would be curious if anyone is having the problem using EXT3 with no home drive encryption. 

It would make some sense since they first introduced EXT4 in 9.04 I believe.

---

### Post by adenewton on 2010-03-06
> **zaphod777 said:**
> Not sure if this makes a difference but I used EXT3 instead of EXT4 and didn't use home drive encryption this time where as before I was. Maybe something to do with the new FS causing some errors? I would be curious if anyone is having the problem using EXT3 with no home drive encryption. 

It would make some sense since they first introduced EXT4 in 9.04 I believe.

Good point, I am using Ext4. I just re-installed my system last weekend. Although I've just got it back into a preferred state I guess it wouldn't harm to install again. Something to do when the Mrs goes to work this afternoon.

EDIT: Just remembered when I was 9.04 I was in my old house which I used ehternet, which is why I have always assumed it's down to the way the kernal handles some wireless rlink adapters. As I would have been on Ext4 in my old house with 9.04 when it was first released, and only noticed the problem when I moved house and had to switch to wireless.

---

### Post by atulkakrana on 2010-08-07
> **zaphod777 said:**
> Don't have any trouble when I swap my HDD with the one running Win7.


I liked the way you handled it! Anyway thats a kernel bug and Wifi disconnects due to max load...No fix yet...not even in 10.04..its worse.

---

### Post by david.matheson on 2010-10-15
I'm having this trouble in 10.10.  Just torrent clients, normal transfers don't kick me off my wireless.  I close the torrent client, disconnect, disable and enable wireless, then connect.  Everything goes back to normal.  What do I have to set in KTorrent for this not to happen?

---

