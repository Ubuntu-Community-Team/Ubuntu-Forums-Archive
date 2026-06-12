---
title: "Audio over HDMI - intermittent buzz sound."
date: 2010-08-02
forum: Multimedia Software
---

### Post by Pollywag on 2010-08-02
Hey guys, I'm extremely new at Linux but managed to get Alsa .023 installed on my HTPC and sound working in xbmc. However, every 10-15 seconds when playing audio over HDMI, i get a short burst of static (maybe 0.5 seconds). The static does not interfere with the audio track. I have tried running my laptop using the same cable/tv/port and its fine (win7). Listening through the analog connection on the mobo with headphones produces no such noise.
The noise happens with any audio such as youtube or xbmc.

Gigabyte UD3-H57 USB 3.0
Core i3 530
2GB Corsair 1333 DDR3
1TB WD Green

Running 10.04 Ubuntu

Happy to post any logs you may require but please tell me how to do so because as said, im very new :)

Alex

---

### Post by Pollywag on 2010-08-02
Update.
I tried switching to OSS and ALSA as default sound devices (instead of pulse), didnt help. I also tried a number of different file types. All had the same issue.

---

### Post by Pollywag on 2010-08-02
bump.

---

### Post by Pollywag on 2010-08-03
reinstalled ubuntu
still failing

---

### Post by MltiMike on 2010-12-30
Hi Pollywag,

Did you ever get this issue resolved? I'm having the identical symptoms with my HTPC that I just put together and I'd appreciate any input yo might have.

Interestingly, I'm running a Core i3 540 on a Gigabyte H55N-USB3 board. I wonder if it's an inssue with the ALSA drivers and Gigabyte motherboards. It took me forever to finally find another person that's having the same issue.

---

### Post by MltiMike on 2011-01-03
I've just solved the problem... I'll leave solution/explanation here for anyone else who runs into this problem.

The Intel HDA is optimized for 48kHz audio streams while most MP3s and in-browser streams (Hulu, Youtube, Pandora) are encoded at 44.1kHz. While there should be auto-sample rate adjustment happening, it looks like there is a problem/bug with the current ALSA implementation that is causing the timing to be off and thus this intermittent buzz to occur.

The fix I used was to create a virtual device in my asound.conf so ALSA would change the sample rate before sending it to the device:
```

~> cat /etc/asound.conf
pcm.hdmi3 {
  type hw
  card 0
  device 3
}

pcm.hdmi3_48kHz {
  type rate
  slave {
    pcm hdmi3
    rate 48000
  }
}

pcm.!default hdmi3_48kHz

```

---

