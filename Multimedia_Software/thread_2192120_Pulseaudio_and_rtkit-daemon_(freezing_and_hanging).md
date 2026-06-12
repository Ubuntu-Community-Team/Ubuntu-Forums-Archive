---
title: "Pulseaudio and rtkit-daemon (freezing and hanging)"
date: 2013-12-06
forum: Multimedia Software
---

### Post by the-solipsist on 2013-12-06
Every once in a while my OS freezes (the cursor won't move, any playing audio skips, the clock stops).  Going through syslog reveals that threads of PulseAudio (process 2079 in the below log) are being demoted by rtkit-daemon.  I've scoured the net, but can't find any suggestions on how I can troubleshoot this further and solve it.

The past threads I found on this:
[http://ubuntuforums.org/showthread.php?t=1542075&page=2](http://ubuntuforums.org/showthread.php?t=1542075&page=2)
and
[http://ubuntuforums.org/showthread.php?t=1874171](http://ubuntuforums.org/showthread.php?t=1874171)

In neither case was a solution found.  I did want to necrobump those threads, hence this.

```
Dec  5 19:57:51 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 19:57:51 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 19:57:51 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 19:57:51 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 19:57:51 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 19:57:51 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 19:58:56 sirius kernel: [13951.321147] psmouse serio1: TrackPoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Dec  5 20:02:04 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 20:02:04 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 20:02:04 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 20:02:04 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 20:02:04 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 20:02:04 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 20:04:09 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 20:04:09 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 20:04:09 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 20:04:09 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 20:04:09 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 20:04:09 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 20:05:14 sirius kernel: [14329.557475] psmouse serio1: TrackPoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Dec  5 20:09:26 sirius kernel: [14581.713769] psmouse serio1: TrackPoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Dec  5 20:10:28 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 20:10:28 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 20:10:28 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 20:10:28 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 20:10:28 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 20:10:28 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 20:17:01 sirius CRON[9835]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  5 20:17:50 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 20:17:50 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 20:17:50 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 20:17:50 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 20:17:50 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 20:17:50 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 862552 bytes (4889 ms).
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: snd_pcm_dump():
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: Soft volume PCM
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: Control: PCM Playback Volume
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: min_dB: -51
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: max_dB: 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: resolution: 256
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: Its setup is:
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   stream       : PLAYBACK
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   access       : MMAP_INTERLEAVED
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   format       : S16_LE
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   subformat    : STD
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   channels     : 2
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   rate         : 44100
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   exact rate   : 44100 (44100/1)
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   msbits       : 16
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   buffer_size  : 16384
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_size  : 8192
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_time  : 185759
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   tstamp_mode  : ENABLE
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_step  : 1
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   avail_min    : 15944
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_event : 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   start_threshold  : -1
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   stop_threshold   : 4611686018427387904
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   silence_threshold: 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   silence_size : 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   boundary     : 4611686018427387904
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel MID' device 0 subdevice 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: Its setup is:
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   stream       : PLAYBACK
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   access       : MMAP_INTERLEAVED
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   format       : S16_LE
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   subformat    : STD
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   channels     : 2
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   rate         : 44100
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   exact rate   : 44100 (44100/1)
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   msbits       : 16
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   buffer_size  : 16384
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_size  : 8192
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_time  : 185759
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   tstamp_mode  : ENABLE
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_step  : 1
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   avail_min    : 15944
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_event : 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   start_threshold  : -1
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   stop_threshold   : 4611686018427387904
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   silence_threshold: 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   silence_size : 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   boundary     : 4611686018427387904
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   appl_ptr     : 25980834
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   hw_ptr       : 26180088
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: snd_pcm_delay() returned a value that is exceptionally large: -765960 bytes (-4342 ms).
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: snd_pcm_dump():
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: Soft volume PCM
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: Control: PCM Playback Volume
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: min_dB: -51
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: max_dB: 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: resolution: 256
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: Its setup is:
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   stream       : PLAYBACK
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   access       : MMAP_INTERLEAVED
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   format       : S16_LE
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   subformat    : STD
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   channels     : 2
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   rate         : 44100
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   exact rate   : 44100 (44100/1)
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   msbits       : 16
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   buffer_size  : 16384
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_size  : 8192
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_time  : 185759
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   tstamp_mode  : ENABLE
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_step  : 1
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   avail_min    : 15944
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_event : 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   start_threshold  : -1
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   stop_threshold   : 4611686018427387904
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   silence_threshold: 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   silence_size : 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   boundary     : 4611686018427387904
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel MID' device 0 subdevice 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c: Its setup is:
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   stream       : PLAYBACK
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   access       : MMAP_INTERLEAVED
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   format       : S16_LE
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   subformat    : STD
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   channels     : 2
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   rate         : 44100
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   exact rate   : 44100 (44100/1)
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   msbits       : 16
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   buffer_size  : 16384
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_size  : 8192
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_time  : 185759
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   tstamp_mode  : ENABLE
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_step  : 1
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   avail_min    : 15944
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   period_event : 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   start_threshold  : -1
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   stop_threshold   : 4611686018427387904
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   silence_threshold: 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   silence_size : 0
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   boundary     : 4611686018427387904
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   appl_ptr     : 25989654
Dec  5 20:31:29 sirius pulseaudio[2079]: [alsa-sink-CX20585 Analog] alsa-util.c:   hw_ptr       : 26181144
Dec  5 20:34:38 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 20:34:38 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 20:34:38 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 20:34:38 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 20:34:38 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 20:34:38 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 20:49:19 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 20:49:19 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 20:49:19 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 20:49:19 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 20:49:19 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 20:49:19 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 20:58:47 sirius kernel: [17544.542448] psmouse serio1: TrackPoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Dec  5 20:59:49 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 20:59:49 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 20:59:49 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 20:59:49 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 20:59:49 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 20:59:49 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 20:59:50 sirius kernel: [17607.587061] psmouse serio1: TrackPoint at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Dec  5 21:00:52 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 21:00:52 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 21:00:52 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 21:00:52 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 21:00:52 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 21:00:52 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 21:01:54 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 21:01:54 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 21:01:54 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 21:01:54 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 21:01:54 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 21:01:54 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 21:01:56 sirius kernel: [17733.621894] psmouse serio1: TrackPoint at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Dec  5 21:02:58 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 21:02:58 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 21:02:58 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 21:02:58 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 21:02:58 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 21:02:58 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 21:04:01 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 21:04:01 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 21:04:01 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 21:04:01 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 21:04:01 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 21:04:01 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 21:12:24 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 21:12:24 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 21:12:24 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 21:12:24 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 21:12:24 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 21:12:24 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 21:17:01 sirius CRON[10333]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  5 21:18:42 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 21:18:42 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 21:18:42 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 21:18:42 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 21:18:42 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 21:18:42 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 21:28:09 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 21:28:09 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 21:28:09 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 21:28:09 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 21:28:09 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 21:28:09 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 21:29:14 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 21:29:14 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 21:29:14 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 21:29:14 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 21:29:14 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 21:29:14 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 21:29:14 sirius kernel: [19372.667018] psmouse serio1: TrackPoint at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Dec  5 22:17:01 sirius CRON[10644]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  5 22:32:14 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 22:32:14 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 22:32:14 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 22:32:14 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 22:32:14 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 22:32:14 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 23:17:01 sirius CRON[11067]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  5 23:21:34 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 23:21:34 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 23:21:34 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 23:21:34 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 23:21:34 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 23:21:34 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 23:44:40 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 23:44:40 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 23:44:40 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 23:44:40 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 23:44:40 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 23:44:40 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 23:52:01 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 23:52:01 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 23:52:01 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 23:52:01 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 23:52:01 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 23:52:01 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  5 23:59:21 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  5 23:59:21 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  5 23:59:21 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  5 23:59:21 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  5 23:59:21 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  5 23:59:21 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  6 00:17:01 sirius CRON[11551]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  6 00:20:23 sirius kernel: [29648.005652] psmouse serio1: TrackPoint at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Dec  6 00:32:59 sirius kernel: [30404.467398] psmouse serio1: TrackPoint at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Dec  6 00:40:18 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  6 00:40:18 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  6 00:40:18 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  6 00:40:18 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  6 00:40:18 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  6 00:40:18 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  6 00:48:43 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  6 00:48:43 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  6 00:48:43 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  6 00:48:43 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  6 00:48:43 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  6 00:48:43 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  6 00:59:12 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  6 00:59:12 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  6 00:59:12 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  6 00:59:12 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  6 00:59:12 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  6 00:59:12 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  6 01:02:21 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  6 01:02:21 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  6 01:02:21 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  6 01:02:21 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  6 01:02:21 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  6 01:02:21 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  6 01:05:16 sirius dhclient: DHCPREQUEST of 192.168.1.210 on eth0 to 192.168.1.1 port 67 (xid=0x194041ca)
Dec  6 01:05:16 sirius dhclient: DHCPACK of 192.168.1.210 from 192.168.1.1
Dec  6 01:05:16 sirius dhclient: bound to 192.168.1.210 -- renewal in 16820 seconds.
Dec  6 01:05:16 sirius NetworkManager[900]: <info> (eth0): DHCPv4 state changed reboot -> renew
Dec  6 01:05:16 sirius NetworkManager[900]: <info>   address 192.168.1.210
Dec  6 01:05:16 sirius NetworkManager[900]: <info>   prefix 24 (255.255.255.0)
Dec  6 01:05:16 sirius NetworkManager[900]: <info>   gateway 192.168.1.1
Dec  6 01:05:16 sirius NetworkManager[900]: <info>   hostname 'sirius'
Dec  6 01:05:16 sirius NetworkManager[900]: <info>   nameserver '192.168.1.1'
Dec  6 01:05:16 sirius NetworkManager[900]: <info>   domain name 'lan'
Dec  6 01:05:16 sirius dbus[578]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec  6 01:05:16 sirius dbus[578]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec  6 01:11:48 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  6 01:11:48 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  6 01:11:48 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  6 01:11:48 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  6 01:11:48 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  6 01:11:48 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  6 01:12:51 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  6 01:12:51 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  6 01:12:51 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  6 01:12:51 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  6 01:12:51 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  6 01:12:51 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  6 01:13:55 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  6 01:13:55 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  6 01:13:55 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  6 01:13:55 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  6 01:13:55 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  6 01:13:55 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  6 01:17:05 sirius CRON[11977]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  6 01:20:14 sirius kernel: [33241.218892] psmouse serio1: TrackPoint at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Dec  6 01:21:15 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  6 01:21:15 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  6 01:21:15 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  6 01:21:15 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  6 01:21:15 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  6 01:21:15 sirius rtkit-daemon[1544]: Demoted 3 threads.
Dec  6 01:24:24 sirius rtkit-daemon[1544]: The canary thread is apparently starving. Taking action.
Dec  6 01:24:24 sirius rtkit-daemon[1544]: Demoting known real-time threads.
Dec  6 01:24:24 sirius rtkit-daemon[1544]: Successfully demoted thread 2142 of process 2079 (n/a).
Dec  6 01:24:24 sirius rtkit-daemon[1544]: Successfully demoted thread 2141 of process 2079 (n/a).
Dec  6 01:24:24 sirius rtkit-daemon[1544]: Successfully demoted thread 2079 of process 2079 (n/a).
Dec  6 01:24:24 sirius rtkit-daemon[1544]: Demoted 3 threads.
```

---

### Post by gakocian on 2013-12-20
Hey there,

Unfortunately, I don't have anything to help narrow down the problem, but I just wanted to mention I am suffering from the same issue.  Just got back to my PC last night, and found it was unresponsive, and the hard drive light was solid...  doing something.  No mouse movement, could not login via SSH, although there was a ping reply from the system.   The mouse would move a slight bit every few minutes, but I had to power off the PC in the end...  hopefully someone has some further insight into this.



[QUOTE=the-solipsist;12866451]Every once in a while my OS freezes (the cursor won't move, any playing audio skips, the clock stops).  Going through syslog reveals that threads of PulseAudio (process 2079 in the below log) are being demoted by rtkit-daemon.  I've scoured the net, but can't find any suggestions on how I can troubleshoot this further and solve it.

The past threads I found on this:
[http://ubuntuforums.org/showthread.php?t=1542075&page=2](http://ubuntuforums.org/showthread.php?t=1542075&page=2)
and
[http://ubuntuforums.org/showthread.php?t=1874171](http://ubuntuforums.org/showthread.php?t=1874171)

In neither case was a solution found.  I did want to necrobump those threads, hence this.

---

### Post by rbwohlfarth on 2014-01-12
As a temporary work around, I filtered out the log messages. This at least prevents the logs from filling, which seems to be what froze the system.

```

# sudo echo ':msg,contains,"[alsa-sink-CONEXANT Analog] alsa-util.c" ~' > /etc/rsyslog.d/01-blocklist.conf
# sudo service rsyslog restart

```

---

