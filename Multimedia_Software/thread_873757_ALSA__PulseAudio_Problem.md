---
title: "ALSA / PulseAudio Problem ?"
date: 2008-07-29
forum: Multimedia Software
---

### Post by haelen on 2008-07-29
I've recently been having peculiar audio problems. The main one manifests when I use Mplayer which flickers when I try to play a DVD, or any video or audio file.

I also get the error "AO_ALSA unable to find simple control PCM,0" when this occurs.

If I kill PulseAudio when I restart it I get the error:

```
W: pid.c: Stale PID file, overwriting.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL equalized
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0"): initialization failed.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
```

TIA,
Tim

---

### Post by onehotcutey on 2008-09-12
Just wondering if / how you got this solved.  I receiving the same error code though my audio is not working at all.  Amazingly it was working great just before I rebooted.

Best,
Daniel

---

### Post by judoka9999 on 2008-09-23
*BUMP* Same issue in Intrepid Ibex after doing todays package updates. Curious issue though, because when I run mplayer as root it adjusts the volume fine. My volume control, aumix, and alsamixer programs all adjust PCM volume just fine as a non-root user. I do have a somewhat customized pulse config, but I don't think that is the issue. Nor do I believe its any kind of permissions issue, as again other alsa programs work just fine. Mine might be an mplayer issue. I'll look into it more tonight and post what I find.:guitar:

P.S. For now, running mplayer as root w/ sudo is fixing the issue w/ me. I just hope compiz gets along w/ mplayer now that it is running as root.

Update: Sorry folks, I haven't gotten a chance to look into this any further, I've had to implement some new features in a web app that weren't required 24 hours ago... I will get to this as soon as I can.

---

