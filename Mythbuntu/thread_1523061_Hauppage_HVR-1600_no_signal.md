---
title: "Hauppage HVR-1600 no signal"
date: 2010-07-03
forum: Mythbuntu
---

### Post by Jack_Simth on 2010-07-03
Hello all,

I have a Hauppage HVR-1600 that's giving me grief; I get static on the one channel I expect to get video (I've got a DTA converter box), and w_scan shows nothing.  Per a [How to Get Help]("http://ubuntuforums.org/showthread.php?t=736528") thread, I'm listing a few things...

/var/log/mythtv: Attached, as they're somewhat lengthy.

dmesg info on what's going on with the cx18 driver...
```
jack@jack-desktop:~$ dmesg | grep cx
[   24.821593] cx18:  Start initialization, version 1.2.0
[   24.821642] cx18-0: Initializing card 0
[   24.821647] cx18-0: Autodetected Hauppauge card
[   24.822022] cx18 0000:01:06.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   24.822029] cx18-0: Unreasonably low latency timer, setting to 64 (was 2)
[   24.823308] cx18-0: cx23418 revision 01010000 (B)
[   25.123822] cx18-0: Autodetected Hauppauge HVR-1600
[   25.123824] cx18-0: Simultaneous Digital and Analog TV capture supported
[   25.243585] IRQ 17/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[   25.259809] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   25.261762] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   25.274426] cx18-0: Registered device video0 for encoder MPEG (64 x 32 kB)
[   25.274431] DVB: registering new adapter (cx18)
[   25.354009] cx18-0: DVB Frontend registered
[   25.354011] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
[   25.354039] cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
[   25.354058] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   25.354076] cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
[   25.354079] cx18-0: Initialized card: Hauppauge HVR-1600
[   25.354098] cx18:  End initialization
[   25.376880] cx18 0000:01:06.0: firmware: requesting v4l-cx23418-cpu.fw
[   25.546792] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   25.571386] cx18 0000:01:06.0: firmware: requesting v4l-cx23418-apu.fw
[   25.667479] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   25.673637] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   25.896396] cx18 0000:01:06.0: firmware: requesting v4l-cx23418-cpu.fw
[   26.027630] cx18 0000:01:06.0: firmware: requesting v4l-cx23418-apu.fw
[   26.345667] cx18 0000:01:06.0: firmware: requesting v4l-cx23418-dig.fw
[   26.533213] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   26.552236] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[   31.326449] cx18-0: unregister DVB
[   31.327718] cx18 0000:01:06.0: PCI INT A disabled
[   31.327720] cx18-0: Removed Hauppauge HVR-1600
[   36.340532] cx18:  Start initialization, version 1.2.0
[   36.340577] cx18-0: Initializing card 0
[   36.340581] cx18-0: Autodetected Hauppauge card
[   36.340671] cx18 0000:01:06.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   36.341957] cx18-0: cx23418 revision 01010000 (B)
[   36.556308] cx18-0: Autodetected Hauppauge HVR-1600
[   36.556310] cx18-0: Simultaneous Digital and Analog TV capture supported
[   36.652956] IRQ 17/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[   36.657340] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   36.658421] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   36.661516] cx18-0: Registered device video0 for encoder MPEG (64 x 32 kB)
[   36.661519] DVB: registering new adapter (cx18)
[   36.681836] cx18 0000:01:06.0: firmware: requesting v4l-cx23418-cpu.fw
[   36.791487] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   36.838998] cx18-0: DVB Frontend registered
[   36.839001] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
[   36.839029] cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
[   36.839049] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   36.839069] cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
[   36.839071] cx18-0: Initialized card: Hauppauge HVR-1600
[   36.839092] cx18:  End initialization
[   36.849646] cx18 0000:01:06.0: firmware: requesting v4l-cx23418-apu.fw
[   36.947837] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   36.953800] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   37.161019] cx18 0000:01:06.0: firmware: requesting v4l-cx23418-cpu.fw
[   37.292774] cx18 0000:01:06.0: firmware: requesting v4l-cx23418-apu.fw
[   37.638704] cx18 0000:01:06.0: firmware: requesting v4l-cx23418-dig.fw
[   37.857978] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   37.876856] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)

```I'm running Ubuntu 9.10, MythTV 0.22.  Any suggestions?


Edit: This may or may not be important... but when I try to tell MythTV to scan on the analog side, it just hangs there until I tell it to stop.
And the terminal then says DTVParamHelper::toString() index out of bounds.  Hmm....

Edit:
I've got a workaround in place; the S-Video input works, and I've got something that works that will convert the output from the Digital Transport Adapter to RCA, and some more adapters to convert it to S-video (video channel only...) and the line-in.  Which works.  I'll leave this up in case anyone wants to take an actual crack at it, though.

---

### Post by hineas on 2010-09-27
I know this is a few months old, but in the past I have had problems for months without getting them fixed...

I had a similar problem with Mythbuntu 9.10 during the channel scan.  I read a lot on the forums that there seemed to be a bug that would cause the channel scan to hang when it reached a channel with no signal.  My work around was to populate my channel list directly from schedulesdirect.org.  I don't remember exactly where to do that, but it is somewhere in mythtv-setup (I believe it is in video sources).  Luckily, this bug has been fixed in 10.04.

As for the one channel static issue--I can't help you there unless it is an issue with the scan.  I, for one, am having issues where all of my channels except for one are crystal clear...  I hope you already have everything figured out!

---

### Post by klc5555 on 2010-09-28
> **hineas said:**
> 
As for the one channel static issue--I can't help you there unless it is an issue with the scan.  I, for one, am having issues where all of my channels except for one are crystal clear...  I hope you already have everything figured out!

If it's one single analog channel that's not crystal clear, then you may need to search for sources of RF interference: the PC power supply and fans, for example, traditionally wipe out most of the frequency range for analog channels 5 and 6.

If it's one single digital channel that's not crystal clear with the Hauppauge 1600, then you should probably thank the gods that it's only one.

Anyway, assuming that it's the weakest digital signal that's unacceptably artifacting, and that you've compiled and are using the latest cx18 driver, which incorporates some DVB signal-strength patches, then the only recommendations are to make sure the cabling's tight with only the absolute minimum necessary splitting, and to use a good drop amp on the cable line in (Motorola or similar).

If that doesn't help, then the only sure cure is to use a better, more Linux-friendly digital card. PCHDTV HD-5500, of course; or perhaps even something like the new-style digital-only AverMedia 180 (or other inexpensive Phillips tuner cards) come to mind, though these latter can be a bit tricky to set up the first time.

---

### Post by Quadari on 2010-09-28
> **Jack_Simth said:**
> I have a Hauppage HVR-1600 that's giving me grief; I get static on the one channel I expect to get video 

I fully admit I know nothing about DTA converter boxes, but modulo that I was having the same problem last week with my HVR-1600.  I had mine just plugged directly into the cable coming in from the wall, and was trying to get the clear QAM broadcast.

I sort of detailed out how I got it working in the posts on this page:
[http://ubuntuforums.org/showthread.php?t=1563981&page=6](http://ubuntuforums.org/showthread.php?t=1563981&page=6)

So hopefully that's of some help.

Also, supposedly the HVR-1600 is known to have finicky reception.  I haven't run into this problem at all, but other people have suggested that getting an inline amp.  I've been told that there are reasonable ones from Motorola on amazon.com or just from radio shack.

---

