---
title: "No sound when playing ac3 in mplayer"
date: 2008-08-23
forum: Multimedia Software
---

### Post by miceagol on 2008-08-23
I have problems playing videos with ac3 audio (including DVD's) in mplayer. The relevant output of mplayer is as follows:
```

Forced audio codec: hwac3
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 448000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
[AO_ALSA] alsa-lib: conf.c:3843:(parse_args) Unknown parameter AES0
[AO_ALSA] alsa-lib: conf.c:3969:(snd_config_expand) Parse arguments error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM plug:spdif,AES0=6
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)

```
This is my .asoundrc file,
```

pcm.!default {
	type plug
	slave.pcm "iec958:CARD=Revolution51,DEV=0" # taken from aplay -L
}

```
and this is my mplayer configuration file:
```

[default]
# Write your default config options here!

monitoraspect=16:10
subfont-text-scale=3
xy=2

ac=hwac3,
ao=alsa:device=plug=spdif
#af=resample=44100

vo=xv
zoom=1
dvd-device=/dev/scd0

```

This is my audio setup:
Sound card => M-audio Revolution 5.1
Output => Digital Coaxial S/PDIF connected to [this amplifier]("http://www.xtz.se/produkt.php?allmant=true&produkt=5&eng=true")

Any inputs on what the problem is here? Can't my amplifier decode DTS sound streams even if it has a D/A decoder? If this is so, why do I get sound in VLC (but with a small issue [described in this post]("http://ubuntuforums.org/showthread.php?t=898433"))?

---

### Post by Orfintain on 2008-08-24
I think i'm haveing trouble with ac3 too, I tried a couple different players

---

### Post by generica on 2009-01-11
I have had this exact issue for a long time.  I gave up.  I got the exact same error messages as you.  Does it work when you play a DTS source with -ac hwdts?  Because that seems to work for me, but it doesn't help with AC3 encoded content.


> **miceagol said:**
> I have problems playing videos with ac3 audio (including DVD's) in mplayer. The relevant output of mplayer is as follows:
```

Forced audio codec: hwac3
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 448000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
[AO_ALSA] alsa-lib: conf.c:3843:(parse_args) Unknown parameter AES0
[AO_ALSA] alsa-lib: conf.c:3969:(snd_config_expand) Parse arguments error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM plug:spdif,AES0=6
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)

```
This is my .asoundrc file,
```

pcm.!default {
	type plug
	slave.pcm "iec958:CARD=Revolution51,DEV=0" # taken from aplay -L
}

```
and this is my mplayer configuration file:
```

[default]
# Write your default config options here!

monitoraspect=16:10
subfont-text-scale=3
xy=2

ac=hwac3,
ao=alsa:device=plug=spdif
#af=resample=44100

vo=xv
zoom=1
dvd-device=/dev/scd0

```

This is my audio setup:
Sound card => M-audio Revolution 5.1
Output => Digital Coaxial S/PDIF connected to [this amplifier]("http://www.xtz.se/produkt.php?allmant=true&produkt=5&eng=true")

Any inputs on what the problem is here? Can't my amplifier decode DTS sound streams even if it has a D/A decoder? If this is so, why do I get sound in VLC (but with a small issue [described in this post]("http://ubuntuforums.org/showthread.php?t=898433"))?

---

### Post by xzero1 on 2009-01-17
Try: mplayer -ao alsa:device=hw=0.0 -ac3 hwac3...

At least this works with my svn mplayer.

---

### Post by Bill.Pringlemeir on 2009-01-17
The AES0=6 option is to put the spdif (co-axial/optical) connector in the proper mode.  You can run 'man iecset'.  Basically there are two modes for the spdif connector.  For my sound blaster Live card, this is "IEC958 Optical Raw" when running alsamixer.  This is a toggle button.  It is either on or off.

You will get two channel sound with it off when playing normal mp3,etc.  I have an ATSC/HDTV card.  This supports NTSC (old style tv) as well.  In order to play the NTSC, I have to set the 'raw' to off.  This routes the sound through the spdif like it was an RCA cable.  The sound card interprets the write like two channel sound.  On my sony amp, it shows 2 channel PCM, 48kHz.  The sound card will convert the sound so that it is the expected 48kHz that the spdif mandates.

Now to play DTS/AC3/Dolby Digital, you need the 'raw' set to on.  Then the sound card sends the data to the card as is.  The AES0=6 is mplayers attempt to get the spdif set to 'raw'.  You can do this manually by using one of alsamixer, amixer, or iecset.  The last two are good for wrapper scripts or aliases.  The raw compressed data is AC3 or DTS that mplayer steals from the avi, mpeg-ts, etc stream.  It is compressed data that the amp (DTS/AC3 sound device) will decode to get the 5.1 sound.

---

### Post by _zifban on 2010-04-06
I had a similar problem with ac3 passthrough giving only static/silence or mplayer crashing, depending on the selected device. The ac3 passthrough has worked before but after kubuntu upgrade and time passing it stopped working. I was not able to change the audio setting with iecset, it had no effect to the audio bit. However, disabling (muting) the equalizer with alsamixer fixed the problem and ac3 passthrough works with 5.1 channels. The warnings/errors "[AO_ALSA] alsa-lib: .... Unknown parameter AES0" are still displayed when running mplayer.

---

