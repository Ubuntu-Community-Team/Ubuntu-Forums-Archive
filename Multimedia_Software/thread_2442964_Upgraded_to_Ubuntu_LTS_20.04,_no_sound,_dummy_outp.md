---
title: "Upgraded to Ubuntu LTS 20.04, no sound, dummy output"
date: 2020-05-09
forum: Multimedia Software
---

### Post by dsp2020 on 2020-05-09
So I upgraded to Ubuntu LTS latest version from the previous version using **sudo do-release-upgrade -d**. Now I can only see dummy output in Audio Volume Settings. 

My sound card info is
```

myuser@myhost:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I try speaker test and I get no sound 
```

myuser@myhost:~$ speaker-test -t wav -c 2

speaker-test 1.2.2

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 1048576
Period size range from 32 to 349526
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
^CTime per period = 4.441137

```

***_BUT_*** I get sound as root
```

myuser@myhost:~$ sudo speaker-test -t wav -c 2

speaker-test 1.2.2

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 8192
Period size range from 1024 to 1024
Using max buffer size 8192
Periods = 4
was set period_size = 1024
was set buffer_size = 8192
 0 - Front Left
 1 - Front Right
Time per period = 2.852056
 0 - Front Left
^CWrite error: -4,Interrupted system call
xrun_recovery failed: -4,Interrupted system call
Transfer failed: Interrupted system call

```

So is this some permission missing problem?
```

myuser@myhost:~$ ls -l /dev/snd/*
crw-rw----+ 1 root audio 116,  7 May 10 00:09 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  5 May 10 00:09 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  6 May 10 00:09 /dev/snd/hwC0D3
crw-rw----+ 1 root audio 116,  3 May 10 00:09 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  2 May 10 00:22 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  4 May 10 00:09 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  1 May 10 00:09 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 May 10 00:09 /dev/snd/timer

/dev/snd/by-path:
total 0
lrwxrwxrwx 1 root root 12 May 10 00:09 pci-0000:00:1b.0 -> ../controlC0

```

---

### Post by dsp2020 on 2020-05-09
timidity was hogging the sound device. disabling the service fixed it

```
sudo systemctl stop timidity
sudo systemctl disable timidity
```

---

