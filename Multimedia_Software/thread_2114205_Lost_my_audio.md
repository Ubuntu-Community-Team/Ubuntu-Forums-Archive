---
title: "Lost my audio"
date: 2013-02-09
forum: Multimedia Software
---

### Post by shafi on 2013-02-09
Hey guys,
recently I just lost audio from my ubuntu 12.10. It was working fine, I have installed some gedit plugins and after that noticed that I have no sound in my system anymore, I googled alot, but couldn't get any clue.
I tried most of the steps mentioned here: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) but still no result.
Can some one help me please?

These info might help to find out the problem:
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: 92HD81B1X5 Analog [92HD81B1X5 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```

 speaker-test 

speaker-test 1.0.25

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
Time per period = 11.374248
 0 - Front Left
Time per period = 11.367080
 0 - Front Left

```
syslog output:
```

Feb  9 20:01:44 user-HP-ProBook-5320m pulseaudio[2609]: [alsa-sink] alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Feb  9 20:03:12  pulseaudio[2609]: last message repeated 5 times

```
```

 fuser -v /dev/snd/* /dev/dsp*
Specified filename /dev/dsp* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  tokhi     25579 F.... pulseaudio

```
Thanks.

---

### Post by tgalati4 on 2013-02-09
Sometimes installing software will change permissions and/or ownership.  Check the permissions of your audio devices and change them if necessary: (12.10 installation)

tgalati4@Mint14-Extensa /dev/snd $ ls -la
total 0
drwxr-xr-x   3 root root      220 Feb  9 08:21 .
drwxr-xr-x  16 root root     4240 Feb  9 08:21 ..
drwxr-xr-x   2 root root       60 Feb  9 08:21 by-path
crw-rw---T+  1 root audio 116,  7 Feb  9 08:21 controlC0
crw-rw---T+  1 root audio 116,  6 Feb  9 08:21 hwC0D0
crw-rw---T+  1 root audio 116,  5 Feb  9 08:21 hwC0D1
crw-rw---T+  1 root audio 116,  4 Feb  9 08:21 pcmC0D0c
crw-rw---T+  1 root audio 116,  3 Feb  9 08:21 pcmC0D0p
crw-rw---T+  1 root audio 116,  2 Feb  9 08:21 pcmC0D2c
crw-rw---T+  1 root audio 116,  1 Feb  9 08:21 seq
crw-rw---T+  1 root audio 116, 33 Feb  9 08:21 timer

It's possible that your sound chip is having problems.  Try shutdown, remove power, battery, and let it sit for 10 minutes, then reboot.  Many times, hardware problems will act like software problems--causing you to chase after solutions which ultimately don't work because it's really a hardware problem to begin with.

---

### Post by shafi on 2013-02-10
> **tgalati4 said:**
> Sometimes installing software will change permissions and/or ownership.  Check the permissions of your audio devices and change them...

This didn't work for me, I removed the battery and files permission also look fine.
```
~$ ls -la /dev/snd/
total 0
drwxr-xr-x   3 root root      220 Feb 10 18:24 .
drwxr-xr-x  17 root root     4200 Feb 10 18:24 ..
drwxr-xr-x   2 root root       60 Feb 10 18:24 by-path
crw-rw---T+  1 root audio 116,  7 Feb 10 18:24 controlC0
crw-rw---T+  1 root audio 116,  6 Feb 10 18:24 hwC0D0
crw-rw---T+  1 root audio 116,  5 Feb 10 18:24 hwC0D3
crw-rw---T+  1 root audio 116,  4 Feb 10 18:25 pcmC0D0c
crw-rw---T+  1 root audio 116,  3 Feb 10 18:26 pcmC0D0p
crw-rw---T+  1 root audio 116,  2 Feb 10 18:25 pcmC0D3p
crw-rw---T+  1 root audio 116,  1 Feb 10 18:24 seq
crw-rw---T+  1 root audio 116, 33 Feb 10 18:24 timer

```

---

