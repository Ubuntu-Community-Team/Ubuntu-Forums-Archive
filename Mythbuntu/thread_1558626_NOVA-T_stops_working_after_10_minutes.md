---
title: "NOVA-T stops working after 10 minutes"
date: 2010-08-22
forum: Mythbuntu
---

### Post by jammln on 2010-08-22
Hi There,

I've recently upgraded to 2.6.32-24 and all seemed to work perfectly.

I have two PCI tuners from Hauppauge, the old WINTV and a NOVA-T 500 giving me three tuners that worked fine before I upgraded.

I noticed the issue first when a number of shows give a 'File could not be found' error. 

Turns out that my NOVA-T stop working after about 10 minutes from a restart. Immediately after booting I can get mplayer to tune into three different programs on the three DVB-T tuners. All programs on different streams (BBC, ITV, C4). All three will run fine for 10 minutes and then two suddenly stop working. The end of the verbose output from mplayer is:

```
COLLECT_SECTION, start: 64, size: 184, collected: 184 8%  0% 39.5% 0 0 
SKIP: 0+1, TID: 0, TLEN: 37, COLLECTED: 184
PARSE_PAT: section_len: 37, section 0/0
PROG: 0 (1-th of 7), PMT: 16
PROG: 4671 (2-th of 7), PMT: 4671
PROG: 4479 (3-th of 7), PMT: 4479
PROG: 4415 (4-th of 7), PMT: 4415
PROG: 4351 (5-th of 7), PMT: 4351
PROG: 4236 (6-th of 7), PMT: 4236
PROG: 4172 (7-th of 7), PMT: 4172
COLLECT_SECTION, start: 64, size: 184, collected: 184 8%  0% 39.5% 0 0 
SKIP: 0+1, TID: 0, TLEN: 37, COLLECTED: 184
PARSE_PAT: section_len: 37, section 0/0
PROG: 0 (1-th of 7), PMT: 16
PROG: 4671 (2-th of 7), PMT: 4671
PROG: 4479 (3-th of 7), PMT: 4479
PROG: 4415 (4-th of 7), PMT: 4415
PROG: 4351 (5-th of 7), PMT: 4351
PROG: 4236 (6-th of 7), PMT: 4236
PROG: 4172 (7-th of 7), PMT: 4172
COLLECT_SECTION, start: 64, size: 184, collected: 184 8%  0% 39.5% 0 0 
SKIP: 0+1, TID: 0, TLEN: 37, COLLECTED: 184
PARSE_PAT: section_len: 37, section 0/0
PROG: 0 (1-th of 7), PMT: 16
PROG: 4671 (2-th of 7), PMT: 4671
PROG: 4479 (3-th of 7), PMT: 4479
PROG: 4415 (4-th of 7), PMT: 4415
PROG: 4351 (5-th of 7), PMT: 4351
PROG: 4236 (6-th of 7), PMT: 4236
PROG: 4172 (7-th of 7), PMT: 4172
dvb_streaming_read, attempt N. 6 failed with errno 11 when reading 464 bytes
dvb_streaming_read, attempt N. 5 failed with errno 0 when reading 464 bytes
dvb_streaming_read, attempt N. 4 failed with errno 0 when reading 464 bytes
dvb_streaming_read, attempt N. 3 failed with errno 0 when reading 464 bytes
dvb_streaming_read, attempt N. 2 failed with errno 0 when reading 464 bytes
dvb_streaming_read, attempt N. 1 failed with errno 0 when reading 464 bytes
COLLECT_SECTION, start: 64, size: 184, collected: 184
SKIP: 0+1, TID: 0, TLEN: 37, COLLECTED: 184
PARSE_PAT: section_len: 37, section 0/0
PROG: 0 (1-th of 7), PMT: 16
PROG: 4671 (2-th of 7), PMT: 4671
PROG: 4479 (3-th of 7), PMT: 4479
PROG: 4415 (4-th of 7), PMT: 4415
PROG: 4351 (5-th of 7), PMT: 4351
PROG: 4236 (6-th of 7), PMT: 4236
PROG: 4172 (7-th of 7), PMT: 4172
dvb_streaming_read, attempt N. 6 failed with errno 0 when reading 2048 bytes
dvb_streaming_read, attempt N. 5 failed with errno 0 when reading 2048 bytes
dvb_streaming_read, attempt N. 4 failed with errno 0 when reading 2048 bytes
dvb_streaming_read, attempt N. 3 failed with errno 0 when reading 2048 bytes
dvb_streaming_read, attempt N. 2 failed with errno 0 when reading 2048 bytes
dvb_streaming_read, attempt N. 1 failed with errno 0 when reading 2048 bytes
dvb_streaming_read, return 0 bytes
TS_PARSE: COULDN'T SYNC
ds_fill_buffer: EOF reached (stream: audio)  
ds_fill_buffer: EOF reached (stream: audio)  01/6601  8%  0% 41.8% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  02/6602  8%  0% 41.8% 0 0 

Broken frame at 0x813900                                                  
ds_fill_buffer: EOF reached (stream: audio)  03/6603  8%  0% 41.8% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  04/6604  8%  0% 41.8% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  05/6605  8%  0% 41.8% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  06/6606  8%  0% 41.8% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  07/6607  8%  0% 41.8% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  08/6608  8%  0% 41.8% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  09/6609  8%  0% 41.8% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  10/6610  8%  0% 41.8% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  11/6611  8%  0% 41.8% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  12/6612  8%  0% 41.8% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  13/6613  8%  0% 41.8% 0 0 
ds_fill_buffer: EOF reached (stream: video)  
ds_fill_buffer: EOF reached (stream: video)  
EOF code: 1  9594.6 A-V: -0.285 ct: -0.472 6613/6613  8%  0% 41.8% 0 0 

Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: mp3lib
Uninit video: ffmpeg
DVBIN_CLOSE, close(2), fd=7, COUNT=2
DVBIN_CLOSE, close(1), fd=6, COUNT=1
DVBIN_CLOSE, close(0), fd=5, COUNT=0
alsa-uninit: pcm closed
vo: uninit ...

Exiting... (End of file)

```

Any further attempt to run mplayer with that tuner gives
```

DVB_CONFIG, can't open device /dev/dvb/adapter3/frontend0, skipping
OPEN_DVB: prog=BBC ONE, card=1, type=2

dvb_streaming_start(PROG: BBC ONE, CARD: 1, FILE: (null))
PROGRAM NUMBER 5: name=BBC ONE, freq=578000000
ERROR OPENING FRONTEND DEVICE /dev/dvb/adapter0/frontend0: ERRNO 16
DVB_SET_CHANNEL2, COULDN'T OPEN DEVICES OF CARD: 0, EXIT
ERROR, COULDN'T SET CHANNEL  5: Failed to open dvb://1@BBC ONE.

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)

```

I'm not having much luck seeing others with the same issue. Any ideas?

---

### Post by nickrout on 2010-08-22
Anything in the logs? or dmesg?

Are the device nodes still there? ```
ls /dev/dvb/adapter0/frontend0
```

Does unloading and reloading the kernel module help?

```
modprobe -r modulename
modprobe modulename
```

(sorry i can't recall what module drives that device.)

---

### Post by mymythtv on 2010-08-23
Hmmm - could be the same kernel-bug which also hit me...

My combined FE/BE froze when doing playback, and worked sometime to figure out what was causing the problem - first thought it was Nvidia driver and/or gfx failure, but then I noticed that my Nova T-500 also failed to record ( scheduled ) - resulting in garbled recordings...
The first 4-5 minutes of the recording were ok, but then the rest were unwatchable...

Upgraded Nvidia driver, replaced fgx and used a lot of time reading, but finally fixed it by downgrading my kernel from 2.6.32-XX to 2.6.31-21 as a lot of reading indicated problems with 2.6.32 kernel...

Others also reported success by upgrading kernel to 2.6.34

Don't know if it's the same problem, but it seems 2.6.32 is causing a lot of noise......

---

### Post by jammln on 2010-08-24
Unfortunately unloading and reloading the module causes it to be removed from lsmod until I reboot.

I wanted to look in messages and syslog but neither appear to be there! and synaptic says that those apps no longer exist. Any thoughts?

How would I upgrade to .34? Synaptic doesn't give me the option, is it not stable yet?

TIA

---

