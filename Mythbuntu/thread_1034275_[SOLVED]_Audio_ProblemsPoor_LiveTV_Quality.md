---
title: "[SOLVED] Audio Problems/Poor LiveTV Quality"
date: 2009-01-08
forum: Mythbuntu
---

### Post by RonPDX on 2009-01-08
Good morning everyone, 

After spending what fells like an eternity on google trying solve a couple of problems I am hoping that someone can point me in the right direction. 

Basically I am getting poor audio/video and high memory usage, my log is below and I have already looked around and I can not find a solution. I have installed the firmware as directed from some other posts. 

**Update**
This problem was fixed by doing a fresh install of 8.10.

Specs --
Tuner: Pinnacle PCTV HD PCI 801i
OS: dual XP/Mythbuntu 8.10
Dell Dimension 2400
Intel Celeron 2.4g w/ 2g of memory

```
==> /var/log/mythtv/mythbackend.log <==
2009-01-08 02:27:34.755 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:27:36.131 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:27:38.523 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:27:40.359 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:27:42.795 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:27:43.351 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:27:45.603 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:27:46.147 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:27:48.423 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:27:49.182 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:27:51.391 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:27:52.959 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:27:55.203 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:27:56.307 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:27:58.763 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:27:59.655 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:01.836 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:02.915 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:03.076 Expiring 53 MBytes for 2012 @ Thu Jan 8 02:00:00 2009 => Paid Programming
2009-01-08 02:28:03.125 Expiring 67 MBytes for 2008 @ Thu Jan 8 02:05:00 2009 => Poker After Dark
2009-01-08 02:28:05.203 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:07.175 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:09.327 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:10.055 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:12.315 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:13.607 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:15.899 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:16.751 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:19.028 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:19.548 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:21.807 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:22.315 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:24.535 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:25.063 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:27.399 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:28.307 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:30.643 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:31.803 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:33.983 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:34.539 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:36.691 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:37.247 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:39.423 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:39.955 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:42.163 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:42.699 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:44.923 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:45.931 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:48.359 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:50.163 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:52.647 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:53.375 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:55.583 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:56.115 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:28:58.407 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:28:59.103 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:29:01.327 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:29:02.363 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:29:04.719 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:29:05.251 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:29:07.579 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:29:09.235 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:29:11.459 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:29:12.171 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:29:14.483 NVR(/dev/video0) Error: Resetting and re-queueing
2009-01-08 02:29:15.022 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
2009-01-08 02:29:15.215 TVRec(1): Changing from WatchingLiveTV to None
2009-01-08 02:29:17.732 Finished recording Good Eats "The Muffin Man": channel 2066

==> /var/log/mythtv/mythfrontend.log <==
2009-01-08 02:29:12.872 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:12.872 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:12.872 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:12.873 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:12.873 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:12.873 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:12.873 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:12.873 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.295 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.295 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.295 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.295 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.296 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.296 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.296 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.296 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.296 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.297 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.297 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.297 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.297 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.297 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.297 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.298 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.298 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.298 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.298 NVP: Prebuffer wait timed out 10 times.
2009-01-08 02:29:13.660 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.660 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.660 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.660 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.661 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.661 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.661 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.661 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.661 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.661 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.662 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.662 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.662 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.662 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.662 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.663 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.663 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:13.663 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.025 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.025 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.025 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.025 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.025 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.026 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.026 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.026 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.026 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.026 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.027 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.027 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.027 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.027 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.028 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.028 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.028 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.028 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.451 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.452 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.452 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.452 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.452 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.452 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.453 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.453 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.453 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.453 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.453 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.454 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.454 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.454 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.454 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.454 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.455 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.456 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.629 NVP: Prebuffer wait timed out 10 times.
2009-01-08 02:29:14.757 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.757 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.758 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.758 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.758 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.758 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.758 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.759 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.759 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.759 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.759 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.759 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.760 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.820 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.820 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.820 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.821 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-08 02:29:14.821 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Jan  8 02:29:09 stiles-desktop kernel: [  796.612186] cx88[0]:   iq 10: 0x00180c00 [ arg #1 ]
Jan  8 02:29:09 stiles-desktop kernel: [  796.612188] cx88[0]: fifo: 0x00180c00 -> 0x183400
Jan  8 02:29:09 stiles-desktop kernel: [  796.612191] cx88[0]: ctrl: 0x00180400 -> 0x180460
Jan  8 02:29:09 stiles-desktop kernel: [  796.612194] cx88[0]:   ptr1_reg: 0x00181740
Jan  8 02:29:09 stiles-desktop kernel: [  796.612197] cx88[0]:   ptr2_reg: 0x00180478
Jan  8 02:29:09 stiles-desktop kernel: [  796.612200] cx88[0]:   cnt1_reg: 0x00000000
Jan  8 02:29:09 stiles-desktop kernel: [  796.612203] cx88[0]:   cnt2_reg: 0x00000000
Jan  8 02:29:09 stiles-desktop kernel: [  796.612218] cx88[0]/0: [e0025d80/4] timeout - dma=0x13000000
Jan  8 02:29:09 stiles-desktop kernel: [  796.612222] cx88[0]/0: [e0025a80/0] timeout - dma=0x13626000
Jan  8 02:29:09 stiles-desktop kernel: [  796.612225] cx88[0]/0: [e0025b40/1] timeout - dma=0x136a4000
Jan  8 02:29:09 stiles-desktop kernel: [  796.612228] cx88[0]/0: [e0025c00/2] timeout - dma=0x13702000
Jan  8 02:29:09 stiles-desktop kernel: [  796.612231] cx88[0]/0: [e0025cc0/3] timeout - dma=0x13780000
Jan  8 02:29:12 stiles-desktop kernel: [  799.548033] cx88[0]: video y / packed - dma channel status dump
Jan  8 02:29:12 stiles-desktop kernel: [  799.548058] cx88[0]:   cmds: initial risc: 0x13000000
Jan  8 02:29:12 stiles-desktop kernel: [  799.548062] cx88[0]:   cmds: cdt base    : 0x00180440
Jan  8 02:29:12 stiles-desktop kernel: [  799.548066] cx88[0]:   cmds: cdt size    : 0x0000000c
Jan  8 02:29:12 stiles-desktop kernel: [  799.548070] cx88[0]:   cmds: iq base     : 0x00180400
Jan  8 02:29:12 stiles-desktop kernel: [  799.548074] cx88[0]:   cmds: iq size     : 0x00000010
Jan  8 02:29:12 stiles-desktop kernel: [  799.548077] cx88[0]:   cmds: risc pc     : 0x13780034
Jan  8 02:29:12 stiles-desktop kernel: [  799.548081] cx88[0]:   cmds: iq wr ptr   : 0x00000102
Jan  8 02:29:12 stiles-desktop kernel: [  799.548084] cx88[0]:   cmds: iq rd ptr   : 0x00000106
Jan  8 02:29:12 stiles-desktop kernel: [  799.548088] cx88[0]:   cmds: cdt current : 0x00000488
Jan  8 02:29:12 stiles-desktop kernel: [  799.548092] cx88[0]:   cmds: pci target  : 0x13619800
Jan  8 02:29:12 stiles-desktop kernel: [  799.548095] cx88[0]:   cmds: line / byte : 0x02f00000
Jan  8 02:29:12 stiles-desktop kernel: [  799.548099] cx88[0]:   risc0: 0x80008000 [ sync resync count=0 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548106] cx88[0]:   risc1: 0x1c0003c0 [ write sol eol count=960 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548112] cx88[0]:   risc2: 0x1361a000 [ arg #1 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548116] cx88[0]:   risc3: 0x1c0003c0 [ write sol eol count=960 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548122] cx88[0]:   iq 0: 0x18000200 [ write sol count=512 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548128] cx88[0]:   iq 1: 0x1361be00 [ arg #1 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548132] cx88[0]:   iq 2: 0x1c0003c0 [ write sol eol count=960 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548138] cx88[0]:   iq 3: 0x13619440 [ arg #1 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548142] cx88[0]:   iq 4: 0x71010000 [ jump irq1 cnt0 count=0 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548157] cx88[0]:   iq 5: 0x80008000 [ arg #1 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548161] cx88[0]:   iq 6: 0x1c0003c0 [ write sol eol count=960 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548168] cx88[0]:   iq 7: 0x1361a000 [ arg #1 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548171] cx88[0]:   iq 8: 0x1c0003c0 [ write sol eol count=960 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548177] cx88[0]:   iq 9: 0x1361a780 [ arg #1 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548180] cx88[0]:   iq a: 0x18000100 [ write sol count=256 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548186] cx88[0]:   iq b: 0x1361af00 [ arg #1 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548189] cx88[0]:   iq c: 0x140002c0 [ write eol count=704 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548195] cx88[0]:   iq d: 0x1361b000 [ arg #1 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548198] cx88[0]:   iq e: 0x1c0003c0 [ write sol eol count=960 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548205] cx88[0]:   iq f: 0x1361b680 [ arg #1 ]
Jan  8 02:29:12 stiles-desktop kernel: [  799.548208] cx88[0]: fifo: 0x00180c00 -> 0x183400
Jan  8 02:29:12 stiles-desktop kernel: [  799.548210] cx88[0]: ctrl: 0x00180400 -> 0x180460
Jan  8 02:29:12 stiles-desktop kernel: [  799.548214] cx88[0]:   ptr1_reg: 0x00180f00
Jan  8 02:29:12 stiles-desktop kernel: [  799.548217] cx88[0]:   ptr2_reg: 0x00180448
Jan  8 02:29:12 stiles-desktop kernel: [  799.548220] cx88[0]:   cnt1_reg: 0x00000000
Jan  8 02:29:12 stiles-desktop kernel: [  799.548223] cx88[0]:   cnt2_reg: 0x00000000
Jan  8 02:29:12 stiles-desktop kernel: [  799.548238] cx88[0]/0: [e0025b40/1] timeout - dma=0x13780000
Jan  8 02:29:12 stiles-desktop kernel: [  799.548243] cx88[0]/0: [e0025c00/2] timeout - dma=0x13702000
Jan  8 02:29:12 stiles-desktop kernel: [  799.548247] cx88[0]/0: [e0025cc0/3] timeout - dma=0x136a4000
Jan  8 02:29:12 stiles-desktop kernel: [  799.548250] cx88[0]/0: [e0025d80/4] timeout - dma=0x13626000
Jan  8 02:29:12 stiles-desktop kernel: [  799.548253] cx88[0]/0: [e0025a80/0] timeout - dma=0x13000000
Jan  8 02:29:15 stiles-desktop kernel: [  802.380039] cx88[0]: video y / packed - dma channel status dump
Jan  8 02:29:15 stiles-desktop kernel: [  802.380057] cx88[0]:   cmds: initial risc: 0x13626000
Jan  8 02:29:15 stiles-desktop kernel: [  802.380063] cx88[0]:   cmds: cdt base    : 0x00180440
Jan  8 02:29:15 stiles-desktop kernel: [  802.380068] cx88[0]:   cmds: cdt size    : 0x0000000c
Jan  8 02:29:15 stiles-desktop kernel: [  802.380072] cx88[0]:   cmds: iq base     : 0x00180400
Jan  8 02:29:15 stiles-desktop kernel: [  802.380075] cx88[0]:   cmds: iq size     : 0x00000010
Jan  8 02:29:15 stiles-desktop kernel: [  802.380079] cx88[0]:   cmds: risc pc     : 0x13626958
Jan  8 02:29:15 stiles-desktop kernel: [  802.380083] cx88[0]:   cmds: iq wr ptr   : 0x00000106
Jan  8 02:29:15 stiles-desktop kernel: [  802.380087] cx88[0]:   cmds: iq rd ptr   : 0x0000010a
Jan  8 02:29:15 stiles-desktop kernel: [  802.380090] cx88[0]:   cmds: cdt current : 0x00000478
Jan  8 02:29:15 stiles-desktop kernel: [  802.380093] cx88[0]:   cmds: pci target  : 0x13619440
Jan  8 02:29:15 stiles-desktop kernel: [  802.380097] cx88[0]:   cmds: line / byte : 0x00f00000
Jan  8 02:29:15 stiles-desktop kernel: [  802.380101] cx88[0]:   risc0: 0x80008200 [ sync resync count=512 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380107] cx88[0]:   risc1: 0x1c0003c0 [ write sol eol count=960 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380113] cx88[0]:   risc2: 0x135a33c0 [ arg #1 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380118] cx88[0]:   risc3: 0x1c0003c0 [ write sol eol count=960 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380124] cx88[0]:   iq 0: 0x1c0003c0 [ write sol eol count=960 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380130] cx88[0]:   iq 1: 0x135aaa40 [ arg #1 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380133] cx88[0]:   iq 2: 0x1c0003c0 [ write sol eol count=960 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380139] cx88[0]:   iq 3: 0x135ab1c0 [ arg #1 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380142] cx88[0]:   iq 4: 0x1c0003c0 [ write sol eol count=960 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380149] cx88[0]:   iq 5: 0x135ab940 [ arg #1 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380152] cx88[0]:   iq 6: 0x13618900 [ write irq2 irq1 22 21 cnt0 resync count=2304 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380161] cx88[0]:   iq 7: 0x1c0003c0 [ arg #1 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380164] cx88[0]:   iq 8: 0x13619080 [ write irq2 irq1 22 21 cnt0 resync 12 count=128 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380173] cx88[0]:   iq 9: 0x80008200 [ arg #1 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380176] cx88[0]:   iq a: 0x1c0003c0 [ write sol eol count=960 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380182] cx88[0]:   iq b: 0x135a33c0 [ arg #1 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380186] cx88[0]:   iq c: 0x1c0003c0 [ write sol eol count=960 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380192] cx88[0]:   iq d: 0x135a3b40 [ arg #1 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380195] cx88[0]:   iq e: 0x1c0003c0 [ write sol eol count=960 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380201] cx88[0]:   iq f: 0x135aa2c0 [ arg #1 ]
Jan  8 02:29:15 stiles-desktop kernel: [  802.380204] cx88[0]: fifo: 0x00180c00 -> 0x183400
Jan  8 02:29:15 stiles-desktop kernel: [  802.380207] cx88[0]: ctrl: 0x00180400 -> 0x180460
Jan  8 02:29:15 stiles-desktop kernel: [  802.380210] cx88[0]:   ptr1_reg: 0x00182070
Jan  8 02:29:15 stiles-desktop kernel: [  802.380213] cx88[0]:   ptr2_reg: 0x00180498
Jan  8 02:29:15 stiles-desktop kernel: [  802.380217] cx88[0]:   cnt1_reg: 0x00000045
Jan  8 02:29:15 stiles-desktop kernel: [  802.380220] cx88[0]:   cnt2_reg: 0x00000000
Jan  8 02:29:15 stiles-desktop kernel: [  802.380237] cx88[0]/0: [e0025a80/0] timeout - dma=0x13626000
Jan  8 02:29:15 stiles-desktop kernel: [  802.380243] cx88[0]/0: [e0025b40/1] timeout - dma=0x136a4000
Jan  8 02:29:15 stiles-desktop kernel: [  802.380246] cx88[0]/0: [e0025c00/2] timeout - dma=0x13702000
Jan  8 02:29:15 stiles-desktop kernel: [  802.380249] cx88[0]/0: [e0025cc0/3] timeout - dma=0x13780000
Jan  8 02:29:15 stiles-desktop kernel: [  802.380252] cx88[0]/0: [e0025d80/4] timeout - dma=0x13000000
Jan  8 02:30:01 stiles-desktop /USR/SBIN/CRON[6995]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Jan  8 02:30:01 stiles-desktop /USR/SBIN/CRON[7009]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

==> /var/log/Xorg.0.log <==
(II) intel(0): Modeline "1600x1200"x70.0  190.25  1600 1712 1888 2176  1200 1201 1204 1249 -hsync +vsync (87.4 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) intel(0): EDID vendor "MEL", prod id 17472
(II) intel(0): EDID vendor "MEL", prod id 17472
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x1200"x0.0  229.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (106.2 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x85.0  149.43  1280 1376 1512 1744  960 961 964 1008 -hsync +vsync (85.7 kHz)
(II) intel(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) intel(0): Modeline "1600x1200"x70.0  190.25  1600 1712 1888 2176  1200 1201 1204 1249 -hsync +vsync (87.4 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) intel(0): EDID vendor "MEL", prod id 17472
(II) intel(0): EDID vendor "MEL", prod id 17472
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x1200"x0.0  229.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (106.2 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x85.0  149.43  1280 1376 1512 1744  960 961 964 1008 -hsync +vsync (85.7 kHz)
(II) intel(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) intel(0): Modeline "1600x1200"x70.0  190.25  1600 1712 1888 2176  1200 1201 1204 1249 -hsync +vsync (87.4 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) intel(0): EDID vendor "MEL", prod id 17472
(II) intel(0): EDID vendor "MEL", prod id 17472
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x1200"x0.0  229.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (106.2 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x85.0  149.43  1280 1376 1512 1744  960 961 964 1008 -hsync +vsync (85.7 kHz)
(II) intel(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) intel(0): Modeline "1600x1200"x70.0  190.25  1600 1712 1888 2176  1200 1201 1204 1249 -hsync +vsync (87.4 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) intel(0): EDID vendor "MEL", prod id 17472
(II) intel(0): xf86BindGARTMemory: bind key 6 at 0x07540000 (pgoffset 30016)
(WW) cx88 IR (Pinnacle PCTV HD 800i): unable to handle keycode 370
(WW) cx88 IR (Pinnacle PCTV HD 800i): unable to handle keycode 403
(WW) cx88 IR (Pinnacle PCTV HD 800i): unable to handle keycode 402
(II) intel(0): xf86UnbindGARTMemory: unbind key 6
(II) intel(0): xf86BindGARTMemory: bind key 6 at 0x07540000 (pgoffset 30016)
(II) intel(0): xf86UnbindGARTMemory: unbind key 6

==> /home/stiles/.xsession-errors <==
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Unable to create /home/stiles/.dbus/session-bus
x-session-manager[6476]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/stiles/.config/metacity/sessions/10bae0ec8788110638123141011248069200000064760003.ms: Failed to open file '/home/stiles/.config/metacity/sessions/10bae0ec8788110638123141011248069200000064760003.ms': No such file or directory
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:6597): WARNING **: Unable to add monitor: Not supported

(gnome-panel:6594): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 26
x-session-manager[6476]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Failure: Module initalization failed
starting HAL detection for ac adaptors...none found
Throttle level is 0

** (nm-applet:6656): WARNING **: No connections defined
evolution-alarm-notify-Message: Setting timeout for 77869 1231488000 1231410131
evolution-alarm-notify-Message:  Fri Jan  9 00:00:00 2009

evolution-alarm-notify-Message:  Thu Jan  8 02:22:11 2009

Window manager warning: Invalid WM_TRANSIENT_FOR window 0xa2 specified for 0x1e000fe ().
6594
  PID TTY          TIME CMD
 6536 ?        00:00:00 pulseaudio
Window manager warning: Invalid WM_TRANSIENT_FOR window 0xa2 specified for 0x1e00423 ().
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-01-08 02:25:19.832 Using runtime prefix = /usr
2009-01-08 02:25:20.307 XScreenSaver support enabled
2009-01-08 02:25:20.309 DPMS is active.
2009-01-08 02:25:20.310 Empty LocalHostName.
2009-01-08 02:25:20.311 Using localhost value of stiles-desktop
2009-01-08 02:25:20.350 New DB connection, total: 1
2009-01-08 02:25:20.357 Connected to database 'mythconverg' at host: localhost
2009-01-08 02:25:20.360 Closing DB connection named 'DBManager0'
2009-01-08 02:25:20.367 Primary screen 0.
2009-01-08 02:25:20.369 Connected to database 'mythconverg' at host: localhost
2009-01-08 02:25:20.372 Using screen 0, 1024x768 at 0,0
Can't retrieve password by Login Manager
wot_cache.add_target: caching google.com
google.com: 0: (r, c) = (93, 80)
google.com: 0: (i) = (0)
google.com: 0: (l) = (0)
google.com: 0: (t) = (98)
google.com: 1: (r, c) = (94, 79)
google.com: 1: (i) = (0)
google.com: 1: (l) = (0)
google.com: 1: (t) = (98)
google.com: 2: (r, c) = (93, 77)
google.com: 2: (i) = (0)
google.com: 2: (l) = (0)
google.com: 2: (t) = (97)
google.com: 4: (r, c) = (93, 75)
google.com: 4: (i) = (0)
google.com: 4: (l) = (0)
google.com: 4: (t) = (97)

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       27G  6.4G   20G  26% /
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M  344K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  2.9M 1006M   1% /dev
tmpfs                1008M  368K 1008M   1% /dev/shm
/dev/sda2             233G  104G  130G  45% /host
lrm                  1008M  2.0M 1006M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda2             233G  104G  130G  45% /media/c

==> uname -a <==
Linux stiles-desktop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

==> lsusb <==
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f9:01bb Brother Industries, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 2233:f102 RadioShack Corporation 
Bus 002 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

==> lshw <==
computer
    description: Space-saving Computer
    product: Dimension 2400
    vendor: Dell Computer Corporation
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=space-saving cpus=1 power-on_password=enabled uuid=44454C4C-3100-1046-8059-C8C04F573431
  *-core
       description: Motherboard
       product: 0C2425
       vendor: Dell Computer Corp.
       physical id: 0
       version: A01
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A05 (12/02/2003)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.50GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2500MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 128KiB
             capacity: 128KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_1
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_2
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant Systems, Inc.
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-multimedia:0
                description: Multimedia video controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder
                vendor: Conexant Systems, Inc.
                physical id: 6
                bus info: pci@0000:01:06.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: vpd pm bus_master cap_list
                configuration: driver=cx8800 latency=64 maxlatency=55 mingnt=20 module=cx8800
           *-multimedia:1
                description: Multimedia controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port]
                vendor: Conexant Systems, Inc.
                physical id: 6.1
                bus info: pci@0000:01:06.1
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=cx88_audio latency=64 maxlatency=255 mingnt=4 module=cx88_alsa
           *-multimedia:2
                description: Multimedia controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
                vendor: Conexant Systems, Inc.
                physical id: 6.2
                bus info: pci@0000:01:06.2
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=cx88-mpeg driver manager latency=64 maxlatency=88 mingnt=6 module=cx8802
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 9
                bus info: pci@0000:01:09.0
                logical name: eth0
                version: 01
                serial: [REMOVED]
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=[REMOVED] latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: WDC WD2500AAJB-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 00.0
                serial: [REMOVED]
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=3c162f0d
              *-volume:0
                   description: Windows FAT volume
                   vendor: Dell 4.1
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT16
                   serial: [REMOVED]
                   size: 39MiB
                   capacity: 39MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=DellUtility
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /host
                   logical name: /boot
                   logical name: /media/c
                   version: 3.1
                   serial: [REMOVED]
                   size: 232GiB
                   capacity: 232GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-03-25 17:23:41 filesystem=ntfs label=DRV2_VOL2 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-disk:1
                description: ATA Disk
                product: ST340014A
                vendor: Seagate
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 3.16
                serial: [REMOVED]
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9dc96e9e
              *-volume:0
                   description: Windows FAT volume
                   vendor: Dell 4.1
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: FAT16
                   serial: [REMOVED]
                   size: 39MiB
                   capacity: 39MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=DellUtility
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   version: 3.1
                   serial: [REMOVED]
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-03-26 00:23:07 filesystem=ntfs state=clean
           *-cdrom:0
                description: DVD reader
                product: CD-RW  CRX320EE
                vendor: SONY
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: RYK4
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: SCSI CD-ROM
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/scd1
                logical name: /dev/sr1
                capabilities: audio
                configuration: status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

