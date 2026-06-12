---
title: "Regulatory domain changed from World to Am"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by Mat11 on 2010-12-21
Hi i'm using Ubuntu 9.10 on a i386 laptop and have noticed a signal drop while checking my Administration Log File viewer. I noticed on the file starting :-cfg 80211:Regulatory domain World, then another set of frequencies and below that calling CRDA for country : Am
cfg 80211 : Regulatory domain changed to country : Am

My question is-- how do i set it back to Regulatory domain : EU ?

Here is my output :-

23.249349] cfg80211: Calling CRDA to update world regulatory domain
Dec 21 10:32:00 matt-laptop kernel: [   23.271599] ath5k 0000:02:00.0: enabling device (0000 -> 0002)
Dec 21 10:32:00 matt-laptop kernel: [   23.271612] ath5k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 21 10:32:00 matt-laptop kernel: [   23.271715] ath5k 0000:02:00.0: registered as 'phy0'
Dec 21 10:32:00 matt-laptop kernel: [   23.281409] cfg80211: World regulatory domain updated:
Dec 21 10:32:00 matt-laptop kernel: [   23.281414]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 21 10:32:00 matt-laptop kernel: [   23.281417]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 21 10:32:00 matt-laptop kernel: [   23.281420]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 21 10:32:00 matt-laptop kernel: [   23.281423]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 21 10:32:00 matt-laptop kernel: [   23.281426]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 21 10:32:00 matt-laptop kernel: [   23.281429]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 21 10:32:00 matt-laptop kernel: [   23.465798] eth0: link down
Dec 21 10:32:00 matt-laptop kernel: [   23.466085] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 21 10:32:00 matt-laptop kernel: [   23.654002] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 21 10:32:00 matt-laptop kernel: [   23.722417] __ratelimit: 3 callbacks suppressed
Dec 21 10:32:00 matt-laptop kernel: [   23.722421] type=1505 audit(1292927520.319:13): operation="profile_replace" pid=855 name=/usr/share/gdm/guest-session/Xsession
Dec 21 10:32:00 matt-laptop kernel: [   23.734791] hda_codec: Unknown model for ALC861-VD, trying auto-probe from BIOS...
Dec 21 10:32:00 matt-laptop kernel: [   23.734884] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input7
Dec 21 10:32:00 matt-laptop kernel: [   23.778875] type=1505 audit(1292927520.375:14): operation="profile_replace" pid=858 name=/sbin/dhclient3
Dec 21 10:32:00 matt-laptop kernel: [   23.779710] type=1505 audit(1292927520.375:15): operation="profile_replace" pid=858 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Dec 21 10:32:00 matt-laptop kernel: [   23.780164] type=1505 audit(1292927520.379:16): operation="profile_replace" pid=858 name=/usr/lib/connman/scripts/dhclient-script
Dec 21 10:32:00 matt-laptop kernel: [   23.787644] type=1505 audit(1292927520.383:17): operation="profile_replace" pid=861 name=/usr/bin/evince
Dec 21 10:32:00 matt-laptop kernel: [   23.805910] type=1505 audit(1292927520.403:1     operation="profile_replace" pid=861 name=/usr/bin/evince-previewer
Dec 21 10:32:00 matt-laptop kernel: [   23.831619] type=1505 audit(1292927520.427:19): operation="profile_replace" pid=861 name=/usr/bin/evince-thumbnailer
Dec 21 10:32:00 matt-laptop kernel: [   23.845092] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Dec 21 10:32:00 matt-laptop kernel: [   23.845251] cfg80211: Calling CRDA for country: AM
Dec 21 10:32:00 matt-laptop kernel: [   23.845683] type=1505 audit(1292927520.443:20): operation="profile_replace" pid=897 name=/usr/lib/cups/backend/cups-pdf
Dec 21 10:32:00 matt-laptop kernel: [   23.850313] cfg80211: Regulatory domain changed to country: AM
Dec 21 10:32:00 matt-laptop kernel: [   23.850318]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 21 10:32:00 matt-laptop kernel: [   23.850321]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Dec 21 10:32:00 matt-laptop kernel: [   23.850324]     (5170000 KHz - 5250000 KHz @ 20000 KHz), (N/A, 1800 mBm)
Dec 21 10:32:00 matt-laptop kernel: [   23.850327]     (5250000 KHz - 5330000 KHz @ 20000 KHz), (N/A, 1800 mBm)

Hope someone can help ?

Many Thanks

Matt

---

### Post by Mat11 on 2010-12-21
\

---

