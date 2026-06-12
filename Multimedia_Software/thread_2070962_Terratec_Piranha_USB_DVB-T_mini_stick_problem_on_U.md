---
title: "Terratec Piranha USB DVB-T mini stick problem on Ubuntu 12.04 Precise Pangolin 64bit"
date: 2012-10-14
forum: Multimedia Software
---

### Post by mmesh on 2012-10-14
Hi!

I'm trying to get Terratec Piranha USB DVB-T to work on my Ubu 12.04 installation.
This is output that could possible help someone help me:
```

root@LinMF:/etc/modprobe.d# lsusb
...
Bus 006 Device 005: ID 187f:0100 Siano Mobile Silicon Stallar Board

```

```

[ 1336.999943] usb 6-2: new full-speed USB device number 6 using uhci_hcd
[ 1337.159540] smsusb_probe: line: 421: rom interface 0 is not used
[ 1337.255300] usb 6-2: USB disconnect, device number 6
[ 1339.719483] usb 6-2: new full-speed USB device number 7 using uhci_hcd

```

```

Oct 14 13:15:07 LinMF kernel: [ 1337.255300] usb 6-2: USB disconnect, device number 6
Oct 14 13:15:09 LinMF kernel: [ 1339.719483] usb 6-2: new full-speed USB device number 7 using uhci_hcd
Oct 14 13:15:09 LinMF mtp-probe: checking bus 6, device 7: "/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2"
Oct 14 13:15:09 LinMF mtp-probe: bus: 6, device: 7 was not an MTP device

```

```

root@LinMF:/etc/modprobe.d# lsmod
Module                  Size  Used by
smsusb                 13808  0 
hidp                   22628  1 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
vboxdrv               282587  3 vboxpci,vboxnetadp,vboxnetflt
md4                    12595  0 
vesafb                 13844  1 
snd_hda_codec_hdmi     32474  4 
btusb                  18288  4 
ir_lirc_codec          12859  0 
lirc_dev               19204  1 ir_lirc_codec
mxm_wmi                12979  0 
ir_mce_kbd_decoder     12777  0 
ir_sony_decoder        12510  0 
ir_jvc_decoder         12507  0 
ir_rc6_decoder         12507  0 
ir_rc5_decoder         12507  0 
ir_nec_decoder         12507  0 
smsmdtv                37242  1 smsusb
rc_core                26412  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,smsmdtv
nvidia              12336440  50 
snd_hda_codec_realtek   224173  1 
dm_multipath           23230  0 
joydev                 17693  0 
usblp                  18307  0 
serio_raw              13211  0 
snd_hda_intel          33773  5 
rfcomm                 47604  12 
parport_pc             32866  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
bnep                   18281  2 
snd_hwdep              13668  1 snd_hda_codec
bluetooth             180104  28 hidp,btusb,rfcomm,bnep
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ppdev                  17113  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
xpad                   18179  0 
ff_memless             13097  1 xpad
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
nls_utf8               12557  1 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cifs                  287317  2 
binfmt_misc            17540  1 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i7core_edac            28102  0 
edac_core              53746  3 i7core_edac
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  1 mxm_wmi
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  62099  0 
pata_jmicron           12747  0 
usbhid                 47199  0 
hid                    99559  2 hidp,usbhid
usb_storage            49198  0

```

As You can see smsusb and smsmdtv modules are loading properly but after that nothing happens :(
I installed linux-firmware-nonfree which in turn has:
```

root@LinMF:/etc/modprobe.d# dpkg -L linux-firmware-nonfree |grep sms
/lib/firmware/sms1xxx-hcw-55xxx-dvbt-02.fw

```
firmware that is supposedly needed for this tv card.
I also copied firmware from windows drivers into /lib/firmware and renamed it:
```

root@LinMF:/etc/modprobe.d# ls -l /lib/firmware/dvbt_bda_stellar_usb.inp 
-rw-r--r-- 1 root root 38144 Lis 10 21:58 /lib/firmware/dvbt_bda_stellar_usb.inp

```
and still nothing :(

Can someone, please, help?

---

