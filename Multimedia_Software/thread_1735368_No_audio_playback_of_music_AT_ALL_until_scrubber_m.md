---
title: "No audio playback of music AT ALL until scrubber moved"
date: 2011-04-21
forum: Multimedia Software
---

### Post by blackdalek on 2011-04-21
I have a problem with audio file playback (all formats - mp3, ogg, etc.). When I try to play a file with rhythmbox or totem, the whole system gets sluggish and the mouse pointer jerks about the screen and there is no sound at all... UNTIL I drag the playback slider along with the mouse for a second, then playback is normal and the mouse pointer and system returns to normal speed... How do I fix this?

Problem is on maverick 10.10

top shows this if run from another machine using ssh...
```

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1760 ilyekkak   9 -11  214m  36m  34m S 93.7  3.6  15:10.41 pulseaudio         
10608 ilyekkak  20   0  549m  30m  16m S  3.3  3.1   0:02.23 totem              
 8856 root      20   0  207m  44m  15m S  1.0  4.5   5:41.06 Xorg               
 9293 ilyekkak  20   0  299m  27m  13m S  1.0  2.7   2:25.11 xchat              
 1068 mysql     20   0  184m 3628 1208 S  0.3  0.4   0:07.40 mysqld             
10422 ilyekkak  20   0  547m  90m  29m S  0.3  9.0   0:09.81 firefox-bin        
10619 ilyekkak  20   0 19276 1320  944 R  0.3  0.1   0:00.06 top                
    1 root      20   0 23892 1796 1152 S  0.0  0.2   0:00.49 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S  0.0  0.0   0:01.17 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      20   0     0    0    0 R  0.0  0.0   0:01.33 events/0           
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns              
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr
```

---

### Post by blackdalek on 2011-04-21
The problem goes away when pulseaudio is completely removed and replaced with alsa.

The problem resurfaces when pulseaudio is installed again.

---

### Post by blackdalek on 2011-04-24
Also, when I uninstall pulseaudio (to fix the no audio problem), I get a new problem when I install alsa - I can only get 2 output channels (front left and right). None of the other speakers work. All 6 speakers used to work in pulseaudio before pulseaudio stopped working properly.

---

### Post by blackdalek on 2011-04-25
I guess no one else has this problem then.

---

### Post by blackdalek on 2011-04-25
Maybe I am asking the wrong question. I will rephrase...

How do I stop pulseaudio using up 99% of CPU cycles and almost locking up the computer while it fails to output any sound when attempting to play audio?

---

### Post by blackdalek on 2011-04-25
bump...

---

### Post by blackdalek on 2011-04-26
So.... any theories on this pulseaudio issue at all?

---

### Post by lidex on 2011-04-27
Yeah, don't recall seeing this before. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by blackdalek on 2011-04-28
Here is my alsa-info link URL -
[http://www.alsa-project.org/db/?f=b18ac036c4c54a4a69bcca52960dc72f42e196fb](http://www.alsa-project.org/db/?f=b18ac036c4c54a4a69bcca52960dc72f42e196fb)

---

### Post by lidex on 2011-04-28
> **blackdalek said:**
> Here is my alsa-info link URL -
[http://www.alsa-project.org/db/?f=b18ac036c4c54a4a69bcca52960dc72f42e196fb](http://www.alsa-project.org/db/?f=b18ac036c4c54a4a69bcca52960dc72f42e196fb)

According to this pulse is running - so you re-installed it? When was the last time you updated your system? Try this:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo update-grub
```
**Reboot**

---

### Post by blackdalek on 2011-04-28
> **lidex said:**
> According to this pulse is running - so you re-installed it? When was the last time you updated your system?

Well, I thought the idea was to try and fix pulseaudio on my system so I re-installed it again. Do you need me to uninstall it again?

This system gets updated every day that there is an update available.

---

### Post by lidex on 2011-04-28
Your current kernel is 35-24, my maverick install is at 35-29 is why i ask.

Try removing your pulse config files:
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
Now these outputs please:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by blackdalek on 2011-04-28
hmm... my mirror is [http://mirror.internode.on.net](http://mirror.internode.on.net)
I don't know why my kernel wasn't updated. I had some trouble connecting to it the other day, but it seemed to be working again.
I will check again and maybe change to a different mirror.
I will be back later to get the other output you ask for.

---

### Post by blackdalek on 2011-04-28
I tried updating but it is not telling me there are any updates above 2.6.35-24

hold on... is this because I am using the 64bit version?

---

### Post by blackdalek on 2011-04-28
output from my terminal -

```
ilyekkakai@ilyekkakai-desktop:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  ilyekkakai   2087 F.... pulseaudio
```

the second command generated output which extended beyond the scroll buffer, so I can only paste the remainder of the output. Also, it hung at the end and did not return to a cursor, so I had to Ctrl-C out of it -

```
D: alsa-mixer.c: Looking at profile output:analog-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround40.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround40:1
I: alsa-util.c: Error opening PCM device surround40:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround40.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround40:1
I: alsa-util.c: Error opening PCM device surround40:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround40.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround40:1
I: alsa-util.c: Error opening PCM device surround40:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround40.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround40:1
I: alsa-util.c: Error opening PCM device surround40:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
D: alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround40.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround40:1
I: alsa-util.c: Error opening PCM device surround40:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-41
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround41:1
I: alsa-util.c: Error opening PCM device surround41:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround41:1
I: alsa-util.c: Error opening PCM device surround41:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround41:1
I: alsa-util.c: Error opening PCM device surround41:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround41:1
I: alsa-util.c: Error opening PCM device surround41:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-41+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
D: alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround41:1
I: alsa-util.c: Error opening PCM device surround41:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-50
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround50:1
I: alsa-util.c: Error opening PCM device surround50:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround50:1
I: alsa-util.c: Error opening PCM device surround50:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround50:1
I: alsa-util.c: Error opening PCM device surround50:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround50:1
I: alsa-util.c: Error opening PCM device surround50:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround50:1
I: alsa-util.c: Error opening PCM device surround50:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-51
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround51:1
I: alsa-util.c: Error opening PCM device surround51:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround51:1
I: alsa-util.c: Error opening PCM device surround51:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround51:1
I: alsa-util.c: Error opening PCM device surround51:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround51:1
I: alsa-util.c: Error opening PCM device surround51:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround51.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround51:1
I: alsa-util.c: Error opening PCM device surround51:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-71
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround71.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround71:1
I: alsa-util.c: Error opening PCM device surround71:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-mono
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround71.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround71:1
I: alsa-util.c: Error opening PCM device surround71:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround71.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround71:1
I: alsa-util.c: Error opening PCM device surround71:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround71.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround71:1
I: alsa-util.c: Error opening PCM device surround71:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.surround71.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM surround71:1
I: alsa-util.c: Error opening PCM device surround71:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.iec958.0:CARD=1,AES0=4,AES1=130,AES2=0,AES3=2'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM iec958:1
I: alsa-util.c: Error opening PCM device iec958:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.iec958.0:CARD=1,AES0=4,AES1=130,AES2=0,AES3=2'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM iec958:1
I: alsa-util.c: Error opening PCM device iec958:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.iec958.0:CARD=1,AES0=4,AES1=130,AES2=0,AES3=2'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM iec958:1
I: alsa-util.c: Error opening PCM device iec958:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.iec958.0:CARD=1,AES0=4,AES1=130,AES2=0,AES3=2'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM iec958:1
I: alsa-util.c: Error opening PCM device iec958:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.iec958.0:CARD=1,AES0=4,AES1=130,AES2=0,AES3=2'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM iec958:1
I: alsa-util.c: Error opening PCM device iec958:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.iec958.0:CARD=1,AES0=4,AES1=130,AES2=0,AES3=2'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM iec958:1
I: alsa-util.c: Error opening PCM device iec958:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.iec958.0:CARD=1,AES0=4,AES1=130,AES2=0,AES3=2'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM iec958:1
I: alsa-util.c: Error opening PCM device iec958:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.iec958.0:CARD=1,AES0=4,AES1=130,AES2=0,AES3=2'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM iec958:1
I: alsa-util.c: Error opening PCM device iec958:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.iec958.0:CARD=1,AES0=4,AES1=130,AES2=0,AES3=2'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM iec958:1
I: alsa-util.c: Error opening PCM device iec958:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.iec958.0:CARD=1,AES0=4,AES1=130,AES2=0,AES3=2'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM iec958:1
I: alsa-util.c: Error opening PCM device iec958:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:1
I: alsa-util.c: Error opening PCM device a52:1: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 1
I: (alsa-lib)pcm.c: Unknown PCM hdmi:1
I: alsa-util.c: Error opening PCM device hdmi:1: Invalid argument
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 1
I: (alsa-lib)pcm.c: Unknown PCM hdmi:1
I: alsa-util.c: Error opening PCM device hdmi:1: Invalid argument
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 1
I: (alsa-lib)pcm.c: Unknown PCM hdmi:1
I: alsa-util.c: Error opening PCM device hdmi:1: Invalid argument
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 1
I: (alsa-lib)pcm.c: Unknown PCM hdmi:1
I: alsa-util.c: Error opening PCM device hdmi:1: Invalid argument
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 1
I: (alsa-lib)pcm.c: Unknown PCM hdmi:1
I: alsa-util.c: Error opening PCM device hdmi:1: Invalid argument
D: alsa-mixer.c: Looking at profile input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D0c' failed (-2)
I: alsa-util.c: Error opening PCM device hw:1: No such file or directory
D: alsa-mixer.c: Looking at profile input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.front.0:CARD=1'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM front:1
I: alsa-util.c: Error opening PCM device front:1: No such file or directory
D: alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D0c' failed (-2)
I: alsa-util.c: Error opening PCM device hw:1: No such file or directory
D: alsa-mixer.c: Looking at profile input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.iec958.0:CARD=1,AES0=4,AES1=130,AES2=0,AES3=2'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM iec958:1
I: alsa-util.c: Error opening PCM device iec958:1: No such file or directory
D: alsa-mixer.c: Looking at profile input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)confmisc.c: Unable to find definition 'cards.MPU-401 UART.pcm.iec958.0:CARD=1,AES0=4,AES1=130,AES2=0,AES3=2'
I: (alsa-lib)conf.c: function snd_func_refer returned error: No such file or directory
I: (alsa-lib)conf.c: Evaluate error: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM iec958:1
I: alsa-util.c: Error opening PCM device iec958:1: No such file or directory
E: module-alsa-card.c: Failed to find a working profile.
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
I: module-udev-detect.c: Card /devices/virtual/sound/card1 (alsa_card.1) failed to load module.
I: module-udev-detect.c: Found 2 cards.
I: module.c: Loaded "module-udev-detect" (index: #5; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-bluetooth-discover.so': failure
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #6; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-gconf.so': failure
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci-0000_00_04.0.analog-stereo'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci-0000_00_04.0.analog-stereo'.
I: module.c: Loaded "module-default-device-restore" (index: #8; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #9; argument: "").
I: module.c: Loaded "module-always-sink" (index: #10; argument: "").
I: module.c: Loaded "module-intended-roles" (index: #11; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_04.0.analog-stereo becomes idle, timeout in 5 seconds.
D: module-suspend-on-idle.c: Source alsa_input.pci-0000_00_04.0.analog-stereo becomes idle, timeout in 5 seconds.
I: module.c: Loaded "module-suspend-on-idle" (index: #12; argument: "").
D: dbus-util.c: Successfully connected to D-Bus system bus 47b86c37fb1242e3435eb70700000014 as :1.52
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session2"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session2
I: module.c: Loaded "module-console-kit" (index: #13; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #14; argument: "").
D: main.c: Got org.pulseaudio.Server!
I: main.c: Daemon startup complete.
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
D: alsa-sink.c: Wakeup from ALSA!
D: alsa-sink.c: Wakeup from ALSA!
I: client.c: Created 1 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 16, local 16
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
D: module-augment-properties.c: Looking for .desktop file for gnome-settings-daemon
D: alsa-sink.c: Wakeup from ALSA!
I: alsa-sink.c: Underrun!
I: alsa-sink.c: Increasing wakeup watermark to 30.00 ms
D: alsa-source.c: Wakeup from ALSA!
I: module-suspend-on-idle.c: Source alsa_input.pci-0000_00_04.0.analog-stereo idle for too long, suspending ...
D: source.c: Suspend cause of source alsa_input.pci-0000_00_04.0.analog-stereo is 0x0004, suspending
I: alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_04.0.analog-stereo idle for too long, suspending ...
D: sink.c: Suspend cause of sink alsa_output.pci-0000_00_04.0.analog-stereo is 0x0004, suspending
I: alsa-sink.c: Device suspended...
D: reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio0 changed: not busy
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
```

this bit was in red text -
```
E: module-alsa-card.c: Failed to find a working profile.
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
```

This is the exit output -
```
^CI: main.c: Got signal SIGINT.
I: main.c: Exiting.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-device-restore" (index: #0).
I: module.c: Unloaded "module-device-restore" (index: #0).
I: module.c: Unloading "module-stream-restore" (index: #1).
I: module.c: Unloaded "module-stream-restore" (index: #1).
I: module.c: Unloading "module-card-restore" (index: #2).
I: module.c: Unloaded "module-card-restore" (index: #2).
I: module.c: Unloading "module-augment-properties" (index: #3).
I: module.c: Unloaded "module-augment-properties" (index: #3).
I: module.c: Unloading "module-alsa-card" (index: #4).
D: alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.pci-0000_00_04.0.analog-stereo"
I: source.c: Freeing source 0 "alsa_output.pci-0000_00_04.0.analog-stereo.monitor"
D: core-subscribe.c: Dropped redundant event due to change event.
D: alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci-0000_00_04.0.analog-stereo"
I: card.c: Freed 0 "alsa_card.pci-0000_00_04.0"
I: module.c: Unloaded "module-alsa-card" (index: #4).
I: module.c: Unloading "module-udev-detect" (index: #5).
I: module.c: Unloaded "module-udev-detect" (index: #5).
I: module.c: Unloading "module-esound-protocol-unix" (index: #6).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #6).
I: module.c: Unloading "module-native-protocol-unix" (index: #7).
I: client.c: Freed 1 "GNOME Volume Control Media Keys"
I: module.c: Unloaded "module-native-protocol-unix" (index: #7).
I: module.c: Unloading "module-default-device-restore" (index: #8).
I: module.c: Unloaded "module-default-device-restore" (index: #8).
I: module.c: Unloading "module-rescue-streams" (index: #9).
I: module.c: Unloaded "module-rescue-streams" (index: #9).
I: module.c: Unloading "module-always-sink" (index: #10).
I: module.c: Unloaded "module-always-sink" (index: #10).
I: module.c: Unloading "module-intended-roles" (index: #11).
I: module.c: Unloaded "module-intended-roles" (index: #11).
I: module.c: Unloading "module-suspend-on-idle" (index: #12).
I: module.c: Unloaded "module-suspend-on-idle" (index: #12).
I: module.c: Unloading "module-console-kit" (index: #13).
D: module-console-kit.c: Removing session /org/freedesktop/ConsoleKit/Session2
I: client.c: Freed 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session2"
I: module.c: Unloaded "module-console-kit" (index: #13).
I: module.c: Unloading "module-position-event-sounds" (index: #14).
I: module.c: Unloaded "module-position-event-sounds" (index: #14).
I: main.c: Daemon terminated.
```

---

### Post by blackdalek on 2011-04-28
Um... I don't know what happened, but I just launched rhythmbox to see what happened and the music started playing with no hiccups?? weird... :confused:
I just checked my packages.. and pulseaudio is indeed still installed and running... only this time without incident.

EDIT: Ok, I just found out that the problem still exists. Only this time *some* songs are now unaffected and will play normally.

---

### Post by blackdalek on 2011-04-28
scratch that - it seems now I am back to square 1.

I didn't touch anything except for rhythmbox and now all files are again unplayable. It must have been some freak coincidence that allowed it to play a few songs then it gave up and went back to not working.

Maybe it can only handle playing 2 or 3 songs shortly after a reboot, then dies.

---

### Post by lidex on 2011-04-28
Let's try this. 
```
echo "options snd-intel8x0 index=0 ac97_quirk=3 enable=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by blackdalek on 2011-04-29
> **lidex said:**
> Let's try this. 


Ok, I did that and rebooted. Problem still persists.

---

### Post by lidex on 2011-04-29
Hmmm. Try paring it down to just this:
```
options snd-intel8x0 ac97_quirk=3
```
Open with:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by blackdalek on 2011-04-30
I made the changes to alsa-base.conf - still no luck. No change.

---

### Post by lidex on 2011-04-30
You didn't copy-and-paste from my last post, did you? I missed my typo there - fixing it now. How about that kernel? Start your update-manager and click the 'Settings' button at bottom left. On the 'Updates' tab, make sure the top three boxes are checked. As you close that out it will probably want to reload. Next:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo update-grub
```
Reboot.
Now:
```
uname -a
```

---

### Post by blackdalek on 2011-05-01
I did spot your typo before making the edit.

I did not have pre-release updates checked - never have done.
I selected pre-release updates and made the updates as suggested. Still no kernel upgrades.

Are you *sure* 2.6.35-24 isn't the current version for 64bit? Remember I said I was using the 64bit kernel? I even changed my repo mirror to be sure it wasn't just my usual repo mirror that was out of date. No further kernel updates show up for me.

Anyway...
My kernel name is still -

Linux ilyekkakai-desktop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

---

### Post by lidex on 2011-05-01
I'm not sure exactly how that works. You may need to install the meta-package to be prompted to upgrade or maybe your synaptic settings don't force the highest version number. Anyway, these are the packages available in maverick-updates amd64:
[http://packages.ubuntu.com/search?searchon=contents&keywords=generic&mode=&suite=maverick-updates&arch=amd64](http://packages.ubuntu.com/search?searchon=contents&keywords=generic&mode=&suite=maverick-updates&arch=amd64)

---

### Post by blackdalek on 2011-05-07
Ok, my kernel is now 2.6.35-28 - it didn't help at all. pulseaudio is STILL using 99% of CPU cycles while not outputting any sound in Rhythmbox. :(

---

### Post by lidex on 2011-05-08
OK. Remove your pulse settings again:
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Now re-install pulse:
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
```
```
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio
```
**Reboot.**

---

### Post by blackdalek on 2011-05-22
> **lidex said:**
> OK. Remove your pulse settings again:
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Now re-install pulse:
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
```
```
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio
```
**Reboot.**

Sorry, but this did not help at all. :(
(well, actually... it did seem to help at first boot - until I realised that I was only getting sound out of 2 speakers. Looking at the system>preferences>sound revealed the hardware had changed to analog stereo duplex. When I changed it back to the correct 7.1 channel, the problem resurfaced. Tried changing back to analog stereo duplex - got no sound at all.)


Over the weekend, I decided to take the plunge and upgrade to Ubuntu 11.04...
All audio problems magically disappeared. Neato! :):):)

I guess I shall never know what went wrong with pulseaudio.

---

