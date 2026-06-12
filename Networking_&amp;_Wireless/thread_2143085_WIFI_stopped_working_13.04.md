---
title: "WIFI stopped working? 13.04"
date: 2013-05-07
forum: Networking &amp; Wireless
---

### Post by {davros} on 2013-05-07
just like that its gone....


```
davros@davros64:~$ lspci -vvnn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
davros@davros64:~$ dmesg | egrep 'wlan0|iwl'
davros@davros64:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:145e]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:3658]
	Kernel driver in use: r8169
davros@davros64:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


davros@davros64:~$ rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
davros@davros64:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
parport_pc             28284  0 
bnep                   18258  2 
ppdev                  17106  0 
rfcomm                 47863  0 
bluetooth             251354  10 bnep,rfcomm
binfmt_misc            17540  1 
snd_hda_codec_hdmi     37407  1 
hid_generic            12548  0 
uvcvideo               82296  0 
usbhid                 47346  0 
hid                   101248  2 hid_generic,usbhid
snd_hda_codec_idt      55123  1 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40785  1 uvcvideo
snd_hda_intel          44397  3 
videodev              131329  2 uvcvideo,videobuf2_core
snd_hda_codec         190010  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
usb_storage            61749  1 
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18798  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30417  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi_event,snd_seq_midi
lp                     17799  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
coretemp               13596  0 
ir_jvc_decoder         12507  0 
ir_mce_kbd_decoder     12777  0 
snd_timer              29989  2 snd_pcm,snd_seq
ir_rc5_decoder         12507  0 
ir_lirc_codec          12859  0 
ir_sanyo_decoder       12513  0 
ir_sony_decoder        12510  0 
lirc_dev               19204  1 ir_lirc_codec
joydev                 17613  0 
kvm_intel             138733  0 
i915                  631614  3 
kvm                   452835  1 kvm_intel
snd                    69533  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
drm_kms_helper         49082  1 i915
psmouse                97838  0 
mei                    46588  0 
drm                   295908  4 i915,drm_kms_helper
ir_rc6_decoder         12507  0 
ir_nec_decoder         12507  0 
parport                46562  3 lp,ppdev,parport_pc
rc_rc6_mce             12502  0 
hp_accel               26012  0 
ene_ir                 18427  0 
soundcore              12680  1 snd
lis3lv02d              20200  1 hp_accel
rc_core                26352  11 ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,ene_ir,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
microcode              22923  0 
hp_wmi                 18085  0 
input_polldev          13896  1 lis3lv02d
sparse_keymap          13890  1 hp_wmi
video                  19467  1 i915
serio_raw              13215  0 
i2c_algo_bit           13564  1 i915
mac_hid                13253  0 
lpc_ich                17060  0 
wmi                    19256  1 hp_wmi
ahci                   30063  2 
libahci                32088  1 ahci
r8169                  68680  0 
davros@davros64:~$ lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 004: ID 064e:a127 Suyin Corp. 



```

13.04
3.9.0-030900 kernel


any ideas?

---

### Post by Hadaka on 2013-05-07
Hi, give this a try..
```
sudo apt-get install bcmwl-kernel-source 
sudo modprobe wl
```
thanks.

---

### Post by daman1986 on 2014-02-10
@hadaka
Thanks a lot , after struggling for a day with this problem. Your 2 liner command magically worked for me.:)

---

