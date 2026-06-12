---
title: "Newbie with problems detecting wireless network"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by Bludkill on 2010-04-06
[FONT=Verdana]Decided to take the plunge. I'm running Ubuntu 9.10 on a Dell M6400, using Wubi for Windows 7 x64. My ISP sets my router password at source, meaning I'm unable to disable wireless encryption (which is WPA 2 Personal). That being said, I don't seem to be able to detect *any* wireless networks (I can still connect via ethernet, which does not require the password). I'm not certain where the problem is, so I'll outline my steps and what the results were:

Under "**System > Administration > Hardware Drivers**" I have the "**Broadcom STA proprietary wireless driver**" installed (for BCM4311-, BCM4312-, BCM4321-, and BCM4322- based hardware).

The driver is activated and currently in use.
[/FONT]
===
[FONT=Verdana] When I type 
"**nm-tool**", I get

[I]NetworkManager Tool

State: disconnected

- Device: eth2 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unavailable
  Default:           no
  HW Address:        00:23:4D:5C:6F:42

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:21:70:8A:79:A7

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off
[/I][/FONT]
===
[FONT=Verdana]When I type:
[/FONT][FONT=Verdana]"**sudo lshw -C networks**"

I get:

[I]  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth2
       version: 01
       serial: 00:23:4d:5c:6f:42
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f1ffc000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5761e Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:8a:79:a7
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5761e-v3.60 latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:32 memory:f1be0000-f1beffff memory:f1bf0000-f1bfffff
[/I]
[/FONT]===
When I type:
"**lsmod**" I get

[I]binfmt_misc            10220  1 
ppdev                   8232  0 
joydev                 13088  0 
pcmcia                 40116  0 
snd_hda_codec_idt      73008  1 
dell_wmi                3216  0 
lib80211_crypt_tkip    10016  0 
yenta_socket           27628  1 
rsrc_nonstatic         11840  1 yenta_socket
pcmcia_core            42692  3 pcmcia,yenta_socket,rsrc_nonstatic
wl                   1277380  0 
lib80211                7812  2 lib80211_crypt_tkip,wl
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ricoh_mmc               4480  0 
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci_pci               8928  0 
sdhci                  20484  1 sdhci_pci
snd                    77096  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               5256  1 sdhci
dell_laptop             9692  0 
soundcore               9088  1 snd
dcdbas                  9136  1 dell_laptop
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
psmouse                57124  0 
serio_raw               6596  0 
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16644  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
nvidia              10316904  38 
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
lp                     11908  0 
parport                40528  2 ppdev,lp
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
ohci1394               33780  0 
intel_agp              33040  0 
ieee1394              100896  1 ohci1394
tg3                   123748  0 
video                  23612  0 
output                  3680  1 video[/I]

===
When I type:
"**rfkill list**" I get

[I]0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes[/I]

===
When I type:
"**iwconfig**" I get

[I]lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:167
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
[/I]
===
Finally, the networking icon reads as follows (when plugged into the ethernet):

[I]Wireless networks
wireless is disabled
[/I]

For what it's worth, I've also set up the VPN network with my network SSID and password, but I don't think that it's doing anything, since I can't see any wireless networks.

--------------------

Anyway, that's where I am. I've tried going through the troubleshooting guides, but I can't figure out what's wrong. Any thoughts? Thanks for the help, all!

---

### Post by MeeMaw on 2010-04-06
Well, I may be way off, but I saw this;

> 
"rfkill list" I get

0: dell-wifi: Wireless LAN
Soft blocked: no
Hard blocked: yes


I'm thinking that 'hard blocked: yes' means that your wireless is turned off (this IS a laptop?)

Is it possible that the switch on your wireless has gotten turned off? Please check that the switch is not off by mistake.

Also, I'm sure you already know this, but wireless won't work when the wired ethernet is plugged in.

I'm sure someone else who knows more than I will come along soon and get you going.

;)

---

### Post by bkratz on 2010-04-06
Since this is a Dell laptop, you might want to look at post 3 and on of this thread, about Dell_laptop.

[http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop](http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop)

---

### Post by Bludkill on 2010-04-06
> **MeeMaw said:**
> Well, I may be way off, but I saw this;



I'm thinking that 'hard blocked: yes' means that your wireless is turned off (this IS a laptop?)

Is it possible that the switch on your wireless has gotten turned off? Please check that the switch is not off by mistake.

Also, I'm sure you already know this, but wireless won't work when the wired ethernet is plugged in.


;)

Alas, the wireless is on; it works fine when I boot into Windows. And I've tried booting with the ethernet unplugged and plugged; it doesn't seem to make a difference (and neither does plugging/unplugging/etc...)

Poop. 



> **bkratz said:**
> Since this is a Dell laptop, you might want to  look at post 3 and on of this thread, about Dell_laptop.

[http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop](http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop)

Thanks for the link. My wireless card is the Dell Wireless 1510 802.11 a/g/n 2x3 Mini-Card, not the Intel 4965AGN, but I'll try fiddling with the dell-laptop module in the meantime.

---

### Post by bkratz on 2010-04-06
> **Bludkill said:**
> Alas, the wireless is on; it works fine when I boot into Windows. And I've tried booting with the ethernet unplugged and plugged; it doesn't seem to make a difference (and neither does plugging/unplugging/etc...)

Poop. 





Thanks for the link. My wireless card is the Dell Wireless 1510 802.11 a/g/n 2x3 Mini-Card, not the Intel 4965AGN, but I'll try fiddling with the dell-laptop module in the meantime.


I realize that it is a Broadcom device, but that really doesn't matter, it is the interaction between Dell_laptop and Dell_wmi
modules, it may help-maybe not.


See this too
[https://bugzilla.kernel.org/show_bug.cgi?id=14098](https://bugzilla.kernel.org/show_bug.cgi?id=14098)


and this

[http://ubuntuforums.org/showthread.php?t=1377829](http://ubuntuforums.org/showthread.php?t=1377829)

---

### Post by Bludkill on 2010-04-06
> **bkratz said:**
> I realize that it is a Broadcom device, but that really doesn't matter, it is the interaction between Dell_laptop and Dell_wmi
modules, it may help-maybe not.


See this too
[https://bugzilla.kernel.org/show_bug.cgi?id=14098](https://bugzilla.kernel.org/show_bug.cgi?id=14098)


and this

[http://ubuntuforums.org/showthread.php?t=1377829](http://ubuntuforums.org/showthread.php?t=1377829)


OMG. I'm sorry I ever doubted you. I just rebooted into Ubuntu and the first thing I tried - typing "sudo rmmod -f dell-laptop" - instantly activated my wireless (I'd already typed in all the VPN configuration). It was magical - one command (the first one I tried) and everything was fixed.

For anyone who stumbles upon this...

[SIZE=5]**sudo rmmod -f dell-laptop**[/SIZE]

Thanks so much! I really appreciate it!

---

### Post by bkratz on 2010-04-06
> **Bludkill said:**
> OMG. I'm sorry I ever doubted you. I just rebooted into Ubuntu and the first thing I tried - typing "sudo rmmod -f dell-laptop" - instantly activated my wireless (I'd already typed in all the VPN configuration). It was magical - one command (the first one I tried) and everything was fixed.

For anyone who stumbles upon this...

[SIZE=5]**sudo rmmod -f dell-laptop**[/SIZE]

Thanks so much! I really appreciate it!

Thanks should go to Chili555, it is his solution, but if you go to the thread tools above and mark it as solved perhaps some searcher will find it and benefit.


And did you blacklist it so it doesn't rear it face again. like in the last post?
Otherwise you would have to do it every boot.

---

### Post by Bludkill on 2010-04-06
> **bkratz said:**
> Thanks should go to Chili555, it is his solution, but if you go to the thread tools above and mark it as solved perhaps some searcher will find it and benefit.


And did you blacklist it so it doesn't rear it face again. like in the last post?
Otherwise you would have to do it every boot.


Thread solved! Thanks to Chili for the solution, and thanks to you for pointing it out.. In any case, it's now been blacklisted for good...

sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf

---

### Post by MeeMaw on 2010-04-06
Cool!!! Glad you got it!    (Yay, chili555!!!)

---

