---
title: "PVR-500 Records but Live TV fails"
date: 2010-10-26
forum: Mythbuntu
---

### Post by LorenzoS on 2010-10-26
I have a PVR-500, the dual tuner version of the PVR-150.  Tuner 1 is connected directly to the cable jack, Tuner 2 receives from my cable box.  Both successfully record with no problems.  Tuner 1 successfully plays live TV, but tuner 2 fails.  

Here is the portion of my mythbackend.log.  At 14:45:14 I start live tv with tuner1, which is successful.  Then at 14:45:29 I switched input to tuner2 which gave me a black screen on the frontend and the below errors in the backend log.

Any help or suggestions would be appreciated.

_Begin watching live TV on tuner1, works fine:_
```
2010-10-26 14:45:14.279 TVRec(1): Changing from None to WatchingLiveTV
2010-10-26 14:45:14.316 TVRec(1): HW Tuner: 1->1
2010-10-26 14:45:15.076 ProgramInfo(): Updated pathname '':'' -> '1002_20101026144514.mpg'
2010-10-26 14:45:15.092 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-10-26 14:45:15.108 ProgramInfo(): Updated pathname '':'' -> '1002_20101026144514.mpg'
2010-10-26 14:45:15.148 ProgramInfo(): Updated pathname '':'' -> '1002_20101026144514.mpg'
2010-10-26 14:45:16.929 RecBase(1:/dev/video0): GetKeyframePositions(1,9223372036854775807,#2) out of 3
2010-10-26 14:45:17.037 ProgramInfo(): Updated pathname '':'' -> '1002_20101026144514.mpg'
2010-10-26 14:45:17.093 ProgramInfo(): Updated pathname '':'' -> '1002_20101026144514.mpg'
2010-10-26 14:45:17.150 ProgramInfo(): Updated pathname '':'' -> '1002_20101026144514.mpg'
2010-10-26 14:45:17.207 ProgramInfo(): Updated pathname '':'' -> '1002_20101026144514.mpg'
2010-10-26 14:45:17.262 ProgramInfo(): Updated pathname '':'' -> '1002_20101026144514.mpg'
2010-10-26 14:45:29.455 ProgramInfo(): Updated pathname '':'' -> '1002_20101026144514.mpg'

```
_Attempt to switch input to tuner2, fails_
```
2010-10-26 14:45:29.456 TVRec(1): Changing from WatchingLiveTV to None
2010-10-26 14:45:29.458 ProgramInfo(1002_20101026144514.mpg), Error: Unknown type, recording width was 0
2010-10-26 14:45:29.594 ProgramInfo(): Updated pathname '':'' -> '1002_20101026144514.mpg'
2010-10-26 14:45:29.597 Finished recording The Talk: channel 1002
2010-10-26 14:45:29.643 ProgramInfo(): Updated pathname '':'' -> '1002_20101026144514.mpg'
2010-10-26 14:45:30.054 MainServer::ANN Playback
2010-10-26 14:45:30.055 adding: Uranus as a client (events: 0)
2010-10-26 14:45:30.057 TVRec(2): Changing from None to WatchingLiveTV
2010-10-26 14:45:30.061 TVRec(2): HW Tuner: 2->2
2010-10-26 14:45:31.226 ret_pid(0) child(13039) status(0x0)
2010-10-26 14:45:32.258 ret_pid(0) child(13039) status(0x0)
2010-10-26 14:45:33.297 ret_pid(0) child(13039) status(0x0)
2010-10-26 14:45:34.297 ret_pid(0) child(13039) status(0x0)
Audio input set to 0
2010-10-26 14:45:35.298 ret_pid(0) child(13039) status(0x0)
2010-10-26 14:45:36.298 ret_pid(0) child(13039) status(0x0)
Audio input set to 1
2010-10-26 14:45:37.069 ret_pid(13039) child(13039) status(0x0)
2010-10-26 14:45:37.070 External Tuning program exited with no error
2010-10-26 14:45:37.072 MainServer::ANN Playback
2010-10-26 14:45:37.073 adding: Uranus as a client (events: 0)
2010-10-26 14:45:37.282 ProgramInfo(): Updated pathname '':'' -> '1071_20101026144537.mpg'
2010-10-26 14:45:37.295 ProgramInfo(): Updated pathname '':'' -> '1071_20101026144537.mpg'
2010-10-26 14:45:37.300 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-10-26 14:45:37.302 ProgramInfo(): Updated pathname '':'' -> '1002_20101026144514.mpg'
2010-10-26 14:45:37.413 TVRec(2): Changing from WatchingLiveTV to None
2010-10-26 14:45:37.414 ProgramInfo(1071_20101026144537.mpg), Error: Unknown type, recording width was 0
*** glibc detected *** /usr/bin/mythbackend: malloc(): memory corruption: 0x0a062e39 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0x52ee591]
/lib/tls/i686/cmov/libc.so.6(+0x6e395)[0x52f1395]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x5c)[0x52f2f9c]
/usr/lib/nvidia-current/libGL.so.1(+0x33e80)[0xaa9e80]
```

---

### Post by LorenzoS on 2010-10-28
OK, I found my own problem when I saw this in my log:
```
2010-10-28 21:40:30.113 TVRec(2): Changing from None to WatchingLiveTV
2010-10-28 21:40:30.117 TVRec(2) Error: Start channel invalid, setting to '2' on input Composite 1 instead.
2010-10-28 21:40:30.121 ChannelBase(2): IsTunable(Composite 2,2) Requested non-existant input 'Composite 2':'-1'
```

I did not have the startup channel set to 3 in my capture card setup to the Composite In would work with the cable box input.  Setting it fixed the problem, although I don't understand why this did not cause an error on recordings, or why this error did not show up every time in my mythbackend.log.

---

