---
title: "jack installation problem....i think..."
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by vj air on 2007-06-04
sorry about the length of the post, thought id give you what its giving me....

trying to install jack as paret of a veejay install. when i type :

**vj@vj-desktop:~/Desktop/veejay-1.0$ make**

i get this :

make  all-recursive
make[1]: Entering directory `/home/vj/Desktop/veejay-1.0'
Making all in aclib
make[2]: Entering directory `/home/vj/Desktop/veejay-1.0/aclib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/vj/Desktop/veejay-1.0/aclib'
Making all in bio2jack
make[2]: Entering directory `/home/vj/Desktop/veejay-1.0/bio2jack'
if /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../libvjmem    -march=pentium4 -mtune=pentium4  -msse -mfpmath=sse  -MT bio2jack.lo -MD -MP -MF ".deps/bio2jack.Tpo" -c -o bio2jack.lo bio2jack.c; \
        then mv -f ".deps/bio2jack.Tpo" ".deps/bio2jack.Plo"; else rm -f ".deps/bio2jack.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../libvjmem -march=pentium4 -mtune=pentium4 -msse -mfpmath=sse -MT bio2jack.lo -MD -MP -MF .deps/bio2jack.Tpo -c bio2jack.c  -fPIC -DPIC -o .libs/bio2jack.o
bio2jack.c:30:23: error: jack/jack.h: No such file or directory
bio2jack.c:31:29: error: jack/ringbuffer.h: No such file or directory
bio2jack.c:159: error: expected specifier-qualifier-list before 'jack_port_t'
bio2jack.c:218: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sample_t'
bio2jack.c:219: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'nframes_t'
bio2jack.c: In function 'getDriver':
bio2jack.c:287: error: 'jack_driver_t' has no member named 'mutex'
bio2jack.c:291: error: 'jack_driver_t' has no member named 'jackd_died'
bio2jack.c:291: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:297: error: 'jack_driver_t' has no member named 'last_reconnect_attempt'
bio2jack.c:300: error: 'jack_driver_t' has no member named 'last_reconnect_attempt'
bio2jack.c: In function 'tryGetDriver':
bio2jack.c:321: error: 'jack_driver_t' has no member named 'mutex'
bio2jack.c: In function 'releaseDriver':
bio2jack.c:354: error: 'jack_driver_t' has no member named 'mutex'
bio2jack.c: At top level:
bio2jack.c:384: error: expected ')' before '*' token
bio2jack.c:401: error: expected ')' before '*' token
bio2jack.c:415: error: expected ')' before '*' token
bio2jack.c:429: error: expected ')' before '*' token
bio2jack.c:439: error: expected declaration specifiers or '...' before 'sample_t'
bio2jack.c: In function 'sample_move_float_short':
bio2jack.c:444: error: 'src' undeclared (first use in this function)
bio2jack.c:444: error: (Each undeclared identifier is reported only once
bio2jack.c:444: error: for each function it appears in.)
bio2jack.c: At top level:
bio2jack.c:449: error: expected ')' before '*' token
bio2jack.c:459: error: expected declaration specifiers or '...' before 'sample_t'
bio2jack.c: In function 'sample_move_float_char':
bio2jack.c:464: error: 'src' undeclared (first use in this function)
bio2jack.c: At top level:
bio2jack.c:469: error: expected ')' before '*' token
bio2jack.c:506: error: expected ')' before 'nframes'
bio2jack.c:892: error: expected ')' before 'nframes'
bio2jack.c:906: error: expected ')' before 'nframes'
bio2jack.c: In function 'JACK_shutdown':
bio2jack.c:939: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:940: error: 'jack_driver_t' has no member named 'jackd_died'
bio2jack.c: In function 'JACK_OpenDevice':
bio2jack.c:990: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:993: error: 'jack_driver_t' has no member named 'in_use'
bio2jack.c:997: error: 'jack_driver_t' has no member named 'in_use'
bio2jack.c:1015: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1019: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1029: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1035: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1035: error: 'JACK_callback' undeclared (first use in this function)
bio2jack.c:1038: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1038: error: 'JACK_bufsize' undeclared (first use in this function)
bio2jack.c:1042: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1042: error: 'JACK_srate' undeclared (first use in this function)
bio2jack.c:1047: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1052: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1059: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1070: error: 'jack_driver_t' has no member named 'output_port'
bio2jack.c:1070: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1071: error: 'JACK_DEFAULT_AUDIO_TYPE' undeclared (first use in this function)
bio2jack.c:1072: error: 'JackPortIsOutput' undeclared (first use in this function)
bio2jack.c:1084: error: 'jack_driver_t' has no member named 'input_port'
bio2jack.c:1084: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1086: error: 'JackPortIsInput' undeclared (first use in this function)
bio2jack.c:1090: error: 'jack_driver_t' has no member named 'in_use'
bio2jack.c:1095: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1106: error: 'jack_driver_t' has no member named 'jack_port_name_count'
bio2jack.c:1106: error: 'jack_driver_t' has no member named 'jack_port_name_count'
bio2jack.c:1108: error: 'jack_driver_t' has no member named 'jack_port_name_count'
bio2jack.c:1111: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1112: error: 'jack_driver_t' has no member named 'jack_output_port_flags'
bio2jack.c:1112: warning: assignment makes pointer from integer without a cast
bio2jack.c:1118: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1118: error: 'jack_driver_t' has no member named 'jack_port_name'
bio2jack.c:1119: error: 'jack_driver_t' has no member named 'jack_output_port_flags'
bio2jack.c:1119: warning: assignment makes pointer from integer without a cast
bio2jack.c:1151: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1151: error: 'jack_driver_t' has no member named 'output_port'
bio2jack.c:1171: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1171: error: 'jack_driver_t' has no member named 'output_port'
bio2jack.c:1184: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1184: error: 'jack_driver_t' has no member named 'output_port'
bio2jack.c:1197: error: 'jack_driver_t' has no member named 'jack_port_name_count'
bio2jack.c:1201: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1201: error: 'jack_driver_t' has no member named 'jack_port_name'
bio2jack.c:1202: error: 'jack_driver_t' has no member named 'jack_output_port_flags'
bio2jack.c:1202: warning: assignment makes pointer from integer without a cast
bio2jack.c:1206: error: 'jack_driver_t' has no member named 'jack_output_port_flags'
bio2jack.c:1215: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1215: error: 'jack_driver_t' has no member named 'output_port'
bio2jack.c:1229: error: 'jack_driver_t' has no member named 'jack_port_name_count'
bio2jack.c:1229: error: 'jack_driver_t' has no member named 'jack_port_name_count'
bio2jack.c:1231: error: 'jack_driver_t' has no member named 'jack_port_name_count'
bio2jack.c:1234: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1234: error: 'jack_driver_t' has no member named 'jack_input_port_flags'
bio2jack.c:1234: warning: assignment makes pointer from integer without a cast
bio2jack.c:1240: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1240: error: 'jack_driver_t' has no member named 'jack_port_name'
bio2jack.c:1241: error: 'jack_driver_t' has no member named 'jack_input_port_flags'
bio2jack.c:1241: warning: assignment makes pointer from integer without a cast
bio2jack.c:1273: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1273: error: 'jack_driver_t' has no member named 'input_port'
bio2jack.c:1289: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1289: error: 'jack_driver_t' has no member named 'input_port'
bio2jack.c:1302: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1302: error: 'jack_driver_t' has no member named 'input_port'
bio2jack.c:1314: error: 'jack_driver_t' has no member named 'jack_port_name_count'
bio2jack.c:1318: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1318: error: 'jack_driver_t' has no member named 'jack_port_name'
bio2jack.c:1319: error: 'jack_driver_t' has no member named 'jack_input_port_flags'
bio2jack.c:1319: warning: assignment makes pointer from integer without a cast
bio2jack.c:1323: error: 'jack_driver_t' has no member named 'jack_input_port_flags'
bio2jack.c:1332: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1332: error: 'jack_driver_t' has no member named 'input_port'
bio2jack.c:1356: error: 'jack_driver_t' has no member named 'jackd_died'
bio2jack.c:1357: error: 'jack_driver_t' has no member named 'state'
bio2jack.c: In function 'JACK_CloseDevice':
bio2jack.c:1386: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1389: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1396: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1400: error: 'jack_driver_t' has no member named 'jack_port_name_count'
bio2jack.c:1402: error: 'jack_driver_t' has no member named 'jack_port_name_count'
bio2jack.c:1403: error: 'jack_driver_t' has no member named 'jack_port_name'
bio2jack.c:1404: error: 'jack_driver_t' has no member named 'jack_port_name'
bio2jack.c:1414: error: 'jack_driver_t' has no member named 'in_use'
bio2jack.c:1416: error: 'jack_driver_t' has no member named 'client'
bio2jack.c: In function 'JACK_ResetFromDriver':
bio2jack.c:1440: error: 'jack_driver_t' has no member named 'state'
bio2jack.c: In function 'JACK_Open':
bio2jack.c:1473: error: 'JackPortIsPhysical' undeclared (first use in this function)
bio2jack.c: In function 'JACK_OpenEx':
bio2jack.c:1555: error: 'jack_driver_t' has no member named 'jack_output_port_flags'
bio2jack.c:1555: error: 'JackPortIsInput' undeclared (first use in this function)
bio2jack.c:1556: error: 'jack_driver_t' has no member named 'jack_input_port_flags'
bio2jack.c:1556: error: 'JackPortIsOutput' undeclared (first use in this function)
bio2jack.c:1573: error: 'jack_driver_t' has no member named 'jack_port_name_count'
bio2jack.c:1575: error: 'jack_driver_t' has no member named 'jack_port_name_count'
bio2jack.c:1577: error: 'jack_driver_t' has no member named 'jack_port_name'
bio2jack.c:1578: error: 'jack_driver_t' has no member named 'jack_port_name_count'
bio2jack.c:1579: error: 'jack_driver_t' has no member named 'jack_port_name_count'
bio2jack.c:1581: error: 'jack_driver_t' has no member named 'jack_port_name'
bio2jack.c:1586: error: 'jack_driver_t' has no member named 'jack_port_name'
bio2jack.c:1592: error: 'jack_driver_t' has no member named 'in_use'
bio2jack.c:1604: error: 'sample_t' undeclared (first use in this function)
bio2jack.c:1609: error: 'jack_driver_t' has no member named 'pPlayPtr'
bio2jack.c:1616: error: 'jack_driver_t' has no member named 'pRecPtr'
bio2jack.c:1690: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1695: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1696: error: 'jack_driver_t' has no member named 'output_port'
bio2jack.c:1703: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:1704: error: 'jack_driver_t' has no member named 'input_port'
bio2jack.c: In function 'JACK_Close':
bio2jack.c:1752: error: 'jack_driver_t' has no member named 'pPlayPtr'
bio2jack.c:1752: error: 'jack_driver_t' has no member named 'pPlayPtr'
bio2jack.c:1753: error: 'jack_driver_t' has no member named 'pPlayPtr'
bio2jack.c:1755: error: 'jack_driver_t' has no member named 'pRecPtr'
bio2jack.c:1755: error: 'jack_driver_t' has no member named 'pRecPtr'
bio2jack.c:1756: error: 'jack_driver_t' has no member named 'pRecPtr'
bio2jack.c: In function 'JACK_Write':
bio2jack.c:1794: error: 'jack_driver_t' has no member named 'pPlayPtr'
bio2jack.c:1803: error: 'jack_driver_t' has no member named 'state'
bio2jack.c:1806: error: 'jack_driver_t' has no member named 'state'
bio2jack.c:1834: error: 'sample_t' undeclared (first use in this function)
bio2jack.c:1834: error: expected expression before ')' token
bio2jack.c:1838: error: expected expression before ')' token
bio2jack.c:1847: error: 'jack_driver_t' has no member named 'pPlayPtr'
bio2jack.c: In function 'JACK_Read':
bio2jack.c:1877: error: 'jack_driver_t' has no member named 'pRecPtr'
bio2jack.c:1884: error: 'jack_driver_t' has no member named 'state'
bio2jack.c:1887: error: 'jack_driver_t' has no member named 'state'
bio2jack.c:1913: error: 'jack_driver_t' has no member named 'pRecPtr'
bio2jack.c:1924: error: 'jack_driver_t' has no member named 'volumeEffectType'
bio2jack.c:1928: error: 'jack_driver_t' has no member named 'volume'
bio2jack.c:1929: error: 'sample_t' undeclared (first use in this function)
bio2jack.c:1929: error: expected expression before ')' token
bio2jack.c:1933: error: expected expression before ')' token
bio2jack.c:1944: error: expected expression before ')' token
bio2jack.c:1948: error: expected expression before ')' token
bio2jack.c: In function 'JACK_SetVolumeForChannelFromDriver':
bio2jack.c:1976: error: 'jack_driver_t' has no member named 'volume'
bio2jack.c: In function 'JACK_GetVolumeForChannel':
bio2jack.c:2032: error: 'jack_driver_t' has no member named 'volume'
bio2jack.c: In function 'JACK_SetVolumeEffectType':
bio2jack.c:2062: error: 'jack_driver_t' has no member named 'volumeEffectType'
bio2jack.c:2063: error: 'jack_driver_t' has no member named 'volumeEffectType'
bio2jack.c: In function 'JACK_SetState':
bio2jack.c:2079: error: 'jack_driver_t' has no member named 'state'
bio2jack.c:2082: error: 'jack_driver_t' has no member named 'state'
bio2jack.c:2085: error: 'jack_driver_t' has no member named 'state'
bio2jack.c: In function 'JACK_GetState':
bio2jack.c:2104: error: 'jack_driver_t' has no member named 'state'
bio2jack.c: In function 'JACK_GetBytesStoredFromDriver':
bio2jack.c:2176: error: 'jack_driver_t' has no member named 'pPlayPtr'
bio2jack.c:2181: error: 'jack_driver_t' has no member named 'pPlayPtr'
bio2jack.c: In function 'JACK_GetBytesFreeSpaceFromDriver':
bio2jack.c:2214: error: 'jack_driver_t' has no member named 'pPlayPtr'
bio2jack.c:2218: error: 'jack_driver_t' has no member named 'pPlayPtr'
bio2jack.c: In function 'JACK_GetBytesUsedSpace':
bio2jack.c:2255: error: 'jack_driver_t' has no member named 'pRecPtr'
bio2jack.c:2262: error: 'jack_driver_t' has no member named 'pRecPtr'
bio2jack.c: In function 'JACK_GetPositionFromDriver':
bio2jack.c:2291: error: 'jack_driver_t' has no member named 'state'
bio2jack.c:2331: error: 'jack_driver_t' has no member named 'position_byte_offset'
bio2jack.c: In function 'JACK_SetPositionFromDriver':
bio2jack.c:2390: error: 'jack_driver_t' has no member named 'position_byte_offset'
bio2jack.c: In function 'JACK_GetMaxOutputBufferedBytes':
bio2jack.c:2441: error: 'jack_driver_t' has no member named 'pPlayPtr'
bio2jack.c:2445: error: 'jack_driver_t' has no member named 'pPlayPtr'
bio2jack.c:2446: error: 'jack_driver_t' has no member named 'pPlayPtr'
bio2jack.c: In function 'JACK_GetMaxInputBufferedBytes':
bio2jack.c:2463: error: 'jack_driver_t' has no member named 'pRecPtr'
bio2jack.c:2467: error: 'jack_driver_t' has no member named 'pRecPtr'
bio2jack.c:2468: error: 'jack_driver_t' has no member named 'pRecPtr'
bio2jack.c: In function 'JACK_CleanupDriver':
bio2jack.c:2516: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:2517: error: 'jack_driver_t' has no member named 'in_use'
bio2jack.c:2518: error: 'jack_driver_t' has no member named 'state'
bio2jack.c:2522: error: 'jack_driver_t' has no member named 'jackd_died'
bio2jack.c:2524: error: 'jack_driver_t' has no member named 'last_reconnect_attempt'
bio2jack.c: In function 'JACK_Init':
bio2jack.c:2551: error: 'jack_driver_t' has no member named 'mutex'
bio2jack.c:2556: error: 'jack_driver_t' has no member named 'volumeEffectType'
bio2jack.c:2560: error: 'jack_driver_t' has no member named 'volume'
bio2jack.c: In function 'JACK_GetJackOutputLatency':
bio2jack.c:2584: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:2585: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:2585: error: 'jack_driver_t' has no member named 'output_port'
bio2jack.c: In function 'JACK_GetJackInputLatency':
bio2jack.c:2600: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:2601: error: 'jack_driver_t' has no member named 'client'
bio2jack.c:2601: error: 'jack_driver_t' has no member named 'input_port'
make[2]: *** [bio2jack.lo] Error 1
make[2]: Leaving directory `/home/vj/Desktop/veejay-1.0/bio2jack'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/vj/Desktop/veejay-1.0'
make: *** [all] Error 2


anything that stands out as obviously wrong?

---

### Post by qx! on 2007-06-09
yes - as I said - this (lack of elasticity, flexibility etc.) is a good reason to change distro :( I didn't worked it out, just aborted. I've tried to compile it WITH JACK DISABLED - every time **** happens.
dyne:bolic and suse have veejay packages/modules, but I wish to try it under slack.

---

### Post by rudlavibizon on 2007-06-20
I compiled successfully veejay on ubuntu studio, yesterday. Following a how-to that vj air followed. I didn't have that error but I installed a packet called libsamplerate-dev that a guy on a [vjair's thread in vjforums]("http://www.vjforums.com/showthread.php?t=21314&page=2")  said in his reply would fix this issue. I did this beforehand, so i don't know if there would be that kind of an error in the first place. VJ air you should check this reply if you haven't yet.

---

### Post by vj air on 2007-06-21
yeh, ive done that but i still get the same results unfortuntely.

---

