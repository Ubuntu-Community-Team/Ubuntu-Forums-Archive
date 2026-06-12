---
title: "Trouble installing drivers for intel proset4965AGN"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by Maus1231 on 2009-01-04
Linux (mostly) noob) here...
trying to set up a wireless connection in kubuntu...using an intel pro/set 4965AGN card...iv tried some how-to sites and so far nothing has worked,

one thing iv tried that hasnt worked is this --> 
[http://intellinuxwireless.org/?p=mac80211&n=howto-mac80211](http://intellinuxwireless.org/?p=mac80211&n=howto-mac80211)
which is supposed to lead to -->
[http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)

the first wget works properly and the file downloads

the next set of commands returns this:

darkwings@D4rkbooK:~$ tar xvf mac80211-10.0.4.tgz
mac80211-10.0.4/origin/GIT
mac80211-10.0.4/origin/net/mac80211/debugfs_sta.h
mac80211-10.0.4/origin/net/mac80211/ieee80211.c
mac80211-10.0.4/origin/net/mac80211/debugfs_key.c
mac80211-10.0.4/origin/net/mac80211/sta_info.h
mac80211-10.0.4/origin/net/mac80211/ieee80211_common.h
mac80211-10.0.4/origin/net/mac80211/aes_ccm.c
mac80211-10.0.4/origin/net/mac80211/tkip.h
mac80211-10.0.4/origin/net/mac80211/ieee80211_cfg.c
mac80211-10.0.4/origin/net/mac80211/rc80211_simple.c
mac80211-10.0.4/origin/net/mac80211/ieee80211_rate.h
mac80211-10.0.4/origin/net/mac80211/wep.c
mac80211-10.0.4/origin/net/mac80211/wpa.c
mac80211-10.0.4/origin/net/mac80211/debugfs.c
mac80211-10.0.4/origin/net/mac80211/debugfs.h
mac80211-10.0.4/origin/net/mac80211/ieee80211_ioctl.c
mac80211-10.0.4/origin/net/mac80211/hostapd_ioctl.h
mac80211-10.0.4/origin/net/mac80211/ieee80211_iface.c
mac80211-10.0.4/origin/net/mac80211/Makefile
mac80211-10.0.4/origin/net/mac80211/tkip.c
mac80211-10.0.4/origin/net/mac80211/debugfs_key.h
mac80211-10.0.4/origin/net/mac80211/wme.c
mac80211-10.0.4/origin/net/mac80211/debugfs_netdev.c
mac80211-10.0.4/origin/net/mac80211/ieee80211_i.h
mac80211-10.0.4/origin/net/mac80211/ieee80211_led.c
mac80211-10.0.4/origin/net/mac80211/ieee80211_key.h
mac80211-10.0.4/origin/net/mac80211/ieee80211_led.h
mac80211-10.0.4/origin/net/mac80211/wme.h
mac80211-10.0.4/origin/net/mac80211/sta_info.c
mac80211-10.0.4/origin/net/mac80211/michael.c
mac80211-10.0.4/origin/net/mac80211/debugfs_netdev.h
mac80211-10.0.4/origin/net/mac80211/debugfs_sta.c
mac80211-10.0.4/origin/net/mac80211/regdomain.c
mac80211-10.0.4/origin/net/mac80211/ieee80211_cfg.h
mac80211-10.0.4/origin/net/mac80211/ieee80211_sta.c
mac80211-10.0.4/origin/net/mac80211/wpa.h
mac80211-10.0.4/origin/net/mac80211/michael.h
mac80211-10.0.4/origin/net/mac80211/aes_ccm.h
mac80211-10.0.4/origin/net/mac80211/wep.h
mac80211-10.0.4/origin/net/mac80211/Kconfig
mac80211-10.0.4/origin/net/mac80211/ieee80211_rate.c
mac80211-10.0.4/origin/net/wireless/radiotap.c
mac80211-10.0.4/origin/net/wireless/sysfs.c
mac80211-10.0.4/origin/net/wireless/wext.c
mac80211-10.0.4/origin/net/wireless/core.h
mac80211-10.0.4/origin/net/wireless/sysfs.h
mac80211-10.0.4/origin/net/wireless/Makefile
mac80211-10.0.4/origin/net/wireless/core.c
mac80211-10.0.4/origin/net/wireless/Kconfig
mac80211-10.0.4/origin/include/linux/ieee80211.h
mac80211-10.0.4/origin/include/linux/nl80211.h
mac80211-10.0.4/origin/include/linux/wireless.h
mac80211-10.0.4/origin/include/net/ieee80211_radiotap.h
mac80211-10.0.4/origin/include/net/mac80211.h
mac80211-10.0.4/origin/include/net/iw_handler.h
mac80211-10.0.4/origin/include/net/cfg80211.h
mac80211-10.0.4/origin/include/net/wireless.h
mac80211-10.0.4/origin/include/net/wext.h
mac80211-10.0.4/pending/0011-mac80211-HT-IEEE-802.11n-TX-AMPDU-MLME-implementa.patch
mac80211-10.0.4/pending/0020-mac80211-HT-fix-master-mode-net-type.patch
mac80211-10.0.4/pending/0030-mac80211-fix-monitor-mode.patch
mac80211-10.0.4/pending/0013-mac80211-HT-IEEE-802.11n-block-ack-support.patch
mac80211-10.0.4/pending/0094-mac80211-hw-scan-fix-1.patch
mac80211-10.0.4/pending/0097-mac80211-ht-agg-teardown-fix.patch
mac80211-10.0.4/pending/0095-mac80211-hw-scan-fix-2.patch
mac80211-10.0.4/pending/0092-mac80211-sta-hw-scanning.patch
mac80211-10.0.4/pending/0021-mac80211-HT-IEEE-802.11n-RX-aggregation-MLME-supp.patch
mac80211-10.0.4/pending/0098-mac80211-tasklet_enable-fix.patch
mac80211-10.0.4/pending/0024-mac80211-HT-fix-wrong-param-used-for-ieee80211_ht.patch
mac80211-10.0.4/pending/0093-mac80211-clean-extra-ie.patch
mac80211-10.0.4/pending/0018-mac80211-HT-add-addtional-type-parameter-for-ieee.patch
mac80211-10.0.4/pending/0032-mac80211-fix-kernel-panic-during-shutdown-time.patch
mac80211-10.0.4/pending/0096-mac80211-workaround-wpa-reassoc.patch
mac80211-10.0.4/pending/0022-mac80211-HT-IEEE-802.11n-RX-aggregation-debugfs-s.patch
mac80211-10.0.4/pending/0012-mac80211-HT-IEEE-802.11n-debugfs-support.patch
mac80211-10.0.4/pending/0019-mac80211-HT-fix-ieee80211_send_addba_resp-interfa.patch
mac80211-10.0.4/pending/0027-mac80211-add-802.11h-channel-switch-packet-handling.patch
mac80211-10.0.4/pending/0002-mac80211-add-IEEE802.11e-WMM-structures.patch
mac80211-10.0.4/pending/0029-mac80211-add-rate-scaling-algorithm-selection-capab.patch
mac80211-10.0.4/pending/0031-mac80211-fix-an-printk-warning-for-size_t.patch
mac80211-10.0.4/pending/0015-mac80211-HT-add-IEEE-802.11n-qos-queues.patch
mac80211-10.0.4/pending/0035-mac802211-fix-send_addba_resp.patch
mac80211-10.0.4/pending/0025-mac80211-HT-use-KERN_DEBUG-for-HT-debugging-messa.patch
mac80211-10.0.4/pending/0004-mac80211-debugfs-support-for-TSM-and-DLS.patch
mac80211-10.0.4/pending/0003-mac80211-IEEE802.11e-WMM-TS-management-and-DLS-supp.patch
mac80211-10.0.4/pending/0028-mac80211-fix-compile-error-if-CONFIG_NET_SCHED-unde.patch
mac80211-10.0.4/pending/0006-mac80211-add-WE-nick-power-and-txpower-capabilitie.patch
mac80211-10.0.4/pending/0017-mac80211-HT-IEEE-802.11n-RX-aggregation-API-and-M.patch
mac80211-10.0.4/pending/0007-mac80211-Fix-user-specified-TXPOWER-from-being-over.patch
mac80211-10.0.4/pending/0023-mac80211-HT-AP-mode-block-ack-MLME-support.patch
mac80211-10.0.4/pending/0010-mac80211-HT-add-TX-AMPDU-MLME-data.patch
mac80211-10.0.4/pending/0026-mac80211-rssi-averaging-filter.patch
mac80211-10.0.4/pending/0005-mac80211-IEEE802.11e-WMM-misc-fix-and-cleanup.patch
mac80211-10.0.4/pending/0016-mac80211-HT-IEEE-802.11n-RX-aggregation-BAR-supor.patch
mac80211-10.0.4/pending/0009-mac80211-HT-add-IEEE-802.11n-TX_AMPDU-API.patch
mac80211-10.0.4/pending/0034-mac802211-fix-ba-processing.patch
mac80211-10.0.4/pending/0033-mac80211-fix-a-msdu-header.patch
mac80211-10.0.4/pending/0091-mac80211-fix-hidden-ssid.patch
mac80211-10.0.4/pending/0008-mac80211-HT-IEEE_802.11n_TX_AMPDU-send-actframes.patch
mac80211-10.0.4/pending/0001-mac80211-Add-basic-IEEE-802.11n-support.patch
mac80211-10.0.4/pending/0014-mac80211-HT-IEEE-802.11n-block-ack-debugfs-suppor.patch
mac80211-10.0.4/pending/0090-mac80211-IPv6-fix.patch
mac80211-10.0.4/patches/div_round_up.patch
mac80211-10.0.4/patches/device_rename.patch
mac80211-10.0.4/patches/class_dev_to_dev-wireless.patch
mac80211-10.0.4/patches/post-genlmsg_put.patch
mac80211-10.0.4/patches/post-nla_nul_string.patch
mac80211-10.0.4/patches/ilog2.sh
mac80211-10.0.4/patches/i_private.sh
mac80211-10.0.4/patches/ieee80211_ptr.sh
mac80211-10.0.4/patches/dev_release.patch
mac80211-10.0.4/patches/delayed_work.sh
mac80211-10.0.4/patches/nlmsg_new.patch
mac80211-10.0.4/patches/class_dev_to_dev-wireless-ieee80211_ptr.patch
mac80211-10.0.4/patches/block-cipher.patch
mac80211-10.0.4/patches/seq_open_const.patch
mac80211-10.0.4/patches/tcf_destroy_chain.patch
mac80211-10.0.4/patches/net_sch_fifo.patch
mac80211-10.0.4/patches/fix-qos-sysfs-no-class_dev.patch
mac80211-10.0.4/patches/debugfs_rename.patch
mac80211-10.0.4/patches/nl80211-remove.patch
mac80211-10.0.4/patches/post-nla_binary.patch
mac80211-10.0.4/patches/nlmsg_trim.patch
mac80211-10.0.4/patches/kcompat-delayed_work.h
mac80211-10.0.4/patches/nla_put_flag.patch
mac80211-10.0.4/patches/kcompat-math.h
mac80211-10.0.4/patches/rtnl_notify.patch
mac80211-10.0.4/patches/delayed_work.patch
mac80211-10.0.4/patches/qdisc-api.patch
mac80211-10.0.4/patches/ieee80211_ptr.patch
mac80211-10.0.4/patches/debugfs_create_symlink.patch
mac80211-10.0.4/patches/skb_mac_header.patch
mac80211-10.0.4/patches/nl80211-remove-kconfig.patch
mac80211-10.0.4/patches/kcompat-skb_mac_header.h
mac80211-10.0.4/patches/nla_policy.patch
mac80211-10.0.4/stubs/README
mac80211-10.0.4/scripts/make_change_log
mac80211-10.0.4/scripts/determine_compat
mac80211-10.0.4/scripts/push-to-bughost
mac80211-10.0.4/scripts/patch_kernel_post
mac80211-10.0.4/scripts/generate_modified
mac80211-10.0.4/scripts/patch_kernel
mac80211-10.0.4/scripts/generate_compatible
mac80211-10.0.4/scripts/git-clean-unreachable
mac80211-10.0.4/scripts/generate_origin
mac80211-10.0.4/README
mac80211-10.0.4/TODO
mac80211-10.0.4/CHANGES
mac80211-10.0.4/FILES
mac80211-10.0.4/ORIGIN_FILES
mac80211-10.0.4/Makefile
darkwings@D4rkbooK:~$ mac80211-10.0.4/origin/GIT
bash: mac80211-10.0.4/origin/GIT: Permission denied
darkwings@D4rkbooK:~$ mac80211-10.0.4/origin/net/mac80211/Makefiletar xvf mac80211-10.0.4.tgz
bash: mac80211-10.0.4/origin/net/mac80211/Makefiletar: No such file or directory
darkwings@D4rkbooK:~$ mac80211-10.0.4/origin/GIT
bash: mac80211-10.0.4/origin/GIT: Permission denied
darkwings@D4rkbooK:~$ mac80211-10.0.4/origin/net/mac80211/Makefile   



hopefully im not just overlooking something obvious,

thanks in advance

---

### Post by Maus1231 on 2009-01-04
Aaaand more info as per the sticky....

laptop-dell xps m1710 

lspci/lsusb--

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7950 GTX (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
darkwings@D4rkbooK:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 001 Device 005: ID 0b97:7761 O2 Micro, Inc.
Bus 001 Device 004: ID 413c:a005 Dell Computer Corp.
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 001: ID 0000:0000
darkwings@D4rkbooK:~$         


ifconfig/iwconfig--

eth0      Link encap:Ethernet  HWaddr 00:18:8b:dc:e7:9f
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fedc:e79f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:56749419 (54.1 MB)  TX bytes:3221090 (3.0 MB)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1700 (1.6 KB)  TX bytes:1700 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:57:92:0f
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:92970 (90.7 KB)  TX bytes:42971 (41.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-57-92-0F-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

darkwings@D4rkbooK:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lsmod--

Module                  Size  Used by
usbhid                 32128  0
hid                    38784  1 usbhid
binfmt_misc            12808  1
ipv6                  267780  10
af_packet              23812  2
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0
acpi_cpufreq           10796  1
cpufreq_conservative     8712  0
cpufreq_stats           7104  0
cpufreq_userspace       5284  0
cpufreq_ondemand        9740  0
cpufreq_powersave       2688  0
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    15112  0
sbshc                   7680  1 sbs
container               5632  0
dock                   11280  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0
dm_crypt               15364  0
dm_mod                 62660  1 dm_crypt
arc4                    2944  2
ecb                     4480  2
blkcipher               8324  1 ecb
sbp2                   24072  0
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0
snd_hda_intel         344856  1
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
iwl4965               105844  0
snd_seq_midi            9376  0
iwlwifi_mac80211      218980  1 iwl4965
snd_rawmidi            25760  1 snd_seq_midi
nvidia               7825536  26
video                  19856  8
output                  4736  1 video
cfg80211               15112  1 iwlwifi_mac80211
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
sdhci                  19076  0
i2c_core               24832  1 nvidia
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mmc_core               51460  1 sdhci
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0
iTCO_wdt               13092  0
iTCO_vendor_support     4868  1 iTCO_wdt
serio_raw               7940  0
intel_agp              25492  0
snd                    56996  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi_acer                9644  0
button                  9232  0
battery                14212  0
agpgart                34760  2 nvidia,intel_agp
dcdbas                  9504  0
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
evdev                  13056  6
pcspkr                  4224  0
psmouse                40336  0
ext3                  136840  1
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0
sd_mod                 30720  3
sr_mod                 17956  0
cdrom                  37408  1 sr_mod
ata_generic             8324  0
pata_acpi               8320  0
ohci1394               33584  0
ieee1394               93752  2 sbp2,ohci1394
ata_piix               19588  2
ehci_hcd               37900  0
libata                159344  3 ata_generic,pata_acpi,ata_piix
scsi_mod              151436  5 sbp2,sg,sd_mod,sr_mod,libata
tg3                   116228  0
uhci_hcd               27024  0
usbcore               146412  4 usbhid,ehci_hcd,uhci_hcd
thermal                16796  0
processor              37384  4 acpi_cpufreq,thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1


sudo lshw -C network--
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.12.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status
        -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)




iwlist scan--
darkwings@D4rkbooK:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results



linux version--
darkwings@D4rkbooK:~$ lsb_release -d
Description:    Ubuntu 8.04.1



kernel--
darkwings@D4rkbooK:~$ uname -mr
2.6.24-22-generic i686



and network restart--
darkwings@D4rkbooK:~$ sudo /etc/init.d/networking restart
[sudo] password for darkwings:
 * Reconfiguring network interfaces...                                   [ OK ]




hope something in there is helpful.
thanks again

---

### Post by Maus1231 on 2009-01-04
Am i doomed to windows????????

---

### Post by Maus1231 on 2009-01-04
dont want to call it solved but im going to withdraw my question....unfortunately its back to windows for me, as i have to have functional wifi when i head back to my dorm next week.

The fact that i didnt even get so much as a shrug out of anyone is...irritating....was this really that complicated of a problem?

---

