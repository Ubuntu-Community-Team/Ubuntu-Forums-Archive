---
title: "constant mini-freezes in audio/video in Maverick"
date: 2010-12-18
forum: Multimedia Software
---

### Post by pickarooney on 2010-12-18
I've been goign nuts trying to find the source of this niggling problem I've had since upgrading to Maverick. Whenever I'm watching anything I will get these short freezes of about half a second before he file continues playing. It will happen on average 3-4 times per hour on a video file. 

For MP3 playback it's even worse, I'll get a stutter every couple of minutes, sometimes several in the same song. I reformatted completely and installed Maverick from scratch. For about a day I thought I had it sorted but then it started happening again.

I checked dmesg and there are a number of worrying lines like this:

> [40616.032093] ata1.00: failed command: WRITE DMA
[40616.032108] ata1.00: cmd ca/00:20:df:b6:82/00:00:00:00:00/e0 tag 0 dma 16384 out
[40616.032111]          res 40/00:00:00:4f:c2/00:00:00:00:00/10 Emask 0x24 (host bus error)
[40616.032118] ata1.00: status: { DRDY }
[40616.032153] ata1: soft resetting link
[40616.233445] ata1.00: configured for UDMA/100
[40616.251572] ata1.01: configured for UDMA/100
[40616.251583] ata1.00: device reported invalid CHS sector 0
[40616.251602] ata1: EH complete
[52427.040041] ata1: lost interrupt (Status 0x50)
[52427.040083] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[52427.040091] ata1.00: BMDMA stat 0x66, BMDMA stat 0x0, BMDMA stat 0x0, BMDMA stat 0x0, BMDMA stat 0x0
[52427.040100] ata1.00: failed command: WRITE DMA EXT
[52427.040115] ata1.00: cmd 35/00:00:bf:a7:9a/00:02:00:00:00/e0 tag 0 dma 262144 out
[52427.040118]          res 40/00:00:00:4f:c2/00:00:00:00:00/10 Emask 0x24 (host bus error)
[52427.040125] ata1.00: status: { DRDY }
[52427.040160] ata1: soft resetting link
[52427.249587] ata1.00: configured for UDMA/100
[52427.266169] ata1.01: configured for UDMA/100
[52427.266180] ata1.00: device reported invalid CHS sector 0


The thing is that this problem occurs on all three of my hard drives (2 SATA, one IDE) so it's extremely unlikely all three have become damaged on the day I updated. Could this be a kernel problem of some sort? On an unrelated note all but one of my USB ports fails to recognise any portable music players.

---

### Post by tictacman on 2010-12-19
I was also suffering from the problem of choppy mp3 playback. It's really annoying isn't it?

I found a possible fix, see below.  It didn't work for me, but perhaps it might work for you.
> 

Bug Report: [https://bugs.launchpad.net/ubuntu/+s...0?***ments=all](https://bugs.launchpad.net/ubuntu/+s...0?***ments=all)

Workaround for glitchy (crackling, skipping) audio is to open:
/etc/pulse/default.pa

Find the line that looks like this and add "tsched=0".
Code:
load-module module-udev-detect
It should look like this:
Code:
load-module module-udev-detect tsched=0
Save and reboot (or just log out).


Note this will not fix a problem with that specific chipset in the bug report with a muted speaker/headphone. I have no idea where to go with that one. Lidex and I have been trying to figure it out.

Source: [http://ubuntuforums.org/newreply.php?do=newreply&p=9948061](http://ubuntuforums.org/newreply.php?do=newreply&p=9948061)

As for me, I have had hardware problems.  In dmesg I get messages regarding my wifi card.

[> 18646.969994] ath5k phy0: gain calibration timeout (2447MHz)

After removing the driver with modprobe, mp3 playback seems to be perfect.

---

### Post by pickarooney on 2010-12-19
I removed pulse yesterday to see would it help so don't have that file, but I do still have the problem. I think this more a hardware or kernel problem at this stage.

---

### Post by pickarooney on 2010-12-26
I'm not getting any closer to resolving this after a couple of kernel updates and that suggestion above. Has anyone experienced this sort of every-twenty-minutes-the-video-skips-forward-a-second problem?

---

