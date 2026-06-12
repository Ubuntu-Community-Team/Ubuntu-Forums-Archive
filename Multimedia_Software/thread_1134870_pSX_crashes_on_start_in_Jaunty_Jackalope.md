---
title: "pSX crashes on start in Jaunty Jackalope"
date: 2009-04-24
forum: Multimedia Software
---

### Post by Anonymoose on 2009-04-24
I just upgraded to 9.04 and now I cannot get pSX (installed from the "http://ubuntu.global-web.us/intrepid binary/" repository) to work. When I run it in the terminal I get this: 

 * PulseAudio configured for per-user sessions
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
/usr/bin/pSX: line 9: 10591 Segmentation fault      ./pSX
 * PulseAudio configured for per-user sessions

I had an inkling it maybe had something to do with the script that tries to kill pulseaudio on start. So I tried gksu killall pulseaudio, and sudo /etc/init.d/pulseaudio stop and pulseaudio -k and then /opt/pSX/pSX, but no combination worked. And when trying to do pulseaudio -k, I got this curious message: 

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.

So I went and added myself and root to pulse, pulse-access and pulse-rt, but I still get this message. And when I try to use sudo, I get: 

E: core-util.c: Home directory /home/anonymous not ours.
E: main.c: Failed to kill daemon: Permission denied

And I couldn't find any material on what to alter the rlimit values and such to do what I want it to do, and I just don't really know what I'm doing. I don't even know if pulse is the issue. I'd really appreciate it if someone could give me an idea on how to get this working, because I really do not want to have to boot into my second HDD just to use 8.10 so I can use my emulator, which I use quite often. Thanks in advance.

---

### Post by Anonymoose on 2009-04-24
bumping

---

### Post by binbash on 2009-04-24
Try this : 

Stop Pulse Audio
start psx
Start Pulse Audio

---

### Post by Anonymoose on 2009-04-24
> **binbash said:**
> Try this : 

Stop Pulse Audio
start psx
Start Pulse Audio

No go. 

I have since restarted and no longer get the error about not being a member of pulse-rt when I am, although it still didn't do anything. However, I've discovered running pSX from the terminal in sudo (but making it the command for the launcher doesn't) makes it work for reasons I don't quite understand, albeit not as well as it used to, or at least it seems that way to me. I'm still curious as to why this makes a difference and if there's any way I could get it to work like it used to in Intrepid. Thanks for the feedback.

---

### Post by Moridin333 on 2009-05-02
The problem is that pulse audio will restart on its own (in Jaunty) after you kill the process.  You can turn this off in a configuration file (I forgot which one) but I still got a seg fault.

while I hate to suggest this, pSX will work even with pulseaudio on with sudo.

I've got a little script to start pSX on my desktop.

metacity --replace &
gksudo /home/david/pSX/pSX
compiz --replace &


this also turns off compiz to stop any screen tearing.

---

### Post by DeathOnJuice on 2009-05-03
Darn, I thought that was what was causing the problem. I'd still be interested in that configuration file, though, in case it provides any leads. I really don't like running in sudo.

---

### Post by Moridin333 on 2009-05-04
I assume you're talking about ~.pSX/psx.ini

here it is

```
[Paths]
SaveStatePath=/home/david/.pSX/saves
MemoryCardPath=/home/david/.pSX/cards
CDImagePath=cdimages
ScreenShotsPath=/home/david/.pSX/screenshots

[BIOS]
PS1=bios/scph1001.bin
PS2=bios/scph39001.bin

[Input]
JoystickDevice1=
Key1Select=65
Key1Start=36
Key1Up=111
Key1Right=114
Key1Down=116
Key1Left=113
Key1L2=37
Key1R2=105
Key1L1=50
Key1R1=62
Key1Triangle=38
Key1Circle=39
Key1Cross=52
Key1Square=53
Key1L3=-1
Key1R3=-1
Key1LStickX=-1
Key1LStickY=-1
Key1RStickX=-1
Key1RStickY=-1
Joy1SelectType=0
Joy1SelectDef=-1
Joy1StartType=0
Joy1StartDef=-1
Joy1UpType=0
Joy1UpDef=-1
Joy1RightType=0
Joy1RightDef=-1
Joy1DownType=0
Joy1DownDef=-1
Joy1LeftType=0
Joy1LeftDef=-1
Joy1L2Type=0
Joy1L2Def=-1
Joy1R2Type=0
Joy1R2Def=-1
Joy1L1Type=0
Joy1L1Def=-1
Joy1R1Type=0
Joy1R1Def=-1
Joy1TriangleType=0
Joy1TriangleDef=-1
Joy1CircleType=0
Joy1CircleDef=-1
Joy1CrossType=0
Joy1CrossDef=-1
Joy1SquareType=0
Joy1SquareDef=-1
Joy1L3Type=0
Joy1L3Def=-1
Joy1R3Type=0
Joy1R3Def=-1
Joy1LStickXType=0
Joy1LStickXDef=-1
Joy1LStickYType=0
Joy1LStickYDef=-1
Joy1RStickXType=0
Joy1RStickXDef=-1
Joy1RStickYType=0
Joy1RStickYDef=-1
Joy1Rumble=1
JoystickDevice2=
Key2Select=-1
Key2Start=-1
Key2Up=-1
Key2Right=-1
Key2Down=-1
Key2Left=-1
Key2L2=-1
Key2R2=-1
Key2L1=-1
Key2R1=-1
Key2Triangle=-1
Key2Circle=-1
Key2Cross=-1
Key2Square=-1
Key2L3=-1
Key2R3=-1
Key2LStickX=-1
Key2LStickY=-1
Key2RStickX=-1
Key2RStickY=-1
Joy2SelectType=0
Joy2SelectDef=-1
Joy2StartType=0
Joy2StartDef=-1
Joy2UpType=0
Joy2UpDef=-1
Joy2RightType=0
Joy2RightDef=-1
Joy2DownType=0
Joy2DownDef=-1
Joy2LeftType=0
Joy2LeftDef=-1
Joy2L2Type=0
Joy2L2Def=-1
Joy2R2Type=0
Joy2R2Def=-1
Joy2L1Type=0
Joy2L1Def=-1
Joy2R1Type=0
Joy2R1Def=-1
Joy2TriangleType=0
Joy2TriangleDef=-1
Joy2CircleType=0
Joy2CircleDef=-1
Joy2CrossType=0
Joy2CrossDef=-1
Joy2SquareType=0
Joy2SquareDef=-1
Joy2L3Type=0
Joy2L3Def=-1
Joy2R3Type=0
Joy2R3Def=-1
Joy2LStickXType=0
Joy2LStickXDef=-1
Joy2LStickYType=0
Joy2LStickYDef=-1
Joy2RStickXType=0
Joy2RStickXDef=-1
Joy2RStickYType=0
Joy2RStickYDef=-1
Joy2Rumble=1
KeyStatusDisplay=23
KeyMute=104
KeyIncVolume=86
KeyDecVolume=82
KeyIncXAVolume=117
KeyDecXAVolume=112
KeySoundStatus=106
KeyFastForward=22
KeyShowVram=95
KeyIncGamma=81
KeyDecGamma=89
KeyIncBrightness=80
KeyDecBrightness=88
KeyIncContrast=79
KeyDecContrast=87
KeyScreenShot=96
EscapeMode=0

[Controllers]
Controller1Type=-1
Controller2Type=-1

[Cards]
Card1=
Card2=

[Sound]
Frequency=-1
Sync=1
Reverb=1
Interpolate=1
Latency=32
XALatency=20
Device=

[Graphics]
BilinearInterpolation=1
FrameSkip=0
SleepWhenIdle=1
PauseWhenDefocused=1
StatusIcons=0
NTSCWidth=-1
NTSCHeight=-1
NTSCRefresh=-1
PALWidth=-1
PALHeight=-1
PALRefresh=-1
FullscreenVSync=0
WindowedSync=0
Gamma=1.000000
Brightness=0.000000
Contrast=0.000000
ScreenshotFormat=0
FullscreenAdapter=-1
FullscreenAspectRatio=-1
Mode16bit=0

[CDROM]
Driver=-1
SubcodeReading=-1

[Language]
CurrentLanguage=

```

---

