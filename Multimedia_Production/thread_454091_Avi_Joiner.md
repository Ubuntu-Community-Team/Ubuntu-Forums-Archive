---
title: "Avi Joiner"
date: 2007-05-25
forum: Multimedia Production
---

### Post by cox377 on 2007-05-25
Hello All

Looking for a bit of advice,

I'm looking for a decent app to join avi files together,

In addition I need an app to convert Avi to Dvd

Would be greatly appreciative of any tips / pointers

CoXen

---

### Post by eye208 on 2007-05-25
> **cox377 said:**
> I'm looking for a decent app to join avi files together,
Avidemux and MEncoder.

> In addition I need an app to convert Avi to Dvd
KmPg2 - [http://kmpg2.sourceforge.net/](http://kmpg2.sourceforge.net/) - convert anything to MPEG-2 for DVD use
DVDAuthor Wizard - [http://dvdauthorwizard.sourceforge.net/](http://dvdauthorwizard.sourceforge.net/) - make DVD from MPEG-2 clips, with menus etc.

---

### Post by Titus A Duxass on 2007-05-25
For avi files I think it's something along these lines.
At the CLI enter cat filename.avi filename2.avi > endfilename.avi

Do a search of the forum.

---

### Post by regomodo on 2007-05-25
Virtualdubmod is real good for this. Open the 1st avi then "append avi segment" for all the others.

Not sure if Vdub is on Linux, should be.

---

### Post by cox377 on 2007-05-25
Cheers guys i shall take a look

---

### Post by nedecor on 2007-05-25
> **regomodo said:**
> Virtualdubmod is real good for this. Open the 1st avi then "append avi segment" for all the others.

Not sure if Vdub is on Linux, should be.

VirtualDub is not available for linux. It is windows only, AVIDemux is the closest alternative.

Jake

---

### Post by cox377 on 2007-05-29
thing is with AVIDEMUX i cannot work out how to join avi files together, do i have to install a plugin for it?

Edit - Just seen it

---

### Post by aeiah on 2007-05-30
a simple mencoder command will join files. as for converting avi to dvd, i use tovid. i made an automated script for tovid that i can get to from nautilus scripts. a terminal will pop up and ask if the film is in one or two parts, then you load the part(s), it joins them together if necessary, then converts to dvd, then converts that to an iso. most of the functionality is already in tovid. ill post the script up when im back at my computer if anyone's interested. its pretty rudimentary though. its set for ntsc but probably easily changed.

---

### Post by C01eMaN on 2007-10-21
> **aeiah said:**
> a simple mencoder command will join files. as for converting avi to dvd, i use tovid. i made an automated script for tovid that i can get to from nautilus scripts. a terminal will pop up and ask if the film is in one or two parts, then you load the part(s), it joins them together if necessary, then converts to dvd, then converts that to an iso. most of the functionality is already in tovid. ill post the script up when im back at my computer if anyone's interested. its pretty rudimentary though. its set for ntsc but probably easily changed.

that would be awsome if u could post that m8... i think a few ppl could use it 

:guitar:

---

### Post by lovejia on 2008-01-04
If you want to join AVI to mpg, wmv, mp4, avi, vcd, svd, dvd, I suggest you use this [COLOR="Blue"][avi joiner]("http://www.mp4videojoiner.com/avi-joiner.html")[/COLOR]

---

### Post by FrankVdb on 2008-01-19
As already mentioned, the cat command is an easy way to join files.

Say, I want to join the following files:
film123.avi.001
film123.avi.002
film123.avi.003
film123.avi.004
film123.avi.005

The following command joins them into the eventual movie:
cat film* > film123.avi

---

### Post by yabbies on 2008-01-20
the cat command works great for avi
like posted above

you will also need to install mencoder from synaptic.

so if you have 2 avi files lets call them movie1 and movie 2. Create a folder, put the 2 avis in the folder and put it in a convenient place. Open a terminal and cd (change directories) to the folder.

concatenate the files with

```
cat movie1.avi movie2.avi > combo.avi
```

now that they have been joined, almost 99% of the time you will get an src moves backwards error, because of the millisecond space between the two joined files where the time code stamp starts back at 0.

so you need mencoder to fix this error to regenerate the time code.

to do so stay in the directory that you created and type or paste

```
mencoder -o YOUR_FINAL.avi -noidx -oac copy -ovc copy combo.avi
```

after which you will have a joined avi that you can transcode to mpg and burn to a working dvd.

---

### Post by cmcfarland21 on 2008-03-23
I followed the above directions except my Final Movie now has no audio.

Can anyone help?

---

### Post by Creative2 on 2008-03-23
avimerge 
avimerge -o OUTPUT.avi -i fileavi fileavi fileavi

---

