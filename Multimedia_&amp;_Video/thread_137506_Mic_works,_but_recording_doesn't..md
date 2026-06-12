---
title: "Mic works, but recording doesn't."
date: 2006-02-28
forum: Multimedia &amp; Video
---

### Post by torx on 2006-02-28
I just installed my new mic and after enabling capture and unmuting it in ALSA mixer, i can hear my voice fine. But when i tried recording using the default sound recorder, the "time elapsed bar" seems to go really fast for all three formats (.OGG, .FLAC and .WAV). And when i play it back, there is no sound recorded/

Does anyone knows how to fix this?

---

### Post by t-bird on 2006-03-07
[QUOTE=torx]I just installed my new mic and after enabling capture and unmuting it in ALSA mixer, i can hear my voice fine. But when i tried recording using the default sound recorder, the "time elapsed bar" seems to go really fast for all three formats (.OGG, .FLAC and .WAV). And when i play it back, there is no sound recorded/

Does anyone knows how to fix this?[/QUOTE]


I have the same problem! Please HELP! :(

---

### Post by stelloscuro on 2006-03-08
Help!, I also have the same problem on my thinkpad, can anyone shed any light on this?

---

### Post by MacSlow on 2006-03-09
Same here too. I've plugged my headset into my SBLive and can hear the "echo" of my voice just fine. But no single program for sound-recording I tried works. It's just silence, although no error is reported.

I would really like an overview-schematic of a typical audio-stack for Linux (under Gnome) to help me figure out what's obviously missing here. 

Best regards...

MacSlow

---

### Post by t-bird on 2006-03-13
Please help us!:(

---

### Post by ptt on 2006-03-14
I had the same problem, it turned out that I have to use the 'Capture' channel for recording, and the 'Microphone' channel for direct audio. I hope this solves your problems for now, but the sound in ubuntu can use some more unification and clarity.

Good luck, Piers

---

### Post by t-bird on 2006-03-16
Ok, i finally can record sound and use skype!!!
What i did is this, i dont know if it is logic but on my pc works.

1) chmod 777 /dev/dsp
2) in multimedia selector i put esd in sink and input.

to record sound i use "Audacity" it work "out of the box" , and skype too. \\:D/ 

I hope u all can fix the problem.
Byez!

---

### Post by stelloscuro on 2006-11-10
I solved this on my thinkpad T21 by setting adc to capture in alsamixer, along with capture.  Still can't get Skype stable, grrr :evil:

---

### Post by catchvik on 2006-11-30
hi t-bird ...
can you please explain your second step . very much appreciated 
vikas

---

