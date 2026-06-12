---
title: "Need help debugging intermittent loss of internet"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by distended on 2011-08-27
My internet connection drops out every few hours or so for a minute or two each time.  I've only noticed this behavior since I've switched to Ubuntu (11.04) from Windows.  I don't know how to tell definitively if this is an OS/driver issue or something on my ISP side, and could use any help you all could offer.

Clicking on connection information in the system tray shows my driver as r8169.

lspci | grep Ethernet
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

Please let me know what I can try to figure this out.  Thanks in advance.

---

### Post by northd_tech on 2011-08-28
I haven't worked with that particular card very much, but it sounds like a power management thing to me.  Looking through the **man ifconfig** and **info ifconfig** documentation, I didn't see any power settings there- it must be in the Realtek driver itself if there are power [saving] settings.  To see what driver modules you are using, can you post the results of this terminal command?

```
lsmod
```

---

### Post by distended on 2011-08-28
[FONT=Courier New]Thanks for your reply... here's the result of lsmod

Module                  Size  Used by
parport_pc             32111  0 
vesafb                 13449  1 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
fglrx                2434640  112 
snd_usb_audio          91410  1 
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_hwdep              13274  2 snd_hda_codec,snd_usb_audio
gspca_zc3xx            50969  0 
snd_pcm                80042  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
snd                    55295  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
gspca_main             27894  1 gspca_zc3xx
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
videodev               75143  1 gspca_main
lp                     13349  0 
serio_raw              12990  0 
dcdbas                 14054  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  0 
uas                    17676  0 
firewire_ohci          31504  0 
r8169                  42534  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
[/FONT]

---

### Post by bkratz on 2011-08-28
> **distended said:**
> [FONT=Courier New]Thanks for your reply... here's the result of lsmod

Module                  Size  Used by
parport_pc             32111  0 
vesafb                 13449  1 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
fglrx                2434640  112 
snd_usb_audio          91410  1 
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_hwdep              13274  2 snd_hda_codec,snd_usb_audio
gspca_zc3xx            50969  0 
snd_pcm                80042  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
snd                    55295  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
gspca_main             27894  1 gspca_zc3xx
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
videodev               75143  1 gspca_main
lp                     13349  0 
serio_raw              12990  0 
dcdbas                 14054  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  0 
uas                    17676  0 
firewire_ohci          31504  0 
[COLOR="Red"]r8169   [/COLOR]               42534  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
[/FONT]


There have been many many (many) threads on the forums about how the  RTL8111/8168B PCI Express Gigabit when using the r8169 driver is flaky in operation. The proper driver is actually r8168.  Anyway, here is a good start.


[http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489)

---

### Post by distended on 2011-08-28
Oooh, thanks much for this find bkratz.  I just loaded the new driver.  Will update after a while if it runs smoothly.

---

