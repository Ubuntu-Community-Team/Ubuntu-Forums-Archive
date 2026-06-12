---
title: "Wireles: can't obtain IP"
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by DeadEyes on 2006-01-08
Hi I'm having endless problems with my wireless network can see any solutions.

I'm using kbutunu 5.10 with a Zyxel wireless nic which has a Texas Instruments chipset (104c:9066).
The native acx111 drivers work for a while but crash out after a few minutes. There is an error message about the card can't be recalibrated. This appears the be a bug/feature not yet implemented in the acx driver so I switched to ndiswrapper. I could not find my card in their list but used a driver for another card which works and has the same chipset.

ndiswrapper -l
```

Installed ndis drivers:
netcg54l        driver present, hardware present

```

iwlist wlan0 scan shows my router
```

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:CC:2D:70:80
                    ESSID:"wssid286"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:0/100  Signal level:-44 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    ...
                    ...

```

iwconfig wlan0
```

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:4096 B   Fragment thr:4096 B
          Power Management:off
          Link Quality:100  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
from this i can see my ap hasn't been set neither has my essid, I'm not sure what off/any means!
If I use kWifiManager and set mode to AdHoc I now get this
iwconfig wlan0
```

wlan0     IEEE 802.11g  ESSID:"wssid286"
          Mode:Ad-Hoc  Frequency:2.442 GHz  Cell: 00:0F:CC:2D:70:80
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:4096 B   Fragment thr:4096 B
          Power Management:off
          Link Quality:100/100  Signal level:-45 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

by running tail -f on the syslogs I see that dhclient is constantly running but failing, the usual no offer received.

I feel like I've typed every variation of iwconfig possible, does anyone know what else I can try.

---

### Post by harisund on 2006-01-08
I doubt if you are using AdHoc. I think the managed mode is more appropriate. 

Are you using a wep key? Did you enter that anywhere? 

ok simply type this at the command line and post back if it worked.. (note: use sudo as appropriately.)

iwconfig wlan0 mode Managed essid <your essid name> key restricted <your wep key>
dhclient wlan0

---

### Post by az on 2006-01-08
Type lsmod and check to see if both the native linux driver (acx) and ndiswrapper are loaded.  If that is the case, add the module name to /etc/hotplug/blacklist and reboot.  You may have a conflict between the two modules which both want to use the ressource.

---

### Post by DeadEyes on 2006-01-08
Thanks for the replies.

[QUOTE=harisund]I doubt if you are using AdHoc. I think the managed mode is more appropriate. 

Are you using a wep key? Did you enter that anywhere? 

ok simply type this at the command line and post back if it worked.. (note: use sudo as appropriately.)

iwconfig wlan0 mode Managed essid <your essid name> key restricted <your wep key>
dhclient wlan0[/QUOTE]

I am using a WEP key it's being set in the KwifiManager. I tried the iwconfig command using the following
```

sudo iwconfig wlan0 channel 7 mode Managed essid wssid286 key restricted xxxx-xxxx-xx ap 00:0F:CC:2D:70:80 commit

```

running iwconfig wlan0
```

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:4096 B   Fragment thr:4096 B
          Power Management:off
          Link Quality:100  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


[QUOTE=azz]
Type lsmod and check to see if both the native linux driver (acx) and ndiswrapper are loaded. If that is the case, add the module name to /etc/hotplug/blacklist and reboot. You may have a conflict between the two modules which both want to use the ressource.
[/QUOTE]

```

lsmod | grep acx
returns nothing

lsmod | grep ndis
ndiswrapper           114376  0
usbcore               104316  4 ndiswrapper,ehci_hcd,uhci_hcd

```

and the whole lot
```

Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
af_packet              20232  2
floppy                 52692  0
rtc                    11832  0
pcspkr                  3652  0
emu10k1_gp              3712  0
gameport               14472  2 emu10k1_gp
snd_emu10k1x           17444  0
snd_rawmidi            22816  1 snd_emu10k1x
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_emu10k1x
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_emu10k1x,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_emu10k1x,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_emu10k1x,snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
hw_random               5268  0
pci_hotplug            24628  0
intel_agp              21276  1
nls_iso8859_1           4224  1
vfat                   12288  1
fat                    46492  1 vfat
nls_cp437               5888  2
ntfs                   92016  1
dm_mod                 50364  1
evdev                   9088  0
tsdev                   7616  0
ndiswrapper           114376  0
nvidia               3711364  12
agpgart                32328  2 intel_agp,nvidia
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
e100                   32768  0
mii                     5248  1 e100
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  4 ndiswrapper,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  5
ide_generic             1664  0
ata_piix                9476  0
libata                 47876  1 ata_piix
scsi_mod              124872  1 libata
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  310
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  67
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```

Do you think that if I try using different drivers that use the same chipset I might get better results?

---

### Post by DeadEyes on 2006-01-09
Ok I'm back on the net sans winXP.
I'm not sure how I did it though :confused: 
I'll try to come up with a definitive answer over the next few days for people scouring this place for answers.
I changed driver to dwl-g650 (I was planning on trying any driver with the same chipset)
After seeing another post I found out my nic and router protocols were different
802.11b and 802.11g
Thanks to Lambert for this  command:
```

sudo iwpriv wlan0 network_type b

```

I then ran this script which I found somewhere else (sorry can't remember where) and modified
```

iwconfig wlan0 essid wssid286 mode ad-hoc
sleep 1
iwconfig wlan0 key xxxx-xxxx-xx open
sleep 1
iwconfig wlan0 key open
iwconfig wlan0 key on
sleep 3
iwconfig wlan0 essid wssid286 mode managed
sleep 1
iwconfig wlan0 key xxxx-xxxx-xx open
sleep 1
iwconfig wlan0 key open
sleep 15

```

I hadn't wrote the script correctly so error/fix error/fix etc run.

At this point I issued the iwconfig command an saw that all my settings looked correct essid,ap etc.

I tried pinging a site with no luck tried again using an ip address with success.

so finally

```

sudo dhclient wlan0

```

and here I am :) as I said I hope to nail down the exact steps when have time but for the moment maybe this will give people some ideas.

---

