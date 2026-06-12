---
title: "Conexant CX23880  PCMCIA - 'A known bug in driver cx8800 0.0.5 impedes VBI capturing"
date: 2006-11-26
forum: Multimedia &amp; Video
---

### Post by torstenaf on 2006-11-26
I'm trying to use a Conexant CX23880 based TV Tuner on the PCMCIA bus.  It doesn't work, but I've had a report of it working at some point in time.

I'm using Ubuntu Edgy Eft 6.10.

**lspci**
[I]07:00.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
07:00.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)[/I]

Here is one error I get when starting **kdetv**, but I can't track it down.
* A known bug in driver cx8800 0.0.5 impedes VBI capturing in NTSC mode. Please upgrade.*

Trying to tune a frequency with **ivtv-tune 55.25**:
[I]ioctl VIDIOC_S_FREQUENCY failed
[/I]

I tried to **cat /dev/video0**, and got a huge file, but no video.  :(

It looks like I'm stuck for now.

---

