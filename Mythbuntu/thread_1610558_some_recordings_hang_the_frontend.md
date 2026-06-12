---
title: "some recordings hang the frontend"
date: 2010-10-31
forum: Mythbuntu
---

### Post by itlarson on 2010-10-31
There are a few specific shows, all on the same channel which hang the frontend.  It seems to happen at a specific point in the recording.  It requires killing the frontend to fix.  It started occuring after I installed a new divco fusion hdtv7 dual tuner.  HGere is the log from when it hangs:

2010-10-31 20:13:51.777 AO, ERROR: Audio buffer overflow, 24665089 audio samples lost!
2010-10-31 20:13:51.785 AO, ERROR: Audio buffer overflow, 24669185 audio samples lost!
2010-10-31 20:13:51.794 AO, ERROR: Audio buffer overflow, 24673281 audio samples lost!
2010-10-31 20:13:51.796 NVP(1): Prebuffer wait timed out 370 times.
2010-10-31 20:13:51.796 NVP(1), Error: Timed out waiting for prebuffering too long. Exiting..
2010-10-31 20:13:51.796 NVP(1), Error: Video frame buffering failed too many times.
2010-10-31 20:13:51.803 AO, ERROR: Audio buffer overflow, 24677377 audio samples lost!
2010-10-31 20:13:51.812 AO, ERROR: Audio buffer overflow, 24681473 audio samples lost!
2010-10-31 20:13:51.821 AO, ERROR: Audio buffer overflow, 24685569 audio samples lost!
2010-10-31 20:13:51.830 AO, ERROR: Audio buffer overflow, 24689665 audio samples lost!
2010-10-31 20:13:51.839 AO, ERROR: Audio buffer overflow, 24693761 audio samples lost!
2010-10-31 20:13:51.849 AO, ERROR: Audio buffer overflow, 24697857 audio samples lost!
2010-10-31 20:13:51.858 AO, ERROR: Audio buffer overflow, 24701953 audio samples lost!
2010-10-31 20:13:51.867 AO, ERROR: Audio buffer overflow, 24706049 audio samples lost!
2010-10-31 20:13:51.876 AO, ERROR: Audio buffer overflow, 24710145 audio samples lost!
2010-10-31 20:13:51.885 AO, ERROR: Audio buffer overflow, 24714241 audio samples lost!
2010-10-31 20:13:51.894


Any ideas?

---

### Post by ian dobson on 2010-11-01
Hi,

Maybe try increasing your audio buffer size (under the Frontend setup,playback).

Regards
Ian Dobson

---

