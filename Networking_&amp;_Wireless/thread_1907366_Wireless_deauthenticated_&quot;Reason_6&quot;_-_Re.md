---
title: "Wireless deauthenticated &quot;Reason 6&quot; - Realtek RTL8188CE"
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by rodrigor on 2012-01-11
Hi.

I have a Lenovo x220 with a Realtek RTL8188CE wireless card.
Things were working fine, but now I'm having problems with the wireless, seems to drop the connection, several times per minute.

this is what i get from dmesg, it repeats (forever):

```
[44306.752385] wlan0: deauthenticated from c8:3a:35:3e:c4:10 (Reason: 6)
[44306.857410] cfg80211: All devices are disconnected, going to restore regulatory settings
[44306.857422] cfg80211: Restoring regulatory settings
[44306.857431] cfg80211: Calling CRDA to update world regulatory domain
[44306.864261] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[44306.864275] cfg80211: World regulatory domain updated:
[44306.864280] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[44306.864287] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[44306.864293] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[44306.864299] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[44306.864304] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[44306.864310] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[44308.244747] wlan0: authenticate with c8:3a:35:3e:c4:10 (try 1)
[44308.247381] wlan0: authenticated
[44308.247411] wlan0: associate with c8:3a:35:3e:c4:10 (try 1)
[44308.251188] wlan0: RX AssocResp from c8:3a:35:3e:c4:10 (capab=0x411 status=0 aid=1)
[44308.251199] wlan0: associated
[44308.262221] cfg80211: Calling CRDA for country: CN
[44308.265157] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[44308.265166] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[44308.265170] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[44308.265176] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[44308.265179] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[44308.265184] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[44308.265188] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[44308.265193] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[44308.265197] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[44308.265201] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[44308.265205] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[44308.265210] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[44308.265214] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[44308.265219] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[44308.265223] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[44308.265228] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[44308.265231] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[44308.265236] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[44308.265240] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[44308.265245] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[44308.265248] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[44308.265253] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[44308.265257] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[44308.265262] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[44308.265265] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[44308.265270] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[44308.265274] cfg80211: Disabling freq 2484 MHz
[44308.265282] cfg80211: Regulatory domain changed to country: CN
[44308.265285] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[44308.265290] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[44308.265294] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)

```my system:
```
rrosa@rrosa-X220:~/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b4)
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 6 Series Chipset Family LPC Controller [8086:1c4f] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
0d:00.0 System peripheral [0880]: Ricoh Co Ltd Device [1180:e823] (rev 04)

``````
rrosa@rrosa-X220:~/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011$ cat /proc/version
Linux version 2.6.38-13-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #53-Ubuntu SMP Mon Nov 28 19:33:45 UTC 2011

```I'm using 11.04
wired connection works fine.
windows connections works fine.

i tried the driver my realtek, but it still happens.

any ideas?
how do i revert to the default driver?

is it possible to tell what is failing from the data i attached?
what else should i provide?

thanks!
regards,
Rodrigo.

---

### Post by pommessemmel on 2012-04-09
Same problem on my Gigabyte T1132N with  

06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

I also get these messages from dmesg and I also tried the drivers from realtek.
Doing a bios update or changing stuff there didn't make a difference.

My System: Kubuntu 11.10 (64bit) with 3.0.0-17 kernel

---

