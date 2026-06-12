---
title: "interference in speakers"
date: 2020-07-02
forum: Multimedia Software
---

### Post by lvm on 2020-07-02
I have some weird interference in speakers. Well, the interference itself is not weird at all - usual AC mains humming, and looks like it picks up some radio station too, but weirdly only when nothing is playing. As soon as I start some playback the interference is gone, and I don't mean it is drowned out - gone even if a complete silence is played. I just made an mp3 file with no sound at all, and as soon as I start it speakers give a gentle pop and all interference disappears and resumes exactly 6 seconds after the playback has stopped. Possibly some sort of AGC-related thing in speakers because they produce the same interference even when disconnected from PC. Anyhow, is there a way to make the interference stop apart from continuously playing the sounds of sweet silence? Audio is onboard Realtek ALC892, pulseaudio, analogue line out into active stereo speakers, microphone is disabled (analogue stereo output profile).

---

### Post by lvm on 2020-07-02
Ok, this issue is caused by audio powersaving and deleting 'load-module module-suspend-on-idle' in /etc/pulse/default.pa and system.pa and restarting pulseaudio disables audio powersaving and fixes this issue.

---

