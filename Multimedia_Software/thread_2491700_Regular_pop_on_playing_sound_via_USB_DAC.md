---
title: "Regular pop on playing sound via USB DAC"
date: 2023-10-17
forum: Multimedia Software
---

### Post by mguymurray on 2023-10-17
Hi

I have an Audiolab USB DAC. When playing music through it from a Kubuntu PC I get a regular pop almost exactly like the sound of a scratched vinyl record, even moving between channels. 

The DAC works fine with a Raspberry pi and the PC works fine with any other DAC, its just this combination. It even happens using MPD with bit perfect streaming.

What could possibly be causing this sound?

Any suggestions as to how to stop it would be much appreciated.

Many thanks

---

### Post by #&amp;thj^% on 2023-10-17
See if power saver is at fault
```
cat /sys/module/snd_hda_intel/parameters/power_save
1

```
If it shows a "!" as above try this:
```
echo "0" | sudo tee /sys/module/snd_hda_intel/parameters/power_save

```
Let me know if that works and we will make it persistent across resarts/boots.

---

### Post by mguymurray on 2023-10-18
Hi, thanks for the prompt response.

power_save was set to 1. Changed it to 0 as suggested but problem persists.

Guy

---

### Post by #&amp;thj^% on 2023-10-18
Thanks for the try, will you show me this please:
```
inxi -Axxx
```
I'm kind of drawn to audio problems, and there has been a handful or two lately.

---

### Post by mguymurray on 2023-10-20
Audio:
  Device-1: Intel Sunrise Point-LP HD Audio vendor: CLEVO/KAPOK
    driver: snd_hda_intel v: kernel bus-ID: 00:1f.3 chip-ID: 8086:9d71
    class-ID: 0403
  Sound Server-1: ALSA v: k5.15.0-87-generic running: yes
  Sound Server-2: JACK v: 1.9.20 running: no
  Sound Server-3: PulseAudio v: 15.99.1 running: yes
  Sound Server-4: PipeWire v: 0.3.48 running: yes

---

