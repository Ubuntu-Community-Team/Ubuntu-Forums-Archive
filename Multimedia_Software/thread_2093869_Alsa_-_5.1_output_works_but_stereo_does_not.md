---
title: "Alsa - 5.1 output works but stereo does not"
date: 2012-12-12
forum: Multimedia Software
---

### Post by PeterTaps on 2012-12-12
Folks,

I have built a minimal Ubuntu 12.04 system + OpenBox. The audio system is pure alsa. There is no pulseaudio install on this one.

The system has a Soundblaster card in it. All the six pins go to an audio receiver.

I also created an .asoundrc file. Here are the contents:

pcm.!default {
  type hw
  card CA0106
}

When I run the following command, all the speakers work perfectly:

$ speaker-test -c 6 -t wav

I have also installed and configured VLC 2.0.4 to use CA1016 5.1 output.

I have three .mp4 files. One has 5.1 audio in it. The second one has stereo audio and the third one has mono audio in it.

When I play 5.1 audio file, all the speakers work as expected. However, when I play stereo audio file or the mono audio file, I get no sound at all.

I am wondering if anyone can tell me what could be wrong with my setup and if there is a way to fix it.

Thank you in advance for your help.

Regards,
Peter

---

