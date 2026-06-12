---
title: "mp3's won't play on my player"
date: 2010-07-26
forum: Multimedia Software
---

### Post by Amy_1990 on 2010-07-26
I have some mp3's that will not play on my player they play on rhythmbox.Someone else ripped them for me.The only thing that is different is the sample rate it's different on all the mp3's and i don't know what to do is there a way to change this or is there something else that would be causing this and a way to repair them 
[IMG]http://www.qtl.co.il/img/copy.png[/IMG][[IMG]http://www.google.com/favicon.ico[/IMG]]("http://www.google.com/search?q=and%20i%20don%27t%20know%20what%20else%20to%20do.so%20if%20anyone%20knows%20how%20to%20change%20this%20or")[IMG]http://www.qtl.co.il/img/trans.png[/IMG]

---

### Post by Amy_1990 on 2010-07-26
I just encoded one of the mp3's using ffmpeg it changed the sample rate but it turns the size of a 4.3 MB mp3 into 12.8 about 3x the size and it also gives me this error

[mp3 @ 0x9fe2e40] Header missing

I have a lot of these mp3's some play and some don't but they all play in rhythmbox so if anybody can help me it will be very much appreciated.

---

### Post by Chronon on 2010-07-26
I have never used it but this package sounds promising:
[http://packages.ubuntu.com/lucid/mp3diags](http://packages.ubuntu.com/lucid/mp3diags)

---

### Post by themusicalduck on 2010-07-27
How do you mean that they won't play on your player? Do you mean like a portable mp3 player?

Are you sure that the sample rate is different or the bitrate? If the samplerate is anything other than 44,100Hz or 48,000 Hz then it might cause problems, but it would be strange if it was ripped at something different to that. A different bitrate shouldn't cause any problems.

---

### Post by Amy_1990 on 2010-07-27
Yes a mp3 player.When it goes to play the mp3 it just stops and goes to the next one.The sample rate is different on all the mp3's and i just now looked all of the bit rate's are different also.I can change the sample and bit rate with ffmpeg but it makes the file about 3x bigger a 11.9 mb file becomes 33 mb.thats not a problem but the header is.I can't get that fixed and i don't know why.

---

### Post by Chronon on 2010-07-27
It sounds like something is wrong with them to begin with.  There are only a few sample rates that should be used normally: 22.05 kHz, 44.1 kHz, 48 kHz.  

You can try the package I linked before, it's in the repositories so you can find it with Synaptic or the Software Center.  It claims to fix many different problems for mp3 files specifically.

---

### Post by Amy_1990 on 2010-07-28
Ok i had my friend to rip the files again they all riped at a sample rate of 22050 Hz and the bitrate of 56 kbps i have not tried them in my mp3 player yet but when i try to change the sample rate in ffmpeg to 44100 Hz it makes the file about 3X larger it makes a 11MB file 33.9MB.Would you know why?The 22050 sample rate is that alright or should it be 44100?

---

### Post by ron999 on 2010-07-28
Hi
If you still need to change those files from 22050Hz into 56Kb at 44100Hz then this command should do it without inflating the file size:-

```
ffmpeg -i input.mp3 -f wav - | ffmpeg -i - -ab 56k -ar 44100 output.mp3
```

---

### Post by Amy_1990 on 2010-07-28
Thank you all so much i loaded the mp3 files on my mp3 player and all 30 files worked now just 60 more to try i think they will work.The only question i have now is would it be better to keep them at 22050 Hz or change them to 44100 Hz like the rest of my mp3 files?

---

### Post by ron999 on 2010-07-28
Hi
Each time we convert mp3 files the quality deteriorates slightly.
So if those 22050Hz files play OK then it's best to leave them as they are.
:D

---

### Post by Amy_1990 on 2010-07-28
Kind of what i was thinking

Thank you so much my problem is solved

---

