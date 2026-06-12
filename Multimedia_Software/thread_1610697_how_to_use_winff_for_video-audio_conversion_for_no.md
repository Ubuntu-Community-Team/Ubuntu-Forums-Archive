---
title: "how to use winff for video-audio conversion for nokia 5800?"
date: 2010-11-01
forum: Multimedia Software
---

### Post by som21 on 2010-11-01
hi,
i am using ubuntu lucid now and using ubuntu for 2years now.except nokia pc-suite i do not miss other s/w for windows.i tried to convert audio and video for using in nokia 5800,but i am not very successful mainly due to my inexperience.i installed winff and ffmpeg and searched a bit in this forum.found a few guides but mostly the converted files shows 'unable to play video or audio' in nokia 5800.
so if any of you could please post some working winff command,i'll be really grateful.
```
-r 29.97 -vcodec libxvid -vtag XVID -s 400x240 -aspect 16:9 -maxrate 1200k -b 1200k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv -trellis -aic -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 44100 -ab 160k -ac 2 -async1 
```this is the example of wiff preset command for nokian810(but not working for me).apparently there is no need for -i or output file(and here i get confused from the command lines posted in the forum.
for the people who want to help and wondering what format does this phone support,here is codec support list from forumnokia

```
&#65279;Phone Manufacturer: Nokia
Phone UID: 0x2000da56
Phone Model: (C) Nokia 5800 XpressMusic
Phone SW Version:
V 30.0.011
29-06-09
RM-356
************************************************
MDF DevVideoRecord encoders (7):
************************************************
Get info for encoder 0x101f86d5
Identifier: ARM MPEG-4 Video Encoder
Codec is NOT accelerated
Codec does NOT support direct capture
Supported input formats (5):
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
Supported output formats (16):
 *  video/mp4v-es 
 *  video/mp4v-es; profile-level-id=8 
 *  video/mp4v-es; profile-level-id=1 
 *  video/mp4v-es; profile-level-id=9 
 *  video/mp4v-es; profile-level-id=2 
 *  video/mp4v-es; profile-level-id=3 
 *  video/mp4v-es; profile-level-id=4 
 *  video/mp4v-es; profile-level-id=5 
 *  video/MP4V-ES 
 *  video/MP4V-ES; profile-level-id=8 
 *  video/MP4V-ES; profile-level-id=1 
 *  video/MP4V-ES; profile-level-id=9 
 *  video/MP4V-ES; profile-level-id=2 
 *  video/MP4V-ES; profile-level-id=3 
 *  video/MP4V-ES; profile-level-id=4 
 *  video/MP4V-ES; profile-level-id=5 
Rate&size: 15.000000, 128 x 96
Rate&size: 15.000000, 176 x 144
Rate&size: 30.000000, 352 x 288
Rate&size: 30.000000, 320 x 240
Rate&size: 30.000000, 640 x 480
Rate&size: 30.000000, 720 x 480
Rate&size: 25.000000, 720 x 576
Coding standard specific info: 
Implementation specific info: 
************************************************
Get info for encoder 0x10204bfe
Identifier: TI DM299
Codec is accelerated
Codec supports direct capture
Supported input formats (0):
Supported output formats (6):
 *  video/h263-2000 
 *  video/h263-2000; profile=0 
 *  video/h263-2000; profile=0; level=10 
 *  video/h263-2000; profile=0; level=20 
 *  video/h263-2000; profile=0; level=30 
 *  video/h263-2000; profile=0; level=45 
Rate&size: 30.000000, 352 x 288
Rate&size: 30.000000, 176 x 144
Rate&size: 30.000000, 128 x 96
Coding standard specific info: 
Implementation specific info: 
************************************************
Get info for encoder 0x10204bff
Identifier: TI DM299
Codec is accelerated
Codec supports direct capture
Supported input formats (0):
Supported output formats (7):
 *  video/mp4v-es 
 *  video/mp4v-es; profile-level-id=1 
 *  video/mp4v-es; profile-level-id=2 
 *  video/mp4v-es; profile-level-id=3 
 *  video/mp4v-es; profile-level-id=4 
 *  video/mp4v-es; profile-level-id=8 
 *  video/mp4v-es; profile-level-id=9 
Rate&size: 30.000000, 640 x 480
Rate&size: 30.000000, 352 x 288
Rate&size: 30.000000, 320 x 240
Rate&size: 30.000000, 176 x 144
Rate&size: 30.000000, 128 x 96
Coding standard specific info: 
Implementation specific info: 
************************************************
Get info for encoder 0x10282cfc
Identifier: ARM H.263 Video Encoder
Codec is NOT accelerated
Codec does NOT support direct capture
Supported input formats (1):
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
Supported output formats (6):
 *  video/H263-2000 
 *  video/H263-2000; profile=0 
 *  video/H263-2000; profile=0; level=10 
 *  video/H263-2000; profile=0; level=45 
 *  video/H263-2000; profile=0; level=20 
 *  video/H263-2000; profile=0; level=30 
Rate&size: 15.000000, 128 x 96
Rate&size: 15.000000, 176 x 144
Rate&size: 30.000000, 352 x 288
Coding standard specific info: 
Implementation specific info: 
************************************************
Get info for encoder 0x10282cfd
Identifier: ARM MPEG-4 Video Encoder
Codec is NOT accelerated
Codec does NOT support direct capture
Supported input formats (5):
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
Supported output formats (16):
 *  video/mp4v-es 
 *  video/mp4v-es; profile-level-id=8 
 *  video/mp4v-es; profile-level-id=1 
 *  video/mp4v-es; profile-level-id=9 
 *  video/mp4v-es; profile-level-id=2 
 *  video/mp4v-es; profile-level-id=3 
 *  video/mp4v-es; profile-level-id=4 
 *  video/mp4v-es; profile-level-id=5 
 *  video/MP4V-ES 
 *  video/MP4V-ES; profile-level-id=8 
 *  video/MP4V-ES; profile-level-id=1 
 *  video/MP4V-ES; profile-level-id=9 
 *  video/MP4V-ES; profile-level-id=2 
 *  video/MP4V-ES; profile-level-id=3 
 *  video/MP4V-ES; profile-level-id=4 
 *  video/MP4V-ES; profile-level-id=5 
Rate&size: 15.000000, 128 x 96
Rate&size: 15.000000, 176 x 144
Rate&size: 30.000000, 352 x 288
Rate&size: 30.000000, 320 x 240
Rate&size: 30.000000, 640 x 480
Rate&size: 30.000000, 720 x 480
Rate&size: 25.000000, 720 x 576
Coding standard specific info: 
Implementation specific info: 
************************************************
Get info for encoder 0x20001c13
Identifier: ARM H264 Video Encoder Hw Device
Codec is NOT accelerated
Codec does NOT support direct capture
Supported input formats (12):
 * Raw YUV, 4:2:0, left (as defined in ITU-R BT.601 and as used in MPEG-2, MPEG-4 Part 2), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, top-left (as defined in ITU-R BT.601 and as used in AVC), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, left (as defined in ITU-R BT.601 and as used in MPEG-2, MPEG-4 Part 2), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, top-left (as defined in ITU-R BT.601 and as used in AVC), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, left (as defined in ITU-R BT.601 and as used in MPEG-2, MPEG-4 Part 2), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, top-left (as defined in ITU-R BT.601 and as used in AVC), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, left (as defined in ITU-R BT.601 and as used in MPEG-2, MPEG-4 Part 2), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
 * Raw YUV, 4:2:0, top-left (as defined in ITU-R BT.601 and as used in AVC), plane mode [Y00Y01Y02Y03...U0...V0...]
Supported output formats (10):
 *  video/H264 
 *  video/H264; profile-level-id=42800A 
 *  video/H264; profile-level-id=42800B 
 *  video/H264; profile-level-id=42800C 
 *  video/H264; profile-level-id=42800D 
 *  video/H264; profile-level-id=428014 
 *  video/H264; profile-level-id=428015 
 *  video/H264; profile-level-id=428016 
 *  video/H264; profile-level-id=42801E 
 *  video/H264; profile-level-id=42900B 
Rate&size: 30.000000, 176 x 144
Rate&size: 30.000000, 640 x 480
Rate&size: 30.000000, 352 x 288
Rate&size: 30.000000, 128 x 96
Rate&size: 30.000000, 320 x 240
Rate&size: 30.000000, 720 x 240
Rate&size: 30.000000, 720 x 288
Rate&size: 30.000000, 720 x 480
Rate&size: 25.000000, 720 x 576
Coding standard specific info: 
Implementation specific info: 
************************************************
Get info for encoder 0x101f850a
Identifier: ARM H.263 Video Encoder
Codec is NOT accelerated
Codec does NOT support direct capture
Supported input formats (1):
 * Raw YUV, 4:2:0, middle (as defined in ITU-R BT.601 and as used in MPEG-1), plane mode [Y00Y01Y02Y03...U0...V0...]
Supported output formats (6):
 *  video/H263-2000 
 *  video/H263-2000; profile=0 
 *  video/H263-2000; profile=0; level=10 
 *  video/H263-2000; profile=0; level=45 
 *  video/H263-2000; profile=0; level=20 
 *  video/H263-2000; profile=0; level=30 
Rate&size: 15.000000, 128 x 96
Rate&size: 15.000000, 176 x 144
Rate&size: 30.000000, 352 x 288
Coding standard specific info: 
Implementation specific info: 
************************************************
MDF DevVideoRecord encoders retrieved successfully!




MDF DevVideoRecord pre-processors (0):
************************************************
MDF DevVideoRecord pre-processors retrieved successfully!





DevSound encoders (5):
************************************************
Codec: " P16"
Supported sampling rates: 8kHz 16kHz 48kHz 
Supported encodings: Signed 16 Bit PCM 
Supported number of channels: Mono 
************************************************
Codec: "G711"
Supported sampling rates: 8kHz 
Supported encodings: Signed 8 Bit PCM Signed 16 Bit PCM Signed 8 bit ALaw Signed 8 bit MuLaw 
Supported number of channels: Mono 
************************************************
Codec: "G729"
Supported sampling rates: 8kHz 
Supported encodings: Signed 8 Bit PCM Signed 16 Bit PCM Signed 8 bit ALaw Signed 8 bit MuLaw 
Supported number of channels: Mono 
************************************************
Codec: "ILBC"
Supported sampling rates: 8kHz 
Supported encodings: Signed 8 Bit PCM Signed 16 Bit PCM Signed 8 bit ALaw Signed 8 bit MuLaw 
Supported number of channels: Mono 
************************************************
Codec: " AMR"
Supported sampling rates: 8kHz 
Supported encodings: Signed 16 Bit PCM 
Supported number of channels: Mono 

DevSound decoders (9):
************************************************
Codec: " P16"
Supported sampling rates: 8kHz 11kHz 16kHz 22kHz 32kHz 44.1kHz 48kHz 12kHz 24kHz 
Supported encodings: Signed 16 Bit PCM 
Supported number of channels: Mono Stereo 
************************************************
Codec: " MP3"
Supported sampling rates: 8kHz 11kHz 16kHz 22kHz 32kHz 44.1kHz 48kHz 12kHz 24kHz 
Supported encodings: 
Supported number of channels: Mono Stereo 
************************************************
Codec: " AWB"
Supported sampling rates: 16kHz 
Supported encodings: 
Supported number of channels: Mono 
************************************************
Codec: "G711"
Supported sampling rates: 8kHz 
Supported encodings: Signed 16 Bit PCM 
Supported number of channels: Mono 
************************************************
Codec: "G729"
Supported sampling rates: 8kHz 
Supported encodings: Signed 16 Bit PCM 
Supported number of channels: Mono 
************************************************
Codec: "ILBC"
Supported sampling rates: 8kHz 
Supported encodings: Signed 16 Bit PCM 
Supported number of channels: Mono 
************************************************
Codec: " AMR"
Supported sampling rates: 8kHz 
Supported encodings: Signed 16 Bit PCM 
Supported number of channels: Mono 
************************************************
Codec: "NFMR"
Supported sampling rates: 8kHz 11kHz 16kHz 22kHz 32kHz 44.1kHz 48kHz 88.2kHz 96kHz 
Supported encodings: Signed 8 Bit PCM Signed 16 Bit PCM Signed 8 bit ALaw Signed 8 bit MuLaw 
Supported number of channels: Mono Stereo 
************************************************
Codec: "UPNP"
Supported sampling rates: 8kHz 11kHz 16kHz 22kHz 32kHz 44.1kHz 48kHz 88.2kHz 96kHz 
Supported encodings: Signed 8 Bit PCM Signed 16 Bit PCM Signed 8 bit ALaw Signed 8 bit MuLaw 
Supported number of channels: Mono Stereo 
************************************************
DevSound codecs retrieved successfully!




MMF Controllers (19):
************************************************
Get info about MMF Controller 0x101f7d96
Controller Name: Symbian Audio Tone controller
Found 4 supported Play Formats.
Supported file extensions (1): .sqn
Supported MIME types (0): 
Supported file extensions (2): .nrt, .rng
Supported MIME types (0): 
Supported file extensions (1): ?
Supported MIME types (0): 
Supported file extensions (2): .nrt, .rng
Supported MIME types (0): 
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x101f8503
Controller Name: Camcorder controller
Found 0 supported Play Formats.
Found 3 supported Record Formats.
Supported file extensions (1): .3g2
Supported MIME types (1): video/3gpp2
Supported file extensions (1): .mp4
Supported MIME types (1): video/mp4
Supported file extensions (1): .3gp
Supported MIME types (1): video/3gpp
************************************************
Get info about MMF Controller 0x101f8514
Controller Name: Real Video Player
Found 10 supported Play Formats.
Supported file extensions (1): .sdp
Supported MIME types (1): application/sdp
Supported file extensions (1): .mp4
Supported MIME types (2): video/mp4, video/mpeg4
Supported file extensions (2): .3gp, .mrc
Supported MIME types (1): video/3gpp
Supported file extensions (4): .ra, .rm, .rmvb, .rv
Supported MIME types (7): application/x-pn-realmedia, video/vnd.rn-realvideo, application/vnd.rn-realmedia, audio/x-pn-realaudio, video/x-pn-realvideo, audio/vnd.rn-realaudio, audio/x-realaudio
Supported file extensions (1): .awb
Supported MIME types (1): audio/amr-wb
Supported file extensions (1): .amr
Supported MIME types (1): audio/amr
Supported file extensions (1): .3g2
Supported MIME types (1): video/3gpp2
Supported file extensions (1): .xps
Supported MIME types (1): application/x-ext-packetsrc
Supported file extensions (1): .avi
Supported MIME types (4): application/x-pn-avi-plugin, video/avi, video/x-msvideo, video/msvideo
Supported file extensions (1): .mp3
Supported MIME types (1): audio/mp3
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x101f8b24
Found 6 supported Play Formats.
Supported file extensions (1): .rmf
Supported MIME types (1): audio/rmf
Supported file extensions (1): .mid
Supported MIME types (1): audio/sp-midi
Supported file extensions (1): .mxmf
Supported MIME types (1): audio/mobile-xmf
Supported file extensions (1): .rmf
Supported MIME types (1): audio/x-beatnik-rmf
Supported file extensions (1): .rmf
Supported MIME types (1): audio/x-rmf
Supported file extensions (1): .mid
Supported MIME types (1): audio/midi
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x101fafb1
Controller Name: 3GP Audio Controller Plugin
Found 7 supported Play Formats.
Supported file extensions (2): .m4a, .mp4
Supported MIME types (1): audio/mp4
Supported file extensions (1): .3g2
Supported MIME types (1): audio/3gpp2
Supported file extensions (2): .3ga, .3gp
Supported MIME types (1): audio/3gpp
Supported file extensions (2): .3ga, .3gp
Supported MIME types (1): audio/3gpp
Supported file extensions (2): .3ga, .3gp
Supported MIME types (1): audio/3gpp
Supported file extensions (2): .3ga, .3gp
Supported MIME types (1): audio/3gpp
Supported file extensions (2): .3ga, .3gp
Supported MIME types (1): audio/3gpp
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x101fafb4
Controller Name: AAC Audio Controller Plugin
Found 2 supported Play Formats.
Supported file extensions (1): .aac
Supported MIME types (1): audio/aac
Supported file extensions (1): .aac
Supported MIME types (1): audio/aac
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x101fafb7
Controller Name: MP3 Audio Controller Plugin
Found 2 supported Play Formats.
Supported file extensions (1): .mp3
Supported MIME types (1): audio/mpeg
Supported file extensions (1): .mp3
Supported MIME types (2): audio/mpeg, audio/mp3
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x101fafba
Controller Name: AMR Audio Play Controller Plugin
Found 1 supported Play Formats.
Supported file extensions (1): .amr
Supported MIME types (1): audio/amr
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x101fafbd
Controller Name: AWB Audio Play Controller Plugin
Found 1 supported Play Formats.
Supported file extensions (1): .awb
Supported MIME types (1): audio/amr-wb
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x101fafc0
Controller Name: AMR Audio Record Controller Plugin
Found 0 supported Play Formats.
Found 1 supported Record Formats.
Supported file extensions (1): .amr
Supported MIME types (1): audio/amr
************************************************
Get info about MMF Controller 0x101ff931
Controller Name: SI Controller Plugin
Found 0 supported Play Formats.
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x101ff934
Controller Name: TTS Controller Plugin
Found 1 supported Play Formats.
Supported file extensions (1): .txt
Supported MIME types (1): text/plain
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x10202702
Found 6 supported Play Formats.
Supported file extensions (1): .rmf
Supported MIME types (1): audio/rmf
Supported file extensions (1): .mid
Supported MIME types (1): audio/sp-midi
Supported file extensions (1): .mxmf
Supported MIME types (1): audio/mobile-xmf
Supported file extensions (1): .rmf
Supported MIME types (1): audio/x-beatnik-rmf
Supported file extensions (1): .rmf
Supported MIME types (1): audio/x-rmf
Supported file extensions (1): .mid
Supported MIME types (1): audio/midi
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x1020383b
Controller Name: 3GP Audio Record Controller Plugin
Found 0 supported Play Formats.
Found 1 supported Record Formats.
Supported file extensions (1): .mp4
Supported MIME types (1): audio/mp4
************************************************
Get info about MMF Controller 0x10207406
Controller Name: MCC Controller
Found 0 supported Play Formats.
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x10207b65
Controller Name: Helix Audio Controller
Found 1 supported Play Formats.
Supported file extensions (2): .ra, .rm
Supported MIME types (1): audio/x-pn-realaudio
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x1028334a
Controller Name: Helix_WMV
Found 1 supported Play Formats.
Supported file extensions (1): .wmv
Supported MIME types (1): video/x-ms-wmv
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x10283351
Controller Name: Helix_WMA
Found 1 supported Play Formats.
Supported file extensions (1): .wma
Supported MIME types (1): audio/x-ms-wma
Found 0 supported Record Formats.
************************************************
Get info about MMF Controller 0x101f5022
Controller Name: Symbian Audio controller
Found 3 supported Play Formats.
Supported file extensions (1): .au
Supported MIME types (4): audio/basic, audio/x-au, audio/au, audio/x-basic
Supported file extensions (1): .raw
Supported MIME types (0): 
Supported file extensions (1): .wav
Supported MIME types (2): audio/wav, audio/x-wav
Found 3 supported Record Formats.
Supported file extensions (1): .au
Supported MIME types (4): audio/basic, audio/x-au, audio/au, audio/x-basic
Supported file extensions (1): .raw
Supported MIME types (0): 
Supported file extensions (1): .wav
Supported MIME types (2): audio/wav, audio/x-wav
************************************************
MMF Controllers retrieved successfully!




MMF Codecs:
************************************************
Looking for MMF AAC Decoder (0x101faf81):
Found.
Looking for MMF AAC Encoder (0x1020382f):
Found.
Looking for MMF AMR-NB Decoder (0x101faf67):
Found.
Looking for MMF AMR-NB Encoder (0x101faf68):
Found.
Looking for MMF AMR-WB Decoder (0x101faf5e):
Found.
Looking for MMF eAAC+ Decoder (0x10207aa9):
Found.
Looking for MMF MP3 Decoder (0x101faf85):
Found.
************************************************
MMF Codecs retrieved successfully!
************************************************

This document is a part of Forum Nokia device specification at www.forum.nokia.com/devices.

Specifications are subject to change without notice. 

Copyright © 2009 Nokia Corporation. All rights reserved.
Nokia and Forum Nokia are trademarks or registered trademarks of Nokia Corporation. Java and all Java-based marks are trademarks or registered trademarks of Sun Microsystems, Inc. Other product and company names mentioned herein may be trademarks or trade names of their respective owners.

Disclaimer:
The information in this document is provided “as is,” with no warranties whatsoever, including any warranty of merchantability, fitness for any particular purpose, or any warranty otherwise arising out of any proposal, specification, or sample. This document is provided for informational purposes only.
Nokia Corporation disclaims all liability, including liability for infringement of any proprietary rights, relating to implementation of information presented in this document. Nokia Corporation does not warrant or represent that such use will not infringe such rights.
Nokia Corporation retains the right to make changes to this document at any time, without notice.

Licence:
A licence is hereby granted to download and print a copy of this document for personal use only. No other licence to any other intellectual property rights is granted herein. 

```
so if any of you kindly help me in this regard,i'll be highly obliged.thanks in advance

---

### Post by som21 on 2010-11-02
please does anybody have any suggestion?

---

### Post by som21 on 2010-11-02
bump

---

### Post by mutex023 on 2010-11-03
I had the same problem for nokia Xpressmusic 5320, and had solved it by converting the video into mp4 format using PiTivi, the exact procedure I have forgotten, will let you know soon

---

### Post by som21 on 2010-11-03
thanks

---

### Post by mutex023 on 2010-11-03
First install the following from synaptic pkg manager-
1.libfaac (could be libfaac0 or libfaac1) - this is the AAC audio encoder
2.libmpeg2-4
3.All gstreamer-plugins (no need to install the ones ending with 'dbg').
4.ffmpeg
5.pitivi

Now Run Pitivi from Applications->Sound and Video
In Pitivi, go to Project->Project Settings.
Under video output, set the correct width and height for your phone. In my case it was: 176x144
This is the maximum video resolution your phone can support. Find out by googling.
Set Frame Rate 30fps.
Set Audio Output to CD
Under Export to select, Container=MP4 Muxer, Audio Encoder=AAC Audio Encoder, Video Codec=FFmpeg mpeg4 part 2
Click OK

Now add the video file by drag drop to the Clip Library. Then again drag it from clip library to the video 
timeline below, make sure to align it to the leftmost corner.
Just click on play button to make sure its playing fine.
Now just click on the 'Render Project' button in the toolbar above (filmstrip icon).
Click choose file, give some <filename.mp4> as filename and hit render.
The mp4 created should now play once you copy to your phone.
Enjoy!

---

### Post by som21 on 2010-11-03
gr8;i'll try and let you know

---

### Post by som21 on 2010-11-04
i worked upto the adding of video file;but the 'render project' button is not active.any suggestion?

---

### Post by Davsdu on 2010-11-04
Hi there sorry to interrupt without being able to help with Winff -- I personally gave up on Winff for my Nokia 5800 device. But if you just need a video encoder that'll work with your Nokia 5800 then you might be interested in Mobile Media Converter ( [http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm) ). You'll also need to install mencoder from medibuntu. I followed the instructions at [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository) and after that I am now able to watch movies which have been converted from avi into mp4 files (I use the iphone/ipod profile but others might work as well). The conversion doesn't take too long time (around 15 minutes for a 24 minutes video clip) and quality is alright.

---

### Post by mutex023 on 2010-11-05
> **som21 said:**
> i worked upto the adding of video file;but the 'render project' button is not active.any suggestion?

Did you add the video clip to the video timeline below - the two horizontal strips at the bottom ? Read the steps carefully.

---

### Post by ziri on 2011-02-02
Hi, I succeeded to create a winff preset that works with Nokia 5800. Just unzip the file and from the Winff menu, select Edit->Preset->Import. 
Enjoy :p

---

