---
title: "get playback url should be local but cannot be found"
date: 2011-08-23
forum: Mythbuntu
---

### Post by tmfizzle on 2011-08-23
Hello, 
  I had 10.10 installed working flawlessly, then I decided to upgrade to 11.04 and have been having strange problems ever since.  I will start with the ones that are giving me the most trouble.

1.  I get 0 byte recordings on a regular basis, I check the logs and usually see ```
2011-08-23 01:30:02.429 ProgramInfo(1431_20110823010000.mpg), Error: GetPlaybackURL: '1431_20110823010000.mpg' should be local, but it can not be found.
2011-08-23 01:30:02.464 ProgramInfo(1431_20110823010000.mpg), Error: GetPlaybackURL: '1431_20110823010000.mpg' should be local, but it can not be found.

``` I was also seeing timeout tuning errors, but those seem to have been fixed with increasing the timeouts for channel lock and also setting quicktune to always.


2. Choppy audio playback
```
2011-08-23 08:00:23.648 AFD: Opened codec 0x1f2ad40, id(MPEG2VIDEO) type(Video)
2011-08-23 08:00:23.688 AFD: codec AC3 has 2 channels
2011-08-23 08:00:23.724 AFD: Opened codec 0x1f25ee0, id(AC3) type(Audio)
2011-08-23 08:03:55.441 [ac3 @ 0x7fb3970db580]frame CRC mismatch
2011-08-23 08:03:55.494 [ac3 @ 0x7fb3970db580]frame sync error
2011-08-23 08:03:55.530 AFD Error: Unknown audio decoding error
2011-08-23 08:10:15.199 RingBuf(/myth/recordings/1131_20110823073000.mpg): Waited 1.0 seconds for data
                        to become available... 27396 < 32768
2011-08-23 08:10:16.132 [ac3 @ 0x7fb3970db580]incomplete frame

``` and also ```
2011-08-20 18:31:10.799 [ac3 @ 0x7f07cc333580]frame sync error
2011-08-20 18:31:10.838 AFD Error: Unknown audio decoding error
2011-08-20 18:31:15.094 AFD: Audio stream changed

```

Backend
Core2duo 3.0g 4g ram HD Homerun Tuner

---

