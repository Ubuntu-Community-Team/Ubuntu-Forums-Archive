---
title: "Slow speed on home network, fast on others ..."
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2011-06-27
Hi all,

**Wireless Card**: 

```
*-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: b4:82:fe:3c:ad:72
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=rtl819xSE  driverversion=0019.1207.2010 firmware=63 ip=192.168.0.60 latency=0  multicast=yes wireless=802.11bg
       resources: irq:17 ioport:2000(size=256) memory:d4000000-d4003fff
```**Computer**: Toshiba Satellite Pro L510 laptop.

**Issues**:  I wrangled with my laptop's internet speed issue a few months ago but  gave up when all failed. In a nutshell, three machines on our home LAN  get speeds of 10+Mbps while my Toshiba, the most modern (and that might  be the problem!), achieves 1Mbps tops; generally around 0.4-0.7.

Regardless  what I tried - and this included installing a 32bit Ubuntu after  Realtek advised me that the driver was for 32bit and results would be  unpredicatble on 64bit - nothing has changed. 

The wireless  signal strength on the network icon unpredictably slips to about 50% for  a few seconds then back up to 100%. When I right click the network icon  and 'Edit Connections' and go to 'Wireless', the other three networks I  have used (and use rarely) all show when I last used them correctly. My  home network shows 'Last Used = Never' and always has. 

What I  have outlined above is the same for 10.04 LTS and 10.10 using either  Xfce or Gnome. Identical results. I have deleted the home network and  re-created it, tried wicd instead of Network Manager; these things don't  fix and don't seem to be the issue. An ethernet cable plugged into the same install gives 10+Mbps, same as the other three machines. It is wireless only on the Toshiba that gives any issue.

**The plot thickens**: I  recently went to see the in-laws. After getting on their LAN and  computing for awhile, I had the idea to check the speed. 4Mbps! That was  correct! A few days later we went somewhere else and connected to their  network. Same result. My speed test matched their network speed. 

On both occasions wireless signal strength icon rock solid, no jumps to 50%. 

Get home, 0.7Mbps. So, I'm guessing it is not the card or driver; they are capable of achieving better speeds. #-o

**Ideas**:  Perhaps there's a setting on my router that could be wrong for this  laptop (remembering the other three are getting 10Mbsp +), or a  setting on my laptop that is wrong for my router. (Or both!) 

I have modem into a wired router then the wireless router daisy-chained to the wired router. All static IPs and the wired is the gateway IP on all four computers (three of which are wireless). I'm thinking maybe killing the wired router, get the modem directly into the wireless and using one router may make the job easier. 

I am about to start digging if anyone would like to join me or has any clues ...

---

### Post by Bucky Ball on 2011-06-27
Well, so far ...

```
binky@tosher:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          postconf: fatal: open /etc/postfix/main.cf: No such file or directory
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
```... on 10.10.

Checked out the routers but all looks fine. All pretty straightforward unless I've overlooked something ...

---

### Post by Bucky Ball on 2011-06-30
I also just got this when I tried restarting the network a couple of times:

```
binky@tosher:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
SIOCDELRT: No such process
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
                                                                         [ OK ]
binky@tosher:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
```I also haven't mentioned that this card works faultlessly in Windows7 on the same machine (achieving speeds of up to 10+Mbps). Pretty sick of this poor showing and lack of any concrete fix from Realtek (or lack of effort to remedy this situation). The forums and internet generally are strewn with tales of woe regarding Linux and this card and no support from Realtek forthcoming ...

* PS: I also added 'r8192se_pci' to the end of the /etc/modules file, as I'd seen advised on other pages, to no avail. No different. Might give up, disable the card, and buy a cheap wireless dongle (the last I bought worked out of the box and achieves 10+Mbps from behind a brick wall).

---

### Post by TechSupportx86 on 2011-06-30
What router do you have? 

Also do you have any other wireless devices on your network that show the same speed?

---

### Post by Bucky Ball on 2011-06-30
Please read original posts. All info there.

---

### Post by TechSupportx86 on 2011-06-30
Everything except for the make/model of router...

The reason i ask is if you can get full speeds on other networks under ubuntu, with the only variable being the router. Then it leads me to believe the problem lies with your router, not your card or driver. 

Now i could blindly tell you different settings which may or may be present on your router, or you can tell me which router you have to help speed this process along.

Also the vague reference to to the "three machines on our home LAN" do not specify whether they are WIRED or WIRELESS.

---

### Post by Bucky Ball on 2011-06-30
Of interest. Just checked which modules my machine is currently using. This is a section of the readout of 'lsmod | more':

```
**r8192se_pci           509996  0 **
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_cod
ec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
dm_raid45              75026  0 
xor                     4709  1 dm_raid45
usbhid                 42030  0 
hid                    84710  1 usbhid
usb_storage            50436  0 
ahci                   22210  3 
video                  22176  0 
**r8169                  42254  0** 
output                  2527  1 video
libahci                26148  1 ahci
**mii                     5261  1 r8169**
```
Wondering if the r8169 is conflicting with the r8192se_pci???

* UPDATE: Scratch that. r8169 seems obviously to be related to eth0, the hardwire connection. Nothing to do with wireless.

---

### Post by Bucky Ball on 2011-06-30
Some details, in order of appearance, from my dmesg which might give someone a clue:

```
[   24.479914] Linux kernel driver for RTL8192 based WLAN cards
[   24.479916] Copyright (c) 2007-2008, Realsil Wlan Driver
[   24.479963] rtl819xSE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 1
7
[   24.479971] rtl819xSE 0000:03:00.0: setting latency timer to 64
``````
[   24.898138] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   24.898142] InitializeAdapter8192SE(): Set MRC settings on as default!!
[   24.898144] HW_VAR_MRC: Turn on 1T1R MRC!
[   24.898690] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.038610] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   25.038615] InitializeAdapter8192SE(): Set MRC settings on as default!!
[   25.038617] HW_VAR_MRC: Turn on 1T1R MRC!
[   25.045917] set_swcam():EntryNo is 0,KeyIndex is 0,KeyType is 1,is_mesh is 0

``````
[   29.519258] Linking with MyAccessPoint,channel:6, qos:0, myHT:1, networkHT:0, mode:4 cur_net.flags:0x2
[   29.555336]   alloc irq_desc for 48 on node -1
[   29.555339]   alloc kstat_irqs on node -1
[   29.555354] fglrx_pci 0000:01:00.0: irq 48 for MSI/MSI-X
[   29.555883] [fglrx] Firegl kernel thread PID: 1404
[   29.556085] [fglrx] IRQ 48 Enabled
[   29.591964] ============>sync_scan_hurryup out
[   29.592021] rtllib_associate_procedure_wq(), chan:6
[   29.592025] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[   29.602070] ==============>rtllib_associate_procedure_wq():ieee->current_network.qos_data.qos_mode is 0,ieee->qos_capability is 1
[   29.603829] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[   29.605974] Associated successfully
[   29.605978] normal associate
[   29.605992] rtl8192_SetWirelessMode(), wireless_mode:2, bEnableHT = 0
[   29.605995] Using B rates:22
[   29.605998] Successfully associated, ht not enabled(0, 0)
[   29.606005] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000000
[   29.607581] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

``````
[   32.710327] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000000
[   32.711371] ===>rtllib_wx_set_power(): power disable
[   32.711709] alg name:WEP
[   32.711728] r8192_wx_set_enc_ext() group:1, alg:1, last_pairwise_key_type:0, key_len:5
[   32.712336] set_swcam():EntryNo is 0,KeyIndex is 0,KeyType is 1,is_mesh is 0
[   32.712427] notify_wx_assoc_event(): Tell user space disconnected
[   32.712441] Linking with MyAccessPoint,channel:6, qos:0, myHT:0, networkHT:0, mode:4 cur_net.flags:0x2
[   32.712454] Linking with MyAccessPoint,channel:6, qos:0, myHT:0, networkHT:0, mode:4 cur_net.flags:0x2
[   32.713008] rtllib_associate_procedure_wq(), chan:6
[   32.713012] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[   32.723051] ==============>rtllib_associate_procedure_wq():ieee->current_network.qos_data.qos_mode is 0,ieee->qos_capability is 1
[   32.812770] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[   32.821819] Associated successfully
[   32.821823] normal associate
[   32.821837] rtl8192_SetWirelessMode(), wireless_mode:2, bEnableHT = 0
[   32.821841] Using B rates:22
[   32.821843] Successfully associated, ht not enabled(0, 0)
[   32.821850] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000000
[   32.904292] dm_check_edca_turbo():iot peer is unknown, bssid:00:1b:11:84:af:26

``````
[   33.674415] ===>rtllib_wx_set_power(): power disable
[   39.815179] wlan0: no IPv6 routers present
[   51.171260] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000000

``````
[   91.077210] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000000
```Seems to be doing a lot of the same processes a number of times and I don't have the knowledge to know whether that is what's supposed to be happening. I suspect not.

---

### Post by Bucky Ball on 2011-06-30
> **TechSupportx86 said:**
> Everything except for the make/model of router...

Both D-Link. Unlikely because ...

> 
... if you can get full speeds on other networks under ubuntu, with the only variable being the router. Then it leads me to believe the problem lies with your router, not your card or driver. 
One wired, two wireless, all 10Mbps. Rules out router for everything but wireless on the Toshiba, the fourth machine.

---

### Post by Bucky Ball on 2011-06-30
Okay, here's the news. I blacklisted the Realtek 8192se_pci driver and grabbed my Open Networks USB wireless dongle from the desktop. Rebooted the laptop, plugged the dongle in, online immediately, +10Mbps like the other machines, signal rock solid. Result of 'lshw -C network' for the dongle:

```
 *-network:1
       description: Wireless interface
       physical id: 3
       bus info: usb@2:1.1
       logical name: wlan1
       serial: 00:1a:ef:05:e4:57
       capabilities: ethernet physical wireless
       configuration: broadcast=yes **driver=rtl8187** driverversion=2.6.35-28-generic firmware=N/A ip=192.168.0.60 multicast=yes wireless=IEEE 802.11bg
```The dongle has a Realtek chip also using the driver in bold, but this one works.

I am convinced there is something amiss with the driver for the internal card but that doesn't explain the fact that it worked fine on two other networks recently and achieved speeds of 4Mbps, just seems to be my home LAN. Oh, well. Maybe one day the 8192 driver will be fixed. As mentioned, the internet is strewn with tales of woe regarding this card and Ubuntu/Linux. Might give up, crawl back under my rock and use the dongle, buy another for the desktop ...

---

