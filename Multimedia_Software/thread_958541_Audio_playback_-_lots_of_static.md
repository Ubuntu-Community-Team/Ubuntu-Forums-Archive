---
title: "Audio playback - lots of static"
date: 2008-10-25
forum: Multimedia Software
---

### Post by George_ on 2008-10-25
For some reason, recently (as in for a few hours) whenever I want to play music or video on my computer the audio always comes out with bad quality and static 'round the edges' (I think that's the best way to describe it). I don't think I changed anything manually, but I started noticing it in the middle of a song, so I don't know if I changed it before and just didn't notice. Can anyone help?

Thanks

---

### Post by logos34 on 2008-10-25
maybe try lowering your PCM volume level

---

### Post by George_ on 2008-10-25
Ah, I see. That's fixed the problem. Thanks.

---

### Post by Stray Wolf on 2012-05-16
This still happens in 12.04. On my dell with HDA Intel audio. Turning down the pcm volume in alsamixer helps but it doesn't solve the problem. It's just quieter. I also added this: options snd-hda-intel model=ref to /etc/modprobe.d/alsa-base.conf through gedit. I still have static though. Not as bad as before. Anything else I could do to optimize my sound quality?

BTW - in 12.04 turning down PCM works until log-out or reboot. Then PCM is maxed out again. How do I save my alsa settings?

---

