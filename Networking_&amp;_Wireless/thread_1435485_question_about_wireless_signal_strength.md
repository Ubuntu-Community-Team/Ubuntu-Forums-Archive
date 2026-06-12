---
title: "question about wireless signal strength"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by Gatorade on 2010-03-21
I just installed Linux Mint , and I've noticed that my wireless signal strength is a lot weaker with Mint than when I was using Ubuntu.

I was using a belkin USB 2.0 wireless adapter and I was getting 4 bars , and now I'm only getting 1

anyone have any ideas as to why there was such a drastic loss in the signal strength?

I know this is more of a question to be asked in the Mint forum , but I thought it still applies since I'm comparing it to Ubuntu.

---

### Post by 666f6f on 2010-03-21
The reason is probably that Ubuntu loaded different modules (drivers) for your Wifi card.

You should be able to get the exact model of your Wifi card by running lcpci and what modules are loaded by running lsmod.

It would help if you posted the output here.

---

### Post by 2hot6ft2 on 2010-03-21
> **Gatorade said:**
> 
I was using a belkin **USB** 2.0 wireless adapter
> **666f6f said:**
> The reason is probably that Ubuntu loaded different modules (drivers) for your Wifi card.

You should be able to get the exact model of your Wifi card by running lcpci and what modules are loaded by running lsmod.

It would help if you posted the output here.
It's not a pci adapter so the OP should run
```
lsusb
```
instead of lspci. And that's LSUSB in lower case.;) Other than that, what 666f6f said.

---

### Post by 666f6f on 2010-03-21
Oups, merci :>

---

### Post by 2hot6ft2 on 2010-03-21
> **666f6f said:**
> Oups, merci :>
No problem, it's not like we don't all make mistakes.
:D

---

### Post by Gatorade on 2010-03-21
ok, this is what I got when I ran that code in Mint.

lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:705c Belkin Components F5D7050 v4000 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I'll post back after I switch the hard drive and run it again using Ubuntu.

---

### Post by Gatorade on 2010-03-21
here's what I got when I ran it in Ubuntu.

lsusb
Bus 001 Device 004: ID 050d:705c Belkin Components F5D7050 v4000 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


where does it tell me which drivers are being used?
naturally, I'd like to find out which drivers Ubuntu is using since its giving me better reception, and use the same ones in Mint.


ok, I ran lsmod and this is what I got


lsmod
Module                  Size  Used by
i915                   67844  2 
drm                    96424  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         436148  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
arc4                    9856  6 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
iwlagn                100228  0 
ecb                    10752  6 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 44748  0 
iwlcore                93184  1 iwlagn
iwl3945                97912  0 
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
zd1211rw               52740  0 
soundcore              15200  1 snd
psmouse                61972  0 
video                  25872  0 
led_class              12036  2 iwlcore,iwl3945
mac80211              217592  4 iwlagn,iwlcore,iwl3945,zd1211rw
dcdbas                 15264  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
serio_raw              13444  0 
usbhid                 42336  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
output                 11008  1 video
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
cfg80211               38288  5 iwlagn,iwlcore,iwl3945,zd1211rw,mac80211
tg3                   131204  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


so, how do I transfer the drivers to Mint? 
I have no clue what all that information is telling me. if someone would be so kind as to enlighten me I'd appreciate that, lol.

---

### Post by Gatorade on 2010-03-24
bump

---

### Post by Aped on 2010-03-24
Eh, I don't know lsusb or lspci to give driver versions... try: 

sudo lshw | grep -in 'wireless'

last line spewed out should say something along the lines of:
```

242:                configuration: broadcast=yes [bold]driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007)[/bold] ip=192.168.1.6 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes [color=red]wireless[/color]=IEEE 802.11g
```

The red is from grep's output, thanks to some aliase which you might not have in your rc, but the bold is my own; it should tell you the driver and firmware versions. 

Your firmware shouldn't have changed much since the Ubuntu install, but the driver definitely could have. 

Then just google it and update drivers if you need to, I guess. If you DON'T, that's where trouble comes in.

---

### Post by 666f6f on 2010-03-24
Hello Gatorade,

From the lsusb output it seems you own a Belkin Components F5D7050 v4000 Wireless Adapter. For more information about your adapter you can refer here: [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29)

From the lsmod output (this line especially: mac80211 217592 4 iwlagn,iwlcore,iwl3945,zd1211rw) it seems that Ubuntu has loaded the zd1211rw module (driver) for use with your USB Wifi adapter, and that a second Wifi adapter (integrated into your computer/laptop) exists that uses the iwl3945 module (driver).

I'm not sure which Wifi adapter you actually use to connect to the internet, it is possible that Ubuntu uses the integrated Wifi adapter and that Mint uses the USB adapter (or the opposite), that would be another good reason as to why you get different signal strengths.

To find out that, can you post the output of the iwconfig and route commands?

---

### Post by Aped on 2010-03-24
Snap, good catch 6man. 

Wanna just point out that in most BIOSes, you can disable pieces of hardware; wifi adapters are common targets of this 'hard blacklisting'. Because they're all different, I can't give you too much advice on specifics; just sayin it's an option.

---

### Post by 666f6f on 2010-03-24
> **Aped said:**
> Snap, good catch 6man. 

Wanna just point out that in most BIOSes, you can disable pieces of hardware; wifi adapters are common targets of this 'hard blacklisting'. Because they're all different, I can't give you too much advice on specifics; just sayin it's an option.

Correctus!

---

### Post by Gatorade on 2010-03-29
thanks guys, I'll post back when I get through tweaking it.

---

