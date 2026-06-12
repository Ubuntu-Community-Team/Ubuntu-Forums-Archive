---
title: "Ripping audioCD to wav with music brainz db - how?"
date: 2016-11-04
forum: Multimedia Software
---

### Post by spectatorx on 2016-11-04
Since few hours i'm looking for a program which will let me to rip music to wav format and use music brainz db to gather info about tracks on disc and what is very disappointing i'm unable to find one. If some program supports music brainz database then turns out it doesn't rip CDs at all or it doesn't rip to wav.

I know i could rip to flac but i do not want to, i want lossless wav.

I'm using ubuntu-mate 16.10 but i think this makes no difference.

---

### Post by mc4man on 2016-11-04
There is no real linux app that will rip to wav & tag. You could use windows or maybe thru wine - 
Use EAC(Exact Audio Copy)  to rip the entire CD to one large wav file and  then build a cue sheet with Vorbis style comments for the tagging information.
Or use [dBpoweramp]("https://www.dbpoweramp.com/")

---

### Post by shantiq on 2016-11-12
yes spectator what mc said   and this is what you have to do to [install EAC]("https://ubuntuforums.org/showthread.php?t=2092214&highlight=eac+shantiq") on Ubuntu and it works PERFECTly

Also   flac is lossless   you say lossless wav  but really wav is uncompressed flac ape alac are lossless and contain all the info which is in wav; and that is the meaning of the word lossless   nothing is lost
as opposed to lossy [mp3 m4a etc]



PS   but definitely dBpoweramp much better [you have it free for 21 days]

and you get this from a wav [which they call Wave in their encoders]

```
mediainfo *
General
Complete name                            : 03 Warpaint - New Song.wav
Format                                   : Wave
File size                                : 43.1 MiB
Duration                                 : 4mn 16s
Overall bit rate mode                    : Constant
Overall bit rate                         : 1 411 Kbps
Album                                    : Heads Up
Album/Performer                          : Warpaint
Part/Position                            : 1
Part/Total                               : 1
Track name                               : New Song
Track name/Position                      : 3
Track name/Total                         : 11
Performer                                : Warpaint
Director                                 : Warpaint
Encoded by                               : dBpoweramp Release 16.1
Genre                                    : Indie Rock
Recorded date                            : 2016
Writing application                      : dBpoweramp Release 16.1
Writing library                          : -compression="PCM" -bits="16"
Original source form                     : CD (Lossless)
Original source form/Name                : Heads Up
ITRK                                     : 3/11
Media Type                               : CD (Lossless)
Encoder                                  : Wave

Audio
Format                                   : PCM
Format settings, Endianness              : Little
Format settings, Sign                    : Signed
Codec ID                                 : 1
Duration                                 : 4mn 16s
Bit rate mode                            : Constant
Bit rate                                 : 1 411.2 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Bit depth                                : 16 bits
Stream size                              : 43.1 MiB (100%)


```
```

exiftool *
ExifTool Version Number         : 10.10
File Name                       : 03 Warpaint - New Song.wav
Directory                       : .
File Size                       : 43 MB
File Modification Date/Time     : 2016:11:12 10:05:56+00:00
File Access Date/Time           : 2016:11:12 10:07:11+00:00
File Inode Change Date/Time     : 2016:11:12 10:05:56+00:00
File Permissions                : rw-rw-r--
File Type                       : WAV
File Type Extension             : wav
MIME Type                       : audio/x-wav
Encoding                        : Microsoft PCM
Num Channels                    : 2
Sample Rate                     : 44100
Avg Bytes Per Sec               : 176400
Bits Per Sample                 : 16
Product                         : Heads Up
Artist                          : Warpaint
Software                        : dBpoweramp Release 16.1
Genre                           : Indie Rock
Source Form                     : CD (Lossless)
Title                           : New Song
Date Created                    : 2016
Duration                        : 0:04:16


```

---

