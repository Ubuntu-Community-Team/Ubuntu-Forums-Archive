---
title: "OTA ATSC KWorld 115"
date: 2008-03-28
forum: Mythbuntu
---

### Post by dsbw on 2008-03-28
OK, I detailed my confusions about signal types in the Analog v Digital thread. Now down to getting my particular setup to work. I've done all the usual setup for Kworld and used it to capture signals straight from the wall.

I haven't used it to capture signals from OTA or coming out of the STB.

I followed this [thread to do the scan]("http://ubuntuforums.org/showthread.php?p=3994301#post3994301").

But when I try to do the mplayer dvb:// I get errors. 

Not able to lock to the signal on the given frequency, timeout: 30
dvb_tune, TUNING FAILED
ERROR, COULDN'T SET CHANNEL 0: Failed to open dvb://.

:confused:

---

### Post by dsbw on 2008-03-29
OK, redone, now getting this from  mplayer dvb: //
```

MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not open config files /root/.lircrc and /etc/lirc//lircrc
mplayer: No such file or directory
Failed to read LIRC config file ~/.lircrc.

Playing dvb://.
dvb_tune Freq: 605028615
dvb_streaming_read, attempt N. 6 failed with errno 0 when reading 2048 bytes


Exiting... (End of file)

```

---

### Post by dsbw on 2008-03-31
Anyone?

I've got it scanning in Myth, but I just get blackness when I try to watch.

And a bunch of error messages like the above "attempt N" failed when reading X bytes when using MPLAYER.

---

### Post by thecoolcat on 2008-03-31
Hi, the tuning failed message is perfectly normal. That's because not all channel frequencies are being broadcast in your local area. Per the post you have quoted, you should be able to create a channels configuration file for mplayer to use.

---

### Post by dsbw on 2008-04-01
> **thecoolcat said:**
> Hi, the tuning failed message is perfectly normal. That's because not all channel frequencies are being broadcast in your local area. Per the post you have quoted, you should be able to create a channels configuration file for mplayer to use.

I thought that was what "scan" did, was create the channels.conf for mplayer to use. Else...why am I creating it?

---

