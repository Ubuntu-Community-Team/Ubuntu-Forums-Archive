---
title: "Wireless not working on HP dv6t - Ubuntu 11.10"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by mav35007 on 2012-02-17
Hi,

Firstly, many thanks and appreciation to the linux community for having these forums to help out newbies like me in solving issues :)

I have a HP dv6t select edition laptop and am unable to run Wireless on it on Ubuntu 11.10, even though the hardware switch on the keyboard is ON.

I did some research and found that these commands are primarily used to ascertain what the issue is. I am posting their outputs too.

command 1 - 
cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ashwin 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

command 2-
sudo lshw -C network
[sudo] password for ashwin: 
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 10:1f:74:0f:be:f5
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.2.8 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:a3:ef:8a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-16-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:48 memory:c4500000-c4501fff


command 3 - 
lspci -nn | grep -e 0280 -e 0200

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
0d:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
19:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)

command 4 - 
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

command 5 - 

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

command 6 - 

lsmod

Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
arc4                   12529  2 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
usbhid                 47198  0 
hid                    95463  1 usbhid
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
hp_accel               21880  0 
lis3lv02d              19888  1 hp_accel
wmi                    19256  1 hp_wmi
input_polldev          13896  1 lis3lv02d
snd_seq_midi_event     14899  1 snd_seq_midi
iwlagn                314257  0 
fglrx                2928969  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              462046  1 iwlagn
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  571221  2 
cfg80211              199630  2 iwlagn,mac80211
drm_kms_helper         42558  1 i915
rts_pstor             445246  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   236290  3 i915,drm_kms_helper
psmouse                73882  0 
mei                    41480  0 
serio_raw              13166  0 
i2c_algo_bit           13423  1 i915
lp                     17799  0 
video                  19412  1 i915
parport                46562  3 parport_pc,ppdev,lp
usb_storage            57901  1 
uas                    18027  0 
xhci_hcd               82820  0 
ahci                   26002  2 
libahci                26861  1 ahci
r8169                  52788  0 


Please let me know if is this the right way to post info, as I am new to these forums :)
Hope the commands are right!

Thanks in advance for the help.

---

