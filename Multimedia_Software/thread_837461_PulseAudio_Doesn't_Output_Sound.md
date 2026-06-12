---
title: "PulseAudio Doesn't Output Sound"
date: 2008-06-22
forum: Multimedia Software
---

### Post by Azzuron on 2008-06-22
Hello. I have a bit of an unusual story perhaps, but in the end my sound is not working at all, and I have been trying to uncover the reason for this. I hope that someone out there is more experienced than I, and will be able to give me a hand with this situation.

Story: I installed ubuntu on my desktop about two months ago. I did not have any speakers at the time, so i cannot tell if sound worked then or not. I did go out and buy a USB headset which i plugged into the desktop, and sound did work with this, but it appears to be a separate audio device. I had to mess around with mixers to get volume controls to work and the like. Also, not all sound was able to come through this device, only some simple sounds.

I went out and bought a pair of cheap speakers recently, and replaced the headset with them, i reverted the mixer settings back to what they were before, and i was able to get sound through the speakers after a little messing around. everything worked great it was fun and awesome. 

I installed a game into wine, and that went well, but caused the sound to stop all together in ubuntu. So, i read around and heard that pulse audio was the problem, so i followed the recommendation to kill the process. I did and sound seemed to come back. After reading some more people said you could uninstall it to avoid having to kill the process all the time, and so i did that also. It was at that time that sound stopped working all together. I get nothing out of my computer anymore. I cannot find a configuration that will output audio, using ALSA, OSS, or Pulse. 

I followed the configuration of this site: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio), and in the Pulse audio manager, i can see that i have a sound device, i set it as the device i want to use  (Default sink), and played a movie. the audio is not there, but the playback volume meter is saying that sound is being outputted. I verified that the jack on the back of my computer is not the issue, these speakers work on another system, and none of the jacks on the backside of my PC are outputting audio. I don't know what else to do at this point. Please help if possible! thanks :)

---

### Post by Azzuron on 2008-06-22
I have found that there apparently is sound, the volume level is so low, that you cannot hear it. In the pulse manager i can adjust the volume above 100% but this distorts the audio really bad, and the amount that it needs to be raised is over 200% for it to be anywhere near as loud as i would need it to be.

---

### Post by xc3RnbFO8P on 2008-06-22
In alsamixer do you got **External Amplifier**?

---

### Post by Azzuron on 2008-06-22
I do not, i have only two meters, one for master one for capture.

---

### Post by xc3RnbFO8P on 2008-06-22
What about volume control> edit> preferences is something unchecked?

---

### Post by Azzuron on 2008-06-22
Well the problem seems to be solved. its strange that the headphone and PCM controls both increase volume to my speakers, but only one of them up to the top is not enough, both had to be moved. Thanks :)

---

### Post by xc3RnbFO8P on 2008-06-22
Congratulation :)

---

