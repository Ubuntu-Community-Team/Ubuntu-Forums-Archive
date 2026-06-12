---
title: "RTL8111, got ip but no internet"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by stekke86 on 2009-04-16
Hi,

since i installed ubuntu 8.10 my wired connection doesn't work anymore, never had any problems with it before.
The problem is not the driver because I tried this already.

When I plug in my cable the ethernet gets an ip-address from a dhcp this happens correctly, my wireless is also connected. I see the network manager wanting to use the wired connection but something goes wrong because I can't open a webpage, surf to the router or ping an ip address (internal or external).
I already made a file with some output and attached it here, you can see the error in dmesg.

The wireless connection works fine.

I already searched the forum but couldn't find a solution,
hopefully someone can help me?

Thanks in regards,
Stijn

---

### Post by superprash2003 on 2009-04-16
bring down one of the interfaces and then try..
for example :

first bring down eth0 by typing **sudo ifdown eth0** .. does it work now? to bring it back type sudo ifup eth0.. If that doesnt work , try bringing down wlan0

---

### Post by stekke86 on 2009-04-16
Bringing down an interface doesn't help, I tried every order with that.
Wireless always works, wired doesn't.

Greets,
Stijn

---

### Post by superprash2003 on 2009-04-17
so bringing down , the wireless interface.. and then trying using only the wired interface doesnt work? if so , then you would want to try running another OS on this pc to see if your NIC hardware is working

---

### Post by stekke86 on 2009-04-17
Tried this already under windows the wired connection works.
I have also tried that windows may not power the ethernet card down at shutdown, I read it at the forum but it didn't help either.

Greets, 
Stijn

---

### Post by Crafty Kisses on 2009-04-17
What are the results of these commands?
```
iwconfig
lsmod
```

---

### Post by stekke86 on 2009-04-17
**_iwconfig:_**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"WiFi_STEKKE"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:6A:99:71:45   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=59/100  Signal level:-72 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.


**_lsmod:_**
Module                  Size  Used by
xt_limit               10372  8 
xt_tcpudp              11008  19 
ipt_LOG                13700  8 
ipt_MASQUERADE         10752  0 
xt_DSCP                11264  0 
ipt_REJECT             11136  1 
nf_conntrack_irc       13348  0 
nf_conntrack_ftp       15652  0 
xt_state               10112  6 
cifs                  254372  0 
af_packet              25728  4 
vmnet                  48580  13 
vmci                   58964  0 
vmmon                  78064  0 
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
rfcomm                 44560  0 
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
vboxdrv                71576  0 
ppdev                  15748  0 
ipv6                  263972  23 
acpi_cpufreq           15500  1 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container              11520  0 
pci_slot               12680  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
nls_iso8859_1          12032  3 
nls_cp437              13696  3 
vfat                   18944  3 
fat                    57376  1 vfat
parport_pc             39332  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
mmc_block              17924  2 
tifm_sd                18184  0 
pcmcia                 43052  0 
acer_wmi               19008  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
psmouse                45200  0 
joydev                 18368  0 
serio_raw              13444  0 
evdev                  17696  14 
pcspkr                 10624  0 
gspca_vc032x           26112  0 
gspca_main             29312  1 gspca_vc032x
videodev               41344  1 gspca_main
v4l1_compat            22404  1 videodev
tifm_7xx1              13824  0 
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
battery                18436  0 
ac                     12292  0 
mmc_core               58268  3 mmc_block,tifm_sd,sdhci
tifm_core              16028  2 tifm_sd,tifm_7xx1
iwl3945                98932  0 
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
rfkill                 17176  2 iwl3945
mac80211              216820  1 iwl3945
led_class              12164  2 acer_wmi,iwl3945
cfg80211               32392  2 iwl3945,mac80211
r8168                  48144  0 
snd_hda_intel         384176  6 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  2 snd_pcm_oss
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
nvidia               6909268  38 
i2c_core               31892  1 nvidia
snd_seq_dummy          10884  0 
video                  25232  8 
output                 11008  1 video
snd_seq_oss            38528  0 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
wmi                    14504  1 acer_wmi
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
button                 14224  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  2 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
intel_agp              33724  0 
agpgart                42184  2 nvidia,intel_agp
iptable_nat            13448  0 
nf_nat                 25368  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      21900  9 iptable_nat,nf_nat
nf_conntrack           72032  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle         10880  0 
iptable_filter         10752  1 
ip_tables              19600  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22916  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  5 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_piix               24708  4 
ata_generic            12932  0 
uhci_hcd               30864  0 
pata_acpi              12160  0 
ehci_hcd               43788  0 
libata                178208  3 ata_piix,ata_generic,pata_acpi
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
usbcore               149488  6 gspca_vc032x,gspca_main,usbhid,uhci_hcd,ehci_hcd
r8169                  36100  0 
mii                    13440  1 r8169
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3

---

