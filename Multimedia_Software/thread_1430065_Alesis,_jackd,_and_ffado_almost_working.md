---
title: "Alesis, jackd, and ffado almost working"
date: 2010-03-14
forum: Multimedia Software
---

### Post by doogxela on 2010-03-14
I have finally gotten my Alesis MultiMix 8 FireWire mixer to work. I started with a vanilla install of Ubuntu 9.10. I then uninstalled jackd and ffado. Once those were gone, I compiled and installed them from source. The Alesis is now recognized and I can speak into a microphone plugged into the mic inputs and hear the result in the headphone out of the mixer. I have even recorded a little using ardour. There is something not quite right, though.

If I plug the mic into mic1, it only picks up the left channel (I only hear it in the left headphone and only the left meter shows input). Mic2 only gives me the right channel. Mic3 is back to only the left channel, but it is very quiet. I have to turn it almost to max gain to get any real usable levels. Mic4 finally gives me both channels, but again, the gain has to be very hot before I can get any usable level.

I don't currently have any way to test the 1/4" inputs, as I only have one mic with an XLR cable. Does anyone have any ideas why I would be getting these results with the four different XLR inputs?

---

### Post by rlameiro on 2010-03-15
check the other thread.

Your mic its mono, and the in channels of the alesis are also mono, so you will ear in one channel only.

---

### Post by doogxela on 2010-03-16
> **rlameiro said:**
> check the other thread.

Your mic its mono, and the in channels of the alesis are also mono, so you will ear in one channel only.

You're right. It is just mono. But why does each input behave differently? I can plug the microphone into the fourth input and get sound in both ears and I can pan it right and left. The other three inputs only give me sound in one ear and panning has no effect on them.

---

### Post by rlameiro on 2010-03-16
I dont know your sound board, but maybe the 4ht input is routed in jack to the left and right outputs inside jack. or maybe its inside the board, that send a monitor to the 2 channels. but the way it should work is like this. One in one out. then you can route as you wish. if you have 8 outputs you can even send the same mic to the 8 outputs, so for me this is not a problem at all, just how it works in audio.
About the 4th channel, chec in the connections window of qjackctl where is connected the 4th capture device.

---

