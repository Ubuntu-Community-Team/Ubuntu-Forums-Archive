---
title: "Qjacktl error after VLC video"
date: 2013-03-21
forum: Multimedia Software
---

### Post by stilllife on 2013-03-21
Hello, I am using Ubuntu 12.04 lowlatency with vlc and qjacktl. I routed vlc to jack but at the end of a video a costant noise comes out and this error is repeated on the log

```
JackAudioDriver::ProcessGraphAsyncMaster: Process error
```

then sometimes the noise stops, sometimes I need to kill qjacktl. 
The configuration of qjack is 

period 512, buffer 2, freq 44100, realtime, alsa.

Here the last piece of cat qtjackd.log | grep ERROR

```

Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackEngine::XRun: client = vlc_3984 was not run: state = 1
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackEngine::XRun: client = vlc_3984 was not run: state = 1
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:14 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackEngine::XRun: client = vlc_3984 was not run: state = 1
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackEngine::XRun: client = vlc_3984 was not run: state = 1
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackEngine::XRun: client = vlc_3984 was not run: state = 1
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: Cannot read socket fd = 16 err = Connection reset by peer
Fri Mar 22 00:27:15 2013: ERROR: NotifyClient fails name = vlc_3984 event = 18 val1 = 0 val2 = 0
Fri Mar 22 00:27:15 2013: ERROR: Cannot write socket fd = 16 err = Broken pipe
Fri Mar 22 00:27:15 2013: ERROR: Cannot write socket fd = 16 err = Broken pipe
Fri Mar 22 00:27:15 2013: ERROR: Cannot write socket fd = 16 err = Broken pipe
Fri Mar 22 00:27:15 2013: ERROR: Cannot write socket fd = 16 err = Broken pipe
Fri Mar 22 00:27:15 2013: ERROR: Cannot write socket fd = 16 err = Broken pipe
Fri Mar 22 00:27:15 2013: ERROR: Cannot write socket fd = 16 err = Broken pipe
Fri Mar 22 00:27:15 2013: ERROR: Cannot write socket fd = 16 err = Broken pipe
Fri Mar 22 00:27:15 2013: ERROR: Cannot read socket fd = 16 err = Broken pipe
Fri Mar 22 00:27:15 2013: ERROR: Could not read result
Fri Mar 22 00:27:15 2013: ERROR: NotifyClient fails name = vlc_3984 event = 18 val1 = 1 val2 = 0
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:15 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot read socket fd = -1 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: NotifyClient fails name = vlc_3984 event = 18 val1 = 0 val2 = 0
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: Cannot read socket fd = -1 err = Bad file descriptor
Fri Mar 22 00:27:16 2013: ERROR: NotifyClient fails name = vlc_3984 event = 18 val1 = 1 val2 = 0
Fri Mar 22 00:27:16 2013: ERROR: Failed to find port 'vlc_3984:out_1' to destroy
Fri Mar 22 00:27:16 2013: ERROR: Failed to find port 'vlc_3984:out_2' to destroy
Fri Mar 22 00:27:16 2013: ERROR: Unknown error...
Fri Mar 22 00:27:16 2013: ERROR: WARNING: 17 message buffer overruns!


```


Any idea? Thanks

---

