---
title: "No sound through headphones in Ubuntu 16.04"
date: 2018-04-21
forum: Multimedia Software
---

### Post by boombam123 on 2018-04-21
Hi,
I have a custom built-desktop with windows 10 and ubuntu dual-boot. Sound works as expected on windows but on ubuntu only the sound through my monitor speakers work (Displayport via dedicated GPU). It looks like my audio card may not be working correctly since audio input (microphone) does not work either. 

I am troubleshooting using the instructions on this page: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Here is my ALSA Info output (step #3)
[http://www.alsa-project.org/db/?f=fe747d951c0b9342d4010a01be2e1ec7ec29cfde](http://www.alsa-project.org/db/?f=fe747d951c0b9342d4010a01be2e1ec7ec29cfde)

Here is the output from step #4: 
```
dvanced Linux Sound Architecture Driver Version k4.13.0-38-generic. 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xef340000 irq 126
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xef080000 irq 17
  1:        : sequencer
  2: [ 1]   : control
  3: [ 1- 3]: digital audio playback
  4: [ 1- 7]: digital audio playback
  5: [ 1- 8]: digital audio playback
  6: [ 1- 9]: digital audio playback
  7: [ 1- 0]: hardware dependent
  8: [ 0]   : control
  9: [ 0- 0]: digital audio playback
 10: [ 0- 0]: digital audio capture
 11: [ 0- 2]: digital audio capture
 12: [ 0- 4]: digital audio capture
 13: [ 0- 1]: digital audio playback
 14: [ 0- 1]: digital audio capture
 15: [ 0- 0]: hardware dependent
 33:        : timer
01-00: HDA Codec 0
00-00: HDA Codec 0
00-00: CA0132 Analog : CA0132 Analog : playback 1 : capture 1
00-01: CA0132 Digital : CA0132 Digital : playback 1 : capture 1
00-02: CA0132 Analog Mic-In2 : CA0132 Analog Mic-In2 : capture 1
00-04: CA0132 What U Hear : CA0132 What U Hear : capture 1
01-03: HDMI 0 : HDMI 0 : playback 1
01-07: HDMI 1 : HDMI 1 : playback 1
01-08: HDMI 2 : HDMI 2 : playback 1
01-09: HDMI 3 : HDMI 3 : playback 1
Client info
  cur  clients : 1
  peak clients : 1
  max  clients : 192


Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
total 152
-rw-r--r-- 1 root root  1415 Feb 15 03:34 analog-input-aux.conf
-rw-r--r-- 1 root root  2056 Feb 15 03:34 analog-input.conf
-rw-r--r-- 1 root root  5769 Feb 15 03:34 analog-input.conf.common
-rw-r--r-- 1 root root  2185 Feb 15 03:34 analog-input-dock-mic.conf
-rw-r--r-- 1 root root  1420 Feb 15 03:34 analog-input-fm.conf
-rw-r--r-- 1 root root  2196 Feb 15 03:34 analog-input-front-mic.conf
-rw-r--r-- 1 root root  2298 Feb 15 03:34 analog-input-headphone-mic.conf
-rw-r--r-- 1 root root  2360 Feb 15 03:34 analog-input-headset-mic.conf
-rw-r--r-- 1 root root  2797 Feb 15 03:34 analog-input-internal-mic-always.conf
-rw-r--r-- 1 root root  3155 Feb 15 03:34 analog-input-internal-mic.conf
-rw-r--r-- 1 root root  2486 Feb 15 03:34 analog-input-linein.conf
-rw-r--r-- 1 root root  2662 Feb 15 03:34 analog-input-mic.conf
-rw-r--r-- 1 root root  1330 Feb 15 03:34 analog-input-mic.conf.common
-rw-r--r-- 1 root root  1457 Feb 15 03:34 analog-input-mic-line.conf
-rw-r--r-- 1 root root  2185 Feb 15 03:34 analog-input-rear-mic.conf
-rw-r--r-- 1 root root  1425 Feb 15 03:34 analog-input-tvtuner.conf
-rw-r--r-- 1 root root  1385 Feb 15 03:34 analog-input-video.conf
-rw-r--r-- 1 root root  1929 Feb 15 03:34 analog-output.conf
-rw-r--r-- 1 root root 10609 Feb 15 03:34 analog-output.conf.common
-rw-r--r-- 1 root root  2139 Feb 15 03:34 analog-output-headphones-2.conf
-rw-r--r-- 1 root root  3147 Feb 15 03:34 analog-output-headphones.conf
-rw-r--r-- 1 root root  4095 Feb 15 03:34 analog-output-lineout.conf
-rw-r--r-- 1 root root  1993 Feb 15 03:34 analog-output-mono.conf
-rw-r--r-- 1 root root  3725 Feb 15 03:34 analog-output-speaker-always.conf
-rw-r--r-- 1 root root  4521 Feb 15 03:34 analog-output-speaker.conf
-rw-r--r-- 1 root root   159 Feb 15 03:34 hdmi-output-0.conf
-rw-r--r-- 1 root root   161 Feb 15 03:34 hdmi-output-1.conf
-rw-r--r-- 1 root root   161 Feb 15 03:34 hdmi-output-2.conf
-rw-r--r-- 1 root root   161 Feb 15 03:34 hdmi-output-3.conf
-rw-r--r-- 1 root root   163 Feb 15 03:34 hdmi-output-4.conf
-rw-r--r-- 1 root root   163 Feb 15 03:34 hdmi-output-5.conf
-rw-r--r-- 1 root root   163 Feb 15 03:34 hdmi-output-6.conf
-rw-r--r-- 1 root root   163 Feb 15 03:34 hdmi-output-7.conf
-rw-r--r-- 1 root root   712 Feb 15 03:34 iec958-stereo-output.conf

```

One thing I noticed is that in my Alsa mixers I cannot increase or decrease the volume on anything besides master and PCM:
 [ATTACH=CONFIG]279397[/ATTACH]

I am currently working through steps 10 and beyond in the troubleshooting - will update if I find the solution!



EDIT:

I used hdajackretask to install bootoverride - with I have solved one problem: my computer is able to detect the headphone jack and also detect when I plug/unplug my headphones. As you can see from the screenshot below there is audio "playing" on this output but there is no audio in my headphones. If I unplug the headphones the audio stops "playing" so there is something going right here.

The other thing to add is muting and unputing things (besides master/pcm) has NO effect on the audio playing in pavucontrol (i'm not sure if that is  expected)>




[ATTACH=CONFIG]279400[/ATTACH]

---

### Post by boombam123 on 2018-04-21
Update: I think the problem is my headphone jack is not recognized. I see S/PDIF as an output but my headphones do not get detected. When I select analog duplex in pavucontrol it says "headphones (unplugged)"

---

### Post by lisati on 2018-04-21
I see you asked a [similar question]("https://ubuntuforums.org/showthread.php?t=2312773") about a year ago. Did you ever get that solved?

Back in the day when I first used Ubuntu, nearly 11 years ago, the sound didn't work properly with a "clean" install of Feisty (7.04). Making sure that I had applied all updates helped resolve the issue I was having. I would advise making sure that everything is up to date before troubleshooting begins.

What version and flavour of Ubuntu are you using?

---

### Post by boombam123 on 2018-04-21
> **lisati said:**
> I see you asked a [similar question]("https://ubuntuforums.org/showthread.php?t=2312773") about a year ago. Did you ever get that solved?

Back in the day when I first used Ubuntu, nearly 11 years ago, the sound didn't work properly with a "clean" install of Feisty (7.04). Making sure that I had applied all updates helped resolve the issue I was having. I would advise making sure that everything is up to date before troubleshooting begins.

What version and flavour of Ubuntu are you using?

This is actually the same issue from a year ago. I gave up trying last year due to many hours of frustration and used windows instead. But now I need Ubuntu and it would be ideal to have audio in my headphones. 

Sorry, should I have reused the thread? I actually had forgotten about the thread.


I have made sure the alsa drivers are up to date. I am not sure what else I can update?

I am using ubuntu 16.04 LTS (xenial)

---

### Post by lisati on 2018-04-21
Thanks for the update. 

I'm going to step back to allow help from forum users who might might be more knowledgeable of sound issues.

---

### Post by Yellow Pasque on 2018-04-22
You need to enable these in alsamixer (press 'm''):
```
Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
```

---

