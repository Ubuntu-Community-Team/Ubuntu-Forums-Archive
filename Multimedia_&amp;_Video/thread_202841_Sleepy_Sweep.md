---
title: "Sleepy Sweep"
date: 2006-06-24
forum: Multimedia &amp; Video
---

### Post by fdimmling on 2006-06-24
I've used Sweep a couple of times before to make some smaller changes to audio files. It has never been the fastest of all programs but what I experienced now in Dapper makes it a candidade for the Guiness book:

System: Acer Travelmate, 1.73 GHz Pentium M, 512 MB RAM 
Audi File: 316 MByte, ca 32 min Wav file.

Load file in Sweep: 11 min 30 sec.
Delete the first 2 min in the file: 4 min
Write back file to disk: 17 min

While my system (Ubuntu Gnome) takes typically 185 MB Ram, no swap space, after loading the file there was 446MB RAM and 470 MB swap space used. While writing the data back to disk the swap usage rised to 750 MB. This explains the time needed. The whole system is swapping mem almost all the time.

For comparison: Loading an 1.6 GB video file into avidemux and indexing it took 1 min 10 sec.

Any idea what I can do - except buying 1GB of RAM and/or using audacity. 

Friedrich :twisted:

---

### Post by zettberlin on 2006-06-24
[QUOTE=fdimmling]

Any idea what I can do - except buying 1GB of RAM and/or using audacity. 

Friedrich :twisted:[/QUOTE]

sweep., rezound and some others load all Data into RAM - this is a feature ;-) still you run into trouble of course, if you have not got the needed amount of RAM - so using Audacity for big files is indeed recommended but if you dislike it, you can try others:

1.) Ardour can do most of the things sweep can and handles memory much more sophisticated
2.) mhwaveedit looks somewat like sweep, works perfectly with jack and needs quite little recources

---

