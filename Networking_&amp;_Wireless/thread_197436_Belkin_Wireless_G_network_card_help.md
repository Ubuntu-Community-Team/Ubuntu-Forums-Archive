---
title: "Belkin Wireless G network card help"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by killzoneman0 on 2006-06-15
Can anyone tell me how to install this Belkin Card? when i put the cd into the tray, it doesnt load the application to install drivers.  Also when the card is in at startup, it doesnt do anything.  can anyone tell me how to install the card and make it work?

thanks.

---

### Post by noname101 on 2006-06-15
You can try ndiswrapper:
Replace path/to/driver.INF with the path to the .INF file. I have no idea since I don't have a belkin card.
```
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i path/to/driver.INF
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```
For some reason doing ndiswrapper -m doesn't do enough for it to load the module at boot so do the following too:
```
sudo gedit /etc/modules
```
Add at the bottom ndiswrapper.

Then set it up using System | Administration | Networking or just do ifdown wlan0 then ifup wlan0. If its already setup.

---

### Post by killzoneman0 on 2006-06-15
after typing the password, it says

reading package lists...Done
building dependency tree...Done
E:Couldnt't find package ndiswrapper-utils


think i found it out. i might have to update some things.

---

### Post by noname101 on 2006-06-15
[http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils](http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils)
You can download it there.

---

### Post by killzoneman0 on 2006-06-16
how do you know what to put into the boxes for ip address and such? should it be static or dhcp? how would you set it up


when i tried to put an ip address and stuff in it said this when i tried to activate it.

"Check that the settings are correct for this network and that the computer is correctly connected to it."

---

### Post by acesabe on 2006-06-16
I'm trying to get this card up in the (Dapper based) Mepis 6 (RC1) - Dapper shoud load the rt2500 module (the chipset in the Belkin card) automatically (**lsmod** in a terminal) - tricky bit is config. I know the card works with older releases of Ubuntu and others - but now is a bit stubborn. I have it connect when using static IP not DHCP - but only one side so far so no web connect yet...

Also check this wiki page on how-to for the rt2500 based cards

[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo)

---

### Post by noname101 on 2006-06-16
You should use dhcp if you don't know what ip address to put in. Dhcp will get an ip address automatically.

---

### Post by killzoneman0 on 2006-06-16
when i set it to dhcp and activate the card, it wont let me connect still. it is set as eth2 and when i type that in to connect, it says disconnected when in network settings it says it is activated.  it also says that the signal strenght is 0%.  could it be  a problem with my  interfaces document in the network folder?

---

### Post by noname101 on 2006-06-17
Type lsmod and post the output here.

---

### Post by killzoneman0 on 2006-06-17
Module                  Size  Used by
binfmt_misc            15248  1
nls_cp437               8320  1
isofs                  39808  1
udf                    86816  0
rfcomm                 45600  0
l2cap                  30464  5 rfcomm
bluetooth              59268  4 rfcomm,l2cap
ppdev                  11400  0
radeon                124320  0
drm                    96296  1 radeon
powernow_k8            12992  0
cpufreq_userspace       9184  1
cpufreq_stats           8264  0
freq_table              6464  2 powernow_k8,cpufreq_stats
cpufreq_powersave       3328  0
cpufreq_ondemand        9768  0
cpufreq_conservative    10984  0
video                  18824  0
tc1100_wmi              9096  0
sony_acpi               7188  0
pcc_acpi               16128  0
hotkey                 13768  0
dev_acpi               15364  0
container               6272  0
button                  8864  0
acpi_sbs               24600  0
battery                12296  1 acpi_sbs
ac                      7176  1 acpi_sbs
i2c_acpi_ec             7040  1 acpi_sbs
i2c_core               26624  1 i2c_acpi_ec
ndiswrapper           224064  0
dm_mod                 63176  1
ipv6                  300416  10
af_packet              28172  4
md_mod                 76792  0
sr_mod                 19748  0
sbp2                   27908  0
scsi_mod              160504  2 sr_mod,sbp2
parport_pc             40816  0
lp                     15040  0
parport                44172  3 ppdev,parport_pc,lp
joydev                 13184  0
pcmcia                 46368  0
8139cp                 26752  0
snd_atiixp             23704  1
snd_atiixp_modem       19468  0
snd_ac97_codec        110268  2 snd_atiixp,snd_atiixp_modem
snd_ac97_bus            4096  1 snd_ac97_codec
snd_pcm_oss            59424  0
snd_mixer_oss          20608  1 snd_pcm_oss
psmouse                40324  0
bcm43xx               127244  0
serio_raw               9732  0
tsdev                  10240  0
snd_pcm               104584  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              29064  1 snd_pcm
snd                    68576  9 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              13216  1 snd
ieee80211softmac       32640  1 bcm43xx
pcspkr                  3592  0
snd_page_alloc         13968  3 snd_atiixp,snd_atiixp_modem,snd_pcm
8139too                31744  0
mii                     7680  2 8139cp,8139too
sdhci                  17024  0
mmc_core               35460  1 sdhci
ieee80211              39240  2 bcm43xx,ieee80211softmac
ieee80211_crypt         8448  1 ieee80211
yenta_socket           30604  2
rsrc_nonstatic         14592  1 yenta_socket
pcmcia_core            48036  3 pcmcia,yenta_socket,rsrc_nonstatic
usbhid                 43040  0
shpchp                 51360  0
pci_hotplug            33168  1 shpchp
evdev                  14464  2
ext3                  145936  1
jbd                    70952  1 ext3
ide_generic             2816  0
ehci_hcd               36232  0
ohci1394               37324  0
ieee1394              369048  2 sbp2,ohci1394
ohci_hcd               23684  0
usbcore               147004  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd
ide_cd                 35744  1
cdrom                  41144  2 sr_mod,ide_cd
ide_disk               19456  3
generic                 7300  0
atiixp                  8464  1
thermal                16524  0
processor              29224  2 powernow_k8,thermal
fan                     6408  0
capability              7176  0
commoncap               9728  1 capability
vga16fb                15120  1
cfbcopyarea             5120  1 vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4224  1 vga16fb
cfbfillrect             5760  1 vga16fb
fbcon                  43136  72
tileblit                4096  1 fbcon
font                    9984  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit

---

### Post by noname101 on 2006-06-17
Ok try this:
```
sudo modprobe -r bcm43xx
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```
If that works then edit /etc/modprobe.d/blacklist and add at the bottom blacklist bcm43xx.
```
sudo gedit /etc/modprobe.d/blacklist
```

---

### Post by killzoneman0 on 2006-06-18
how would i find the name of my home network to connect to, to see if it works?

---

### Post by noname101 on 2006-06-18
On a wired computer go to your routers ip address. Its probably either 192.168.0.1 or 192.168.1.1 or 192.168.15.1. There's no way for me to know. Though on the wired computer look at the gateway ip address, which should be the ip address of the router.

---

