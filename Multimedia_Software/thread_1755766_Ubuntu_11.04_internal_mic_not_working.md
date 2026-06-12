---
title: "Ubuntu 11.04 internal mic not working"
date: 2011-05-11
forum: Multimedia Software
---

### Post by yousaf05 on 2011-05-11
Hi,
My Asus X52J Internal mic not working.. here is my asla information 

```
http://www.alsa-project.org/db/?f=184ef87f8fbedfed9804cd147b52436bba56123c
```can you please help me fix it?

---

### Post by lidex on 2011-05-11
I think you should change the model quirk in alsa-base.conf.
Open for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Find this line:
```
options snd-hda-intel model=asus-mode3

```
and change to look like this:
```
options snd-hda-intel model=hp-laptop

```
**Reboot**
Now post this output:
```
amixer
```

---

### Post by yousaf05 on 2011-05-17
Thanks Lidex below is the output but still mic not working 

```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 0 [0%] [-28.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [on]
  Front Right: Capture 80 [100%] [6.00dB] [on]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '40dB'
```

---

### Post by lidex on 2011-05-17
Try changing that model to thinkpad.

---

### Post by yousaf05 on 2011-05-18
Im sorry Lidex still no luck 

here is my updated alsa information


[http://www.alsa-project.org/db/?f=2e31a2f63747de58b4314465986e6a7a117de690](http://www.alsa-project.org/db/?f=2e31a2f63747de58b4314465986e6a7a117de690)

---

### Post by lidex on 2011-05-19
OK try ideapad next. No joy remove entire line and replace with:
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```

---

### Post by yousaf05 on 2011-05-19
I tried ideapad nothing changes ,no joy then i replace the string still mic is not working and also it don't recognized headphone plugged in jack

I have no input device in sound preferences

---

### Post by lidex on 2011-05-19
Can you retry those models and post the amixer output for each?
```
amixer
```

---

### Post by yousaf05 on 2011-05-20
amixer for ```
options snd-hda-intel model=ideapad
``` is ```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 48 [65%] [-26.00dB] [on]
  Front Right: Playback 48 [65%] [-26.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 252 [99%] [0.60dB]
  Front Right: Playback 252 [99%] [0.60dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 0 [0%] [-28.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [on]
  Front Right: Capture 80 [100%] [6.00dB] [on]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '40dB'
```
and for ```
options snd-hda-intel model=laptop position_fix=1 enable=yes
``` amixer output is ```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 48 [65%] [-26.00dB] [on]
  Front Right: Playback 48 [65%] [-26.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 252 [99%] [0.60dB]
  Front Right: Playback 252 [99%] [0.60dB]
Simple mixer control 'Mic B',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Mic C',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic E',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic F',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 0 [0%] [-28.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [on]
  Front Right: Capture 80 [100%] [6.00dB] [on]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '40dB'
```

and thanks for your time

---

### Post by lidex on 2011-05-22
For the second amixer you can see you have some different controls.
```
Simple mixer control 'Mic B',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: [COLOR="Red"]Capture [on][/COLOR]
Simple mixer control 'Mic C',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: [COLOR="Red"]Capture [off][/COLOR]
Simple mixer control 'Mic E',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: [COLOR="Red"]Capture [off][/COLOR]
Simple mixer control 'Mic F',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: [COLOR="Red"]Capture [off][/COLOR]
```
Try using alsamixer to enable each one in turn leaving the others muted while checking for input.

---

### Post by yousaf05 on 2011-05-24
Hi Lidex,

I am attaching the snapshot seems like i cannot turn on /off mic C,D,E and F neither i can use up arrow and down arrow to increase or decrease

---

### Post by lifelike27 on 2011-05-24
Try comment #14 and see if it works: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/731706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/731706)

If it does, you're suffering from the same problem as me as there is a patch that's going to be available soon.

---

### Post by yousaf05 on 2011-05-24
cannot do step 3 and 4 because i don't have input source nor internal mic in amixer

---

### Post by Hansholz on 2011-05-24
Try this one. I had the same problem as you, but it wasn't asla-related. This fixed it.

[http://ubuntuforums.org/showthread.php?t=1732074](http://ubuntuforums.org/showthread.php?t=1732074)

---

### Post by yousaf05 on 2011-05-25
Nothing works so i decided to rollback to ubuntu 10.10. Now i have my mic working perfectly by adding ```
options snd-hda-intel model=laptop position_fix=1 enable=yes
``` but now my headphone jack dont recognized that my microphone is plugged in and use internal speaker for output

any idea how to solve it ??

---

### Post by lidex on 2011-05-25
See if this provides any guidance:
[http://ubuntuforums.org/showthread.php?t=1324135](http://ubuntuforums.org/showthread.php?t=1324135)

---

### Post by Emanuele_Z on 2011-05-30
Hi,

I have a similar issue.
Changing settings via alsamixer works, but **every** time I logout/login (or restart) I lose this settings.
Where/how can I fix this?

Cheers,

---

### Post by lidex on 2011-05-30
First try these terminal commands:
```
sudo alsactl save 0
```
No help, then:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

No help? Comment out line 372 in /etc/init.d/alsa-utils
Should look like this when you're done:
```
# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```

---

### Post by redrummy on 2011-07-14
> **Hansholz said:**
> Try this one. I had the same problem as you, but it wasn't asla-related. This fixed it.

[http://ubuntuforums.org/showthread.php?t=1732074](http://ubuntuforums.org/showthread.php?t=1732074)

I've been banging my head against this one for a couple days with my AO751h and this fixed it. Thanks Hansholz! But what bizarre solution. :-s

---

### Post by jmlm-1970 on 2012-03-26
The only solution to make microphone work is to install linux-backports-modules-alsa-generic...
 
 Just go to:
 
 Menu / System / Administration / Synaptic Package Manager
 
 And search and mark for installation:
 
 linux-backports-modules-alsa-generic
 
 tip: if you have multiple versions click on the first and read the description which should inform what name to install...
 
 If after the reboot and mic mute is off, still does not work, just go to terminal and type:
 
 sudo nano /etc/modprobe.d/alsa-base.conf
 
 and add or change the following:
 
 options snd-hda-intel model=auto enable=yes
 
 Then Ctrl+X, type Y to write and exit, reboot and mic will work.
 
 Bye and have lots of fun with Ubuntu (the best).

---

### Post by im.saravanan on 2012-12-25
This worked for me to solve mic problem in ubuntu 11.04. Read carefully and do it. Check the link below for solution


[http://ubuntuforums.org/showthread.php?t=1732074](http://ubuntuforums.org/showthread.php?t=1732074)

---

