---
title: "Intrepid and PulseAudio"
date: 2009-01-16
forum: Multimedia Software
---

### Post by transkinetic on 2009-01-16
From a fresh install, sound worked fine. I tried to set up my bluetooth headset by following this guide: [https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset). Now I get no audio even from my on board device although when I try and play something in totem, I see movement on the pulse audio volume meter (playback).

I had tried esound with a previous install and was able to get audio output to my headset.

Currently my headset shows up as soundcard 1 although it isn't seen at all by pulse audio. Not that pulse audio is being any help right now.

I'll keep fiddling with this and post updates here.

The headset is a motorola. It is paired.

If anyone has any hints, interesting .asoundrc files, reasons why I'm getting no sound at all, please let me know.

I think I might try installing Kubuntu...

---

### Post by wolfen69 on 2009-01-16
if you don't need pulseaudio specifically, you could try removing it and just go with alsa. i had some minor issues when using pulseaudio, but when i removed it, everything was perfect.

---

### Post by John Jason Jordan on 2009-01-17
> **transkinetic said:**
> From a fresh install, sound worked fine. I tried to set up my bluetooth headset by following this guide: [https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset). Now I get no audio even from my on board device although when I try and play something in totem, I see movement on the pulse audio volume meter (playback).

I had tried esound with a previous install and was able to get audio output to my headset.

Currently my headset shows up as soundcard 1 although it isn't seen at all by pulse audio. Not that pulse audio is being any help right now.

I'll keep fiddling with this and post updates here.

The headset is a motorola. It is paired.

If anyone has any hints, interesting .asoundrc files, reasons why I'm getting no sound at all, please let me know.

I think I might try installing Kubuntu...

I tried the guide but it is not working. When I get to the "pactl load-module module-alsa-sink device=bluetooth" command it tells me "Connection failure: Connection refused." I think the problem is that pulseaudio is not properly configured. Or maybe it is not even running. 

I have installed all the pulseaudio packages in Synaptic. The problem is that pulseaudio is rather complex and there is next to nothing in the way of documentation. Lots of how-tos, but they never say what to do when the command fails.

---

### Post by transkinetic on 2009-01-27
Removing pulse audio caused the system to fail at boot time when it failed to load pulse audio...weird. Whatever, I did a fresh install (of ubuntu). I installed bluetooth sco and got sound out working with pulse audio. Yay. No sound input though.

Also, the wiki told me to enter this code but it fails.
[COLOR="DarkOrange"]
Edit: This code works now!
I think it must have worked before as well or I wouldn't have ever gotten audio out working.[/COLOR]
```
pactl load-module module-alsa-sink device=bluetooth
Failure: Module initalization failed

```

Anyhow, I compiled and installed the latest bluez-4.27. At least I think I did. How does one check this?

ps:
I also tried kubuntu. Looks like bluetooth is broken in general atm.

---

### Post by transkinetic on 2009-01-27
I made the default sink alsa_output.bluetooth...all my audio out is directed to the headset.

I made the default source alsa_input.bluetooth...the volume meter shows nothing. It does seem notable that alsa_input.bluetooth shows up in Pulse Audio Manager -> Devices in the input field.

---

### Post by ShepHeard on 2009-01-28
Hi there,

When you remove Pulseaudio, you need to *completely *remove it - follow the guide in [this]("http://ubuntuforums.org/showthread.php?t=1006163") thread to get rid of it completely, and also to update the ALSA drivers. There is an automatic script to do this [here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810").

Though my thread was relating to Skype - these problems seem somewhat more intractable. Removing Pulseasudio and updating ALSA work fine. Just read the whole thread before you do anything - there's maybe only one or two posts relating to the removal of Pulseaudio and Updating ALSA that you need to use.

Hope this helps - good luck!

Shep

---

### Post by transkinetic on 2009-02-03
I followed the guides but am now unable to load the bluetooth sco modules...

```
sudo modprobe snd_bt_sco | dmesg

...

[   39.276753] Bluetooth: L2CAP ver 2.11
[   39.276764] Bluetooth: L2CAP socket layer initialized
[   39.323712] Bluetooth: SCO (Voice Link) ver 0.6
[   39.323729] Bluetooth: SCO socket layer initialized
[   39.359948] Bluetooth: RFCOMM socket layer initialized
[   39.360676] Bluetooth: RFCOMM TTY layer initialized
[   39.360688] Bluetooth: RFCOMM ver 1.10
[   39.402554] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   39.402573] Bluetooth: BNEP filters: protocol multicast
[   39.485846] Bridge firewalling registered
[   42.153475] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   42.723514] [drm] Initialized drm 1.1.0 20060810
[   42.797500] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   43.641737] eth0:  setting half-duplex.
[   43.751949] NET: Registered protocol family 17
[   58.765834] NET: Registered protocol family 10
[   58.770949] lo: Disabled Privacy Extensions
[   58.774368] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   68.968054] ath0: no IPv6 routers present
[  150.384271] ppdev0: registered pardevice
[  150.432092] ppdev0: unregistered pardevice
[  150.563315] ppdev0: registered pardevice
[  150.612672] ppdev0: unregistered pardevice
[  152.695968] ppdev0: registered pardevice
[  152.744310] ppdev0: unregistered pardevice
[  152.837350] type=1503 audit(1233700201.263:5): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/usr/local/lib/libbluetooth.so.3.1.1" pid=5570 profile="/usr/sbin/cupsd"
[  373.577367] snd_bt_sco: disagrees about version of symbol snd_ctl_add
[  373.577386] snd_bt_sco: Unknown symbol snd_ctl_add
[  373.577877] snd_bt_sco: disagrees about version of symbol snd_pcm_new
[  373.577884] snd_bt_sco: Unknown symbol snd_pcm_new
[  373.578286] snd_bt_sco: disagrees about version of symbol snd_card_register
[  373.578293] snd_bt_sco: Unknown symbol snd_card_register
[  373.578697] snd_bt_sco: disagrees about version of symbol snd_card_free
[  373.578704] snd_bt_sco: Unknown symbol snd_card_free
[  373.579397] snd_bt_sco: disagrees about version of symbol snd_ctl_new1
[  373.579404] snd_bt_sco: Unknown symbol snd_ctl_new1
[  373.580056] snd_bt_sco: Unknown symbol snd_card_new
[  373.580490] snd_bt_sco: disagrees about version of symbol snd_pcm_lib_ioctl
[  373.580497] snd_bt_sco: Unknown symbol snd_pcm_lib_ioctl
[  373.580866] snd_bt_sco: disagrees about version of symbol snd_hwdep_new
[  373.580873] snd_bt_sco: Unknown symbol snd_hwdep_new
[  373.581449] snd_bt_sco: disagrees about version of symbol snd_ctl_notify
[  373.581456] snd_bt_sco: Unknown symbol snd_ctl_notify
[  373.590372] snd_bt_sco: disagrees about version of symbol snd_pcm_set_ops
[  373.590389] snd_bt_sco: Unknown symbol snd_pcm_set_ops
[  373.591496] snd_bt_sco: disagrees about version of symbol snd_pcm_period_elapsed
[  373.591504] snd_bt_sco: Unknown symbol snd_pcm_period_elapsed
[  580.503306] snd_bt_sco: disagrees about version of symbol snd_ctl_add
[  580.503330] snd_bt_sco: Unknown symbol snd_ctl_add
[  580.503821] snd_bt_sco: disagrees about version of symbol snd_pcm_new
[  580.503828] snd_bt_sco: Unknown symbol snd_pcm_new
[  580.504283] snd_bt_sco: disagrees about version of symbol snd_card_register
[  580.504291] snd_bt_sco: Unknown symbol snd_card_register
[  580.504695] snd_bt_sco: disagrees about version of symbol snd_card_free
[  580.504702] snd_bt_sco: Unknown symbol snd_card_free
[  580.505395] snd_bt_sco: disagrees about version of symbol snd_ctl_new1
[  580.505402] snd_bt_sco: Unknown symbol snd_ctl_new1
[  580.506015] snd_bt_sco: Unknown symbol snd_card_new
[  580.506447] snd_bt_sco: disagrees about version of symbol snd_pcm_lib_ioctl
[  580.506454] snd_bt_sco: Unknown symbol snd_pcm_lib_ioctl
[  580.506823] snd_bt_sco: disagrees about version of symbol snd_hwdep_new
[  580.506830] snd_bt_sco: Unknown symbol snd_hwdep_new
[  580.507406] snd_bt_sco: disagrees about version of symbol snd_ctl_notify
[  580.507413] snd_bt_sco: Unknown symbol snd_ctl_notify
[  580.517729] snd_bt_sco: disagrees about version of symbol snd_pcm_set_ops
[  580.517749] snd_bt_sco: Unknown symbol snd_pcm_set_ops
[  580.518805] snd_bt_sco: disagrees about version of symbol snd_pcm_period_elapsed
[  580.518813] snd_bt_sco: Unknown symbol snd_pcm_period_elapsed
[  674.475156] snd_bt_sco: disagrees about version of symbol snd_ctl_add
[  674.475175] snd_bt_sco: Unknown symbol snd_ctl_add
[  674.475666] snd_bt_sco: disagrees about version of symbol snd_pcm_new
[  674.475673] snd_bt_sco: Unknown symbol snd_pcm_new
[  674.476124] snd_bt_sco: disagrees about version of symbol snd_card_register
[  674.476132] snd_bt_sco: Unknown symbol snd_card_register
[  674.476537] snd_bt_sco: disagrees about version of symbol snd_card_free
[  674.476544] snd_bt_sco: Unknown symbol snd_card_free
[  674.477236] snd_bt_sco: disagrees about version of symbol snd_ctl_new1
[  674.477243] snd_bt_sco: Unknown symbol snd_ctl_new1
[  674.477861] snd_bt_sco: Unknown symbol snd_card_new
[  674.478294] snd_bt_sco: disagrees about version of symbol snd_pcm_lib_ioctl
[  674.478301] snd_bt_sco: Unknown symbol snd_pcm_lib_ioctl
[  674.478669] snd_bt_sco: disagrees about version of symbol snd_hwdep_new
[  674.478676] snd_bt_sco: Unknown symbol snd_hwdep_new
[  674.479279] snd_bt_sco: disagrees about version of symbol snd_ctl_notify
[  674.479286] snd_bt_sco: Unknown symbol snd_ctl_notify
[  674.528768] snd_bt_sco: disagrees about version of symbol snd_pcm_set_ops
[  674.528803] snd_bt_sco: Unknown symbol snd_pcm_set_ops
[  674.529862] snd_bt_sco: disagrees about version of symbol snd_pcm_period_elapsed
[  674.529870] snd_bt_sco: Unknown symbol snd_pcm_period_elapsed

```

---

