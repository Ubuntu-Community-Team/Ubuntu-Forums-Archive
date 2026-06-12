---
title: "Mythtv LiveTV playback crashes"
date: 2009-09-06
forum: Multimedia Software
---

### Post by Keithamus on 2009-09-06
I have errors when playing back live tv, it'll work  for 2 minutes, 5 minutes, sometimes 30 minutes, but then it will freeze for a while and  crash out.

Here is the log  for mythfrontend:
```

2009-09-06 11:49:18.853 WriteAudio: buffer underrun
2009-09-06 11:49:20.429 NVP: Prebuffer wait timed out 10 times.
2009-09-06 11:49:22.030 NVP: Prebuffer wait timed out 20 times.
2009-09-06 11:49:22.349 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited 4.0 seconds for data to become available...
2009-09-06 11:49:22.349 Checking to see if there's a new livetv program to switch to..
2009-09-06 11:49:23.631 NVP: Prebuffer wait timed out 30 times.
2009-09-06 11:49:25.232 NVP: Prebuffer wait timed out 40 times.
2009-09-06 11:49:25.839 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg) Error: RingBuffer::safe_read(RemoteFile* ...): read failed
2009-09-06 11:49:26.833 NVP: Prebuffer wait timed out 50 times.
2009-09-06 11:49:28.434 NVP: Prebuffer wait timed out 60 times.
2009-09-06 11:49:30.035 NVP: Prebuffer wait timed out 70 times.
2009-09-06 11:49:31.636 NVP: Prebuffer wait timed out 80 times.
2009-09-06 11:49:33.237 NVP: Prebuffer wait timed out 90 times.
2009-09-06 11:49:34.838 NVP: Prebuffer wait timed out 100 times.
2009-09-06 11:49:34.838 NVP, Error: Timed out waiting for prebuffering too long. Exiting..
2009-09-06 11:49:34.839 TV: Attempting to change from WatchingLiveTV to None
2009-09-06 11:49:35.840 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:36.440 NVP: Prebuffer wait timed out 110 times.
2009-09-06 11:49:36.440 NVP, Error: Timed out waiting for prebuffering too long. Exiting..
2009-09-06 11:49:36.840 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:37.840 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:38.041 NVP: Prebuffer wait timed out 120 times.
2009-09-06 11:49:38.041 NVP, Error: Timed out waiting for prebuffering too long. Exiting..
2009-09-06 11:49:38.841 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:39.642 NVP: Prebuffer wait timed out 130 times.
2009-09-06 11:49:39.642 NVP, Error: Timed out waiting for prebuffering too long. Exiting..
2009-09-06 11:49:39.841 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:40.841 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:41.243 NVP: Prebuffer wait timed out 140 times.
2009-09-06 11:49:41.243 NVP, Error: Timed out waiting for prebuffering too long. Exiting..
2009-09-06 11:49:41.841 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:42.842 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:42.844 NVP: Prebuffer wait timed out 150 times.
2009-09-06 11:49:42.844 NVP, Error: Timed out waiting for prebuffering too long. Exiting..
2009-09-06 11:49:43.842 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:44.446 NVP: Prebuffer wait timed out 160 times.
2009-09-06 11:49:44.446 NVP, Error: Timed out waiting for prebuffering too long. Exiting..
2009-09-06 11:49:44.842 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:45.842 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:46.047 NVP: Prebuffer wait timed out 170 times.
2009-09-06 11:49:46.047 NVP, Error: Timed out waiting for prebuffering too long. Exiting..
2009-09-06 11:49:46.843 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:47.648 NVP: Prebuffer wait timed out 180 times.
2009-09-06 11:49:47.648 NVP, Error: Timed out waiting for prebuffering too long. Exiting..
2009-09-06 11:49:47.843 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:48.843 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:49.249 NVP: Prebuffer wait timed out 190 times.
2009-09-06 11:49:49.250 NVP, Error: Timed out waiting for prebuffering too long. Exiting..
2009-09-06 11:49:49.844 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:50.844 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:50.850 NVP: Prebuffer wait timed out 200 times.
2009-09-06 11:49:50.851 NVP, Error: Timed out waiting for prebuffering too long. Exiting..
2009-09-06 11:49:51.844 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:52.452 NVP: Prebuffer wait timed out 210 times.
2009-09-06 11:49:52.452 NVP, Error: Timed out waiting for prebuffering too long. Exiting..
2009-09-06 11:49:52.844 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:53.845 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:54.053 NVP: Prebuffer wait timed out 220 times.
2009-09-06 11:49:54.053 NVP, Error: Timed out waiting for prebuffering too long. Exiting..
2009-09-06 11:49:54.845 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..
2009-09-06 11:49:55.844 MythSocket(7fbe6a54adc0:114): readStringList: Error, timeout.
2009-09-06 11:49:55.844 decodeLongLong() called with offset >= list size.
2009-09-06 11:49:55.845 RingBuf(myth://192.168.0.103:6543/1011_20090906114838.mpg): Waited too long for ringbuffer pause..

```

I watched **top** on both the frontend and backend and total cpu% was very low, 2% on the backend and 15% on the frontend.

Any ideas?

---

### Post by dano1 on 2009-09-07
try this: [http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678)  or search the nvidia forums.

hth, danny

edit: see also: [http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause](http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause)

---

