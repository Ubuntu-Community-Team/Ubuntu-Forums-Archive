---
title: "How to Setup Creative Audigy 2 NX External USB Sound Card?"
date: 2011-12-19
forum: Multimedia Software
---

### Post by jcpeden on 2011-12-19
Hey folks,

I'm trying to run a Creative Labs Audigy NX 2 external USB sound card with Ubuntu Natty and don't know where to begin.

Onboard stereo out works just fine but my USB sound card doesn't appear as a device and I don't have the first clue about how to install it or set it up.

Where should I begin? How do I do this?

Thanks

John

---

### Post by jcpeden on 2011-12-19
Ok,

Made a little progress. I've plugged the USB soundcard straight into the CPU and Ubuntu detected it automatically! Problem was the USB hub I was trying to run it through.

Now I can get the soundcard to output to a set of stereo speakers but I'm having a bit of trouble getting it to run optical 5.1 out.

When I try to configure the sound card through Ubuntu, I'm presented with loads of options...analogue 4.0 + digital input and the like. About 30 in all.

Which do I need to choose to run an optical out?

---

### Post by BicyclerBoy on 2011-12-19
Why not use the S/PDIF of the mobo soundcard?
If you using matrix encoded AC3 or DTS there is no improvement using ext audio device. Chances are the internal mobo will run to higher clock rate with stereo PCM..

The output should be called something like:
Digital Stereo (IEC958) output or S/PDIF.

5.1 matrix audio (AC3/DTS) is digital data stream not an audio stream.
It can not be shared or mixed (not easily) ; no volume control.

Only the latest pulse audio will support digital pass-thru' 5.1 S/PDIF..
So you have to point the media player directly at the alsa IEC958 device to get digital pass-thru'.

e.g.
vlc -aout alsa -alsa-device iec958
& then play a DVD with AC3 or similar..

Will have to see the output:
aplay -l
aplay -L

---

### Post by jcpeden on 2011-12-20
Got it working in the end, I had to plug directly into the HTPC as the USB hub seems to cause problems in Ubuntu.

With the soundcard plugged in, Ubuntu picked it up straight away but there was no sound output. I got this working by selected IEC958 digital output and enabling digital output in gnome-alsamixer.

That said, if the soundcard is unplugged, gnome-alsamixer defaults to off so two questions:

[LIST=1]
[*]Is there a better mixer I can use to manage my sound card and enable digital output to default to on?
[*]What is pulse audio and is it a better solution than Gnome?
[/LIST]
The HTPC I'm using has no digital or SPDIF out, only HDMI (no free ports on my amp) and 3.5mm stereo.


Thanks

John

---

