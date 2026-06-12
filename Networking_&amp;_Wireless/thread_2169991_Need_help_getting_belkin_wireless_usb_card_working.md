---
title: "Need help getting belkin wireless usb card working"
date: 2013-08-24
forum: Networking &amp; Wireless
---

### Post by vanquishedangel on 2013-08-24
OK, I need to get this working as soon as possible, the OS is Ubuntu 13.04 64 bit and the card is a belkin n150 fdl1001

[B]outputs with device plugged in:
[/B]
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ lsusb
Bus 001 Device 004: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
Bus 004 Device 002: ID 0461:4d42 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ 

shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ /sbin/iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ 

[B]On another computer with ubuntu installed it is working, here are its out puts:
[/B]
judy@judy-HP-Compaq-dc7100-SFF-PC923A:~$ lsusb
Bus 001 Device 015: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
Bus 002 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 003: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
judy@judy-HP-Compaq-dc7100-SFF-PC923A:~$ 

judy@judy-HP-Compaq-dc7100-SFF-PC923A:~$ /sbin/iwconfig
wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

judy@judy-HP-Compaq-dc7100-SFF-PC923A:~$ 


I have tried ndiswrapper to no avail, either the drivers dont work or they freeze the computer up. I have also tried "sudo modprobe r8712u" and it gives no errors. I have also tried "ipconfig wlan0 up" but it fails, something about module not loaded. Also this wireless card works great from the live ubuntu cd. I have searched til my eyes were ready to bleed and can olnly find how tos and such for older ubuntu's and for ndis wrapper.

---

### Post by kurt18947 on 2013-08-24
It works from the same 'flavor' live CD but not from a hard drive install?  Hmmm.  It seems that a driver that your device likes is included on the CD.  There are a some experts in this stuff, I am not one.  One thing I'd probably try would be to either connect as a guest or create a new temporary account and try to connect from there.  I wonder if there's something in your /home/user folder that's causing problems.  I don't really have anything else to offer.  Perhaps you could post the output of "lsmod" so everyone can see which modules are loading.  Perhaps there are two fighting over the one adapter or something.

---

### Post by vanquishedangel on 2013-08-24
output of lsmod

Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39815  1 
vesafb                 13828  1 
zram                   18439  2 
xt_hl                  12521  6 
ip6t_rt                12529  3 
nf_conntrack_ipv6      18335  7 
nf_defrag_ipv6         13201  1 nf_conntrack_ipv6
ipt_REJECT             12541  1 
xt_LOG                 17400  9 
xt_limit               12711  12 
xt_tcpudp              12603  18 
xt_addrtype            12635  4 
nf_conntrack_ipv4      14487  7 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_state               12578  14 
ip6table_filter        12815  1 
ip6_tables             27025  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
fglrx                5201161  60 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12620  0 
nf_nat                 25867  1 nf_nat_ftp
nf_conntrack_ftp       13342  1 nf_nat_ftp
bnep                   18036  2 
nf_conntrack           83275  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_state,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12810  1 
rfcomm                 42641  0 
ip_tables              26995  1 iptable_filter
bluetooth             228619  10 bnep,rfcomm
snd_hda_codec_hdmi     36913  1 
x_tables               29803  12 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_state,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  1 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ndiswrapper           283323  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
kvm_amd                59717  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
kvm                   443165  1 kvm_amd
snd_timer              29425  2 snd_pcm,snd_seq
psmouse                95870  0 
hp_wmi                 18048  0 
sp5100_tco             13735  0 
snd                    68876  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
sparse_keymap          13890  1 hp_wmi
shpchp                 37032  0 
amd_iommu_v2           19068  1 fglrx
serio_raw              13215  0 
i2c_piix4              13266  0 
k8temp                 12978  0 
edac_core              62003  0 
wmi                    19070  1 hp_wmi
edac_mce_amd           23114  0 
ppdev                  17073  0 
mac_hid                13205  0 
parport_pc             28152  1 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
binfmt_misc            17500  1 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
pata_acpi              13038  0 
pata_atiixp            13242  0 
floppy                 69449  0 
pata_sil680            13254  2 
tg3                   153796  0 
ptp                    18621  1 tg3
pps_core               14080  1 ptp
ahci                   25731  2 
libahci                31364  1 ahci
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$

---

### Post by kurt18947 on 2013-08-26
To reiterate, I'm no expert but one thing caught my attention.  The adapter works with the live CD so the device is recognized by and works with a 'built-in' driver.  In your 'lsmod' output I see NDISwrapper but no other wifi module that I recognize, not that I'd recognize any and all modules.  There's appears to be no need for NDISwrapper, that is normally used when there is no 'built-in' driver which there is in your case.  I wonder if something to do with NDISwrapper is interfering with the 'built-in' driver and preventing it from driving the device.  Just a guess.  Maybe one of the wifi wizards will check in here.

---

### Post by vanquishedangel on 2013-09-16
I just installed from the disk and it worked, however I have since replacwed the card and bought a different one, ndiswrapper was thewr because After ubuntu wouldn't see the card I gave ndiswrapper a shot, it didnt work. thank you for your time thought.

---

