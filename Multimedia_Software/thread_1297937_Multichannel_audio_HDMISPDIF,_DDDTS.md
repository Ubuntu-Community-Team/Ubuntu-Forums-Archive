---
title: "Multichannel audio HDMI/SPDIF, DD/DTS"
date: 2009-10-22
forum: Multimedia Software
---

### Post by jonasback on 2009-10-22
Hello. 

I've been trying to get some answers lately but finally I've ended up solving them by myself one way or another. However. Now I just want to know if this is even possible.

I have a Nvidia 9800gtx graphics card with 2xDVI. I have connected the cable from my motherboard's spdif-out to the audio-in on my graphics card. I use a DVI->HDMI adapter, and have my computer connected to my 40" Samsung tv. From the tv's spdif out I have a cable to my Logitech Z5500 Digital 5.1 system. 

My question is: Is it possible to get DD 5.1 / DTS sound to my speakers?

I get stereo sound, but that's it. I'm thinking that this is mission impossible. Or is there a solution?

Thanks!

---

### Post by AKADAP on 2009-10-22
As far as I've been able to find out, the answer is no.

DD and DTS are patented formats, you need to pay royalties to encode in those formats.

One should be able to pass through stuff that is already encoded in those formats, but Pulse, since it wants to mix the sounds of many inputs would have to decode then re-encode the sound to do this, so it doesn't. I have not been able to find an option to cause Pulse to pass this data unmolested.

If you want multi-channel sound, at the moment, your only options are analog, or HDMI, and I'm not sure about HDMI.

I'd love to be proven wrong.

---

### Post by jonasback on 2009-10-22
> **AKADAP said:**
> I have not been able to find an option to cause Pulse to pass this data unmolested.

Thank you for your response. But about this, what if I remove pulse and just go with alsa? Would that be possible? I've had A LOT of problems with sound since I tried SPIDF for the first time about a year ago. The problems have usually been solved by completly disabling pulse. Now when I did a clean install a couple of days ago i couldn't get sound over hdmi. Solution -> purge pulse, set up the machine, then reinstall pulse and everything is fine.. :P

---

### Post by AKADAP on 2009-10-23
> **jonasback said:**
> Thank you for your response. But about this, what if I remove pulse and just go with alsa? Would that be possible? I've had A LOT of problems with sound since I tried SPIDF for the first time about a year ago. The problems have usually been solved by completly disabling pulse. Now when I did a clean install a couple of days ago i couldn't get sound over hdmi. Solution -> purge pulse, set up the machine, then reinstall pulse and everything is fine.. :P

I can't help you there, all of my experience is with Pulse.

---

