---
title: "VDPAU on Acer Revo 3610 gives audio, no video"
date: 2011-10-26
forum: Mythbuntu
---

### Post by vagster on 2011-10-26
Hi there,

Have been running my Acer Revo 3610 with Nvidia ION for some time now and have kept on trying VDPAU profiles. However, when I switch to VDPAU, I always get a black screen but with audio playing.

I have the Nvidia 195.36.24 drivers with PowerMizer switched to max.

I have also been into bios and changed the memory to 512Mb and made lots of advised changes to MythTV Playback settings but still the same problem.

Am running Mythbuntu 10.04.1 with 0.24 fixes and the most recent updates.

I see this same behaviour when playing video or recordings.

I have pasted the mythfrontend log in below from starting to stopping playback but don't really see any errors.

```
2011-10-26 22:10:16.628 AFD: Opened codec 0xa1963380, id(DVB_SUBTITLE) type(Subtitle)
2011-10-26 22:10:16.828 Pulse: PulseAudio resume OK
2011-10-26 22:10:17.029 Pulse: PulseAudio suspend OK
2011-10-26 22:10:17.068 AO: Opening audio device 'hdmi' ch 2(2) sr 48000 sf signed 16 bit reenc 0
ALSA lib control.c:902:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2011-10-26 22:10:17.077 ALSA, Error: failed to register mixer device /dev/mixer: No such file or directory
2011-10-26 22:10:17.077 ALSA, Error: Unable to open audio mixer. Volume control disabled
2011-10-26 22:10:17.078 AudioPlayer: Enabling Audio
2011-10-26 22:10:18.734 VDPAU: Created 2 output surfaces.
2011-10-26 22:10:18.735 VDPAU: Version 1
2011-10-26 22:10:18.735 VDPAU: Information NVIDIA VDPAU Driver Shared Library  195.36.24  Thu Apr 22 10:39:56 PDT 2010
2011-10-26 22:10:18.735 VDPAU: Created VDPAU render device 1920x1080
2011-10-26 22:10:18.935 Player(0): Forcing decode extra audio option on (Video method requires it).
2011-10-26 22:10:19.195 Player(0): Video timing method: USleep with busy wait
2011-10-26 22:10:19.197 TV: Changing from None to WatchingPreRecorded
2011-10-26 22:10:19.290 ScreenSaverX11Private: DPMS Deactivated 1
2011-10-26 22:10:19.380 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-10-26 22:10:19.421 TV: ProcessNetworkControlCommand(NETWORK_CONTROL QUERY POSITION) ignoreKeys: 0
2011-10-26 22:10:22.556 TV: ProcessNetworkControlCommand(NETWORK_CONTROL QUERY POSITION) ignoreKeys: 0
2011-10-26 22:10:25.556 TV: ProcessNetworkControlCommand(NETWORK_CONTROL QUERY POSITION) ignoreKeys: 0
2011-10-26 22:10:25.926 TV: Attempting to change from WatchingPreRecorded to None
2011-10-26 22:10:26.005 VDPAU Painter: Clearing VDPAU painter cache.
2011-10-26 22:10:26.008 MythPainter: 2 images not yet de-allocated.
2011-10-26 22:10:26.237 Pulse: PulseAudio resume OK
2011-10-26 22:10:26.288 TV: Changing from WatchingPreRecorded to None
2011-10-26 22:10:26.289 ScreenSaverX11Private: DPMS Reactivated 1

```

Any ideas would be much appreciated.

Cheers

Stephen

---

### Post by nickrout on 2011-10-27
hmmm, many people are using vdpau on those computers successfully with myth, me being one of them.

are you sure your tv will run 1920x1080?

Have you tried running mythfrontend -v playback, which will give extra debugging info.

---

### Post by vagster on 2011-10-27
Thank you for the advice. This was also baffling me as I know people who are running the revo with VDPAU.

Anyway, having been trying to fix this up occasionally for the last few months, nothing was working. But.... I ran it once with the mythfrontend -v playback command that you suggested and now it works!

So, am still baffled but happy as it is working now.

Thanks!

Stephen

---

