---
title: "where are the files from ODVR?"
date: 2010-03-12
forum: Multimedia Software
---

### Post by tropdoug on 2010-03-12
I installed a program to let me use my OlympusVN-4100PC voice recorder in Ubuntu 9.10.

From the terminal the recorder is found ... good

then I ask it to download all the files on it, and the first time I used it it stated all files were donloaded -- but it doesn't say where. The files are supposed to be wav, so I searched my entire system for all wav files and found none of the ones I am looking for

I then tried to specify a folder to download too and this is what I got 

```
douglas@desktop:~$ odvr -d a
Model: 2100PC
"DA_0049.wav" already exists. Skipping this file.
"DA_0050.wav" already exists. Skipping this file.

```I searched using DA* and found nothing!

Anyone able to tell me what is happening, I would really like to get these files onto my computer. 

Alternatively can anyone tell me of a good quality recorder that will work straight up in Ubuntu?

Thanks 
Douglas

---

### Post by tropdoug on 2010-03-12
SOLVED --- This is weird -- I searched  again using 'Gnome Do' and found them straight away, Don't understand that, they were in my home folder deep down. Anyway the next issue was they were all empty files, they contained no data! 

Hmm a bit more research shows that the files are only successful if recorded in XHQ quality, so users make sure that is set via the recorders menu options. 

Tried a download, fully successful and plays in rhythmbox, vlc, movie player etc. 

Now I am going to see if conversion and editing works. 

ODVR is a good program once you work the issues out.

---

