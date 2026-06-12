---
title: "Play a 24 bits sound"
date: 2010-05-24
forum: Multimedia Software
---

### Post by DbianUsr on 2010-05-24
Hi!
I've two problems! First, it's about DTS decoding... When I try to play a DTS file with MPlayer, it seems to be impossible to get a 24 bits sampled sound :

```
libavformat file format detected.
[lavf] Audio stream found, -aid 0
==========================================================================
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
```Here, the file is a 24bits/48kHz source.
My PulseAudio server is configured in 24 bits endian, but it doesn't affect my problem because it's seems to be due to DTS decoding... :(

Then I converted the DTS to PCM, and I tested again with a PCM 24bits/48kHz source... Outcome :
```
Audio only file format detected.
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 48000 Hz, 6 ch, s24le, 6912.0 kbit/100.00% (ratio: 864000->864000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 48000Hz 6ch s16le (2 bytes per sample)
Video: no video
Starting playback...
[reorder_ch] Unsupported sample size: 3, please report this error on the MPlayer mailing list.
[reorder_ch] Unsupported sample size: 3, please report this error on the MPlayer mailing list.
[reorder_ch] Unsupported sample size: 3, please report this error on the MPlayer mailing list.
[reorder_ch] Unsupported sample size: 3, please report this error on the MPlayer mailing list.
[reorder_ch] Unsupported sample size: 3, please report this error on the MPlayer mailing list.
[reorder_ch] Unsupported sample size: 3, please report this error on the MPlayer mailing list.
[reorder_ch] Unsupported sample size: 3, please report this error on the MPlayer mailing list.
  =====  PAUSE  =====
A:   0.1 (00.0) of 4730.0 ( 1:18:50.0) ??,?%
```Well my question : how to play a 24 bits sound on MPlayer?
I notice that I'm a Lucid user, and that my sound card is a Creative Sound Blaster X-Fi Titanium, compatible 24 bits, and greatly configured!

NOTE : VLC seems to play it well, so is it an MPlayer specific problem? I saw that [thread]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-May/076840.html"), it didn't progressed?
Sorry for my English, I'm french :P

---

### Post by mc4man on 2010-05-24
Unfortunately don't have any full rate 24 bit dts files here, all of the 24 bit i have are flac or wma. (if a sample is available that would be great

The closet I have is a 20 bit full rate 5.1 dts, but it did reveal something here that may or may not be applicable to you.

It appears my card doesn't support s24le, but does s16le and s32le.

So while mplayer does this with the 24 bit flac's...
> Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 88200 Hz, 6 ch, s32le, 5838.7 kbit/34.48% (ratio: 729839->2116800)
Selected audio codec: [ffflac] afm: ffmpeg (FFmpeg FLAC audio)
==========================================================================
AO: [pulse] 88200Hz 6ch floatle (4 bytes per sample)
or
> Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 192000 Hz, 2 ch, s32le, 5073.5 kbit/41.29% (ratio: 634182->1536000)
Selected audio codec: [ffflac] afm: ffmpeg (FFmpeg FLAC audio)
==========================================================================
AO: [alsa] 192000Hz 2ch floatle (4 bytes per sample)


With the 20 bit dts it drops to s16le
> Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, s16le, 1536.0 kbit/33.33% (ratio: 192000->576000)
Selected audio codec: [ffdca] afm: ffmpeg (FFmpeg DTS)
==========================================================================
AO: [pulse] 48000Hz 6ch floatle (4 bytes per sample)

Though I could force the format, not to 24 (unsupported), but to 32 with

-format s32le

> Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, s16le, 1536.0 kbit/33.33% (ratio: 192000->576000)
Selected audio codec: [ffdca] afm: ffmpeg (FFmpeg DTS)
==========================================================================
AO: [pulse] 48000Hz 6ch s32le (4 bytes per sample)

So are you sure your dts's are 24 bit vs 20 bit?

Try -format s24le in mplayer command

---

### Post by DbianUsr on 2010-05-25
Thanks for your answer!

> It appears my card doesn't support s24le, but does s16le and s32le.Well I'm surprised because my card certainly support s24le, but MPlayer does the same, event if I use -format s24le :
```
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 768.0 kbit/50.00% (ratio: 96000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
```When I used your command, it works with s32le, a good point :
```
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 768.0 kbit/50.00% (ratio: 96000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
AO: [pulse] 48000Hz 2ch s32le (4 bytes per sample)
```But DTS isn't decoded in 24 bits : *AUDIO: 48000 Hz, 2 ch, s16le*. Any ideas?

Then I played a 24 bits flac, No problem, thanks! s24le doesn't work again but s32le is awesome!

But eternal problem, with PCM 24bits/48kHz, even if I force MPlayer's job with -format s32le, it does the same :
```
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 48000 Hz, 6 ch, s24le, 6912.0 kbit/100.00% (ratio: 864000->864000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 48000Hz 6ch s32le (4 bytes per sample)
Video: no video
Starting playback...
[reorder_ch] Unsupported sample size: 3, please report this error on the MPlayer mailing list.
[reorder_ch] Unsupported sample size: 3, please report this error on the MPlayer mailing list. *Etc...*
```I'm pointing that here, and only here, MPlayer considers sample size : *AUDIO: 48000 Hz, 6 ch, **s24le***. But then it does the same error...
[Here]("http://rapidshare.com/files/391457211/Test.dts.html") is a sample of my 24bits/48 kHz DTS file, corrupted, but usable in MPlayer!

PS : No doubt, MediaInfo confirms, it's a 24bits/48kHz sound ;)

---

### Post by DbianUsr on 2010-05-30
Well, I'm used to upgrade progs with PPA, but I don't always think to SVN...
My problem is solved : Just use the MPlayer's [PPA]("https://launchpad.net/%7Ervm/+archive/mplayer").
For my part, I noticed :
-An excellent H264/VC-1 decoding (even if I use graphic effects and no GPU decoding)
-When I was trying to solve the problem, I've convert my DTS in FLAC (great) but MPlayer was unable to assign the right channels >> SVN version does it well, FLACs surround works perfectly!
-And last : PCM 24bits/48kHz is finally played well :)

Just another thing : DTS-HD source : 4.7 Go >> FLAC : 4.1 Go
OpenSource rocks :P

DbianUsr

---

