---
title: "Mythtv line in issues"
date: 2012-03-12
forum: Mythbuntu
---

### Post by lateNightLinux on 2012-03-12
Hi everyone, 

  I have been using Mythbuntu problem-free for the past few months and recently I had to perform a fresh install to Mythbuntu 11.10. It seems that everything is as it should be except that I can not capture any audio. I am using a Hauppauge pvr-150(low profile) for video and my computers line-in for audio. I've tried for the past few days to  get it to work by playing with the alsa settings, reinstalling , and even just installing Myth on top of Ubuntu 11.10 but to no avail. Ubuntu sees my card and I can record using arecord so its not an OS problem. There must be something I overlooked as I had this setup working previously. If you need any further info that could help solve this problem please let me know. Thanks in advance. -Brian

---

### Post by lateNightLinux on 2012-03-12
Just looking around at some other audio posts and noticed something,
if I do aplay -L it returns the following:
 
```

null
Discard all samples (playback) or generate zero samples (capture)
default:CARD=ICH5
Intel ICH5, Intel ICH5
Default Audio Device
front:CARD=ICH5,DEV=0
Intel ICH5, Intel ICH5
Front speakers
surround40:CARD=ICH5,DEV=0
Intel ICH5, Intel ICH5
4.0 Surround output to Front and Rear speakers
surround41:CARD=ICH5,DEV=0
Intel ICH5, Intel ICH5
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=ICH5,DEV=0
Intel ICH5, Intel ICH5
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=ICH5,DEV=0
Intel ICH5, Intel ICH5
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=ICH5,DEV=0
Intel ICH5, Intel ICH5 - IEC958
IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=ICH5,DEV=0
Intel ICH5, Intel ICH5
Direct sample mixing device
dmix:CARD=ICH5,DEV=4
Intel ICH5, Intel ICH5 - IEC958
Direct sample mixing device
dsnoop:CARD=ICH5,DEV=0
Intel ICH5, Intel ICH5
Direct sample snooping device
dsnoop:CARD=ICH5,DEV=4
Intel ICH5, Intel ICH5 - IEC958
Direct sample snooping device
hw:CARD=ICH5,DEV=0
Intel ICH5, Intel ICH5
Direct hardware device without any conversions
hw:CARD=ICH5,DEV=4
Intel ICH5, Intel ICH5 - IEC958
Direct hardware device without any conversions
plughw:CARD=ICH5,DEV=0
Intel ICH5, Intel ICH5
Hardware device with all software conversions
plughw:CARD=ICH5,DEV=4
Intel ICH5, Intel ICH5 - IEC958
Hardware device with all software conversions
 
```
 
The second line discard all samples doesn't seem right from what other people have posted up. Could this be the problem?

---

### Post by nickrout on 2012-03-12
> **lateNightLinux said:**
> Hi everyone, 

  I have been using Mythbuntu problem-free for the past few months and recently I had to perform a fresh install to Mythbuntu 11.10. It seems that everything is as it should be except that I can not capture any audio. I am using a Hauppauge pvr-150(low profile) for video and my computers line-in for audio. I've tried for the past few days to  get it to work by playing with the alsa settings, reinstalling , and even just installing Myth on top of Ubuntu 11.10 but to no avail. Ubuntu sees my card and I can record using arecord so its not an OS problem. There must be something I overlooked as I had this setup working previously. If you need any further info that could help solve this problem please let me know. Thanks in advance. -Brian

You should be using the audio line in on the pvr150, not the sound card line in.

---

### Post by lateNightLinux on 2012-03-12
> **nickrout said:**
> You should be using the audio line in on the pvr150, not the sound card line in.
 
You were right. You know its been a while since I've messed with the inputs on this thing that I mistook the 
audio input on the card for something else. Could of swore I was using line in, but it works and thats all that 
matters. Thanks.

---

### Post by nickrout on 2012-03-12
When using an external input (as opposed to the tuner) the PVR 150 has it's own mpeg2 hardware encoder which muxes the audio in on the card with the video in on the card to create an stream with mpeg2 video and mp2 sound. I don't know of any pathway to get external sound (like from your sound card) into the stream.

---

### Post by lateNightLinux on 2012-03-12
It's funny, as soon as the problem was resolved someone told me the same thing you said. Well, at least now with this bit of information it'll be easier for me to remember this for the next time. I'm glad at least it was a simple fix and not some major issue.

---

### Post by nickrout on 2012-03-12
Glad it is working for you :)

---

