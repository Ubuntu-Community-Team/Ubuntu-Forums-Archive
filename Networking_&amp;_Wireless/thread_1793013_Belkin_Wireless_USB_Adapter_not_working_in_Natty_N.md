---
title: "Belkin Wireless USB Adapter not working in Natty Narwhal"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by choudharypranay on 2011-06-28
I've recently bought BELKIN Basic Wireless USB Adapter.

When I plug it in Natty Narwhal, wireless networks are detected but on providing the parse key, it is unable to connect to the network.

I could not locate any log files related to it. I'm posting the following output.
```
# lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 050d:945a Belkin Components 
Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 003: ID 046d:c52e Logitech, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
# lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
sco                    17779  2 
bnep                   17785  2 
l2cap                  48656  3 bnep
snd_hda_codec_hdmi     27479  4 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
nouveau               621970  2 
ttm                    65184  1 nouveau
drm_kms_helper         40745  1 nouveau
drm                   180037  4 nouveau,ttm,drm_kms_helper
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  1 nouveau
soundcore              12600  1 snd
video                  18951  1 nouveau
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
ppdev                  12849  0 
lp                     13349  0 
btusb                  18160  1 
psmouse                73312  0 
shpchp                 32345  0 
serio_raw              12990  0 
bluetooth              65565  8 sco,bnep,l2cap,btusb
r8712u                281937  0 
parport_pc             32111  1 
parport                36746  3 ppdev,lp,parport_pc
joydev                 17322  0 
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  2 
e1000e                138627  0 
libahci                25548  1 ahci
```

```
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by choudharypranay on 2011-06-29
I'm able to see wireless connections, but I'm unable to connect to them. My access point uses WPA security type and TKIP encryption type.
Any help will be appreciated. Thanks in advance.

---

### Post by chili555 on 2011-06-29
May we see:```
sudo iwlist wlan0 scan
```> but on providing ***the parse key***, it is unable to connect to the network.What do you mean 'parse key'? Please pardon my misunderstanding.

---

