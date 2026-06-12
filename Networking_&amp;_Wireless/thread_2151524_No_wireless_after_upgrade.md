---
title: "No wireless after upgrade"
date: 2013-06-04
forum: Networking &amp; Wireless
---

### Post by pplatypus on 2013-06-04
I had very slow wireless before and recently upgraded from 10.04 to 12.04.  I tried to install the driver from compat-wireless also to speed it up, but apparently that failed.  Now I have no wireless network availability (no networks recognized).  I have been googling around a little to no avail, so any help is appreciated.

Some output:
```

lsb_release -d
Description:    Ubuntu 12.04.2 LTS

```

```
~$ lspci -nn |grep 'Ralink'
03:00.0 Network controller [0280]: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe [1814:0781]

```

```
~$ iwconfig
eth1      no wireless extensions.


lo        no wireless extensions.

```
```
$ lsmod
Module                  Size  Used by
vesafb                 13846  1 
nvidia              11309216  50 
xt_hl                  12522  6 
ip6t_rt                12559  3 
nf_conntrack_ipv6      14107  7 
nf_defrag_ipv6         13413  1 nf_conntrack_ipv6
ipt_REJECT             12577  1 
xt_LOG                 17454  9 
xt_limit               12712  12 
xt_tcpudp              12604  18 
xt_addrtype            12714  4 
snd_hda_codec_hdmi     32476  4 
xt_state               12579  14 
ip6table_filter        12816  1 
ip6_tables             27686  2 ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12666  0 
nf_conntrack_broadcast    12590  1 nf_conntrack_netbios_ns
nf_nat_ftp             12705  0 
nf_nat                 25646  1 nf_nat_ftp
nf_conntrack_ipv4      14531  9 nf_nat
coretemp               13642  0 
kvm                   422160  0 
ghash_clmulni_intel    13221  0 
aesni_intel            51134  0 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
nf_defrag_ipv4         12730  1 nf_conntrack_ipv4
nf_conntrack_ftp       13453  1 nf_nat_ftp
nf_conntrack           83300  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12811  1 
ip_tables              27474  1 iptable_filter
x_tables               29892  12 xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
psmouse               102506  0 
gpio_ich               13384  0 
snd_hda_codec_realtek    79855  1 
tpm_tis                18767  0 
eeprom_93cx6           13345  0 
snd_hda_intel          34063  5 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
serio_raw              13216  0 
mei                    41410  0 
microcode              23030  0 
lpc_ich                17145  0 
mac_hid                13254  0 
wmi                    19257  0 
parport_pc             32867  0 
ppdev                  17114  0 
nfsd                  263170  2 
nfs                   382064  0 
lockd                  77424  2 nfsd,nfs
fscache                61535  1 nfs
auth_rpcgss            41227  2 nfsd,nfs
nfs_acl                12884  2 nfsd,nfs
sunrpc                245472  6 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
binfmt_misc            17541  1 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
usb_storage            49288  0 
ahci                   25869  3 
libahci                27338  1 ahci
e1000e                198734  0 
btrfs                 781125  0 
zlib_deflate           27140  1 btrfs
libcrc32c              12645  1 btrfs

```

---

### Post by Hadaka on 2013-06-04
Hi, It looks like your device will run on the
rt2800 pci driver. I dont know how well since
your card is N only, but give it a try.
```
sudo apt get update
sudo modprobe -v rt2800pci
```
is it showing a wireless connection now?

---

### Post by pplatypus on 2013-06-04
Unfortunately no, after the upgrade I get:

```
$ sudo modprobe -v rt2800pciinsmod /lib/modules/3.5.0-32-generic/updates/compat/compat.ko 
WARNING: Error inserting compat (/lib/modules/3.5.0-32-generic/updates/compat/compat.ko): Invalid module format
WARNING: Error inserting cfg80211 (/lib/modules/3.5.0-32-generic/updates/net/wireless/cfg80211.ko): Invalid module format
WARNING: Error inserting mac80211 (/lib/modules/3.5.0-32-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting rt2x00lib (/lib/modules/3.5.0-32-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Invalid module format
WARNING: Error inserting rt2x00pci (/lib/modules/3.5.0-32-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko): Invalid module format
WARNING: Error inserting crc_ccitt (/lib/modules/3.5.0-32-generic/kernel/lib/crc-ccitt.ko): Invalid module format
WARNING: Error inserting rt2800lib (/lib/modules/3.5.0-32-generic/updates/drivers/net/wireless/rt2x00/rt2800lib.ko): Invalid module format
FATAL: Error inserting rt2800pci (/lib/modules/3.5.0-32-generic/updates/drivers/net/wireless/rt2x00/rt2800pci.ko): Invalid module format



```

---

### Post by Hadaka on 2013-06-04
Looks like its bumping heades with the compat wireless driver
but, i have never removed the compat driver..i did find this on
a search.
Please keep in mind that linux-backports-modules install modules in  /lib/modules/$(uname -r)/updates/ and upon removal the modules are not  removed. So be sure to rm -rf that updates directory (and only the  updates directory!). 
is this what you installed...
linux-backport-modules...compat-wireless?

---

### Post by chili555 on 2013-06-04
rt2800pci is correct for your device:> chili@Think410:~$ modinfo rt2800pci | grep 0781
alias:          pci:v0000[COLOR="#FF0000"]1814[/COLOR]d0000[COLOR="#FF0000"]0781[/COLOR]sv*sd*bc*sc*i*However, this is a sure sign of a compat-wireless compile gone horribly wrong:> WARNING: Error inserting compat (/lib/modules/3.5.0-32-generic/updates/compat/compat.ko): Invalid module formatWhat package did you compile? How many errors, warnings, sparks, smoke, etc. came up? Please post:```
uname -r
modinfo rt2800pci | head -n5
```Fun!!

---

### Post by pplatypus on 2013-06-04
I didn't notice any problems installing compat-wireless but I must have missed something. 
```
~$ uname -r3.5.0-32-generic

~$ modinfo rt2800pci | head -n5
filename:       /lib/modules/3.5.0-32-generic/updates/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0



```

---

### Post by chili555 on 2013-06-04
> I didn't notice any problems installing compat-wirelessIt didn't install correctly, otherwise, you wouldn't see those errors. Which package did you compile? Did you also try linux-backports-modules?

---

### Post by pplatypus on 2013-06-04
I just installed compat-wireless-3.5.4-1-snpc straight from the compat wireless page.  I'm not sure what linux-backports-modules is, should I try that now?

---

### Post by Hadaka on 2013-06-04
Hi, no dont load anything, chili555 is probably finding a way
to undo what was loaded,please be patient.
thanks.

---

### Post by chili555 on 2013-06-04
Please try this:```
cd Desktop/compat-wireless-3.5.4-1-snpc  [COLOR="#FF0000"]<--or wherever you extracted the files[/COLOR]
sudo su
make uninstall
./scripts/driver-select restore
make clean
./scripts/driver-select rt2x00
make
make install
modprobe -r rt2800pci
modprobe rt2800pci
exit
```If there are _any_ errors or warnings, Hadaka and I want to see them. Thanks.

---

### Post by pplatypus on 2013-06-04
Worked like a charm.  Thank you so much!

---

### Post by Hadaka on 2013-06-04
Great !, glad its working.
please mark this thread solved.
How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

### Post by chili555 on 2013-06-05
Great news. I love the smell of Solved in the morning.

---

