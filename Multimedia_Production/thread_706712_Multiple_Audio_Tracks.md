---
title: "Multiple Audio Tracks"
date: 2008-02-24
forum: Multimedia Production
---

### Post by Jeffery Mewtamer on 2008-02-24
I am attempting to produce video files with two audio tracks. My source files are as follows:

English TV-rips in Mp3/Xvid/AVI format
and
French DVD-rips in Ogg Vorbis/Xvid/OGM format

I want to extract the English audio from the AVIs and place them in the OGM files as an alternate audio track, preferably with the added track as track 1 and the original set as track 2.

Using AviDemux Qt 2.4.1 from the repositories, I have gotten the following results:

I can successfully extract the mp3 audio from the AVIs.
I can extract the Ogg audio from the OGMs, but they will not play.
I can overwrite audio track 1 from the OGMs with the imported mp3, but the timing is broken.
I cannot add a second audio track.

Remembering that I previously used Virtual Dub Mod to do similar work, I attempted to get it running under wine, but it crashes with the following terminal output:

```

jeffery@ubuntu:~/Documents/Software/VirtualDubMod$ wine VirtualDubMod.exe
err:module:import_dll Library corona.dll (which is needed by L"H:\\Documents\\Software\\VirtualDubMod\\VirtualDubMod.exe") not found
err:module:import_dll Library ogg.dll (which is needed by L"H:\\Documents\\Software\\VirtualDubMod\\VirtualDubMod.exe") not found
err:module:import_dll Library vorbis.dll (which is needed by L"H:\\Documents\\Software\\VirtualDubMod\\VirtualDubMod.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"H:\\Documents\\Software\\VirtualDubMod\\VirtualDubMod.exe" failed, status c0000135
jeffery@ubuntu:~/Documents/Software/VirtualDubMod$

```

I also tried the original Virtual Dub and while it runs, it cannot read OGM files.

Any advice on getting AviDemux to do the audio tracks correctly, getting Virtual Dub Mod to run, or another program(preferably from repositories) that can perform this task would be greatly appreciated.

Thank you in advance.

---

