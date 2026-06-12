---
title: "mythtrascode avformatdecoder.cpp decoding error (v0.27)"
date: 2013-10-18
forum: Mythbuntu
---

### Post by haneo on 2013-10-18
Hi,

I am trying to remore commercials from a recoded video. I can see the video with mythfrontend and I can see the commercials breaks markers (Z shortcut).

But mythtranscode fail after . I get this error:


*me@mythtv ~ $ tail  /var/log/mythtv/mythtranscode.20131018214035.8350.log*
*2013-10-18 19:20:44.247458 I [8350/8350] CoreContext transcode.cpp:1503 (TranscodeFile) - mythtranscode: 98% Completed @ 17.6292 fps.*
*2013-10-18 19:21:04.308469 I [8350/8350] CoreContext transcode.cpp:1503 (TranscodeFile) - mythtranscode: 98% Completed @ 17.6372 fps.*
*2013-10-18 19:21:24.356589 I [8350/8350] CoreContext transcode.cpp:1503 (TranscodeFile) - mythtranscode: 98% Completed @ 17.635 fps.*
*2013-10-18 19:21:44.389176 I [8350/8350] CoreContext transcode.cpp:1503 (TranscodeFile) - mythtranscode: 99% Completed @ 17.6346 fps.*
*2013-10-18 19:22:04.403492 I [8350/8350] CoreContext transcode.cpp:1503 (TranscodeFile) - mythtranscode: 99% Completed @ 17.6373 fps.*
*2013-10-18 19:22:24.424987 I [8350/8350] CoreContext transcode.cpp:1503 (TranscodeFile) - mythtranscode: 99% Completed @ 17.6374 fps.*
*2013-10-18 19:22:28.479542 E [8350/8361] VideoDecodeBuffer avformatdecoder.cpp:4676 (GetFrame) - decoding error*
*            eno: Unknown error 541478725 (541478725)*
*2013-10-18 19:22:28.572207 N [8350/8350] CoreContext main.cpp:686 (main) - Transcoding /var/lib/mythtv/2102_20131018170000.mpg done*
*2013-10-18 19:22:28.572235 I [8350/8350] CoreContext mythcontext.cpp:1194 (~MythContext) - Waiting for threads to exit.*
*me@mythtv ~ $ *





Here is the file info:

*me@mythtv ~ $ mediainfo /var/lib/mythtv/2102_20131018170000.mpg*
*General*
*ID                                       : 0 (0x0)*
*Complete name                            : /var/lib/mythtv/2102_20131018170000.mpg*
*Format                                   : MPEG-TS*
*File size                                : 4.84 GiB*
*Duration                                 : 59mn 57s*
*Overall bit rate mode                    : Variable*
*Overall bit rate                         : 11.6 Mbps*

*Video*
*ID                                       : 4113 (0x1011)*
*Menu ID                                  : 1 (0x1)*
*Format                                   : AVC*
*Format/Info                              : Advanced Video Codec*
*Format profile                           : Main@L4.0*
*Format settings, CABAC                   : Yes*
*Format settings, ReFrames                : 4 frames*
*Format settings, GOP                     : M=4, N=32*
*Codec ID                                 : 27*
*Duration                                 : 59mn 56s*
*Bit rate mode                            : Variable*
*Bit rate                                 : 10.6 Mbps*
*Maximum bit rate                         : 20.0 Mbps*
*Width                                    : 1 920 pixels*
*Height                                   : 1 080 pixels*
*Display aspect ratio                     : 16:9*
*Frame rate                               : 29.970 fps*
*Color space                              : YUV*
*Chroma subsampling                       : 4:2:0*
*Bit depth                                : 8 bits*
*Scan type                                : Interlaced*
*Scan order                               : Top Field First*
*Bits/(Pixel*Frame)                       : 0.171*
*Stream size                              : 4.44 GiB (92%)*
*Color primaries                          : BT.709*
*Transfer characteristics                 : BT.709*
*Matrix coefficients                      : BT.709*

*Audio*
*ID                                       : 4352 (0x1100)*
*Menu ID                                  : 1 (0x1)*
*Format                                   : AC-3*
*Format/Info                              : Audio Coding 3*
*Mode extension                           : CM (complete main)*
*Format settings, Endianness              : Big*
*Codec ID                                 : 129*
*Duration                                 : 59mn 57s*
*Bit rate mode                            : Constant*
*Bit rate                                 : 384 Kbps*
*Channel(s)                               : 2 channels*
*Channel positions                        : Front: L R*
*Sampling rate                            : 48.0 KHz*
*Bit depth                                : 16 bits*
*Compression mode                         : Lossy*
*Delay relative to video                  : -39ms*
*Stream size                              : 165 MiB (3%)*


I searched for such error on google without success. Is it a bug ? should I send this to the dev team.

Thanks for all.

---

