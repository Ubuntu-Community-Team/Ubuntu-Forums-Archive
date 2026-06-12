---
title: "pulse audio hates me T_T..."
date: 2010-06-15
forum: Multimedia Software
---

### Post by pr0t3g3 on 2010-06-15
I used tips from another thread to help me out with troubleshooting pulse audio... 
[http://ubuntuforums.org/showthread.php?t=1495994](http://ubuntuforums.org/showthread.php?t=1495994) 
However, It doesn't seem to always work, and the process to make it stick at next restart doesn't work. I've tried other things but it refuses to stick once I've managed to get it to work.

edit:  The problem is, that I cannot adjust the sound.

---

### Post by pr0t3g3 on 2010-06-20
Dun, dun, dunnnnnn!  [SIZE=7][COLOR=Red]_***Bump!***_[/COLOR][/SIZE]   [COLOR=Black]


My post may look unusual but I can't seem to figure out why it's doing this.  I don't really have much time to troubleshoot...so..uh.. any ideas?
[/COLOR]

---

### Post by cj.surrusco on 2010-06-20
Sweet bump. 
...
I don't have the answer to your problem though.

Sorry for getting your hopes up (If I did at all).

---

### Post by pr0t3g3 on 2010-06-20
> **cj.surrusco said:**
> Sweet bump. 
...
I don't have the answer to your problem though.

Sorry for getting your hopes up (If I did at all).
[COLOR=Black][SIZE=7][FONT=Impact]**D'oh**![/FONT][/SIZE][/COLOR]

---

### Post by TRoe on 2010-06-20
So what IS the problem?

---

### Post by pr0t3g3 on 2010-06-20
> **TRoe said:**
> So what IS the problem?
edit: wrong place sorry.  handling multiple threads at once.  The problem is exactly as stated:  I can't adjust the sound on my laptop _*at all*_.  The link shows you the troubleshooting I went through in multiple threads.

---

### Post by TRoe on 2010-06-22
[COLOR=black][FONT=Verdana]It may just be that pulse audio won't behave with your laptop's on-board sound. I recently had issues with pulse audio on my new desktop. It would cause the sound to turn to static when I switched songs, skipped ahead in a song, or changed volume.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]From the looks of it, pulse audio sees an issue with your hardware or setup and never loads the pulse audio daemon.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Did you try a fresh install of Ubuntu to rule out the possibility that you may have inadvertently messed up a config file? If not I would recommend this approach.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]If you did and you're still having issues with volume control, try this:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Hit ALT-F2 and type in "gstreamer-properties" (without quotes). In the window that pops up, change your input and output to something else (ALSA or OSS -- I chose OSS on mine since ALSA still gave me static sometimes).[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Hope this helps... I understand your frustration.[/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by pr0t3g3 on 2010-06-23
> **TRoe said:**
> [COLOR=black][FONT=Verdana]It may just be that pulse audio won't behave with your laptop's on-board sound. I recently had issues with pulse audio on my new desktop. It would cause the sound to turn to static when I switched songs, skipped ahead in a song, or changed volume.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]From the looks of it, pulse audio sees an issue with your hardware or setup and never loads the pulse audio daemon.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Did you try a fresh install of Ubuntu to rule out the possibility that you may have inadvertently messed up a config file? If not I would recommend this approach.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]If you did and you're still having issues with volume control, try this:[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Hit ALT-F2 and type in "gstreamer-properties" (without quotes). In the window that pops up, change your input and output to something else (ALSA or OSS -- I chose OSS on mine since ALSA still gave me static sometimes).[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]Hope this helps... I understand your frustration.[/FONT][/COLOR]

.... I thought I had left behind the 'glitchy-ness' of microsoft ...  Thank you for your input, however It still refused to work, and insists that it's 'waiting for system sound to respond.'   There seems to be ALOT of input methods and commands.  None of them work for me, and when they do, they work one time, then refuse to work another. :\ ... if that's not glitchy I don't know what is.

---

### Post by TRoe on 2010-06-23
Maybe you've done this already, but have you tried this?

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by pr0t3g3 on 2010-06-23
Tried it... doesn't work

---

### Post by TRoe on 2010-06-24
What is your laptop model and soundcard chip set?

---

### Post by pr0t3g3 on 2010-08-11
> **TRoe said:**
> What is your laptop model and soundcard chip set?


_***[COLOR=Red][SIZE=7]NECROMANCY FTW!!!![/SIZE][/COLOR]***_[COLOR=Red][SIZE=7][COLOR=Black]

[SIZE=2]Not sure about the soundchip set but I do know that it is the default sound card that the manufacturer put on here the model of my lapto is: 

Dell Inspiron 8600, a very shady (old) model, There isn't much help for it on the web.

And this sound trouble is probably because of just that:  age.. my sound card was probably made in early 2000 maybe a little later, and lucid lynx came out only in the past year or so?  I think that may be why it's clashing.  Still if there is anyone out there that can help me out; give me a 'flexible'  sound outputer thingy, that can produce sound, on older sound cards for the newest release of ubuntu then you have my thanks!
[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by Linuxforall on 2010-08-11
Switch to pulse less Kubuntu, would work well, I had to do that to enjoy my excellent but ancient Yamaha card, Pulse would make sound crackle like hell.

---

### Post by pr0t3g3 on 2010-08-12
[http://www.ubuntugeek.com/ubuntu-10-04-tip-how-to-fix-waiting-for-sound-system-to-respond-problem.html](http://www.ubuntugeek.com/ubuntu-10-04-tip-how-to-fix-waiting-for-sound-system-to-respond-problem.html)

for all who are having trouble that one unlike the other so-called 'fixes' seems to be permanent.  try the link out.  trust me you won't regret it!

---

