---
title: "Maverick: winealsa seg fault when running Spotify in wine"
date: 2011-01-02
forum: Multimedia Software
---

### Post by SB9784 on 2011-01-02
Hi all,

I've been trying to get Spotify running in wine on Maverick. I've had this running on older versions of Ubuntu in the past, but now it's not working. Spotify loads up fine, but as soon as I try to play some audio it crashes. When running it from the terminal I get the folowing backtrace:

```
Backtrace:
=>0 0x5ad88450 (0x1515e6a4)
  1 0x20317838 in winealsa (+0x17837) (0x1515e744)
  2 0x203180d3 in winealsa (+0x180d2) (0x1515e784)
  3 0x20468ce9 in dsound (+0x28ce8) (0x1515e7d4)
  4 0x2046941b DSOUND_PrimaryCreate+0x3a() in dsound (0x1515e814)
  5 0x2045bc55 DirectSoundDevice_Initialize+0x744() in dsound (0x1515e8e4)
  6 0x2045c2db in dsound (+0x1c2da) (0x1515e934)
  7 0x2045da6f DirectSoundCreate+0x18e() in dsound (0x1515e9a4)
  8 0x00557147 in spotify (+0x157146) (0x1515ea10)
  9 0x005575ec in spotify (+0x1575eb) (0x1515ea48)
  10 0x00556d7d in spotify (+0x156d7c) (0x1515ea60)
  11 0x00556bfa in spotify (+0x156bf9) (0x1515ea78)
  12 0x7bc6e8c0 call_thread_entry_point+0x6f() in ntdll (0x1515eb48)
  13 0x7bc76e95 in ntdll (+0x66e94) (0x1515f398)
  14 0x68145cc9 start_thread+0xd8() in libpthread.so.0 (0x1515f498)
fixme:winmm:MMDRV_Exit Closing while ll-driver open
```

I've tried changing the audio drivers to something else (I unchecked "ALSA" and checked "OSS") but that didn't seem to fix it - in this case Spotify brings up an error message saying there is a problem with the soundcard and it can't play any music.

I don't really understand much about audio drivers - does anyone know what the problem is and how to fix it?

Thanks!

---

### Post by Yellow Pasque on 2011-01-03
Ubuntu has removed OSS from the kernel in Maverick, so it's no longer supported. Try Esound (ESD) output of WINE, since pulseaudio emulates ESD, and I've seen reports of Spotify working with it.

---

