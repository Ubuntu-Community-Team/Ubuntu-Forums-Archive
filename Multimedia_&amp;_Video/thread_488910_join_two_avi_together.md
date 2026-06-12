---
title: "join two avi together"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by ashz on 2007-06-30
hi  peeps, i have two avi files i want to join together is there any software to do this?

thanks in advance

ash

---

### Post by avik on 2007-06-30
You could use avidemux.

---

### Post by RomeReactor on 2007-06-30
Hi. If I'm not mistaken, you can do this from the terminal:
```
cat file1.avi file2.avi > file3.avi
```
where **file1.avi** and **file2.avi** are the names of your existing avi files, and **file3.avi** is the name you want for the joined file. I think I've done this with avi and mpg files, though it doesn't work for wmv.

---

### Post by bashologist on 2007-06-30
This might work. Install mencoder first of course.
```
mencoder -oac copy -ovc copy -o "joined.avi" "1.avi" "2.avi"
```

---

### Post by ashz on 2007-07-01
lol the cat command does not work avi files either, it just made one file of 1.4gb instead, but with only the video of the first 700mb avi file.

thanks anyways mate!!

---

### Post by weblordpepe on 2007-07-01
It would have been halarious if cat worked for that. Not putting you down or anything. I would have beleived it. Its insane the things you can do in the command line on linux.

---

### Post by RomeReactor on 2007-07-01
Yarhhhrr! I could have sworn it worked on avi files too; but it really does on mpg files (well, at least small ones). I've done it before, honest! :popcorn:
It also works for joining those pesky zip files with extensions like **.z01, .z02, .z03**, etc:
```
cat file.z01 file.z02 file.z03 > file.zip
```
after that, you unzip it with:
```
unzip -F file.zip
```

Anyway, like **avik** said, [AviDemux]("http://en.wikipedia.org/wiki/Avidemux") has always worked great for me. Look for it through Add/Remove or Synaptic.

---

### Post by weblordpepe on 2007-07-02
ahaha, damn dude :D

---

### Post by D2sdonger on 2007-07-08
Can somebody please tell me how to join 2 avi's with avidmux.

---

### Post by babya on 2007-07-08
> **D2sdonger said:**
> Can somebody please tell me how to join 2 avi's with avidmux.
I believe you open your 1st clip, then to join your 2nd clip you open it using "Append" under "File".

---

### Post by jaw1959 on 2007-07-12
bashologist's suggestion worked for me.

---

### Post by vertigo1980 on 2007-07-12
> **weblordpepe said:**
> It would have been halarious if cat worked for that. Not putting you down or anything. I would have beleived it. Its insane the things you can do in the command line on linux.

windows does it with the copy /b command, and it works pretty well. like cat, only works with mpeg program streams, not avi or any other container.

---

### Post by weblordpepe on 2007-07-12
Gezuz thats amazing!

---

### Post by southernman on 2007-07-13
> **jaw1959 said:**
> bashologist's suggestion worked for me.

Worked here to. I googled doing this with cat knowing I had joined several files with it before... after trying it with .avi files, It dawned on me - duh dummy - you joined .vob files with cat not .avi

I also tried it with mkvmerge, but it produced the same results of cat with a 1.4gb file that only contained the first part of the movie.

PS. jaw1959 would you be so kind as to mark your post as "SOLVED" for others looking for a fix.

Laterz

---

### Post by bobpaul on 2007-07-24
> **RomeReactor said:**
> Yarhhhrr! I could have sworn it worked on avi files too; but it really does on mpg files (well, at least small ones). I've done it before, honest! :popcorn:

MPEG is a headerless (stream) format. The video and audio codecs are assumed. Length is calculated based on filesize and bitrate. AVI is a container format and as such requires a header to define the codecs, bitrates, lengths, and locations of the audio/video parts within the file (ie, the interleave parameters).

AFAIK, to join AVI files one has to ensure all the video and audio is the same format; then strip the headers from the second file, cat the two files together, and update the length field in the first header. You can *maybe* strip the header with dd, but I'm not sure how one would edit the header without a more advanced tool.

---

### Post by rfs1970 on 2007-12-14
Hi There,

I found a very nice website about that:
[http://techtips.chanduonline.com/2006/08/15/how-to-join-multiple-avi-or-mpg-files/](http://techtips.chanduonline.com/2006/08/15/how-to-join-multiple-avi-or-mpg-files/)

anyway, here is the explanation:

> First, let’s get the right programs.

    sudo apt-get install mencoder mplayer

Now that the hard part is out of the way, we’re going to make use of the wonderful cat command. I’d renamed each Bloodspell video as b1.avi - b7.avi. Now to string them all end to end.

    cat b1.avi b2.avi b3.avi b4.avi b5.avi b6.avi b7.avi > bloodspell.avi

Now we’re 2/3 of the way there! Stringing together .avi files can cause a breakdown in the sync between video and sound. So, we’ll use mencoder to sort things out.

    mencoder -forceidx -oac copy -ovc copy bloodspell.avi.avi -o bloodspell_final.avi






;)

---

### Post by ignignokt00 on 2008-01-07
> **bashologist said:**
> This might work. Install mencoder first of course.
```
mencoder -oac copy -ovc copy -o "joined.avi" "1.avi" "2.avi"
```
This worked flawlessly for me, and fast.  Thanks.

---

### Post by jazzman102 on 2008-01-13
mencoder works, sure, but avimerge is a lot easier
```
avimerge -i file1.avi file2.avi filen.avi - o mergedfile.avi
```

---

