---
title: "HDA Intel SigmaTel STAC9221 A1 mic issues: high-pitched background noise"
date: 2012-04-02
forum: Multimedia Software
---

### Post by wayover13 on 2012-04-02
Hi. This issue refers to a highly-customized Ubuntu installation that doesn't use any of the standard GUI stuff. It's a system I built up from scratch from a minimal installation. It does have Xorg and a WM--evilwm. But I try to avoid a lot of the unnecessary overhead of graphical environments and applications, so many of the standard Ubuntu graphical utilities for looking into sound issues will be absent on this machine. Those factors should be borne in mind in considering the following problem.

This machine has HDA Intel SigmaTel STAC9221 A1 sound system, which is generally working. Playback of, for example music or sound in videos is fine. The problem I'm having with the sound concerns recording input from the mic: I can record, but there is a high-pitched background noise in the recording on playback, and I've been unable to get rid of it. 

Oddly, the high-pitched noise is much louder when I record through the rear mic jack than when I record through the front mic jack. In the former case, the noise is just too annoying to listen to the recording for any length of time. In the latter case, it is much quieter and so more tolerable, though it can still be heard.

I've been fiddling with various settings and volume levels using alsamixer--see a screen shot of the features of this card that alsamixer detects at [http://postimage.org/image/6yba5yy4n/](http://postimage.org/image/6yba5yy4n/) (bear in mind this screenshot is just to demonstrate what alsamixer sees: those settings have been adjusted and readjusted many times, so the current adjustments don't match what's shown in the screenshot). As I said, no joy there.

Pulse audio must be a part of the sound equation on this system and is something I understand rather poorly. If it could be playing some role in the sound problems I'm having, I'd appreciate tips on how to diagnose that.

Also, I'm wondering whether there's a possibility the sound chip could be picking up some sort of interference from some other electronic part in this machine that, for whatever reason, affects only the mic input jack? Seems like kind of a long shot. I should also mention this is a machine I got second hand, so I am uncertain whether this problem pre-existed my Ubuntu installation (it came with Windows 7 or some such, but I pulled the original HD and added my own with Ubuntu on it).

Input on this issue will be appreciated.

Thanks,
James

---

### Post by wayover13 on 2012-04-02
Here's some dmesg output in case that will help diagnose the issue:> me@pmycomputer:~$ dmesg |grep HDA
[   20.520122] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.520182] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   20.520213] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.888880] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   20.889196] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   20.889449] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   20.889712] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   20.889964] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   20.890221] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   20.890468] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
James

PS Come to think of it, this looks a bit suspicious: > [   20.889449] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   20.889712] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8 rear mic jack is listed as having two inputs?

---

