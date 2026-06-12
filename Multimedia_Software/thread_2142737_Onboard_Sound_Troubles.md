---
title: "Onboard Sound Troubles"
date: 2013-05-06
forum: Multimedia Software
---

### Post by jouatt on 2013-05-06
Thank you in advance for taking your time. I have been struggling with this issue for a few hours now. I am running Ubuntu 13.04 and a Linux noob. My sound was working fine when I first installed Ubuntu but after starting my computer this morning is has seized to work. I made sure nothing is on mute and the speakers work through a different audio device. Last night I plugged in my wireless headset dongle and the headset worked great with out any tinkering except for changing the output in the Sound settings to the headset. Since then I have unplugged the dongle, restarted the computer, and switched the Output in the Sound settings to my Analog Output. I have also tried numerous tutorials and troubleshooting guides to no avail. Let me know what kind of information I can give to help. Thank you.

---

### Post by papibe on 2013-05-06
Hi jouatt. Welcome to the forum ):P

Could you open a terminal run these commands and post the results?
```
aplay -l

aplay -L

amixer
```
Regards.

---

### Post by jouatt on 2013-05-06
Thanks for the quick replay :)

```
ian@Ian:~$ aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ian@Ian:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=SB
    HDA ATI SB, ALC892 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Hardware device with all software conversions
ian@Ian:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 3 [10%] [-30.00dB] [on]
  Front Right: Playback 3 [10%] [-30.00dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 18 [39%] [2.00dB] [off]
  Front Right: Capture 18 [39%] [2.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line'
  Item0: 'Rear Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Rear Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
```

---

### Post by papibe on 2013-05-06
Thanks.

I don't see any output muted or off.

Could you make sure that in your 'Sound Settings' you have selected the Analog card/output?

Also, could you run this test to see if you can hear it the stereo speakers?
```
speaker-test -c2 -twav
```
Regards.

---

### Post by jouatt on 2013-05-06
The analog card/output is selected and I ran the test but didn't hear anything from the speakers. When I plug in my headset, witch uses a USB dongle, I can get sound from the headset.

---

### Post by papibe on 2013-05-06
May be you need a little more control over pulseaudio.

Install 'PulseAudio Volume Control' (pavucontrol) from the Software Center, and try to set your output devices and volume there.

Let us know how it goes.
Regards.

---

### Post by Yellow Pasque on 2013-05-06
Could be this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984)

---

### Post by jouatt on 2013-05-06
I installed PulseAudio Volume Control but didn't see anything muted or low. I do see the equalizer bounce around when I play music though. Just no sound. Whats strange is that this did work when I first installed Ubuntu but im not sure what I could have done to mess it up.

---

### Post by jouatt on 2013-05-07
Got sound working! I checked out the link Temujin provided and installed Kernel 3.9. Restarted the computer and sound started working. Thanks for all your help guys :)

---

### Post by papibe on 2013-05-07
:) Glad you fixed it, and thanks for sharing your solution.

When you have the chance, please mark the thread as solved ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how).

Regards.

---

