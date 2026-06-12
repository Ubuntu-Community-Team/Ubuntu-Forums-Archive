---
title: "Clicking noise in JACK and ALSA"
date: 2014-10-13
forum: Multimedia Software
---

### Post by redbull00 on 2014-10-13
Hello,
I've been struggling with this issue for a few months and I still can't find a solution. Here's the description:
When I record sound through my microphone using ALSA, there's a clicking noise that distorts the signal. It is even more evident during a skype call and after a few minutes, it becomes so frequent that it's impossible to have a conversation.
When I play virtual instruments through JACK, there's a clicking noise that distorts signal every few seconds. JACK shows that it lost some frames in red coloured text. 

Initially I thought this is occured by varying CPU clock ratio but I fixed it to 4GHz and the problem still occurs. I also tried different sound card, but it didn't help at all. The soundcards I tried are built in Realtek chip and SoundBlaster X-Fi USB. 

Could anyone help please? I can't work with music when this happens (problem doesn't occur during playback) and I really want to use Ubuntu :(

---

### Post by redbull00 on 2014-10-14
[COLOR=#000000]Hello,[/COLOR]
[COLOR=#000000]I've been struggling with this issue for a few months and I still can't find a solution. Here's the description:[/COLOR]
[COLOR=#000000]When I record sound through my microphone using ALSA, there's a clicking noise that distorts the signal. It is even more evident during a skype call and after a few minutes, it becomes so frequent that it's impossible to have a conversation.[/COLOR]
[COLOR=#000000]When I play virtual instruments through JACK, there's a clicking noise that distorts signal every few seconds. JACK shows that it lost some frames in red coloured text. [/COLOR]

[COLOR=#000000]Initially I thought this is occured by varying CPU clock ratio but I fixed it to 4GHz and the problem still occurs. I also tried different sound card, but it didn't help at all. The soundcards I tried are built in Realtek chip and SoundBlaster X-Fi USB. [/COLOR]

[COLOR=#000000]Could anyone help please? I can't work with music when this happens (problem doesn't occur during playback) and I really want to use Ubuntu [/COLOR]:sad:

---

### Post by overdrank on 2014-10-14
Hi and welcome, please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by redbull00 on 2014-10-20
I finally solved this problem, at least partially - there's still a minor issue with Jack but it got much better. It turned out that default settings for PulseAudio are faulty and they included incorrect buffer sizes for my hardware. I really wonder why there's no tool that does it for users since these can be calculated by getting settings from the hardware and asking it about its buffer capacity. The exact solution is presented on arch wiki:
[https://wiki.archlinux.org/index.php/PulseAudio#Setting_the_default_fragment_number_and_buffer_size_in_PulseAudio](https://wiki.archlinux.org/index.php/PulseAudio#Setting_the_default_fragment_number_and_buffer_size_in_PulseAudio)

---

