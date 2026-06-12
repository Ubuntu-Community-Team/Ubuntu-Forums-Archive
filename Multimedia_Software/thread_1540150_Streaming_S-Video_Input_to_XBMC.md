---
title: "Streaming S-Video Input to XBMC"
date: 2010-07-27
forum: Multimedia Software
---

### Post by phoenixkc on 2010-07-27
I have an HTPC running Ubuntu Server 10.04 Lucid with XBMC as the interface (no real window manager installed, I access though SSH). I have a Hauppauge WinTV-HVR-1600 capture card installed that I would like to watch whatever is on the S-Video input through XBMC (I'm using a Wii with the composite piped though a converter to S-video for testing, if it matters). XBMC does support this directly and a solution I've found that seems workable is to stream the video from the HVR to localhost:8080 and pick it up that way.

I've been poking at it for about a week, trying out suggestions I've found either here or elsewhere with no luck. I know the Hauppauge stuff has caused issues on earlier versions of Ubuntu but I've read an increasing amount of success stories with these cards as Ubuntu has matured.

So, time to start again from the beginning and try and figure out what I've missed. What commands do you want to see run? What programs should I be trying? Suggestions please!

---

### Post by phoenixkc on 2010-07-27
A little more info. The card seems to have loaded okay:

```
kyle@xbmc:~$ dmesg | grep cx18
[   14.862804] cx18:  Start initialization, version 1.4.0
[   14.868595] cx18-0: Initializing card 0
[   14.874711] cx18-0: Autodetected Hauppauge card
[   14.881599] cx18 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 16 (level, low) -> IRQ 16
[   14.927934] cx18-0: cx23418 revision 01010000 (B)
[   15.236603] cx18-0: Autodetected Hauppauge HVR-1600
[   15.248108] cx18-0: Simultaneous Digital and Analog TV capture supported
[   15.335118] IRQ 16/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[   15.661202] tuner 3-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[   15.691347] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   15.736719] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   15.785646] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   15.785649] DVB: registering new adapter (cx18)
[   16.006835] cx18-0: DVB Frontend registered
[   16.006838] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   16.006868] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   16.006892] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   16.006914] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   16.006939] cx18-0: Registered device radio0 for encoder radio
[   16.006941] cx18-0: Initialized card: Hauppauge HVR-1600
[   16.007226] cx18:  End initialization
[   16.040277] cx18 0000:01:07.0: firmware: requesting v4l-cx23418-cpu.fw
[   16.042095] cx18-alsa: module loading...
[   16.382590] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   16.407413] cx18 0000:01:07.0: firmware: requesting v4l-cx23418-apu.fw
[   16.546916] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   16.553118] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   16.770247] cx18 0000:01:07.0: firmware: requesting v4l-cx23418-cpu.fw
[   16.905156] cx18 0000:01:07.0: firmware: requesting v4l-cx23418-apu.fw
[   17.223059] cx18 0000:01:07.0: firmware: requesting v4l-cx23418-dig.fw
[   17.480338] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   17.500360] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[  426.252015] cx18-0 843: 2x2 is not a valid size!

```

But when I try to play /dev/video0 with the input set to S-Video 1, I get a black screen in xawtv and a seq fault from vlc.

---

### Post by phoenixkc on 2010-07-28
Progress. Maybe.

Unloaded the drivers with [FONT="Courier New"]make unload[/FONT]. reloaded with [FONT="Courier New"]modprobe cx18[/FONT].

Jumped over to my vnc view and started messing with mplayer. mplayer does not seem to want to actually display video over vnc. But it does seem to be working:

After I ran [FONT="Courier New"]cat /dev/video0 | mplayer - -vo X11[/FONT] I got the following:

```
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  8000.0 kbps (1000.0 kbyte/s)
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 699.1 (11:39.1) of 0.0 (unknown) 90.1% 
```

I think that last line means it's playing something. I'm not that familiar with mplayer so if someone could help me out that would be great. The percentage at the end seems to be heading toward 100% but is slowing down like it's asymptotic.

What I'd really like to do is either capture the output or better yet stream it somewhere viewable from another computer or XBMC. Help please!

man mplayer here I come...

---

