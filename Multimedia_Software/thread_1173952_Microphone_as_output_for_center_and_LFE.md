---
title: "Microphone as output for center and LFE"
date: 2009-05-30
forum: Multimedia Software
---

### Post by Pagnol on 2009-05-30
Hi,

I am using Brutefir as a digital crossover.

At the moment I've got an M1330 and the onboard sound chip is an Intel HDA. I can address every audio output by its index, eg. 0 means the front left speaker. This works with the channels 0, 1, 2 and 3, but it does not work with the channels 4 and 5.
In the Volume Control I found the switch to use the 'microphone as output'. I activated this but the microphone output is now the headphone output and not the channels 4 and 5.

**Is it possible to link the microphone output with the channels 4 and 5 (or center and lfe)?**

(I am using ALSA to address the channels.)

Thanks in advance
Pagnol

---

### Post by Pagnol on 2009-06-21
Via Google I came back to my own thread.

Obviosly the problem persists. I added a screenshot on which you can see a part of Jack's control center. playback_5 und playback_6 represent the third audio output of my notebook. Normally this is an audio input, but one can enably it as an output by activating the switch titled 'use microphone as output' in the Volume Control. But obviosly this switch does not work, because I don't hear anything.

I would really (really!) love (adore!) to know how this ***** switch can be made working.

---

### Post by Pagnol on 2009-06-21
Unexpectedly I made some progess!

I found this thread: [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

I added the line

[PHP]options snd-hda-intel model=3stack[/PHP]

to my /etc/modprobe.d/alsa-base.conf

And now it works. But it the sound is somehow thin and the maximum of loudness is lower than the one of the other outputs.

Besides '3stack' there are two other possible options: '5stack' and 'dell-3stack'.

This is really strange: When connecting my headphones to the first (front) or second (rear) audio output, I hear a loud background noise. When choosing '3stack' as the model and connecting the headphones to the third output, then I don't hear any background noise.

---

