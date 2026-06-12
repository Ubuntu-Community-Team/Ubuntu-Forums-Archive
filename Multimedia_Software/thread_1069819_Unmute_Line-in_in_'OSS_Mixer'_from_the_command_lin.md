---
title: "Unmute Line-in in 'OSS Mixer' from the command line"
date: 2009-02-14
forum: Multimedia Software
---

### Post by Blackie_Chan on 2009-02-14
I usually use mencoder to record TV. But lately, when I record (using a cron job), I get no sound. I've noticed that in 'Volume Control', when the device selected is 'OSS Mixer', in the Recording tab, Line-in is mute. 

I've unmuted Line-in, and ran my record TV script through the command line and it's fine. 

My plan is to modify my record script so that I can unmute 'Line-in'. What tool can I use to unmute 'Line-in' in the 'OSS Mixer' device?

---

### Post by Rangeli on 2009-02-27
I used amixer, but don't know if it works with oss mixer.

---

### Post by Blackie_Chan on 2009-09-10
I have just discovered how to do it. First, install alsa-oss. Then make changes to the Capture source using amixer.```
sudo apt-get install alsa-oss

amixer cget name='Capture Source'	

amixer cset name='Capture Source' '4,4'
```
I initially asked this question because when I was recording tv using mencoder, I had to set my 'Capture source' to be Line-In (in the OSS Mixer device. Then when I when I want to use my microphone (with Skype), I'll have to set the 'capture source' to be microphone.

---

