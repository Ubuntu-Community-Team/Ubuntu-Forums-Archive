---
title: "DVBT Radio channels have no sound on vlc"
date: 2015-11-04
forum: Multimedia Software
---

### Post by ahooyee on 2015-11-04
Hello everyone...
 i play dvbt tv channels without any problem on vlc

but the radio channels have no sound...
....
i did record a radio program on vlc   and the kaffeine played the recorded file  with sound   without any problem...

please help me..
thanks

---

### Post by ahooyee on 2015-11-10
i did run the vlc from terminal and got this errors...```
[h264 @ 0x7f04000f3f80] mmco: unref short failure
[h264 @ 0x7f04000f3f80] mmco: unref short failure
[h264 @ 0x7f04000f3f80] mmco: unref short failure
[00007f0404158938] ts demux: MPEG-4 descriptor not found for pid 0x3f3 type 0x11
[00007f0404158938] ts demux: MPEG-4 descriptor not found for pid 0x623 type 0x11
[00007f0404168738] packetizer_mpeg4audio packetizer: AAC channels: 1 samplerate: 24000
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 8, expected 11) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 12) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 7) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 6) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 7) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 3, expected 5) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 14) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 0, expected 5) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 6) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 9) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS duplicate (received 4, expected 5) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0x50 !!!
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 0, expected 11) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 2, expected 8) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 3, expected 12) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 6, expected 4) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 8, expected 4) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 0, expected 9) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 4) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 4) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 8, expected 0) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 3, expected 14) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 2, expected 7) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 3, expected 15) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 15) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 2, expected 5) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 11) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 8, expected 11) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 6, expected 5) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 11, expected 9) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 5) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 9) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 14) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 9) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 7) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS duplicate (received 12, expected 13) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0x50 !!!
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0xeb !!!
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0xd9 !!!
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0xd8 !!!
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0xd9 !!!
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0x20 !!!
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0x73 !!!
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0xa7 !!!
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0xb1 !!!
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0xb1 !!!
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0xdf !!!
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0xd9 !!!
[00007f0404158938] ts demux error: libdvbpsi error (EIT decoder): invalid section (section_syntax_indicator == 0)
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0xda !!!
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 2, expected 8) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS duplicate (received 6, expected 7) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0x50 !!!
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 10, expected 1) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 0) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 14) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 6, expected 15) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 8, expected 6) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 9) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 1) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0x50 !!!
[00007f0404158938] ts demux error: libdvbpsi error (misc PSI): Bad CRC_32 table 0x73 !!!
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 13) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 2, expected 10) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 0, expected 3) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 0, expected 9) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 4, expected 14) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 2) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS duplicate (received 2, expected 3) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 6) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 11, expected 10) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 8) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 4) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 10) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 1) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 0, expected 11) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 3, expected 8) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 2) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 2, expected 6) for PID 18
[00007f0404158938] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 0) for PID 18


```
does anyone know what the problem is?

---

### Post by ahooyee on 2015-12-03
today,i upgrade the linux kernel to 4.2.0.19  and  vlc plays  radio stations without any problem

---

