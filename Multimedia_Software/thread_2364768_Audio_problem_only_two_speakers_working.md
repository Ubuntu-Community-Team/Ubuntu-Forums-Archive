---
title: "Audio problem: only two speakers working"
date: 2017-06-27
forum: Multimedia Software
---

### Post by hyvenos on 2017-06-27
Hello everybody,

Here is my problem: I use a HTPC with Ubuntu 16.04.02 LTS. After some installation I could watch movies with Kodi using my surround system. 
But some days before it stops working: Now I can only have sound with my front speakers.

My sound card is a Xonar DX and my computer is link to my amp by a HDMI and all my speakers (front-left, front-right, rear-left,rear-right, side-left,side-right, center front and  subwoofer) are plugged to my amp.

I checked many thread on the internet and nothing works for me.

This is what I did so far:

I changed daemon.conf to allow pulse audio to use 8 channels, I change the default profile "front-right,front-left" to "front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right"
I set the outputs mode to Digital Surround 7.1 for the HDMI/DIsplay Port.
I installed pavucontrol to allow me to set my sound card mode to Analog Surround 7.1.

I tried alsamixer to verify that there is no mute channel.
When I test my speakers with the sound control panel I can see 8 speakers but: If I tried to test my sound card I don't have any sound, if I try with HDMI: all the sound of my left speakers are played by my front-left speaker and same for the right speakers wich are played by my front-right speaker.
If I type speaker-test -c 8 to a terminal: I got an awful sound from my front speakers and terminal keeps showing me the list of speakers repetitively.

I checked my logs and I found this error: ```
 pulseaudio[1638]: message repeated 4 times: [ [pulseaudio] alsa-mixer.c: Volume element Master has 8 channels. That's too much! I can't handle that!]
```

I tried to solve this by changing "Volume = merged" to "Volume =" into  /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common (A trick I found somewhere I'm not sure about that but I changed back now)

I found another error in my logs: ```
pulseaudio[1918]: [pulseaudio] protocol-native.c: Client sent non-aligned memblock: index 0, length 65496, frame size: 32
```
I found this error many times but I don't know what is supposed to mean?

So this is where I am, this is my first time with Ubuntu so I'm a little bit confused. Maybe my issue is not clear or there miss some information?

Thank you for your help!

---

### Post by ymbride on 2017-07-19
you can check audio and audio setting than clarify this problem .,thanks for sharing you are problems.,

---

