---
title: "Problem with Rosegarden, timidity and jack"
date: 2007-12-29
forum: Multimedia Production
---

### Post by eddiefur on 2007-12-29
Hi everyone :)

I'm new to linux and recently I discovered Ubuntu Studio. For me, it seemed to be the best distribution for working on music or on others artistic project. (I have Ubuntu Studio 7.10)

**So, my problem is:**

If I open Rosegarden without starting the Jack server, I can hear sounds! but... If jack is running, I will hear no sounds :(...

**What I know :**

- If I check with Patchage, Rosegarden seems to use Timidity as midi synth...
- When Jack is running, Ardour and Hydrogen work perfectly.

**What I want :**

I want rosegarden to work perfectly when jack is running (I want to hear sounds!). I also want to compose some part of melody in rosegarden then after record that in Ardour.

If you can help me, answer me please :)

---

### Post by stmiller on 2007-12-30
Rosegarden does not make or contain any sounds. It just sends midi data. So you'll need a soft synth running, or timidity will do the job.

Start jack first, with qjackctl.

Then make sure timidity is running. Do

```
$ sudo /etc/init.d/timidity start

```

And inside Rosegarden, click on the MIDI setup and make sure to choose timidity.

Or you can find and download a soundfont from the web, like the cadenza soundfont and use qsynth / fluidsynth as a soft synth instead of timidity.

---

### Post by theorganloft on 2007-12-30
> **eddiefur said:**
> Hi everyone :)

I'm new to linux and recently I discovered Ubuntu Studio. For me, it seemed to be the best distribution for working on music or on others artistic project. (I have Ubuntu Studio 7.10)

**So, my problem is:**

If I open Rosegarden without starting the Jack server, I can hear sounds! but... If jack is running, I will hear no sounds :(...

**What I know :**

- If I check with Patchage, Rosegarden seems to use Timidity as midi synth...
- When Jack is running, Ardour and Hydrogen work perfectly.

**What I want :**

I want rosegarden to work perfectly when jack is running (I want to hear sounds!). I also want to compose some part of melody in Rosegarden then after record that in Ardour.

If you can help me, answer me please :)

You would need to start Jack first.  I would also suggest that you take a step back and learn more about Jack.  Jack's terminology  is designed after the pro-sound industry. 

Take a good look at Jack and learn how you can use it to your advantage. [http://www.jackaudio.org](http://www.jackaudio.org)

In Rosegarden, Ardour, and other applications that use Jack, you will find that knowing these terms will get you connected properly. 
There are audio settings that will allow you to connect your audio to channels, busses, etc.  You can also use sends and returns for effects, etc.  
Take another look at Rosegarden.  Here is a screen shot of my Jack:

[IMG]http://theorganloft.googlegroups.com/web/Screenshot-Connections%20-%20JACK%20Audio%20Connection%20Kit-1.png?gda=QZiU4WkAAADcSmRwMIL-YwXLr9ZO7rtcZzttslb6gsC1BE46Bgq4U2G1qiJ7UbTIup-M2XPURDRA3OgJXzCXfCsfQMD4ewcJGM2mFurVBHhDRMy3djj1Ht29aGI_rW-MSebCw70Xz2O3m8Mjs2xKFY_AL14bxgKP[/IMG] 
[IMG]http://theorganloft.googlegroups.com/web/Screenshot-Connections%20-%20JACK%20Audio%20Connection%20Kit-2.png?gda=9E6ml2kAAADcSmRwMIL-YwXLr9ZO7rtcIgbY2jFGl6Gxqrrm_dq0hGG1qiJ7UbTIup-M2XPURDRA3OgJXzCXfCsfQMD4ewcJGM2mFurVBHhDRMy3djj1Ht29aGI_rW-MSebCw70Xz2M9KkRxoXJM_RQU3JNmN5La[/IMG]


Good luck to you...:guitar:

---

### Post by alukin on 2008-06-29
Yeah, you right but in my case rosegarden plays midi using timidity only if jacks is NOT started. Timidity and jackd are incompatible I guess. Timidity has -Oj option but I did not get it working. Fluidsynth works well with jack but you need linux-rt kernel to get acceptable quality of sound.

It is strange that alsa does not have yet it's own sf2 midi emulator in kernel for cards that no not have midi build in. Even stupid windooze can play midi on my notebook with acceptable quality and latency...

---

