---
title: "Major hard crashing with Rosegarden"
date: 2013-12-04
forum: Multimedia Software
---

### Post by junglejuice on 2013-12-04
Hi :)
can someone pls point me in the right direction *preferably* to figure out why rosegarden is crashing soooooo much for me. i'm using it with qjackctl on ubuntu 12.04 x64, a lexicon omega sound device, periods/buffer @3 and frames/period @128 on an 8 core i7 with 8 GB Ram (so these settings shouldn't really be a problem right?) and i'm getting a gigaton of errors that look something like this
```
Wed Dec  4 21:51:41 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:51:41 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:51:41 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 21:51:41 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:51:41 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 21:51:41 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:51:42.162 XRUN callback (2 skipped).
21:51:44.610 XRUN callback (72).
Wed Dec  4 21:51:44 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:51:44 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:51:46.632 XRUN callback (73).
Wed Dec  4 21:51:46 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:51:46 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:51:49.330 XRUN callback (74).
Wed Dec  4 21:51:49 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:51:49 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:51:51.618 XRUN callback (75).
Wed Dec  4 21:51:51 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:51:51 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:52:14.386 XRUN callback (76).
Wed Dec  4 21:52:14 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:52:14 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:53:08.534 XRUN callback (77).
21:53:14.980 XRUN callback (78).
Wed Dec  4 21:53:14 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:53:14 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:53:20.207 XRUN callback (79).
Wed Dec  4 21:53:20 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:53:20 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:53:28.035 XRUN callback (80).
Wed Dec  4 21:53:28 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:53:28 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:53:43.923 XRUN callback (81).
Wed Dec  4 21:53:43 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:53:43 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:53:51.220 XRUN callback (82).
Wed Dec  4 21:53:51 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:53:51 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:53:51 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:53:51 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:53:52.304 XRUN callback (1 skipped).
21:53:54.270 XRUN callback (84).
Wed Dec  4 21:53:54 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:53:54 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:53:56.660 XRUN callback (85).
Wed Dec  4 21:53:56 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:53:56 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:02.569 XRUN callback (86).
Wed Dec  4 21:54:02 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:02 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:07.634 XRUN callback (87).
Wed Dec  4 21:54:07 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:07 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:07 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:07 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:08.318 XRUN callback (1 skipped).
21:54:09.540 XRUN callback (89).
Wed Dec  4 21:54:09 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:09 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:09 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:09 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:10.321 XRUN callback (1 skipped).
21:54:13.911 XRUN callback (91).
Wed Dec  4 21:54:13 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:13 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:13 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:13 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:14.325 XRUN callback (3 skipped).
Wed Dec  4 21:54:14 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:14 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:14 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:14 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:14 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:14 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:14 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:14 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:16.295 XRUN callback (97).
21:54:16.327 XRUN callback (2 skipped).
Wed Dec  4 21:54:16 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:16 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:18.073 XRUN callback (98).
Wed Dec  4 21:54:18 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:18 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:20.472 XRUN callback (99).
Wed Dec  4 21:54:20 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:20 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:20 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:20 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:21 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:21 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:22.334 XRUN callback (3 skipped).
Wed Dec  4 21:54:22 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:22 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:23.194 XRUN callback (103).
Wed Dec  4 21:54:23 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 21:54:23 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:24.268 XRUN callback (104).
21:54:24.336 XRUN callback (1 skipped).
Wed Dec  4 21:54:24 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:24 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:24 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:24 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:25.621 XRUN callback (106).
Wed Dec  4 21:54:25 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:25 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:26.338 XRUN callback (1 skipped).
Wed Dec  4 21:54:26 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:26 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:26 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:26 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:28.341 XRUN callback (1 skipped).
21:54:30.160 XRUN callback (109).
Wed Dec  4 21:54:30 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:30 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:30 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:30 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:30 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:30 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:32.346 XRUN callback (1 skipped).
21:54:34.760 XRUN callback (112).
Wed Dec  4 21:54:34 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 21:54:34 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:34 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 21:54:34 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:36.350 XRUN callback (1 skipped).
21:54:37.119 XRUN callback (114).
Wed Dec  4 21:54:37 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:37 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:46.890 XRUN callback (115).
Wed Dec  4 21:54:46 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:46 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:54.221 XRUN callback (116).
21:54:54.368 XRUN callback (1 skipped).
Wed Dec  4 21:54:54 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:54 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:54 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:54 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:55.995 XRUN callback (118).
Wed Dec  4 21:54:55 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:55 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:56 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:56 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:56 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:56 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:56 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:56 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:54:56 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:54:56 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:54:58.371 XRUN callback (3 skipped).
21:55:03.747 XRUN callback (123).
Wed Dec  4 21:55:03 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:55:03 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:55:04.810 XRUN callback (124).
Wed Dec  4 21:55:04 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:55:04 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:55:05 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:55:05 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:55:06.378 XRUN callback (1 skipped).
21:55:07.474 XRUN callback (126).
Wed Dec  4 21:55:07 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:55:07 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:55:07 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:55:07 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:55:07 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:55:07 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:55:08 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:55:08 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:55:08 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:55:08 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:55:08.382 XRUN callback (4 skipped).
21:55:37.991 XRUN callback (131).
Wed Dec  4 21:55:37 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:55:37 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:55:39.216 XRUN callback (132).
Wed Dec  4 21:55:39 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:55:39 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:55:39 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:55:39 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:55:40.415 XRUN callback (1 skipped).
21:55:51.052 XRUN callback (134).
Wed Dec  4 21:55:51 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:55:51 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:56:14.684 XRUN callback (135).
Wed Dec  4 21:56:14 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:56:14 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:56:15.821 XRUN callback (136).
Wed Dec  4 21:56:15 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 21:56:15 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:56:16.450 XRUN callback (1 skipped).
21:56:41.221 XRUN callback (137).
Wed Dec  4 21:56:41 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:56:41 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:56:41 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:56:41 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:56:41 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:56:41 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:56:41 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:56:41 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:56:41 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:56:41 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:56:41 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:56:41 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:56:42.473 XRUN callback (5 skipped).
21:56:48.985 XRUN callback (143).
Wed Dec  4 21:56:48 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:56:48 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:56:50.903 XRUN callback (144).
Wed Dec  4 21:56:50 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:56:50 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:56:50 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 21:56:50 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:56:52.483 XRUN callback (1 skipped).
21:57:00.749 XRUN callback (146).
Wed Dec  4 21:57:00 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:00 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:57:02.457 XRUN callback (147).
21:57:02.493 XRUN callback (2 skipped).
Wed Dec  4 21:57:02 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 21:57:02 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:57:02 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:02 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:57:30.447 XRUN callback (149).
21:57:30.517 XRUN callback (1 skipped).
Wed Dec  4 21:57:30 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:30 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:57:30 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:30 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:57:30 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 21:57:30 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:57:33.034 XRUN callback (152).
Wed Dec  4 21:57:33 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:33 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:57:33 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:33 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:57:34.523 XRUN callback (1 skipped).
21:57:34.636 XRUN callback (154).
Wed Dec  4 21:57:34 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:34 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:57:35.733 XRUN callback (155).
Wed Dec  4 21:57:35 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 21:57:35 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:57:35 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:35 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:57:35 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:35 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:57:36.527 XRUN callback (3 skipped).
21:57:37.532 XRUN callback (158).
Wed Dec  4 21:57:37 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:37 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:57:37 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 21:57:37 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:57:38.531 XRUN callback (1 skipped).
21:57:41.732 XRUN callback (160).
Wed Dec  4 21:57:41 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:41 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:57:45.142 XRUN callback (161).
Wed Dec  4 21:57:45 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:45 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:57:45 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:45 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:57:46.559 XRUN callback (1 skipped).
21:57:46.640 XRUN callback (163).
Wed Dec  4 21:57:46 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:46 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:57:46 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:46 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:57:47 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:47 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:57:48.562 XRUN callback (2 skipped).
21:57:49.061 XRUN callback (166).
Wed Dec  4 21:57:49 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:49 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:57:49 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:49 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:57:50.565 XRUN callback (2 skipped).
Wed Dec  4 21:57:50 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:50 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:57:52.819 XRUN callback (169).
Wed Dec  4 21:57:52 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:52 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:57:52 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:52 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:57:54.569 XRUN callback (1 skipped).
21:57:56.699 XRUN callback (171).
Wed Dec  4 21:57:56 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:56 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:57:59.235 XRUN callback (172).
Wed Dec  4 21:57:59 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:57:59 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:58:03.108 XRUN callback (173).
Wed Dec  4 21:58:03 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:58:03 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:58:04 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:58:04 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:58:04.577 XRUN callback (1 skipped).
Wed Dec  4 21:58:04 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:58:04 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:58:04 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:58:04 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:58:05 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:58:05 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:58:06.580 XRUN callback (2 skipped).
21:58:08.258 XRUN callback (178).
21:58:08.583 XRUN callback (1 skipped).
Wed Dec  4 21:58:08 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:58:08 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:58:08 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:58:08 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:58:12.605 XRUN callback (180).
Wed Dec  4 21:58:12 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:58:12 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:58:12 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:58:12 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:58:14.617 XRUN callback (1 skipped).
21:59:24.776 XRUN callback (182).
Wed Dec  4 21:59:24 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:59:24 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:59:34.005 XRUN callback (183).
Wed Dec  4 21:59:34 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:59:34 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 21:59:34 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 21:59:34 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
21:59:34.680 XRUN callback (1 skipped).
22:00:21.637 XRUN callback (185).
Wed Dec  4 22:00:21 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:00:21 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:00:25.356 XRUN callback (186).
Wed Dec  4 22:00:25 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:00:25 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:00:26.636 XRUN callback (187).
22:00:26.729 XRUN callback (1 skipped).
Wed Dec  4 22:00:26 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:00:26 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:00:59.716 XRUN callback (188).
Wed Dec  4 22:00:59 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:00:59 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:01:14.802 XRUN callback (189).
Wed Dec  4 22:01:14 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:01:14 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:01:35.009 XRUN callback (190).
Wed Dec  4 22:01:35 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:01:35 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:01:35 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:01:35 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:01:35 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:01:35 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:01:36.812 XRUN callback (2 skipped).
22:02:17.476 XRUN callback (193).
Wed Dec  4 22:02:17 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:17 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:02:29.108 XRUN callback (194).
Wed Dec  4 22:02:29 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:02:29 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:02:30.808 XRUN callback (195).
22:02:30.861 XRUN callback (1 skipped).
Wed Dec  4 22:02:30 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:30 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:02:33.245 XRUN callback (196).
Wed Dec  4 22:02:33 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:33 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:02:33 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:33 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:02:33 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:33 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:02:34.865 XRUN callback (3 skipped).
Wed Dec  4 22:02:34 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:34 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:02:40.977 XRUN callback (200).
Wed Dec  4 22:02:40 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:02:40 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:02:42.350 XRUN callback (201).
22:02:42.872 XRUN callback (4 skipped).
Wed Dec  4 22:02:42 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:42 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:02:42 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:42 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:02:42 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:42 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:02:42 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:02:42 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:02:56.392 XRUN callback (205).
22:02:56.884 XRUN callback (2 skipped).
Wed Dec  4 22:02:56 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:02:56 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:02:56 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:56 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:02:56 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:56 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:02:58.018 XRUN callback (208).
Wed Dec  4 22:02:58 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:58 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:02:58 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:58 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:02:58.886 XRUN callback (5 skipped).
Wed Dec  4 22:02:58 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:58 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:02:58 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:58 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:02:58 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:58 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:02:58 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:02:58 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:00.658 XRUN callback (214).
Wed Dec  4 22:03:00 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:00 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:06.925 XRUN callback (215).
Wed Dec  4 22:03:06 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:06 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:08.501 XRUN callback (216).
22:03:08.895 XRUN callback (2 skipped).
Wed Dec  4 22:03:08 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:08 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:03:08 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:08 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:11.471 XRUN callback (218).
Wed Dec  4 22:03:11 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:11 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:12.605 XRUN callback (219).
22:03:12.899 XRUN callback (1 skipped).
Wed Dec  4 22:03:12 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:12 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:16.840 XRUN callback (220).
Wed Dec  4 22:03:16 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:03:16 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:18.080 XRUN callback (221).
Wed Dec  4 22:03:18 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:18 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:20.729 XRUN callback (222).
Wed Dec  4 22:03:20 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:20 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:24.323 XRUN callback (223).
Wed Dec  4 22:03:24 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:24 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:28.024 XRUN callback (224).
Wed Dec  4 22:03:28 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:28 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:30.464 XRUN callback (225).
Wed Dec  4 22:03:30 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:03:30 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:31.950 XRUN callback (226).
Wed Dec  4 22:03:31 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:31 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:35.787 XRUN callback (227).
Wed Dec  4 22:03:35 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:35 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:36.921 XRUN callback (1 skipped).
Wed Dec  4 22:03:36 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:03:36 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:03:36 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:36 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:39.456 XRUN callback (230).
Wed Dec  4 22:03:39 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:39 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:03:39 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:39 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:40.776 XRUN callback (232).
22:03:40.925 XRUN callback (2 skipped).
Wed Dec  4 22:03:40 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:40 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:03:41 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:41 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:03:41 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:03:41 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:42.927 XRUN callback (3 skipped).
Wed Dec  4 22:03:42 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:42 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:03:42 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:42 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:03:43 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:43 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:03:43 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:03:43 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:03:44 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:44 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:44.929 XRUN callback (2 skipped).
22:03:46.617 XRUN callback (240).
Wed Dec  4 22:03:46 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:03:46 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:48.254 XRUN callback (241).
Wed Dec  4 22:03:48 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:48 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:03:59.483 XRUN callback (242).
Wed Dec  4 22:03:59 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:59 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:03:59 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:03:59 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:04:00.939 XRUN callback (1 skipped).
22:04:07.070 XRUN callback (244).
Wed Dec  4 22:04:07 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:04:07 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:04:13.954 XRUN callback (245).
Wed Dec  4 22:04:13 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:04:13 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:04:15.803 XRUN callback (246).
Wed Dec  4 22:04:15 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:04:15 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:04:25.774 XRUN callback (247).
Wed Dec  4 22:04:25 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:04:25 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:04:26.959 XRUN callback (3 skipped).
Wed Dec  4 22:04:26 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:04:26 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:04:26 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:04:26 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:04:26 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:04:26 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:04:29.114 XRUN callback (251).
Wed Dec  4 22:04:29 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:04:29 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:04:33.599 XRUN callback (252).
Wed Dec  4 22:04:33 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:04:33 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:05:04.753 XRUN callback (253).
22:05:04.977 XRUN callback (1 skipped).
Wed Dec  4 22:05:04 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:04 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:05:04 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:04 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:05:05 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:05 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:05:05 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:05 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:05:05 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:05 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:05:05 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:05:05 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:05:05 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:05 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:05:05 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:05 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:05:06 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:06 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:05:06 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:06 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:05:06 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:06 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:05:06 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:06 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:05:06.980 XRUN callback (9 skipped).
22:05:10.963 XRUN callback (265).
Wed Dec  4 22:05:10 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:10 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:05:11 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:11 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:05:15.653 XRUN callback (267).
Wed Dec  4 22:05:15 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:15 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:05:15 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:15 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:05:16.989 XRUN callback (1 skipped).
22:05:18.732 XRUN callback (269).
Wed Dec  4 22:05:18 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:05:18 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:05:21.893 XRUN callback (270).
Wed Dec  4 22:05:21 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:21 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:05:27.933 XRUN callback (271).
Wed Dec  4 22:05:27 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:27 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:05:27 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:27 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:05:29.001 XRUN callback (1 skipped).
22:05:54.597 XRUN callback (273).
Wed Dec  4 22:05:54 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:54 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:05:59.823 XRUN callback (274).
Wed Dec  4 22:05:59 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:05:59 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:06:01.033 XRUN callback (1 skipped).
Wed Dec  4 22:06:00 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:06:00 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:06:01.849 XRUN callback (276).
Wed Dec  4 22:06:01 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:06:01 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:06:05.057 XRUN callback (277).
Wed Dec  4 22:06:05 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:06:05 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:06:05 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:06:05 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:06:07.040 XRUN callback (1 skipped).
22:06:15.078 XRUN callback (279).
Wed Dec  4 22:06:15 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:06:15 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:06:15 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:06:15 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:06:17.052 XRUN callback (1 skipped).
22:06:30.316 XRUN callback (281).
22:06:31.067 XRUN callback (2 skipped).
Wed Dec  4 22:06:30 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:06:30 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:06:30 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:06:30 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:06:30 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:06:30 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:06:49.072 XRUN callback (284).
Wed Dec  4 22:06:49 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:06:49 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:06:50.540 XRUN callback (285).
Wed Dec  4 22:06:50 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:06:50 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:06:51 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:06:51 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:07:12.771 XRUN callback (287).
Wed Dec  4 22:07:12 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:07:12 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:07:13 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:07:13 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:07:14.849 XRUN callback (289).
22:07:15.107 XRUN callback (1 skipped).
Wed Dec  4 22:07:14 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:07:14 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:07:15.982 JACK connection graph change.
22:07:16.002 ALSA connection graph change.
22:07:16.110 JACK connection change.
22:07:16.112 ALSA connection change.
Wed Dec  4 22:07:15 2013: New client 'jack_rack' with PID 6487
22:07:18.178 XRUN callback (290).
22:07:19.117 XRUN callback (1 skipped).
Wed Dec  4 22:07:18 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:07:18 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:07:18 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:07:21.501 XRUN callback (292).
Wed Dec  4 22:07:21 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:07:21 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:07:21 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:07:21 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:07:21 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:07:21 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:07:21 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:07:21 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:07:21 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:07:22.929 XRUN callback (298).
22:07:23.121 XRUN callback (7 skipped).
Wed Dec  4 22:07:22 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:07:22 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:07:22 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:07:24.658 XRUN callback (300).
22:07:25.123 XRUN callback (5 skipped).
Wed Dec  4 22:07:24 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:07:24 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:07:24 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:07:24 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:07:24 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:07:24 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:07:24 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:07:24 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:07:24 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:07:29.948 XRUN callback (306).
Wed Dec  4 22:07:29 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:07:29 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:07:29 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:07:31.130 XRUN callback (1 skipped).
22:07:52.134 JACK connection change.
22:07:52.177 XRUN callback (308).
Wed Dec  4 22:07:52 2013: Connecting 'rosegarden:master out L' to 'jack_rack:in_1'
Wed Dec  4 22:07:52 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:07:52 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:07:52 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:07:53.153 XRUN callback (1 skipped).
22:07:56.747 JACK connection change.
Wed Dec  4 22:07:56 2013: Connecting 'rosegarden:master out R' to 'jack_rack:in_2'
22:07:59.413 XRUN callback (310).
Wed Dec  4 22:07:59 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:07:59 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:07:59 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:08:01.163 XRUN callback (1 skipped).
22:08:02.615 XRUN callback (312).
22:08:03.166 XRUN callback (1 skipped).
Wed Dec  4 22:08:02 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:08:02 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:08:02 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:08:05.187 XRUN callback (314).
Wed Dec  4 22:08:05 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:08:05 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 2[0m
Wed Dec  4 22:08:05 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:08:07.172 XRUN callback (1 skipped).
22:08:10.849 XRUN callback (316).
Wed Dec  4 22:08:10 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:08:10 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:08:10 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:08:11.178 XRUN callback (1 skipped).
22:08:15.519 JACK connection change.
Wed Dec  4 22:08:15 2013: Connecting 'jack_rack:out_1' to 'system:playback_1'
22:08:19.520 JACK connection change.
Wed Dec  4 22:08:19 2013: Connecting 'jack_rack:out_2' to 'system:playback_2'
22:08:24.595 XRUN callback (318).
Wed Dec  4 22:08:24 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:08:24 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:08:24 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:08:24 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:08:24 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:08:24 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:08:25.195 XRUN callback (3 skipped).
22:08:27.547 XRUN callback (322).
Wed Dec  4 22:08:27 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:08:27 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:08:27 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:08:29.200 XRUN callback (1 skipped).
22:08:30.128 XRUN callback (324).
Wed Dec  4 22:08:30 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:08:30 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:08:30 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:08:30 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:08:30 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:08:30 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:08:31.204 XRUN callback (5 skipped).
Wed Dec  4 22:08:31 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:08:31 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:08:31 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:08:32.859 XRUN callback (330).
Wed Dec  4 22:08:32 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:08:32 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:08:32 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:08:33.207 XRUN callback (1 skipped).
22:08:36.234 XRUN callback (332).
Wed Dec  4 22:08:36 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:08:36 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:08:36 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:08:37.212 XRUN callback (1 skipped).
22:08:39.622 XRUN callback (334).
Wed Dec  4 22:08:39 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:08:39 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:08:39 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:08:41.217 XRUN callback (1 skipped).
22:08:56.923 XRUN callback (336).
Wed Dec  4 22:08:56 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:08:56 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:08:56 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:08:57.232 XRUN callback (1 skipped).
22:09:14.505 XRUN callback (338).
Wed Dec  4 22:09:14 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:09:14 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:09:14 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:09:14 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:09:14 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:09:14 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:09:15.250 XRUN callback (3 skipped).
22:09:15.812 XRUN callback (342).
Wed Dec  4 22:09:15 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:09:15 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:09:15 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:09:17.253 XRUN callback (1 skipped).
22:09:19.269 XRUN callback (344).
Wed Dec  4 22:09:19 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:09:19 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:09:19 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:09:21.258 XRUN callback (1 skipped).
22:09:25.756 XRUN callback (346).
Wed Dec  4 22:09:25 2013: [1m[31mERROR: JackEngine::XRun: client rosegarden finished after current callback[0m
Wed Dec  4 22:09:25 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:09:25 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:09:27.266 XRUN callback (1 skipped).
22:09:40.502 XRUN callback (348).
Wed Dec  4 22:09:40 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:09:40 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:09:40 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:09:40 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:09:40 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:09:40 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:09:41.278 XRUN callback (3 skipped).
22:09:44.785 XRUN callback (352).
Wed Dec  4 22:09:44 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:09:44 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:09:44 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:09:45.283 XRUN callback (1 skipped).
22:09:54.844 XRUN callback (354).
Wed Dec  4 22:09:54 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:09:54 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:09:54 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:09:55.294 XRUN callback (1 skipped).
22:10:25.689 XRUN callback (356).
Wed Dec  4 22:10:25 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:10:25 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 2[0m
Wed Dec  4 22:10:25 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:10:27.325 XRUN callback (1 skipped).
22:10:34.333 XRUN callback (358).
Wed Dec  4 22:10:34 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:10:34 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:10:34 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:10:35.332 XRUN callback (1 skipped).
22:10:52.804 XRUN callback (360).
Wed Dec  4 22:10:52 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:10:52 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:10:52 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:10:52 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:10:52 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:10:52 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:10:53.352 XRUN callback (3 skipped).
22:11:28.641 XRUN callback (364).
Wed Dec  4 22:11:28 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:11:28 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:11:28 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:11:29.385 XRUN callback (1 skipped).
22:11:30.641 XRUN callback (366).
Wed Dec  4 22:11:30 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:11:30 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:11:30 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:11:31.387 XRUN callback (1 skipped).
22:11:38.492 XRUN callback (368).
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:11:38 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:11:39.395 XRUN callback (9 skipped).
22:11:40.622 XRUN callback (378).
Wed Dec  4 22:11:40 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:11:40 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:11:40 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:11:41.401 XRUN callback (1 skipped).
Wed Dec  4 22:11:41 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:11:41 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:11:41 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:11:41 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:11:41 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:11:41 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:11:43.406 XRUN callback (3 skipped).
22:11:43.889 XRUN callback (384).
Wed Dec  4 22:11:43 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:11:43 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:11:43 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:11:43 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:11:43 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:11:43 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:11:44 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:11:44 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:11:44 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:11:45.409 XRUN callback (5 skipped).
22:11:45.817 XRUN callback (390).
Wed Dec  4 22:11:45 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:11:45 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:11:45 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:11:45 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:11:45 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:11:45 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:11:45 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:11:45 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:11:45 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:11:47.413 XRUN callback (5 skipped).
22:11:59.996 XRUN callback (396).
Wed Dec  4 22:11:59 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:11:59 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:11:59 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:12:01.427 XRUN callback (1 skipped).
22:13:28.340 XRUN callback (398).
Wed Dec  4 22:13:28 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:13:28 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:13:28 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:13:29.512 XRUN callback (1 skipped).
22:13:35.145 XRUN callback (400).
Wed Dec  4 22:13:35 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:13:35 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:13:35 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:13:35.518 XRUN callback (1 skipped).
22:13:51.011 XRUN callback (402).
Wed Dec  4 22:13:51 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:13:51 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:13:51 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:13:51 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:13:51 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:13:51 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:13:51.534 XRUN callback (3 skipped).
22:14:02.321 XRUN callback (406).
Wed Dec  4 22:14:02 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:14:02 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:14:02 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:14:03.545 XRUN callback (1 skipped).
22:14:08.178 XRUN callback (408).
Wed Dec  4 22:14:08 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:08 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:14:08 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:14:08 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:08 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:14:08 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:14:09 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:09 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 2[0m
Wed Dec  4 22:14:09 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:14:09.550 XRUN callback (5 skipped).
Wed Dec  4 22:14:09 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:09 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:14:09 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:14:09 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:14:09 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:14:09 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:14:10 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:10 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:14:10 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:14:11.548 XRUN callback (420).
22:14:11.553 XRUN callback (7 skipped).
Wed Dec  4 22:14:11 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:11 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:14:11 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:14:12 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:14:12 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:14:12 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:14:12 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:12 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:14:12 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:14:13.557 XRUN callback (5 skipped).
Wed Dec  4 22:14:13 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:14:13 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:14:13 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:14:15.873 XRUN callback (428).
Wed Dec  4 22:14:15 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:15 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:14:15 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:14:16 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:14:16 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:14:16 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:14:17.561 XRUN callback (3 skipped).
22:14:21.910 XRUN callback (432).
Wed Dec  4 22:14:21 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:21 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:14:21 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:14:23.567 XRUN callback (1 skipped).
22:14:35.612 XRUN callback (434).
Wed Dec  4 22:14:35 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:35 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:14:35 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:14:36.855 XRUN callback (436).
Wed Dec  4 22:14:36 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:36 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:14:36 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:14:37.581 XRUN callback (3 skipped).
22:14:47.368 XRUN callback (438).
22:14:47.590 XRUN callback (1 skipped).
Wed Dec  4 22:14:47 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:47 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 2[0m
Wed Dec  4 22:14:47 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:14:49.913 XRUN callback (440).
Wed Dec  4 22:14:49 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:49 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:14:49 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:14:50 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:14:50 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:14:50 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:14:51.594 XRUN callback (3 skipped).
22:14:51.896 XRUN callback (444).
Wed Dec  4 22:14:51 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:51 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:14:51 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:14:51 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:51 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 2[0m
Wed Dec  4 22:14:51 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:14:53.598 XRUN callback (3 skipped).
22:14:59.875 XRUN callback (448).
Wed Dec  4 22:14:59 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:14:59 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 2[0m
Wed Dec  4 22:14:59 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:15:01.607 XRUN callback (1 skipped).
22:15:03.128 XRUN callback (450).
Wed Dec  4 22:15:03 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:15:03 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:15:03 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:15:03.610 XRUN callback (1 skipped).
22:15:04.875 XRUN callback (452).
Wed Dec  4 22:15:04 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:15:04 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:15:04 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:15:05.613 XRUN callback (1 skipped).
22:15:06.887 XRUN callback (454).
Wed Dec  4 22:15:06 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:15:06 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:15:06 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:15:07.617 XRUN callback (1 skipped).
Wed Dec  4 22:15:07 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:15:07 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:15:07 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:15:09.620 XRUN callback (1 skipped).
22:15:12.492 XRUN callback (458).
Wed Dec  4 22:15:12 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:15:12 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:15:12 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:15:13.625 XRUN callback (1 skipped).
22:15:16.630 XRUN callback (460).
Wed Dec  4 22:15:16 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:15:16 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:15:16 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:15:17.629 XRUN callback (1 skipped).
22:15:21.159 XRUN callback (462).
Wed Dec  4 22:15:21 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:15:21 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:15:21 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:15:21.633 XRUN callback (1 skipped).
Wed Dec  4 22:15:21 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:15:21 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:15:21 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:15:21 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:15:21 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:15:21 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:15:23.636 XRUN callback (3 skipped).
22:15:35.680 XRUN callback (468).
Wed Dec  4 22:15:35 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:15:35 2013: [1m[31mERROR: JackEngine::XRun: client jack_rack finished after current callback[0m
Wed Dec  4 22:15:35 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:15:37.672 XRUN callback (1 skipped).
22:15:44.550 XRUN callback (470).
Wed Dec  4 22:15:44 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:15:44 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:15:44 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:15:45.681 XRUN callback (1 skipped).
22:15:46.547 XRUN callback (472).
Wed Dec  4 22:15:46 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:15:46 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:15:46 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:15:47.685 XRUN callback (1 skipped).
22:16:07.902 XRUN callback (474).
Wed Dec  4 22:16:07 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:16:07 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:16:07 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Wed Dec  4 22:16:08 2013: [1m[31mERROR: JackEngine::XRun: client rosegarden finished after current callback[0m
Wed Dec  4 22:16:08 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:16:08 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:16:09.715 XRUN callback (3 skipped).
22:16:11.781 XRUN callback (478).
Wed Dec  4 22:16:11 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 2[0m
Wed Dec  4 22:16:11 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:16:11 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
22:16:13.758 XRUN callback (1 skipped).
22:16:14.700 XRUN callback (480).
Wed Dec  4 22:16:14 2013: [1m[31mERROR: JackEngine::XRun: client = rosegarden was not run: state = 1[0m
Wed Dec  4 22:16:14 2013: [1m[31mERROR: JackEngine::XRun: client = jack_rack was not run: state = 1[0m
Wed Dec  4 22:16:14 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
```

---

