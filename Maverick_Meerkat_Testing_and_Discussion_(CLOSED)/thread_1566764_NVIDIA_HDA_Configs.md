---
title: "NVIDIA HDA Configs"
date: 2010-09-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Nullack on 2010-09-02
Gday folks,

So I have three Nvidia GTX 480s in tri sli. I've got SLI working fine and the new NVIDIA driver manually installed to support the new X org version as the repo driver is old.

Q: How does the high defintion audio features of the GTX 480 get handled in Linux?

I dont think the closed source nvidia driver configures sound - think it just does graphics?

I went through the ALSA doco and all I could find was details on support NVIDIA HDA for 2XX generation cards not the Fermi generation.

Thanks

EDIT: I see that in the kernel logs noveau isnt supported in fermi chips yet by the look of it, is that right?
```

Sep  3 10:29:10 Bizmark kernel: [    3.256913] nouveau 0000:0c:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
Sep  3 10:29:10 Bizmark kernel: [    3.256916] nouveau 0000:0c:00.0: setting latency timer to 64
Sep  3 10:29:10 Bizmark kernel: [    3.258111] [drm] nouveau 0000:0c:00.0: Unsupported chipset 0x0c0000a3
Sep  3 10:29:10 Bizmark kernel: [    3.258159] nouveau 0000:0c:00.0: PCI INT A disabled
Sep  3 10:29:10 Bizmark kernel: [    3.258162] nouveau: probe of 0000:0c:00.0 failed with error -22
Sep  3 10:29:10 Bizmark kernel: [    3.258171] nouveau 0000:0b:00.0: enabling device (0000 -> 0003)
Sep  3 10:29:10 Bizmark kernel: [    3.258174]   alloc irq_desc for 35 on node -1
Sep  3 10:29:10 Bizmark kernel: [    3.258175]   alloc kstat_irqs on node -1
Sep  3 10:29:10 Bizmark kernel: [    3.258179] nouveau 0000:0b:00.0: PCI INT A -> GSI 35 (level, low) -> IRQ 35
Sep  3 10:29:10 Bizmark kernel: [    3.258182] nouveau 0000:0b:00.0: setting latency timer to 64
Sep  3 10:29:10 Bizmark kernel: [    3.259304] [drm] nouveau 0000:0b:00.0: Unsupported chipset 0x0c0000a3
Sep  3 10:29:10 Bizmark kernel: [    3.259344] nouveau 0000:0b:00.0: PCI INT A disabled
Sep  3 10:29:10 Bizmark kernel: [    3.259346] nouveau: probe of 0000:0b:00.0 failed with error -22
Sep  3 10:29:10 Bizmark kernel: [    3.259357] nouveau 0000:08:00.0: enabling device (0000 -> 0003)
Sep  3 10:29:10 Bizmark kernel: [    3.259360]   alloc irq_desc for 30 on node -1
Sep  3 10:29:10 Bizmark kernel: [    3.259361]   alloc kstat_irqs on node -1
Sep  3 10:29:10 Bizmark kernel: [    3.259365] nouveau 0000:08:00.0: PCI INT A -> GSI 30 (level, low) -> IRQ 30
Sep  3 10:29:10 Bizmark kernel: [    3.259369] nouveau 0000:08:00.0: setting latency timer to 64
Sep  3 10:29:10 Bizmark kernel: [    3.260566] [drm] nouveau 0000:08:00.0: Unsupported chipset 0x0c0000a3
Sep  3 10:29:10 Bizmark kernel: [    3.260606] nouveau 0000:08:00.0: PCI INT A disabled
Sep  3 10:29:10 Bizmark kernel: [    3.260609] nouveau: probe of 0000:08:00.0 failed with error -22
```

---

### Post by VMC on 2010-09-02
Pulseaudio. Try *alsamixer* and see if you have anything muted.

Here's my nVidia audio device:
Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

---

### Post by cariboo on 2010-09-02
HDMI audio output got automagically detected on my system. This one runs a GT210

---

### Post by Nullack on 2010-09-02
Thanks, do you have a fermi chip? i.e. An Nvidia 4XX card?

Alsamixer cant find the fermi HDMI audio which leads me to believe its not supported?

---

### Post by Nullack on 2010-09-02
> **cariboo907 said:**
> HDMI audio output got automagically detected on my system. This one runs a GT210

Hi, thanks but "I went through the ALSA doco and all I could find was details on support NVIDIA HDA for 2XX generation cards not the Fermi generation."

---

### Post by VMC on 2010-09-02
> **Nullack said:**
> Hi, thanks but "I went through the ALSA doco and all I could find was details on support NVIDIA HDA for 2XX generation cards not the Fermi generation."

Here's a **_[link]("http://ubuntuforums.org/showthread.php?t=1487513")_** with the same issue that got solved. Maybe it will work for you.

---

### Post by Nullack on 2010-09-02
That bloke in the thread has an older 2XX generation chip not the 4XX fermi generation that I have. As I said, I know alsa supports 2XX generation as its written in the alsa documentation.

---

### Post by Nullack on 2010-09-03
Ok, sharing some info here in case anyone searching is in the same situation as myself. An NVIDIA developer has kindly answered this question in detail on the NV news linux forum. Basically Fermi is not supported yet and it needs some patches foe GTX 4XX generation cards using the Fermi NVIDIA chips to work.

Info below:


************


For future reference for anyone reading this thread:

The standard kernel ALSA drivers handle the audio portion of NVIDIA GPUs and chipset.

The NVIDIA binary driver is required to pass some of the monitor information to the audio driver.

X must be running for audio to work.

The latest ALSA drivers and library have a couple issues that prevent all this working in some cases. You'll need a few patches from ALSA git to solve this.

a) For all GPUs, and the MCP89 chipset: You need a fix for the PresenceDetect issue:

[http://git.kernel.org/?p=linux/kerne...1cb5fbe7fc9c75](http://git.kernel.org/?p=linux/kerne...1cb5fbe7fc9c75)

b) For all FERMI GPUs: You need a fix so that the kernel driver knows it can handle the new codec IDs:

[http://git.kernel.org/?p=linux/kerne...bf7cef5a942070](http://git.kernel.org/?p=linux/kerne...bf7cef5a942070)

c) The ALSA library and pulseaudio enumerate only a single "high-level" audio device ("PCM") per NVIDIA GPU. However, there are in fact four of them.

The fix for ALSA is at:

[http://git.alsa-project.org/?p=alsa-...dd4916121a4f6a](http://git.alsa-project.org/?p=alsa-...dd4916121a4f6a)

There is no fix for pulseaudio yet, although there was a mailing list discussion where it was agreed that all 4 devices should be exposed.

An alternative is to use the "probe_mask" ALSA module parameter as described on this page:

[http://wiki.xbmc.org/?title=HOW-TO_s...20%2C_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_s...20%2C_or_GT240)

However, please note that the actual values for probe_mask on that page don't make sense; the correct values you should try are 0x101, 0x102, 0x104, 0x108. You can determine which you need by plugging in your HDMI monitor, starting X, then viewing /proc/asound/card*/eld*. Whichever eld file has your monitor's information in it will tell you which probe_mask to use; eld#0.0 -> 0x101, eld#1.0 -> 0x102, eld#2.0 -> 0x104, eld#3.0 -> 0x108. If you use multiple HDMI monitors and want audio on both, logical/bitwise OR the probe_mask values together. Note that the required probe_mask will change if you move monitors to different connectors on your graphics board.

The bug report is here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/611810](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/611810)

---

### Post by VMC on 2010-09-03
Thanks for reporting back on a coming fix. I often wonder what was the outcome on a topic if it doesn't get resolved.

---

### Post by Nullack on 2010-09-03
Thanks mate, since Fermi is pretty common hardware I think it's important it's sorted out before the Maverick production release.

If you dont mind I would prefer not to mark the thread as resolved until a test build is compiled, its tested ok and its all closed.

---

