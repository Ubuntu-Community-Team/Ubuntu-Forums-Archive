---
title: "No HDMI audio with GT 420 card"
date: 2010-10-31
forum: Multimedia Software
---

### Post by z987k on 2010-10-31
I'm getting no sound though HDMI with the Nvidia GT420 card on my laptop.
I read through this thread on the 240: [http://ubuntuforums.org/showthread.php?t=1565479&highlight=GT+420](http://ubuntuforums.org/showthread.php?t=1565479&highlight=GT+420) and mostly everything mentioned there is standard with 10.10.

Nvidia driver 260.19.06, ALSA 1.0.23.  It shows up in alsamixer as HDANvidia, but says "this sound device does not have any controls."

Not entirely sure where to go from here.

---

### Post by Yellow Pasque on 2010-10-31
You'll probably need an ALSA snapshot: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137) (use -s)

---

### Post by z987k on 2010-11-01
it appears I have the latest alsa - 1.0.23

---

### Post by Yellow Pasque on 2010-11-01
latest stable - 1.0.23
latest development - use the -s options as I told you to.

---

### Post by z987k on 2010-11-03
well that broke everything... now the sound card and the video card(sound portion) are not recognized.

further:
linux:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory

---

### Post by efflandt on 2010-11-03
Not sure about GT 420, but for my GT 220 it was simple once I found a thread with the right info.  The alsa in Maverick is already the correct version.  Although, I am running a newer nvidia version 260.19.12 available from x-swat repositories.

First you may want to check the output of **aplay -l** which on my desktop was:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```So mine is card 1 device 3.  Use sudo nano or your favorite editor to create /etc/asound.conf with following in it using whatever your first NVIDIA HDMI card and device are:

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```Then create /etc/modprobe.d/sound.conf with following line in it:

```
options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2
```After reboot that gave me either analog stereo (built-in sound chip) or HDMI stereo in Rythmbox depending upon which I selected in Output tab of Sound Preferences.

IF YOU WANT NVIDIA 260.19.12
Go to System > Administration > Additional Drivers and "remove" nvidia, reboot, then do:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update
```Go to Additional Drivers and "activate" nvidia, reboot, done.

---

### Post by z987k on 2010-11-04
well aplay -l gives:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

So it doesn't seem to be seeing it.

However here's what alsamixer sees:

[IMG]http://lh6.ggpht.com/_4dlM9u1Ei9M/TNMjdjHk7KI/AAAAAAAAEcQ/9FaY5GolxqA/s800/Screenshot.png[/IMG]

I did install the 260.19.12 driver.

lspci shows it is there:
```

01:00.0 VGA compatible controller: nVidia Corporation Device 0df1 (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)

```

but it's not loaded in lsmod as you would expect.

---

### Post by dagame on 2010-11-04
hi, i'm having the same problem as well with maverick. I got exactly the same video card on my Acer aspire 5742G-7200. This is what showed up with aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

Hope we can find a soulution soon. :confused:

---

### Post by efflandt on 2010-11-05
What does **sudo lspci -v** show for your sound device(s) and modules used for them?

My desktop with i5 cpu and GT 220 shows 2 devices (maybe my ALC887 Analog is in the 1st device):

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

Both use:

Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

Also what shows from: **dmesg | grep -i hda**

For **option snd-hda-intel** there are various model=xxx you could try (ignore line numbers on left):

```
  92 ALC662/663/272

  93 ==============

  94   3stack-dig    3-stack (2-channel) with SPDIF

  95   3stack-6ch     3-stack (6-channel)

  96   3stack-6ch-dig 3-stack (6-channel) with SPDIF

  97   6stack-dig     6-stack with SPDIF

  98   lenovo-101e    Lenovo laptop

  99   eeepc-p701    ASUS Eeepc P701

 100   eeepc-ep20    ASUS Eeepc EP20

 101   ecs           ECS/Foxconn mobo

 102   m51va         ASUS M51VA

 103   g71v          ASUS G71V

 104   h13           ASUS H13

 105   g50v          ASUS G50V

 106   asus-mode1    ASUS

 107   asus-mode2    ASUS

 108   asus-mode3    ASUS

 109   asus-mode4    ASUS

 110   asus-mode5    ASUS

 111   asus-mode6    ASUS

 112   asus-mode7    ASUS

 113   asus-mode8    ASUS

 114   dell          Dell with ALC272

 115   dell-zm1      Dell ZM1 with ALC272

 116   samsung-nc10  Samsung NC10 mini notebook

 117   auto          auto-config reading BIOS (default)
```

---

### Post by z987k on 2010-11-05
Two audio devices for lspci -v

```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0487
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at b7100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

and

```
01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
	Subsystem: Acer Incorporated [ALI] Device 0487
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at b3000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

Looks like it's using the wrong driver, although you said that's how it works in your so, I guess that's right.

dmesg has this for hda:

```
[   13.078240] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.078335] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   13.078377] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.129298] hda_codec: ALC272X: BIOS auto-probing.
[   14.136383] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.136387] hda_intel: Disable MSI for Nvidia chipset
[   14.136419] HDA Intel 0000:01:00.1: setting latency timer to 64

```

As for the sound.conf option and  the asound.conf, we don't know the device location so those are of no use yet... right?

Also on reading the asound.conf part to make... what part do we edit to reflect the card and device?  I'm really not following you there.


dagame, I have the 5742G-7200 as well.

---

### Post by efflandt on 2010-11-05
Have you tried the /etc/asound.conf and /etc/modprobe.d/sound.conf I listed above?

Although different ALC and GT note how the tail end of 0xffff and 0xfff2 show up in (the latter is nvidia HDMI):

dmesg | grep -i hda

```
[   12.626434] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.626436] hda_intel: **codec_mask forced to 0xff**
[   12.626477] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.894598] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   16.902126] hda-intel: Codec #1 probe error; disabling it...
[   17.990705] hda-intel: Codec #2 probe error; disabling it...
[   18.096884] hda_codec: ALC887: BIOS auto-probing.
[   18.109923] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.109928] hda_intel: **codec_mask forced to 0xf2**
[   18.109966] HDA Intel 0000:01:00.1: setting latency timer to 64
[   21.241532] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x400f0000
[   22.240333] hda-intel: Codec #4 probe error; disabling it...
[   23.337635] hda-intel: Codec #5 probe error; disabling it...
[   24.433695] hda-intel: Codec #6 probe error; disabling it...
[   25.540977] hda-intel: Codec #7 probe error; disabling it...
[   32.738638] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
```Not sure how to fix or set bdl_pos_adj, but my older dual core laptop mentions that too without HDMI (my old single core desktop does not), and it does not seem to cause any sound issues.  alsamixer ends up showing this as default with my /etc/asound.conf (Output device controlled by Sound Preferences in gnome):

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.23 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: PulseAudio                                     F1:  Help               &#9474;
&#9474; Chip: PulseAudio                                     F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Master                                         Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                                     &#9484;&#9472;&#9472;&#9488;                                     &#9474;
&#9474;                                     &#9474;  &#9474;                                     &#9474;
&#9474;                                     &#9474;  &#9474;                                     &#9474;
&#9474;                                     &#9474;  &#9474;                                     &#9474;
&#9474;                                     &#9474;  &#9474;                                     &#9474;
&#9474;                                     &#9474;  &#9474;                                     &#9474;
&#9474;                                     &#9474;  &#9474;                                     &#9474;
&#9474;                                     &#9474;  &#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9474;&#9618;&#9618;&#9474;                                     &#9474;
&#9474;                                     &#9500;&#9472;&#9472;&#9508;                                     &#9474;
&#9474;                                     &#9474;OO&#9474;                                     &#9474;
&#9474;                                     &#9492;&#9472;&#9472;&#9496;                                     &#9474;
&#9474;                                    30<>30                                    &#9474;
&#9474;                                  < Master >                                  &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```The  HDA Intel page of alsamixer shows all inputs/outputs including S/PDIF and HDA NVidia just shows S/PDIF.

I have no way of testing whether that would work with GT 420, but it is worth trying.

---

### Post by shizzlenullr1 on 2011-01-05
> **efflandt said:**
> Not sure about GT 420, but for my GT 220 it was simple once I found a thread with the right info.  The alsa in Maverick is already the correct version.  Although, I am running a newer nvidia version 260.19.12 available from x-swat repositories.

First you may want to check the output of **aplay -l** which on my desktop was:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```So mine is card 1 device 3.  Use sudo nano or your favorite editor to create /etc/asound.conf with following in it using whatever your first NVIDIA HDMI card and device are:

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```Then create /etc/modprobe.d/sound.conf with following line in it:

```
options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2
```After reboot that gave me either analog stereo (built-in sound chip) or HDMI stereo in Rythmbox depending upon which I selected in Output tab of Sound Preferences.

Awesome this method fixes HDMI sound for Acer 5742G-7200 (420GT). Before it would show the card and let me mess with volume and such but would not play any sound. Not sure exactly what you meant by checking the card but it is also card 1 device 3. Im not sure how you would modify it to work if your card was in a different location but for this laptop just making those files and staight copy/pasting the code makes it works with the normal nvidia driver. Thanks.

---

