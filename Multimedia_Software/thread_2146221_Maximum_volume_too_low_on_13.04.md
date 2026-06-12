---
title: "Maximum volume too low on 13.04"
date: 2013-05-17
forum: Multimedia Software
---

### Post by harzoglups on 2013-05-17
Hi

I've installed the new Ubuntu 13.04. I was using 12.04 before.
The maximum volume is significantly lower on 13.04 compare to 12.04.

It is true with the default sound card but with my bluetooth creatve D1 interface as well :(

Anyone knows how to solve this problem?

Thanks!

---

### Post by tartakynov on 2013-05-18
I had the same problem with my Creative D1 on Ubuntu 13.04. Fixed with PulseAudio Manager (available in software center). Here step-by-step solution, hope it helps:

1. Install PulseAudio Manager
2. Run "paman" from terminal
3. Go to "Devices" tab
4. Double-click on your devices sink and manage your volume

---

### Post by harzoglups on 2013-05-19
Thanks a lot, this helps but I still cannot get the sound as loud as it was with 12.04 or as it is with my windows PC.

In Pulseaudio Manager, if I select directly the overall sink named "alsa_output.usb-041e_Creative_Bluetooth_Audio_D1-01-D1.analog-stereo", the volume is already set to 100%.
I can increase it over 100% but the sound gets saturated.

If I select "subsink" named "Alsa Playback", I can go up to 480% without saturation (by the way I don't understand how it is possible) but it is still lower than what I used to get before.

---

### Post by harzoglups on 2013-05-19
In fact sound is staturated as well by using subsink :(

I don't know what to do and don't understand what has changed between the two ubuntu releases!

---

### Post by tartakynov on 2013-05-20
I believe that something changed in the kernel 3.8 since my Creative BT D1 had perfect sound on Ubuntu 12.04 with kernel 3.5.

---

### Post by harzoglups on 2013-05-20
Yep.
I found a temporary solution: my BT speaker also accept wires... :mad:
No more BT but at least I have an acceptable volume.

---

### Post by andrew-beals on 2013-10-13
Go into the "Sound Settings&#8230;" under the speaker icon and you'll see that some jackhole has defined "100%" volume to be 66-75% of what it actually is.  You can slide it to the real 100% and use the volume settings in your app.  If you use the volume keys, you can only go down until you hit the "100%" mark and then you'll have to mouse back into the "Sound Settings&#8230;" screen to go back over "100%".

---

### Post by leggett-matthew on 2014-03-20
I'm experiencing exactly this same issue with my Creative BT-D1 speaker system.  12.04 worked like a peach and yet 13.04 is quiet, it's like someone thought all bluetooth devices were headphones so set the volume too low on purpose to protect our fragile little ears.  Never bothered upgrading to 13.10 to find out but might give 14.04 a go.  

Does anyone know if this problem persists beyond 13.04 or if there is a decent fix which doesn't distort and saturate the audio?

---

### Post by vmalep on 2014-05-07
Hi,

I had the same problem with the 14.04 version and a bluetooth speaker. Reading this thread, I gave one more tour to the audio settings and noticed the mode option. I switched from "Phone Duplex (HSP/HFP)" to "High Fidelity Playback (A2DP)". This solved the problem.

BR
Pierre

---

### Post by ssam on 2014-05-08
The sound system tried to get smarter about volumes. See [http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/PulseAudioStoleMyVolumes/](http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/PulseAudioStoleMyVolumes/) for details. 100% should be the loudest volume without overdriving and causing clipping, rather than just the loudest. However some sound cards don't properly describe their volumes, and the alsa/pulseaudio developers don't own all possible hardware. You can help by reporting better values to them, see [http://www.freedesktop.org/wiki/Software/PulseAudio/Backends/ALSA/Decibel/](http://www.freedesktop.org/wiki/Software/PulseAudio/Backends/ALSA/Decibel/)

---

### Post by pablosquared on 2014-05-08
```

sudo alsamixer

```

Then select your sound card and then look fot your analogue or digital outputs and make sure they're not set to too low a level. Adjust to taste. I found my RHS and LFE speakers were muted, but LHS and centre were set to a clipping level. By default, it seemed.

---

### Post by syntaxerror74 on 2014-05-17
Oh yes, I know that problem here on 14.04.

I can't say I "solved" it, but I tweaked it in a very crazy way: I had to edit an audio file in Audacity, and cranked up the output volume quite a bit. The result should be easy to guess: maxing out the output volume was WAY LOUDER than the 100% in volume control!
And crazily enough, mucking with the slider in Audacity even affected the volume of my audio playing software!

Talk about peculiar. But heck...it DID have a significant effect after all.

---

