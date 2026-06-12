---
title: "Hardware is fine - microphone doesn't work"
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by kfinnie on 2006-09-10
Tried the comprehensive audio guide - no avail.
I'm dual-booting with XP - sound and microphone work great under XP.
Under Dapper, audio is fine but no sound from microphone - tried with Ekiga and Sound Recorder. Alsamixer shows microphone as active.

Help will be appreciated.

---

### Post by eärendil on 2006-09-20
same thing occurs to me...I've already selected mic for capture in the gnome volume control, but nothing....playback is fine, capture (mic or line in, doesn't matter) is the problem.

My card is a SB PCI512 [CT 4790]

---

### Post by ryu kun on 2006-09-29
Same problem here...

I've tried OSS and ALSA drivers but nothing changed.

Thanks to this annoying issue, I have to switch to Windows for any audio conversation. :(

---

### Post by kfinnie on 2006-10-06
More grist for the mill: Here is the output of aadebug for my system.

ALSA Audio Debug v0.1.0 - Thu Oct  5 23:29:17 PDT 2006
[http://alsa.opensrc.org/index.php?page=aadebug](http://alsa.opensrc.org/index.php?page=aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux tiger 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_intel8x0           33692  1
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd_mpu401              6728  0
snd_mpu401_uart         7808  1 snd_mpu401
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  1 snd_rawmidi
snd                    55268  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
0 [CK8S           ]: NFORCE - NVidia CK8S
                     NVidia CK8S with ALC850 at 0xff6fb000, irq 193
1 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x300, irq 5
 18: [0- 2]: digital audio playback
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 40: [1- 0]: raw midi
 32: [1- 0]: ctl
 33:       : timer
cat: /proc/asound/hwdep: No such file or directory
00-00: Intel ICH : NVidia CK8S : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : NVidia CK8S - MIC ADC : capture 1
00-02: Intel ICH - IEC958 : NVidia CK8S - IEC958 : playback 1
cat: /proc/asound/seq/clients: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  controlC1  midiC1D0  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D2p  timer

CPU -------------------------------------------------------
model name      : AMD Sempron(tm) Processor 2800+
cpu MHz         : 1607.638

RAM -------------------------------------------------------
MemTotal:      1035904 kB
SwapTotal:     2634652 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

---

### Post by Garyu on 2007-02-03
I'm having this problem too. Anyone found a fix?

---

### Post by odzx on 2007-02-07
same problem here
cant get anything out of the mic

---

### Post by tribunal on 2007-02-07
Please, show output of "amixer" cmd here
If it is not installed - you can install it as a part of ALSA (I'm sorry, cannot look at my own Kubuntu, cause I'm at job now)

---

### Post by Garyu on 2007-02-07
OK, tribunal helped me get this thing working, so let's see if I can replicate it. 

This was my original output of amixer:
```

Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [on]
  Front Right: Playback 25 [81%] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [on]
  Front Right: Playback 0 [0%] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [on]
  Front Right: Playback 25 [81%] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [on]
  Front Right: Playback 25 [81%] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [on]
  Front Right: Playback 0 [0%] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [on]
  Front Right: Playback 25 [81%] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [on]
  Front Right: Capture 0 [0%] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [on]
  Front Right: Capture 0 [0%] [on]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'

```
And now my output from amixer looks like this:
```

Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [on]
  Front Right: Playback 25 [81%] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [on]
  Front Right: Playback 25 [81%] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [on]
  Front Right: Playback 25 [81%] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [on]
  Front Right: Playback 23 [74%] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [on]
  Front Right: Playback 25 [81%] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [on]
  Front Right: Capture 31 [100%] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [on]
  Front Right: Capture 31 [100%] [on]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'

```

So what we did was, first I installed KMix (sudo apt-get install kmix). In KMix under the third tab "Switches" I changed to Front mic, and then back to Mic, and then back again, but none of this did much difference. But I had alsamixergui open in the background and realized that the "Mic" volume slider here was turned off all of a sudden (it had volume up previous to this). So I turned it on again in alsamixergui. Now if I yelled in the mic a tiny sound would come out of the speakers at high volume. So after this, I opened up alsamixer in the terminal and pressed TAB once. From here I could set Capture and Capture1 to maximum volumes. (I guess this is the same as "Mic boost"). So now it works! =)

I was doing some other things too by tribunal's suggestion, but what I really think got things going was
1) Front mic / Mic flipping in KMix
2) Turning on Mic in alsamixergui
3) Raising capture volumes in alsamixer (not alsamixergui)

Hope this helps someone else out there... :)

---

### Post by odzx on 2007-02-08
ok . amixer output is:
> Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 7 [26%] [on]
  Front Right: Playback 7 [26%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 20
  Front Left: Capture 20 [100%] [on]
  Front Right: Capture 20 [100%] [on]

it seems like edgy does not recognize my mic. I tried pluging it both in line in and mic socket and got the same results.

---

### Post by danielph on 2007-02-11
> **Garyu said:**
> OK, tribunal helped me get this thing working, so let's see if I can replicate it. 

This was my original output of amixer:


Garyu: from the output below it looks like the only difference here is the volume of the devices:
```
dan[~]$ diff file1 file2
26,27c26,27
<   Front Left: Playback 0 [0%] [on]
<   Front Right: Playback 0 [0%] [on]
---
>   Front Left: Playback 31 [100%] [on]
>   Front Right: Playback 31 [100%] [on]
57,58c57,58
<   Front Left: Playback 0 [0%] [on]
<   Front Right: Playback 0 [0%] [on]
---
>   Front Left: Playback 23 [74%] [on]
>   Front Right: Playback 23 [74%] [on]
71,72c71,72
<   Front Left: Playback 0 [0%] [off]
<   Front Right: Playback 0 [0%] [off]
---
>   Front Left: Playback 31 [100%] [on]
>   Front Right: Playback 31 [100%] [on]
77,78c77,78
<   Front Left: Capture 0 [0%] [on]
<   Front Right: Capture 0 [0%] [on]
---
>   Front Left: Capture 31 [100%] [on]
>   Front Right: Capture 31 [100%] [on]
83,84c83,84
<   Front Left: Capture 0 [0%] [on]
<   Front Right: Capture 0 [0%] [on]
---
>   Front Left: Capture 31 [100%] [on]
>   Front Right: Capture 31 [100%] [on]

```I am had the same problem with no Mic input in applications or using the pipe test in gnome (System, Prefs, Sound). The Mic will feedback if switched on. 

This is a new problem. In the last week I guess and the only thing I can think of is there was a new kernel update. Can someone advise if I have all the modules loaded for using the Mic through ALSA. I have tried skype, Ekiga, and audacity, which all worked last week, but not now.

Here is output from aadebug:

```
dan[~]$ ./aadebug
ALSA Audio Debug v0.1.0 - Sun Feb 11 16:38:41 CET 2007
http://alsa.opensrc.org/aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux morocco 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_intel8x0           34844  5 
snd_usb_audio          80416  1 
snd_usb_lib            18816  1 snd_usb_audio
snd_rawmidi            27264  1 snd_usb_lib
snd_seq_device          9868  1 snd_rawmidi
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_hwdep              10756  1 snd_usb_audio
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  2 snd_pcm_oss
snd_pcm                84612  4 snd_intel8x0,snd_usb_audio,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  20 snd_intel8x0,snd_usb_audio,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
cat: /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  controlC1  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC1D0c  timer

CPU -------------------------------------------------------
model name      : AMD Athlon(tm) XP 2800+
cpu MHz         : 2087.648

RAM -------------------------------------------------------
MemTotal:       775584 kB
SwapTotal:           0 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 02)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

```and amixer
```
dan[~]$ amixer |grep Mic
Simple mixer control 'Mic',0
Simple mixer control 'Mic Boost (+20dB)',0
Simple mixer control 'Mic Select',0
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
  Items: 'Mix' 'Mic'

```I 

Edit: [SIZE=5]**HERE IS THE SOLUTION**[/SIZE]:
Run alsamixer in console.. Go into the playback "tab" and mute mic. Go into the capture tab, I think f4 and hit space on Mic and space on capture until L R Captur is red under both Mic and Capture. make sure you turn up the volume using the up arrows.

Thanks to [http://forums.gentoo.org/viewtopic-t-428841-highlight-krec+record.html](http://forums.gentoo.org/viewtopic-t-428841-highlight-krec+record.html) post from **ElSenorPantelone**

---

### Post by Garyu on 2007-02-12
> **danielph said:**
> Garyu: from the output below it looks like the only difference here is the volume of the devices:

It may be true that the volume settings is the only thing that differs in the amixer output, but that was not the problem I had. I've been messing with volume settings a lot with no difference. What was different about the latest approach was that I used KMix first. Exactly how that made a difference - I have no idea. But I don't care either, the important thing for me is that it is working. 

ALSA seems to have a Windows configuration though. Do some random stuff, it starts working. :-P

---

### Post by carloslosgrande on 2007-02-12
Yup, Danielph, that fixed it for me. Thanks!:guitar:

---

### Post by Admiral-Cyclops on 2007-02-15
> **danielph said:**
> Edit: [SIZE=5]**HERE IS THE SOLUTION**[/SIZE]:
Run alsamixer in console.. Go into the playback "tab" and mute mic. Go into the capture tab, I think f4 and hit space on Mic and space on capture until L R Captur is red under both Mic and Capture. make sure you turn up the volume using the up arrows.

Thanks to [http://forums.gentoo.org/viewtopic-t-428841-highlight-krec+record.html](http://forums.gentoo.org/viewtopic-t-428841-highlight-krec+record.html) post from **ElSenorPantelone**

I tried this, but it did not work.

I have tried everything I can think of, from just enabling the mic and not capture, to the 20+ boost, everything I can think of.

Any ideas?

---

### Post by danielph on 2007-02-15
Go to alsamixer and to playback tab and check that you can here your own voice when you enable Mic and turn up the volume. The "M" key toggles mute and shows [Off] when muted. Gnome volume control does this as well, but alsa is more consistent for trouble shooting. You will obviously need audio output working and speakers attached.

---

### Post by Michelpt on 2007-02-18
Hello, help me pls, I try to use alsamixer, but in Cature-Mode under "Mic" and "Capture" is a red written L R CAPTURE I cannot put the volume up at "Mic"... However I can do this at "Playback" tab. Mic is working (I hear my voice over the speakers), but when I try to call (Gizmo) I can hear, but nobody hears me. I try different ways with muted microphone and not muted. Also sound system is running with a "Full duplex" option. "amixer |grep Mic" outputs:

Simple mixer control 'Mic',0
Simple mixer control 'Mic Boost (+20dB)',0
Simple mixer control 'Mic Select',0
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
  Items: 'Mix' 'Mic'


I don't know what else to do because I am new in Ubuntu, thanx in advance for your help and some advise.

---

### Post by Cappy on 2007-03-02
Aha! This solved my problem! Thank you for posting!

---

### Post by musicinmybrain on 2007-03-02
Same deal here. No matter what I set in alsamixer, I can't record. I've never gotten this to work on Ubuntu, and I've been using it since Hoary. I'm using a Turtle Beach Santa Cruz soundcard, which works fine otherwise, and I can echo the mic input through the speakers just fine; I just can't capture it! It's really quite obnoxious. I've been thinking of buying a new soundcard (M-Audio Audiophile 2496) but I'm hesitant to do so when chances are I couldn't record on it either, even though it's allegedly well-supported by Linux.

---

### Post by Cappy on 2007-03-02
You should try giving your "amixer" output. You should look for the parts that say "Mic", "Capture", and anything with "* Capture". It should say Capture On or 100% Capture On. The reason you can hear yourself but you can't record is that your capture volume is low or [Off]. It should be fixable.
The best way to test if your mic is working is to use "vumeter -r &" and then change your settings. You don't need to restart vumeter everytime you make a change to see if it works either - just leave it on continually while you are changing settings.

Michelpt: Use the up arrow on your keyboard while over Mic/Capture to get your microphone to work. Alternatively, you can also double click on the alsamixer (the sound icon) in the notification area (the area with all the icons of stuff currently running). You can goto Edit --> Preferences and click all of the checkboxes. Then, you should be able to goto the "Capture" tab and turn up the Capture volume too.
If you end up posting "amixer" output, don't use grep because any output from it is useless.

musicinmybrain: You said the sound card works on the live cd - have you tried comparing the amixer output on the live cd to your installed OS?

---

### Post by alexmoon on 2007-03-03
Sorry, I'm veryvery new to Ubuntu and having a bit of a hard time understanding some of the basics here, I think.

I'm trying to get my microphone to work with Skype (or indeed, at all), and having no luck. I've had a look at quite a few different threads on the ubuntu forums, as well as a few on the skype forums.

After reading and trying things for a couple of hours I worked out that I didn't actually have alsamixer installed, and installed it.

I tried to use the GUI to change some of the settings for alsamixer (including turning on the "+20dB boost" option), but it doesn't seem to have made much difference. I've also tried opening alsamixer in the terminal and going into [capture] (using the TAB key). Then made sure that it said "CAPTUR" in red over both "Mic" and "Capture".

"Capture" is at full value (100<>100) but "Mic" has no bar above it. When I press the up arrows for it nothing happens.

Thank you for any advice you can give me.

---

### Post by musicinmybrain on 2007-03-03
I could have overlooked something, but I don't think my capture volume is low or muted.

```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 63 [100%] [on]
  Front Right: Playback 63 [100%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Master',1
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 10 [32%] [off]
  Front Right: Playback 10 [32%] [off]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Center',1
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',1
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control '3D Control - Switch',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 26 [84%] [on]
  Front Right: Playback 26 [84%] [on]
Simple mixer control 'PCM Out Path & Mute',1
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'PCM',1
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [on]
  Front Right: Playback 25 [81%] [on]
Simple mixer control 'Surround',1
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Center',1
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 63
  Mono: Playback 63 [100%] [off]
Simple mixer control 'LFE',1
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 63
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Line',1
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'CD',1
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Boost (+20dB)',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Mic',1
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Video',1
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',1
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Input',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Aux',1
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [on]
  Front Right: Capture 15 [100%] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [on]
  Front Right: Capture 15 [100%] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix',1
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',1
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'ADC',0
  Capabilities: volume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 32767
  Front Left: 32767 [100%] Capture [off]
  Front Right: 32767 [100%] Capture [off]
Simple mixer control 'DAC',0
  Capabilities: volume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 32767
  Front Left: 26214 [80%] Capture [off]
  Front Right: 26214 [80%] Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

```

> **Cappy said:**
> musicinmybrain: You said the sound card works on the live cd - have you tried comparing the amixer output on the live cd to your installed OS?

I said that in a different thread some time ago when I was having trouble getting playback on Edgy. I resolved that problem. I've never gotten microphone (or mixer) capture to work, though, on or off the live cd.

---

### Post by musicinmybrain on 2007-03-03
So now it works. I'm not sure why, though. I tried kmix (despite using Gnome) and there was a reboot in there somewhere. Wish I could post some more helpful "eureka" moment.

---

### Post by garybrlow on 2007-04-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Its a long standing ALSA bug mainly in feisty but the same version might have been applied via updates in edgy/dapper so its related. I myself have no mic/sound capture/recording capabilities as of the moment. Sound capture(mic input etc.) and sound recording features should be working right out of the box like before with no tweaking applied.

Please Read, Review, Confirm the bug and related info here
[https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531). Don't forget to register at launchpad.net if you already haven't done so to post/confirm bugs there and help Ubuntu become better.

Cheers!!!


GaryBrlow :biggrin:

---

### Post by carloslosgrande on 2007-05-03
It seems that since the beta version of Feisty there have been changes that seem to have left some things out of the release version. I had my Mic and skype working fairly well. Upgraded to the new release version (from the CD to clean up some stuff). and now I'm back to square 1.
vumeter shows the mic working.
sound recorder does nothing.
Played around with alsamixer like last time but now no luck. Whats more, now sound recorder says> Your audio capture settings are invalid. Please correct them in the Multimedia settings.
Don't have multimedia settings.
No longer have control over the volume levels except thru alsamixer, ie the volume icon slider makes no difference to the levels.
attachment shows capture is on, etc, etc, as per all the things listed in these forums. I'm gonna try restart and then off to bed, any success will be posted.

---

### Post by Mazrick on 2008-03-18
If you have similar problems...

Try following this post: [http://ubuntuforums.org/showthread.php?p=4540192#post4540192](http://ubuntuforums.org/showthread.php?p=4540192#post4540192)

And make sure to try:

menu item "System/Preferences/Sounds". 
Now go to the "Sounds" tab: Uncheck "Enable software sound mixing (ESD)"
Close the Sound Preferences window.

Reboot and test

This fixed the following message for me:
> Your audio capture settings are invalid. Please correct them in the Multimedia settings
when opening sound recorder

---

### Post by bigbrovar on 2008-05-04
dont know what happened mahn all i know was that i followed ur guide and sound record now works on my freedom hating sony vaio ... first time since i started linux ... i cant thank u enough .. :popcorn:

---

### Post by Th3Professor on 2008-05-06
My hardware's fine, yet mic isn't working properly. I've tried info provided in various threads but none of it has the mic working.

I'm running Ubuntu Studio 8.04 on a new Toshiba laptop.

Any help's greatly appreciated.

---

### Post by cespinal on 2008-05-06
here is my amixer out put: 

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Docking Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 80 [100%] [6.00dB] Playback [off]
  Front Right: 80 [100%] [6.00dB] Playback [off]
Simple mixer control 'External Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 80 [100%] [6.00dB] Playback [off]
  Front Right: 80 [100%] [6.00dB] Playback [off]
Simple mixer control 'Internal Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 80 [100%] [6.00dB] Playback [on]
  Front Right: 80 [100%] [6.00dB] Playback [on]

I am experiencing the same problems... everything seems to work fine but I am not able to record any sounds... BTW my alsamixer does not have much of the features described in this post, specially mic boost.

---

### Post by Th3Professor on 2008-05-10
bump

(more than one of us are still havin' probs with the mic, even after going through current mic-related threads in these forums)

Any input is greatly appreciated. Thanks!

:guitar::guitar::guitar:

---

### Post by cespinal on 2008-05-11
Bawmmmmmp! :)

---

### Post by Th3Professor on 2008-05-12
bump

---

### Post by cespinal on 2008-05-13
bump again... at leat tell me "hey... It just wont work because of ffjdl;fjwel;fjwl;jfowgjwo":lolflag:

---

### Post by Th3Professor on 2008-05-15
bump

(it looks like this is in the archive section now... great.)

we need a new thread. i put one up a few days ago subject: "microphone problems"... though still no response.

---

### Post by cespinal on 2008-05-15
hahahaha Im almot giving up to this!

I installed ubuntu on a Hp Pavilion which is several months  older than mine a couple of days ago and everything worked out of the box!...that led me to think that my sound cards it is just too new.. :(

---

### Post by Th3Professor on 2008-05-15
> **cespinal said:**
> hahahaha Im almot giving up to this!

I installed ubuntu on a Hp Pavilion which is several months  older than mine a couple of days ago and everything worked out of the box!...that led me to think that my sound cards it is just too new.. :(

That might not be the case. The system should be able to handle your soundcard.

---

### Post by cespinal on 2008-05-15
It know :( 

keep me posted when you open a new thread :D

---

### Post by Th3Professor on 2008-05-15
[http://ubuntuforums.org/showthread.php?t=791760](http://ubuntuforums.org/showthread.php?t=791760)

---

