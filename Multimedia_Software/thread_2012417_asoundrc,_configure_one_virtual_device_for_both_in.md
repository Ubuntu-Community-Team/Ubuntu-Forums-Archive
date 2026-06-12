---
title: "asoundrc, configure one virtual device for both input and output"
date: 2012-06-29
forum: Multimedia Software
---

### Post by amarshat on 2012-06-29
Hi,
I have a multiple sound cards connected to my pc, and I have input and output configured as different virtual devices, like this,
pcm.pulse_i {
  type pulse
  device alsa_input.pci-0000_00_1b.0.analog-stereo
}
pcm.pulse_o {
  type pulse
  device alsa_output.pci-0000_00_1b.0.analog-mono
}
Can I combine both of them into one virtual device ? Since my application requires specifying only sound card name for both operations. ?
Thanks in advance.

---

