---
title: "MP3 problem"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by sn0m on 2007-01-08
Chaps
I wander if someone can help me. I downloaded an audio book from limewire in form of 6 mp3 files of 30MB. I tried to burn them in order on gnomebaker as data cd to play on my car stereo, which is an mp3 player by the way as well, but unfortunately it wouldn't burn them in order. So i renamed them, from name.mp3  to just numbers, which did burn them in order but files were transformed from mp3 to text/plain, and funny enough, they wouldn't play on my stereo but f i open them with totem in my lap-top, they play fine.
?whats the problem here.
thanks
koli

---

### Post by Biggus on 2007-01-08
Could it be that you've changed the file extension, ie the files are now called

file1

instead of

file1.mp3

?

---

### Post by sn0m on 2007-01-08
> **Biggus said:**
> Could it be that you've changed the file extension, ie the files are now called

file1

instead of

file1.mp3

?

no mate, i labelled them 1.mp3, 2.mp3 and so on.

---

### Post by Biggus on 2007-01-08
Hmmm, that is indeed a problem.

I used to rename files all the time and forget about the extension, causing the exact problem you've described.

> but files were transformed from mp3 to text/plain

I think this is the portion which is causing the problem.

It seems that, whatever happened, totem still retains the ability to 'see' the file as an mp3, whereas the car stereo doesn't.

I personally don't like gnomebaker (or rather, it doesn't seem to like my burner) so I don't know if it will work, but you could use a program like 'Audio Tag Tool' (Applications->Audio Tag Tool if you have it installed, if not it's available from the Synaptic Package Manager) to add track numbers to the mp3s (the original ones, not the ones which are now text files) and see if gnomebaker will use the id3 tag info to line them up in the correct order.

Myself, I just use the default box which pops up when I stick in a blank disk, it seems to work, and its never failed me yet.

---

### Post by sn0m on 2007-01-09
I was just wandering if someone could post a tutorial how to write audio tags.
I checked the audio tags program help section but i doesn't have any information in it.
It would be nice for beginers like myself to learn how to do that. The mp3 files that i am having a problemat the moment don't seem to have audio tags.
thanks
koli

---

