---
title: "Bluetooth does not work - Lenovo G560"
date: 2013-02-03
forum: Networking &amp; Wireless
---

### Post by chaushev on 2013-02-03
Ubuntu 12.10/Lenovo G560/dual boot Win7
Bluetooth icon is present. I enable bluetooth but it does not work. On "bluetooth settings" the only thing I can change is the on/off icon switch. Visibility, +/- settings are all gray (inactive) and I cannot change them. 
After I did some search on the Internet I installed blueman
```
sudo apt-get install blueman
```
This added another bluetooth icon on the panel featuring more options. Neither of them works. "Setup new device" for instance brings up a message that reads "No adapters found". Bluetooth works fine under Win7. I used to have Ubuntu 10.10 few years back and I remember bluetooth worked fine. 
I am a Linux newbie and any additional info requested will be given.

---

### Post by sanderj on 2013-02-03
you could check dmesg:

```
dmesg | grep -i blue

```

---

### Post by chaushev on 2013-02-04
```
[   23.711897] Bluetooth: Core ver 2.16
[   23.711992] Bluetooth: HCI device and connection manager initialized
[   23.711995] Bluetooth: HCI socket layer initialized
[   23.711996] Bluetooth: L2CAP socket layer initialized
[   23.712010] Bluetooth: SCO socket layer initialized
[   23.721161] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.721166] Bluetooth: BNEP filters: protocol multicast
[   23.736787] Bluetooth: RFCOMM TTY layer initialized
[   23.736794] Bluetooth: RFCOMM socket layer initialized
[   23.736795] Bluetooth: RFCOMM ver 1.11
[ 2896.708034] Modules linked in: rfcomm parport_pc ppdev bnep bluetooth binfmt_misc snd_hda_codec_hdmi joydev coretemp kvm arc4 brcmsmac mac80211 brcmutil cfg80211 cordic microcode snd_hda_codec_conexant snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_hda_intel snd_hda_codec snd_hwdep snd_seq_device uvcvideo videobuf2_core snd_pcm videodev videobuf2_vmalloc videobuf2_memops lpc_ich bcma psmouse serio_raw snd_timer nouveau snd mei ttm drm_kms_helper soundcore snd_page_alloc drm i2c_algo_bit mxm_wmi ideapad_laptop sparse_keymap video wmi mac_hid lp parport hid_a4tech usbhid hid r8169
[ 9999.781234] Modules linked in: rfcomm parport_pc ppdev bnep bluetooth binfmt_misc snd_hda_codec_hdmi joydev coretemp kvm arc4 brcmsmac mac80211 brcmutil cfg80211 cordic microcode snd_hda_codec_conexant snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_hda_intel snd_hda_codec snd_hwdep snd_seq_device uvcvideo videobuf2_core snd_pcm videodev videobuf2_vmalloc videobuf2_memops lpc_ich bcma psmouse serio_raw snd_timer nouveau snd mei ttm drm_kms_helper soundcore snd_page_alloc drm i2c_algo_bit mxm_wmi ideapad_laptop sparse_keymap video wmi mac_hid lp parport hid_a4tech usbhid hid r8169

```

---

### Post by ultimatetechie on 2013-02-04
> **chaushev said:**
> ```
[   23.711897] Bluetooth: Core ver 2.16
[   23.711992] Bluetooth: HCI device and connection manager initialized
[   23.711995] Bluetooth: HCI socket layer initialized
[   23.711996] Bluetooth: L2CAP socket layer initialized
[   23.712010] Bluetooth: SCO socket layer initialized
[   23.721161] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.721166] Bluetooth: BNEP filters: protocol multicast
[   23.736787] Bluetooth: RFCOMM TTY layer initialized
[   23.736794] Bluetooth: RFCOMM socket layer initialized
[   23.736795] Bluetooth: RFCOMM ver 1.11
[ 2896.708034] Modules linked in: rfcomm parport_pc ppdev bnep bluetooth binfmt_misc snd_hda_codec_hdmi joydev coretemp kvm arc4 brcmsmac mac80211 brcmutil cfg80211 cordic microcode snd_hda_codec_conexant snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_hda_intel snd_hda_codec snd_hwdep snd_seq_device uvcvideo videobuf2_core snd_pcm videodev videobuf2_vmalloc videobuf2_memops lpc_ich bcma psmouse serio_raw snd_timer nouveau snd mei ttm drm_kms_helper soundcore snd_page_alloc drm i2c_algo_bit mxm_wmi ideapad_laptop sparse_keymap video wmi mac_hid lp parport hid_a4tech usbhid hid r8169
[ 9999.781234] Modules linked in: rfcomm parport_pc ppdev bnep bluetooth binfmt_misc snd_hda_codec_hdmi joydev coretemp kvm arc4 brcmsmac mac80211 brcmutil cfg80211 cordic microcode snd_hda_codec_conexant snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_hda_intel snd_hda_codec snd_hwdep snd_seq_device uvcvideo videobuf2_core snd_pcm videodev videobuf2_vmalloc videobuf2_memops lpc_ich bcma psmouse serio_raw snd_timer nouveau snd mei ttm drm_kms_helper soundcore snd_page_alloc drm i2c_algo_bit mxm_wmi ideapad_laptop sparse_keymap video wmi mac_hid lp parport hid_a4tech usbhid hid r8169

```

I have the same prob :(

---

### Post by chaushev on 2013-02-04
Solution someone? It is very strange as it used to work on older ubuntu versions

---

