---
title: "no wireless available"
date: 2012-08-23
forum: Networking &amp; Wireless
---

### Post by dstudio on 2012-08-23
I hope this will help:

sudo lshw -C network 

  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d0500000-d0507fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 5c:f9:dd:42:65:6e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.0.105 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:2000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff

lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
    Subsystem: Dell Device [1028:0016]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0564]
    Kernel driver in use: r8169

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

rfkill list all

0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes

lsmod

Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
joydev                 17393  0 
snd_hda_codec_idt      60049  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
rts5139               279514  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505108  3 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
psmouse                73673  0 
i2c_algo_bit           13199  1 i915
mei                    36466  0 
serio_raw              12990  0 
wmi                    18744  1 dell_wmi
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
xhci_hcd               72915  0 
r8169                  43104  0 
libahci                25727  1 ahci

sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35
Aug 23 17:36:11 nedim-Inspiron-5720 NetworkManager[902]: <info> monitoring kernel firmware directory '/lib/firmware'.


Tnx-

---

### Post by Kirk Schnable on 2012-08-23
It looks like you have a Broadcom wireless card which needs additional drivers.

I believe these threads will help you:
[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)
[http://askubuntu.com/questions/166916/broadcom-sta-wireless-drivers-not-working-on-dell-inspiron-5420](http://askubuntu.com/questions/166916/broadcom-sta-wireless-drivers-not-working-on-dell-inspiron-5420)

Kirk

---

