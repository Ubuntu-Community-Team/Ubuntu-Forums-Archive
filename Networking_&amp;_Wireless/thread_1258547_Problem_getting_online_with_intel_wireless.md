---
title: "Problem getting online with intel wireless"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by tobbec on 2009-09-05
Hello,

I'm new to ubuntu (user for 5 days) and for two days I have been trying to get online with my intel wireless card.
Probably read a hundred guides and even tho I have learned allot I still cant get the wireless to work.

I tried using the network manager and also the wicd network manager both with same result.
I can find my wireless network and it also seems like it is getting some kind of response but for some reason it will not connect.
I have tried with WPA, WPA2 and open network all with the same result. Once or twice it have even said that I'm connected but I still can't access internet or get a ping response from my router (192.168.0.1).

Here is some answers from diagnostic commands.

**iwconfig**
wlan0     Link encap:Ethernet  HWaddr 00:1e:65:22:5c:cc  
          inet addr:192.168.0.195  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:65ff:fe22:5ccc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:630 (630.0 B)  TX bytes:5785 (5.7 KB)


**lsmod**
Module                  Size  Used by
i915                   67844  2 
drm                    96424  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434100  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
arc4                    9856  2 
ecb                    10752  2 
snd_seq_dummy          10756  0 
thinkpad_acpi          66560  0 
snd_seq_oss            37760  0 
iwlagn                100228  0 
iwlcore                93184  1 iwlagn
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
led_class              12036  2 thinkpad_acpi,iwlcore
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                61972  0 
pcspkr                 10496  0 
serio_raw              13444  0 
nvram                  16396  1 thinkpad_acpi
snd                    62756  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              217592  2 iwlagn,iwlcore
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
cfg80211               38288  3 iwlagn,iwlcore,mac80211
video                  25360  0 
output                 11008  1 video
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
btusb                  19608  2 
e1000e                121136  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

**dmesg**
[  771.800742] wlan0: direct probe to AP 00:24:01:3e:25:9c try 1
[  771.805438] wlan0 direct probe responded
[  771.805445] wlan0: authenticate with AP 00:24:01:3e:25:9c
[  771.809653] wlan0: authenticated
[  771.809661] wlan0: associate with AP 00:24:01:3e:25:9c
[  771.813224] wlan0: RX ReassocResp from 00:24:01:3e:25:9c (capab=0x431 status=0 aid=1)
[  771.813230] wlan0: associated
[  781.815564] wlan0: disassociating by local choice (reason=3)
[  784.906647] wlan0: deauthenticated
[  784.907864] wlan0: direct probe to AP 00:24:01:3e:25:9c try 1
[  784.912539] wlan0 direct probe responded
[  784.912547] wlan0: authenticate with AP 00:24:01:3e:25:9c
[  784.917228] wlan0: authenticated
[  784.917236] wlan0: associate with AP 00:24:01:3e:25:9c
[  784.925098] wlan0: RX ReassocResp from 00:24:01:3e:25:9c (capab=0x431 status=0 aid=1)
[  784.925104] wlan0: associated
[  794.926912] wlan0: disassociating by local choice (reason=3)
[  798.013809] wlan0: deauthenticated
[  798.015042] wlan0: direct probe to AP 00:24:01:3e:25:9c try 1
[  798.019715] wlan0 direct probe responded
[  798.019723] wlan0: authenticate with AP 00:24:01:3e:25:9c
[  798.023858] wlan0: authenticated
[  798.023866] wlan0: associate with AP 00:24:01:3e:25:9c
[  798.027332] wlan0: RX ReassocResp from 00:24:01:3e:25:9c (capab=0x431 status=0 aid=1)
[  798.027338] wlan0: associated
[  808.029070] wlan0: disassociating by local choice (reason=3)
[  810.916201] wlan0: deauthenticated
[  810.917416] wlan0: direct probe to AP 00:24:01:3e:25:9c try 1
[  810.922090] wlan0 direct probe responded
[  810.922099] wlan0: authenticate with AP 00:24:01:3e:25:9c
[  810.926222] wlan0: authenticated
[  810.926231] wlan0: associate with AP 00:24:01:3e:25:9c
[  810.929806] wlan0: RX ReassocResp from 00:24:01:3e:25:9c (capab=0x431 status=0 aid=1)
[  810.929812] wlan0: associated
[  820.931454] wlan0: disassociating by local choice (reason=3)
[  824.023317] wlan0: deauthenticated
[  824.024484] wlan0: direct probe to AP 00:24:01:3e:25:9c try 1
[  824.029199] wlan0 direct probe responded
[  824.029208] wlan0: authenticate with AP 00:24:01:3e:25:9c
[  824.033392] wlan0: authenticated
[  824.033399] wlan0: associate with AP 00:24:01:3e:25:9c
[  824.037103] wlan0: RX ReassocResp from 00:24:01:3e:25:9c (capab=0x431 status=0 aid=1)
[  824.037108] wlan0: associated
[  834.038979] wlan0: disassociating by local choice (reason=3)
[  837.130519] wlan0: deauthenticated
[  837.131796] wlan0: direct probe to AP 00:24:01:3e:25:9c try 1
[  837.136469] wlan0 direct probe responded
[  837.136478] wlan0: authenticate with AP 00:24:01:3e:25:9c
[  837.140705] wlan0: authenticated
[  837.140713] wlan0: associate with AP 00:24:01:3e:25:9c
[  837.149101] wlan0: RX ReassocResp from 00:24:01:3e:25:9c (capab=0x431 status=0 aid=1)
[  837.149107] wlan0: associated
[  847.151040] wlan0: disassociating by local choice (reason=3)
[  850.042450] wlan0: deauthenticated
[  850.043586] wlan0: direct probe to AP 00:24:01:3e:25:9c try 1
[  850.053604] wlan0 direct probe responded
[  850.053612] wlan0: authenticate with AP 00:24:01:3e:25:9c
[  850.055506] wlan0: authenticated
[  850.055512] wlan0: associate with AP 00:24:01:3e:25:9c
[  850.058901] wlan0: RX ReassocResp from 00:24:01:3e:25:9c (capab=0x431 status=0 aid=1)
[  850.058907] wlan0: associated

**lspci -v**
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
        Subsystem: Intel Corporation Device 1211
        Flags: bus master, fast devsel, latency 0, IRQ 2298
        Memory at f2500000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn


**lshw -C network**
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:1e:65:22:5c:cc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn


**iwlist auth**
wlan0     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current Authentication algorithm :
        open

I'd also prefer to use the network manager or the wicd as I will be installing ubuntu on computers where the user might be novice.

Any help would be much appreciated as the last thing I want to do is run Vista...

Regards

---

### Post by dagoth_pie on 2009-09-05
Do any wireless networks show up as detected if you left click the networking symbol in the top right of the screen?

---

### Post by tobbec on 2009-09-05
> **dagoth_pie said:**
> Do any wireless networks show up as detected if you left click the networking symbol in the top right of the screen?

Yes, it detects 9 wireless networks, one which is mine.
The problem comes when I try to connect, according to the router it even hands out an ip address but still...

---

### Post by dagoth_pie on 2009-09-05
I take it seeing as your in what sounds like a densely populated area you're use WEP or something? And if you know enough to have encrypted it yourself, then you've likely tried clicking on everything so we can rule out something simple like configuration error? I'm struggling to think back to WiFi setup, I haven't done any in a few monthes.

---

### Post by tobbec on 2009-09-05
> **dagoth_pie said:**
> I take it seeing as your in what sounds like a densely populated area you're use WEP or something? And if you know enough to have encrypted it yourself, then you've likely tried clicking on everything so we can rule out something simple like configuration error? I'm struggling to think back to WiFi setup, I haven't done any in a few monthes.
I have tried WPA, WPA2 and Open. I have encrypted it with passphrase and it works great on a XP dist on the same machine. Configuring it i network manager to use WPA/WPA/Open wasn't that hard so I think it can be ruled out.

---

### Post by dagoth_pie on 2009-09-05
Well it's good to rule out underthinking things first
> I'd also prefer to use the network manager or the wicd as I will be installing ubuntu on computers where the user might be novice.

I just noticed you mention installing, are you running it off a live cd or is it installed to the hard drive?

---

### Post by tobbec on 2009-09-05
> **dagoth_pie said:**
> Well it's good to rule out underthinking things first

I just noticed you mention installing, are you running it off a live cd or is it installed to the hard drive?

It's installed.

---

### Post by dagoth_pie on 2009-09-05
Ok, just being safe to rule out any possibilities, turns out that a few people have had similar problems, with various cards. Same symptoms, can sometimes connect, but they also get the same error as you
[http://ubuntuforums.org/showthread.php?t=1123627](http://ubuntuforums.org/showthread.php?t=1123627)
here's one of the threads, I'm reading through the bug report that got posted in the post at the bottom.

---

### Post by dagoth_pie on 2009-09-05
Sorry to double post but I found firstly 
[http://lkml.org/lkml/2008/8/13/435](http://lkml.org/lkml/2008/8/13/435)
that link, which mentions the Wifi card not working on particular kernels,
and also from the other thread
> Try to install the package linux-backports-modules-jaunty (it contains updated drivers).
It could be worth trying
```
sudo apt-get install linux-backports-modules-jaunty
```

---

### Post by tobbec on 2009-09-05
> **dagoth_pie said:**
> Sorry to double post but I found firstly 
[http://lkml.org/lkml/2008/8/13/435](http://lkml.org/lkml/2008/8/13/435)
that link, which mentions the Wifi card not working on particular kernels,
and also from the other thread
 
It could be worth trying
```
sudo apt-get install linux-backports-modules-jaunty
```
 
This helped! I'm now connected and can ping my router. I can how ever still not browse the web with the wireless connection...?
 
When I ping [www.google.com]("http://www.google.com") I get nothing. When I ping 74.125.77.105 (google IP) I get response.
 
I was poking around in resolve.conf when trying to fix the first problem. I now added my isp's DNS servers in the file and now it works!
 
Thanks allot!

---

### Post by cariboo on 2009-09-05
/etc/resolv.conf is controlled by Network Manager, you can set dhcp for the ip address and static dns in Network manager. Try [OpenDNS]("http://www.opendns.com/").

---

