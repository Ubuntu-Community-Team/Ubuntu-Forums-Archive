---
title: "CNet CQU-906 USB Wireless not working"
date: 2011-08-31
forum: Networking &amp; Wireless
---

### Post by repease on 2011-08-31
I have installed Ubuntu 11.04 on my Pavilion tx-1000 and am trying to use the CNet CQU-906 USB Wireless adapter to connect to my wireless network.  The adapter is not being found by the OS, but worked just fine under Windows 7.

Any ideas or suggestions to make this work?  (Really don't want to go back to Win7).

---

### Post by praseodym on 2011-08-31
Hi,

can you post the outputs of:

```
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by repease on 2011-08-31
lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 1004:61a1 LG Electronics, Inc. 
Bus 001 Device 007: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 006: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 001 Device 005: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsmod
Module                  Size  Used by
cdc_ether              13033  0 
usbnet                 25175  1 cdc_ether
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
nvidia               9766978  41 
snd_hda_codec_si3054    12924  1 
snd_hda_codec_realtek   255882  1 
snd_atiixp_modem       18624  0 
snd_hda_intel          24113  2 
snd_via82xx_modem      18305  0 
snd_intel8x0m          18493  0 
snd_hda_codec          90901  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_ac97_codec        105614  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
snd_hwdep              13274  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ac97_bus               12642  1 snd_ac97_codec
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80042  7 snd_hda_codec_si3054,snd_atiixp_modem,snd_hda_intel,snd_via82xx_modem,snd_intel8x0m,snd_hda_codec,snd_ac97_codec
snd_timer              28659  2 snd_seq,snd_pcm
hp_wmi                 13418  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13666  1 hp_wmi
ndiswrapper           192828  0 
uvcvideo               66851  0 
snd                    55295  18 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_atiixp_modem,snd_hda_intel,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_seq,snd_pcm,snd_timer,snd_seq_device
cdc_acm                22150  0 
videodev               75143  1 uvcvideo
psmouse                73312  0 
joydev                 17322  0 
serio_raw              12990  0 
soundcore              12600  1 snd
k8temp                 12872  0 
snd_page_alloc         14073  5 snd_atiixp_modem,snd_hda_intel,snd_via82xx_modem,snd_intel8x0m,snd_pcm
nv_tco                 13331  0 
i2c_nforce2            12906  0 
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  0 
uas                    17676  0 
forcedeth              58190  0 
pata_amd               13762  0 
sata_nv                23176  2

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.

rfkill list - shows no results

---

### Post by wildmanne39 on 2011-08-31
Hi, here is what you need to get this card working, start at post 14.
[http://ubuntuforums.org/showthread.php?p=11086418#post11086418](http://ubuntuforums.org/showthread.php?p=11086418#post11086418)
This is the driver that you will need RTL8188CE-VAU it is way down the page in that realtek link.

Thank you

---

### Post by repease on 2011-08-31
I'm sorry, but I'm still new to Ubuntu and Linux as a whole.

I found the file you said to look for, but I don't know what to do next. Help PLEASE!!

---

### Post by wildmanne39 on 2011-08-31
Hi, open synaptic it is in dash then install kernel-headers and build-essentials.

The kernel headers will be for the latest kernel you have installed and it may already be installed just check to make sure.

then Go to [http://www.realtek.com.tw/downloads/...Downloads=true](http://www.realtek.com.tw/downloads/...Downloads=true)

Download the RTL8188CE-VAU driver then drag it to your desktop, then right click on it and choose extract here.

Then open the terminal, put your cursor on the file you extracted then drag it into the terminal.

Then run these commands one at a time:
```
sudo su
    make
    make install
```
Disconnect your wired connection, then reboot.

It should ask for your router password, enter it and it should connect.
Thank you

---

### Post by nito2721 on 2012-02-25
Try this.

[http://forums.linuxmint.com/viewtopic.php?f=53&t=94495&start=0](http://forums.linuxmint.com/viewtopic.php?f=53&t=94495&start=0)

---

