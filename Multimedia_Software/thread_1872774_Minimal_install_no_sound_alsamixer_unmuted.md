---
title: "Minimal install no sound alsamixer unmuted"
date: 2011-10-31
forum: Multimedia Software
---

### Post by b1101 on 2011-10-31
Just installed 11.10 minimal and am now working on the sound.  I have pulseaudio installed along with alsa, and have looked through the comprehensive guide posted above. However, I have no sound.

According to alsa, the card is a VIA 8237, chip is Realtek ALC655 rev 0.  This agrees with lspci:

```
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: Micro-Star International Co., Ltd. Device 7410
        Flags: medium devsel, IRQ 22
        I/O ports at d800 [size=256]
        Capabilities: <access denied>
        Kernel driver in use: VIA 82xx Audio
        Kernel modules: snd-via82xx

```

I have set all channels in alsamixer to unmuted at maximum volume, and still nothing - no error mesages in console for mplayer or vlc.  (Un/)Muting the master channel in alsamixer does cause static to start and stop with the speakers turned up all the way, so something is there, just not the output.

Quodlibet is telling me this, no idea if related or not:

```
0:00:05.490277912  1462  0x98c6870 ERROR           GST_PIPELINE ./grammar.y:661:_gst_parse_yyparse: no element "gconfaudiosink"
0:00:05.492055364  1462  0x98c6870 ERROR           GST_PIPELINE ./grammar.y:929:_gst_parse_launch: Unrecoverable syntax error while parsing pipeline gconfaudiosink profile=music
W: Invalid GStreamer output pipeline, trying default.
0:00:07.871903020  1462  0x98c6870 ERROR           GST_PIPELINE ./grammar.y:661:_gst_parse_yyparse: no element "gconfaudiosink"
0:00:07.872842246  1462  0x98c6870 ERROR           GST_PIPELINE ./grammar.y:929:_gst_parse_launch: Unrecoverable syntax error while parsing pipeline gconfaudiosink profile=music
W: Invalid GStreamer output pipeline, trying default.

```

I have no idea why the sound is not working, as the previous install (crunchbang 9.04) had no issues with sound.

---

