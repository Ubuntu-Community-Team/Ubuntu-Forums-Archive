---
title: "Dell wireless 1450 USB adapter"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by fastkid105 on 2011-08-05
Hey guys,

i am pretty new to ubuntu. I use **Ubuntu 10.04** and I can't connect internet using **dell wireless 1450 USB adapter. **

Please help me :confused:
Thanks

---

### Post by wildmanne39 on 2011-08-05
Hi, please run these commands
```
lsusb
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by fastkid105 on 2011-08-05
Thankyou for quick reply :)

```
chikku@fridge:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1267:0201 Logic3 / SpectraVideo plc A4Tech SWOP-3 Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 413c:8104 Dell Computer Corp. Wireless 1450 Dual-band (802.11a/b/g) USB2.0 Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
chikku@fridge:~$ lspci -nn l grep 0280
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
chikku@fridge:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

chikku@fridge:~$ rfkill list all
chikku@fridge:~$ lsmod
Module                  Size  Used by
p54usb                 10876  0 
p54common              24921  1 p54usb
led_class               2864  1 p54common
mac80211              204922  2 p54usb,p54common
cfg80211              126485  2 p54common,mac80211
usbhid                 36110  0 
hid                    67032  1 usbhid
mga                    28320  3 
drm                   162471  4 mga
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
ppdev                   5259  0 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                11385  1 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
intel_agp              24177  1 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
parport_pc             25962  1 
shpchp                 28820  0 
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
floppy                 53016  0 
chikku@fridge:~$ 


```

---

### Post by wildmanne39 on 2011-08-05
Hi, run these commands please:
```
dmesg | grep p54
```
```
lsmod | grep p54
```
```
modinfo p54 | grep 8104
```
and post the results here.
Thank you

---

### Post by fastkid105 on 2011-08-08
hey 
```
chikku@fridge:~$ dmesg | grep p54
[   17.232498] usb 1-3: (p54usb) cannot load firmware isl3887usb (-2)!
[   17.246761] p54usb: probe of 1-3:1.0 failed with error -2
[   17.246811] usbcore: registered new interface driver p54usb
chikku@fridge:~$ lsmod | grep p54
p54usb                 10876  0 
p54common              24921  1 p54usb
led_class               2864  1 p54common
mac80211              204922  2 p54usb,p54common
cfg80211              126485  2 p54common,mac80211
chikku@fridge:~$ modinfo p54 | grep 8104
ERROR: modinfo: could not find module p54
chikku@fridge:~$ 

```

---

### Post by wildmanne39 on 2011-08-08
Hi, unplug your wired connection then run these two commands and see if your wireless come on.
```
sudo modprobe -r p54usb 
sudo modprobe p54usb
```

Also has your wireless ever worked?
Thank you

---

### Post by wildmanne39 on 2011-08-08
Hi, if the other suggestion does not get your wireless usb working run this command again please:
```
lspci -nn | grep 0280
```
just copy and paste it.
Thank you

---

### Post by fastkid105 on 2011-08-08
Still not working, and yes my wireless has worked when using windows
```
chikku@fridge:~$ sudo modprobe -r p54 usb
[sudo] password for chikku: 
FATAL: Module p54 not found.
chikku@fridge:~$ sudo modprobe p54usb
chikku@fridge:~$ lspci -nn | grep 0280

```

---

### Post by wildmanne39 on 2011-08-08
Hi, connect to your wired internet connection then try this please.
```
sudo apt-get install linux-firmware-nonfree
``` 
Thank you

---

### Post by fastkid105 on 2011-08-09
That sorts it out, thanks man your are an ABSOLUTE LEGEND! :D

---

### Post by wildmanne39 on 2011-08-09
Hi, your welcome, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

