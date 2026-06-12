---
title: "Recognized HDMI, no output - Ubuntu 12.10, Dell Vostro 3700"
date: 2013-01-15
forum: Multimedia Software
---

### Post by dualon on 2013-01-15
Hi,

Fresh Ubuntu 12.10 64-bit install on a Dell Vostro 3700 with intel integrated graphics and nvidia GT 330M.
An LG TV is connected to the laptop via a HDMI cable. The HDMI option appears in Settings -> Display and the additional desktop area is there if I hit Super + S, but there is no output on the TV and the TV does not appear as an option in Settings -> Sound.

I've tried different cables and HDMI ports, but the problem is most probably not there (since Ubuntu recognizes the TV and the TV works perfectly with another laptop with Ubuntu 12.10).
Reboot, logging in again didn't help either.

I installed the nvidia current driver (after installing build-essential, linux-source and the appropriate linux headers), but it failed to work together with Unity. :/

I've browsed all the HDMI topics on this forum and I've spent my day with google, yet haven't found any solution. :(

I would highly appreciate ANY help or hint, I really want the HDMI to work. :(
Please let me know if I should provide any further information.

System details in pastebin:
[http://pastebin.com/5KNpUWMq](http://pastebin.com/5KNpUWMq)

And here:
```

[LIST=1]
[*]dualon@alpha-neuron:~$ uname -a
Linux alpha-neuron 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
 
dualon@alpha-neuron:~$ sudo lshw -c display
*-display
description: VGA compatible controller
product: GT216 [GeForce GT 330M]
vendor: NVIDIA Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a2
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
configuration: driver=nouveau latency=0
resources: irq:16 memory:f9000000-f9ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fa000000-fa07ffff
*-display
description: VGA compatible controller
product: Core Processor Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 18
width: 64 bits
clock: 33MHz
capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:48 memory:fa400000-fa7fffff memory:b0000000-bfffffff ioport:f080(size=8)
 
dualon@alpha-neuron:~$ xrandr | grep HDMI
HDMI1 connected 1920x1080+1600+0 (normal left inverted right x axis y axis) 160mm x 90mm
 
dualon@alpha-neuron:~$ lsmod | grep hdmi
snd_hda_codec_hdmi     32007  4 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_pcm                96580  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd                    78734  26   snd_hda_codec_hdmi,snd_usb_audio,snd_hda_codec_idt,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
[/LIST]


```

---

### Post by reecehart on 2013-02-02
I've got a similar problem on a Dell XPS 14 Ultrabook.  HDMI works on many models of projectors and displays, but not with a particular projector (Optoma HD20).  Reported here:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1112859](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1112859)

---

### Post by dualon on 2013-02-20
Thank you for opening that bug report. I am not sure if the problem is the same, but the circumstances seem to be very similar.

---

