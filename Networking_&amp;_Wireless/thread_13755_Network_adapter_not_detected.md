---
title: "Network adapter not detected?"
date: 2005-02-02
forum: Networking &amp; Wireless
---

### Post by Swab on 2005-02-02
I just installed Warty on my old Toshiba Portege 3020CT.    As I have no CD-ROM or floppy, I installed by booting to Debian and installing following the install from knoppix instructions.   All seemed to go well.

The problem is that  the network is not working.   /etc/network/interfaces was empty after installing, so copied over my interfaces from Debian, still no luck.  The adapter in question is a D-Link DFE-690TXD, it works perfectly in Debian and other distributions.

What should I be doing, to get this working?

Thanks

---

### Post by mendicant on 2005-02-02
Since it works in Debian, check what modules are loaded:
% lsmod

Check to make sure these modules are also loaded on your Ubuntu install, putting them in /etc/modules if they aren't loaded automatically by some other mechanism (hotplug, discover etc).  If you post the output of lsmod, somebody could probably tell you what is likely to be the module(s) for your card.

---

### Post by Swab on 2005-02-02
OK, well the outputs from Ubuntu and Debian are very different.

First Ubuntu:

```
Module                  Size  Used by
proc_intf               3968  0 
freq_table              4356  0 
cpufreq_userspace       5336  0 
cpufreq_powersave       2048  0 
ipv6                  230020  6 
button                  6936  0 
ac                      5132  0 
battery                 9740  0 
af_packet              20872  0 
yenta_socket           19328  1 
pcmcia_core            63156  1 yenta_socket
donauboe               15360  0 
irda                  167360  1 donauboe
crc_ccitt               2432  2 donauboe,irda
ohci_hcd               19460  0 
usbcore               104292  3 ohci_hcd
parport_pc             32064  0 
parport                37320  1 parport_pc
floppy                 54996  0 
tsdev                   7168  0 
mousedev               10124  1 
rtc                    12216  0 
psmouse                17800  0 
pcspkr                  3816  0 
evdev                   9088  0 
md                     44744  0 
dm_mod                 51068  1 
capability              4872  0 
commoncap               7168  1 capability
ext3                  109544  1 
jbd                    54552  1 ext3
ide_generic             1664  0 
ide_disk               16768  3 
ide_core              125272  2 ide_generic,ide_disk
unix                   26160  498 
fan                     4236  0 
thermal                13200  0 
processor              17712  1 thermal
font                    8576  0 
vesafb                  6688  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

```


And here is the lsmod output from Debian:

```
Module                  Size  Used by
hid                    22464  -
ext3                   95520  -
jbd                    49432  -
snd_ymfpci             54016  -
snd_ac97_codec         45796  -
snd_pcm                81376  -
snd_opl3_lib            8640  -
snd_timer              20000  -
snd_hwdep               6816  -
gameport                3616  -
snd_page_alloc          9028  -
snd_mpu401_uart         5632  -
snd_rawmidi            18944  -
snd_seq_device          6340  -
rtc                    10272  -
```

---

### Post by Swab on 2005-02-02
[QUOTE=][/QUOTE]
 This is what i get when i do ifup eth0 , maybe some clues here?


Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
irda0: unknown hardware address type 783
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
irda0: unknown hardware address type 783
Bind socket to interface: No such device
Failed to bring up eth0.

---

### Post by Swab on 2005-02-03
I figured it out... pcmcia-cs was not installed.  I have no idea why !

---

