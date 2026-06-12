---
title: "wav files too large after mp3 to wav conversion"
date: 2010-09-13
forum: Multimedia Software
---

### Post by Mariane on 2010-09-13
Hi, 

I tried to restore an album which I only have as mp3 files. I tried 2 programs, mpg123 and audacity. Then I burned 2 CDs as audio CDs with k3b. 

Each time it failed because the album was larger than 700MB. The first songs play properly but the next to last has gaps and the last one cannot be heard at all. 

I would like to restore this album, with all its songs, on a CD which can be played on any CD player, so using a DVD instead of a CD is not an option. 

These files should fit on an audio CD because originally the album was on a CD. It seems that converting wav to mp3 and then mp3 to wav increases the files size. 

I tried using Audacity to edit the files to shorten them a bit, removing the silence at the end of the sound track, but this was insufficient. There is one song I like less than others on this album so I could omit it but this I consider to be the last resort. 

All suggestions welcome. 

Mariane

---

### Post by cascade9 on 2010-09-13
WAV-> MP3 then MP3-> WAV conversions shouldnt make the wav file any bigger than the original. 

How long (in minutes) is the album you are trying to burn?

---

### Post by Mariane on 2010-09-13
70.06 minutes

---

### Post by sydbat on 2010-09-13
Try using 'Sound Converter' to convert to .wav. You can find it in Synaptic.

Also, k3b *should* convert automatically, if you have all the restricted extras installed.

---

### Post by ron999 on 2010-09-13
@ Mariane
With K3b look in:-
Settings > Configure K3b > Advanced
Make sure that 'Allow overburning' is ticked.

---

### Post by Chronon on 2010-09-13
CDs are 2 channels at 16-bits per sample and 44,100 samples per second.
2*(16 bits)*(44,100 /second) = 1411.2 kb/s

Perhaps the MP3s and the WAVs encoded from them have a different sampling rate (48,000 samples per second is also commonly used).  Your transcoding software might have an option to force a particular sample rate.

---

### Post by cascade9 on 2010-09-14
> **Mariane said:**
> 70.06 minutes

Should fit fine on a 700MB CD then. 

I'd check the sample rate, like choronon suggested. ;)

---

### Post by Mariane on 2010-11-10
Thanks for the "allow overburning" tip, it helps. But I still have bad burns occasionally when I try to fill a CD up to or near 700 MB. My solution now is to leave out the last song. K3b has a little bar which shows how filled the CD would be, I use this as a guide-line and I stop adding files about one centimeter from the endline. 

Mariane

---

