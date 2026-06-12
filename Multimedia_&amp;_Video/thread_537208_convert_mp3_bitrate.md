---
title: "convert mp3 bitrate"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by stlouis1 on 2007-08-28
well. im still a little new to linux here. but so far im getting by pretty good using it. i spent a 2 hours the other night organizing 20gb of mp3's that i have with amarok....

all i can say is wow, im sure that could have easily taken me 10 hours. but amarok is sweet, i love how it will guess tags by the filename and let you use your own templates, or rename and sort the files by the tags and again allowing custom templates. on windows id have to do that all manually

anyway, the only thing i need now with those files, is the bitrate, i like to keep all my mp3's at 192kbps, i find it to be the best medium between size and quality.

so i need a program now that will scan through my folders and convert my mp3's to a certain bitrate, if i have to do one folder at a time, thats fine. i just dont want to have to convert to file to a different location, and have to copy it back where i want it manually. i already have a 2 backups, i just want something to change the bitrate on the spot

---

### Post by Sp4freel on 2007-08-29
I am prolly as new as you to linux also.  I found another post about converting Mp3's [Here]("http://ubuntuforums.org/showthread.php?t=536953").  and [here]("http://ubuntuforums.org/showthread.php?t=527958")

Alternatly you can install wine (I got it to work but I cant really tell any one how) drop your MP3'3 in to a folder that is easy to find, as it will show up in your file browser as hard disk Z


select the file(s) you want to convert and let it run
[[IMG]http://img512.imageshack.us/img512/1175/ss1xm3.th.jpg[/IMG]](http://img512.imageshack.us/my.php?image=ss1xm3.jpg)
[[IMG]http://img265.imageshack.us/img265/7281/84863777ly3.th.jpg[/IMG]](http://img265.imageshack.us/my.php?image=84863777ly3.jpg)
[[IMG]http://img126.imageshack.us/img126/1235/ss3ag1.th.png[/IMG]](http://img126.imageshack.us/my.php?image=ss3ag1.png)
[[IMG]http://img265.imageshack.us/img265/31/ss4fm2.th.png[/IMG]](http://img265.imageshack.us/my.php?image=ss4fm2.png)
[[IMG]http://img253.imageshack.us/img253/1209/ss5hi4.th.png[/IMG]](http://img253.imageshack.us/my.php?image=ss5hi4.png)

---

### Post by stlouis1 on 2007-08-29
i ended up finding some threads here. installed soundconverter......but it didnt seem to want to convert some of my files. i transferred everything to my windows machine, and then media player couldnt read half the tags that i spent so long setting up so neatly, i dont get it, even windows didnt see the tags on them. i dont understand whats so complicated there. everything on my linux install see's all the tags, but when the same files get on a windows machine, they crap out

---

### Post by wolfen69 on 2007-08-29
just dont use windows (just kidding, sort of)

---

### Post by stlouis1 on 2007-08-29
my desktop will be migrating to kubuntu 64bit soon....so i wont be using windows, on my systems at least

---

### Post by Marat Galiev on 2007-08-30
use lame encoder.
read 
**man lame**

---

### Post by vanadium on 2007-08-30
You should avoid converting the bitrate of yyour mp3s altogether. Doing so, you will end up with lower quality files.

mp3 is a lossy compression scheme. Audio information that you hardly or not hear is thrown away to achieve the reduction in file size. If you now want to transcode mp3s to a different bitrate, the compressed audio is first uncompressed, the recompressed again in a lossy way, i.e., with even more loss in audio information and even more introduction of artifacts (you will not necessarily hear these, though).

the only reason I could see for transcoding is that you want to fit a few more files on a tiny mp3 player of modest quality. Then, it would be useful to transcode the files "on the fly" to a quite low bitrate to take on the road, keeping your original high quality files at home on the disk, and deleting the small files when you do not need them anymore. 

There might be graphical tools to do that, but lame has a build-in facility to do that:

```

 lame --mp3input -b 96 <file.mp3> <destination.mp3>

```

- 96 is an option to transcode to CBR 96 kbps and should be schanged to suit your need.

If you have 100 files to transcode, then run

```

for f in *.mp3 ; do lame --mp3input -b 96 $f <path_to_destination>/$f ; done

```

If <path_to_destination> is your mp3 player, the transcoded files will immediately end up there.

---

### Post by stlouis1 on 2007-08-31
thats handy, thanx

---

### Post by Danthe on 2008-04-28
I found this very useful, thanks a lot.

I just want add something: To avoid any problems when converting files with spaces (" ") on their names, use "$f" instead of $f.

```
for f in *.mp3 ; do lame --mp3input -b 96 "$f" <path_to_destination>/"$f" ; done
```

---

