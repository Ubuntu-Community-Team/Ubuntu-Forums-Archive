---
title: "Wireless Repeatedly Disconnects from Good WiFi Connection"
date: 2013-01-14
forum: Networking &amp; Wireless
---

### Post by kenizl86 on 2013-01-14
For some reason, randomly (and once it starts it repeats about every 40 sec), and repeatedly the Wifi disconnects from a good, strong connection. When it does disconnect, I have to switch the built-in card off (by way of key combo on laptop), then on again and it re-connects. Anybody have any ideas on how to fix it? Thanks for any help!

---

### Post by ahallubuntu on 2013-01-14
What make/model laptop do you have?

What version of Ubuntu are you using?

What type of wireless security is your router using?  (WEP?  WPA2?)

What kind of wireless card?  Open a Terminal window and type this:

sudo lshw -C network

and please paste the output here.

---

### Post by kenizl86 on 2013-01-14
Sorry, I should have posted that in the first place!

Laptop Model: Dell Latitude D600

Ubuntu: Xubuntu 12.04

Wifi Encryption: I'm not to sure how to find this (strangely enough)

Terminal Info:
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:b5:ef:15
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=5705-v3.16 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Network controller
       product: BCM4306 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fafee000-fafeffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:96:ae:80:74
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-35-generic firmware=351.126 link=no multicast=yes wireless=IEEE 802.11bg


Hope that helps!

---

### Post by praseodym on 2013-01-14
This card is shipped with several chipsets. Please show:
```

lspci -nnk | grep -iA2 net
dmesg | grep b43
```
Try pure WPA2-AES (CCMP) encryption, if possible.

---

### Post by kenizl86 on 2013-01-14
lspci:

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
    Subsystem: Dell Latitude D400 [1028:865d]
    Kernel driver in use: tg3
--
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)
    Subsystem: Dell Truemobile 1450 MiniPCI [1028:0003]
    Kernel driver in use: b43-pci-bridge



dmesg:


[   26.499713] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   26.499720] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[   26.499725] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 2032.016290] b43-phy0: Radio hardware status changed to DISABLED
[ 2037.008295] b43-phy0: Radio hardware status changed to ENABLED
[ 2037.156282] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 2037.156296] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 2037.156310] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 2137.008080] b43-phy0: Radio hardware status changed to DISABLED
[ 2142.016292] b43-phy0: Radio hardware status changed to ENABLED
[ 2142.164240] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 2142.164247] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 2142.164252] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 2217.008290] b43-phy0: Radio hardware status changed to DISABLED
[ 2222.016282] b43-phy0: Radio hardware status changed to ENABLED
[ 2222.164283] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 2222.164298] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 2222.164312] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 2262.016158] b43-phy0: Radio hardware status changed to DISABLED
[ 2272.016315] b43-phy0: Radio hardware status changed to ENABLED
[ 2272.164314] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 2272.164328] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 2272.164342] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 2347.008262] b43-phy0: Radio hardware status changed to DISABLED
[ 2352.016108] b43-phy0: Radio hardware status changed to ENABLED
[ 2352.160076] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 2352.160083] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 2352.160088] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 2437.008277] b43-phy0: Radio hardware status changed to DISABLED
[ 2442.016189] b43-phy0: Radio hardware status changed to ENABLED
[ 2442.160107] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 2442.160122] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 2442.160135] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 2477.041101] b43-phy0: Radio hardware status changed to DISABLED
[ 2482.016309] b43-phy0: Radio hardware status changed to ENABLED
[ 2482.164092] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 2482.164107] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 2482.164121] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 4042.024382] b43-phy0: Radio hardware status changed to DISABLED
[ 4052.016090] b43-phy0: Radio hardware status changed to ENABLED
[ 4052.164069] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 4052.164083] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 4052.164097] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 4122.016060] b43-phy0: Radio hardware status changed to DISABLED
[ 4127.008101] b43-phy0: Radio hardware status changed to ENABLED
[ 4127.152091] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 4127.152098] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 4127.152103] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 4297.008247] b43-phy0: Radio hardware status changed to DISABLED
[ 4302.016316] b43-phy0: Radio hardware status changed to ENABLED
[ 4302.164119] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 4302.164134] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 4302.164148] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 4467.008246] b43-phy0: Radio hardware status changed to DISABLED
[ 4472.016287] b43-phy0: Radio hardware status changed to ENABLED
[ 4472.164296] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 4472.164311] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 4472.164324] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 4722.016087] b43-phy0: Radio hardware status changed to DISABLED
[ 4727.008271] b43-phy0: Radio hardware status changed to ENABLED
[ 4727.156272] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 4727.156287] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 4727.156300] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 4797.008482] b43-phy0: Radio hardware status changed to DISABLED
[ 4802.016295] b43-phy0: Radio hardware status changed to ENABLED
[ 4802.164239] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 4802.164245] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 4802.164251] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 4882.016088] b43-phy0: Radio hardware status changed to DISABLED
[ 4887.008102] b43-phy0: Radio hardware status changed to ENABLED
[ 4887.156111] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 4887.156125] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 4887.156139] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 5427.008110] b43-phy0: Radio hardware status changed to DISABLED
[ 5462.016132] b43-phy0: Radio hardware status changed to ENABLED
[ 5462.164077] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 5462.164091] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 5462.164105] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 5587.012296] b43-phy0: Radio hardware status changed to DISABLED
[ 5587.036042] b43-phy0: Radio turned on by software
[ 5587.036048] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 5592.016302] b43-phy0: Radio hardware status changed to ENABLED
[ 5592.156249] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 5592.156259] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 5592.156267] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 5707.008277] b43-phy0: Radio hardware status changed to DISABLED
[ 5712.016146] b43-phy0: Radio hardware status changed to ENABLED
[ 5712.164270] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 5712.164282] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 5712.164292] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 5792.016270] b43-phy0: Radio hardware status changed to DISABLED
[ 5797.008323] b43-phy0: Radio hardware status changed to ENABLED
[ 5797.156262] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 5797.156272] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 5797.156280] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 5867.008285] b43-phy0: Radio hardware status changed to DISABLED
[ 5877.008109] b43-phy0: Radio hardware status changed to ENABLED
[ 5877.156186] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 5877.156201] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 5877.156215] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 5942.016066] b43-phy0: Radio hardware status changed to DISABLED
[ 5947.008302] b43-phy0: Radio hardware status changed to ENABLED
[ 5947.156182] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 5947.156197] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 5947.156211] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 6317.008068] b43-phy0: Radio hardware status changed to DISABLED
[ 6322.016284] b43-phy0: Radio hardware status changed to ENABLED
[ 6322.164241] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 6322.164248] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 6322.164254] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 6422.016061] b43-phy0: Radio hardware status changed to DISABLED
[ 6432.016201] b43-phy0: Radio hardware status changed to ENABLED
[ 6432.164297] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 6432.164312] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[ 6432.164326] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.




How do I do the last suggestion? I'm not to savvy with Linux, so..... yeah.

---

### Post by tgalati4 on 2013-01-14
What is the signal strength as shown in the status bar?  If the signal is too strong, it will shut down the wireless card as a safety precaution.  I have a similar card in my laptop and static electricity will shut it down.  Remove your Ugg boots.

Try reseating the card and antenna connectors.  There should be easy access on the underside.  Dells are kind of flimsy, so things loosen up over time--much like an American car.

---

### Post by kenizl86 on 2013-01-15
The connection is mostly just about 54 mb/s, which I think the max for the card.

I'll try reseating it like you said and see if that works.

---

### Post by praseodym on 2013-01-15
Did you install the package "linux-firmware-nonfree"?

---

### Post by tgalati4 on 2013-01-15
The 40-second interval is interesting.  Do you live near a radar station?

---

### Post by kenizl86 on 2013-01-16
No, I don't. It's not precisely 40 sec, but it ranges around that. Sometimes it stops disconnecting for a while, then goes on another disconnecting spree.

About the "linux-firmware-nonfree" thing, I did not. I had to go through this lengthy process to get the firmware for the card installed (that was a while ago). Are you recommending I do?

---

### Post by praseodym on 2013-01-16
Yes, try that package, reboot, and check
```

dmesg | grep b43
iwconfig
```

---

### Post by kenizl86 on 2013-01-24
I downloaded the package, but it still does it!

Here's the "dmesg" output:

[   25.975629] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   26.072035] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   26.174880] Registered led device: b43-phy0::tx
[   26.174964] Registered led device: b43-phy0::rx
[   26.175049] Registered led device: b43-phy0::radio
[   29.816214] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  234.832408] b43-phy0: Radio hardware status changed to DISABLED
[  234.860103] b43-phy0: Radio turned on by software
[  234.860122] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[  239.824358] b43-phy0: Radio hardware status changed to ENABLED
[  239.924356] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  355.008323] b43-phy0: Radio hardware status changed to DISABLED
[  360.020013] b43-phy0: Radio hardware status changed to ENABLED
[  360.136326] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  990.016316] b43-phy0: Radio hardware status changed to DISABLED
[  995.008404] b43-phy0: Radio hardware status changed to ENABLED
[  995.116243] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 1075.008377] b43-phy0: Radio hardware status changed to DISABLED
[ 1080.016435] b43-phy0: Radio hardware status changed to ENABLED
[ 1080.124361] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)


And here's the "iwconfig" output:

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"HCPLC-Library"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: AC:67:06:1D:31:78   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

eth0      no wireless extensions.

---

### Post by praseodym on 2013-01-25
Ok, plus:
```

rfkill list
lsmod
```

---

### Post by kenizl86 on 2013-01-25
"rfkill":

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

"lsmod":

```

Module                  Size  Used by
pci_stub               12550  1 
vboxpci                22911  0 
vboxnetadp             13328  0 
vboxnetflt             27240  0 
vboxdrv               252189  3 vboxpci,vboxnetadp,vboxnetflt
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
radeon                733824  2 
dcdbas                 14098  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
dm_multipath           22747  0 
psmouse                96718  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39826  0 
serio_raw              13027  0 
snd                    62218  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
video                  19068  0 
mac_hid                13077  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
yenta_socket           27428  0 
drm                   197641  4 radeon,ttm,drm_kms_helper
pcmcia_rsrc            18367  1 yenta_socket
bnep                   17830  2 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
rfcomm                 38139  4 
parport_pc             32114  1 
bluetooth             158479  10 bnep,rfcomm
ppdev                  12849  0 
binfmt_misc            17292  1 
arc4                   12473  2 
i2c_algo_bit           13199  1 radeon
shpchp                 32325  0 
b43                   342669  0 
mac80211              436493  1 b43
cfg80211              178877  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   137273  0 
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16100  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash

```

---

### Post by praseodym on 2013-01-26
```
 [ 234.860122] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
```
Try to reset the BIOS to default settings.

---

### Post by kenizl86 on 2013-01-26
Default for wireless, or for everything in the BIOS?

---

### Post by praseodym on 2013-01-26
Everything

---

### Post by kenizl86 on 2013-01-29
Oddly enough, there doesn't seem to be a "Reset" option in my BIOS. Is there another way to do it?

There is a thing saying that the Wifi in Enabled, and that it can be disabled by "Fn+F2" key.

---

### Post by kenizl86 on 2013-02-25
I reset the BIOS on mine (mine required me to press Alt-F), but it still disconnects. Also, if it helps any, this was the thread that help me set up my Wifi:

[http://ubuntuforums.org/showthread.php?t=2080371](http://ubuntuforums.org/showthread.php?t=2080371)

I sincerely believe it is a software issue, because I previously had Windows XP running on it with no issues with the wifi card.

---

### Post by praseodym on 2013-02-26
Try to update the driver via:
```

sudo apt-get install --reinstall linux-headers-generic build-essential dkms linux-backports-modules-3.6-precise generic
```Reboot.

---

### Post by kenizl86 on 2013-02-28
I put that in and I got this:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-3.6-precise
E: Couldn't find any package by regex 'linux-backports-modules-3.6-precise'
E: Unable to locate package generic

```

---

### Post by kenizl86 on 2013-03-01
Should I try modifying it through iwconfig or ifconfig (somehow)?

---

### Post by bellaseem on 2013-03-01
Well I'm no expert but this seems to stabilize my connection massively, at the expense of making it slower (128kbps speed), so heck try it you have nothing to lose.
```
 sudo iwconfig wlan0 rate 1M 
```

You might need to change wlan0 to your cards name (it could be wlan1 , or some other name like phy0 phy1 , whatever it is...) 

Also if it does get stable (it does for me) try increasing to 2M , 5M , etc... untill you reach a rate that's high and the connection starts dropping again.

---

### Post by praseodym on 2013-03-01
```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms linux-backports-modules-3.6-precise-generic
```
Sorry, I forgot a "-" at the end. Try it again.

---

### Post by kenizl86 on 2013-03-03
(praseodym) I ran it again, and again I got the same thing as last time.

---

### Post by kenizl86 on 2013-03-05
Also, i tried the "iwconfig wlan0 rate 48M" [bellaseem] (that's what I set it to), and it seemed to work, but it's hard to tell for sure.

---

### Post by kenizl86 on 2013-03-05
Uhp, no nevermind. I lied. It didn't work at all. It still is being it's usual, frustrating self.

---

### Post by kenizl86 on 2013-03-10
Anybody have any idea what's wrong? Could it just be that my laptop is in that category of "Not-That-Supported"?

---

### Post by praseodym on 2013-03-10
Try this firmware package:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
```
It contains a file, which may be needed!

---

### Post by kenizl86 on 2013-03-11
I just ran that and rebooted the comp, and after a good 10 min, it disconnected from the internet again. My wifi says I'm getting about 2-3 bars out of 4, and it's running at 54mb/s.

---

