---
title: "[SOLVED] MP3 split - waveform"
date: 2007-12-18
forum: Multimedia &amp; Video
---

### Post by dysphasi on 2007-12-18
I really love mp3splt for my mp3 splitting needs, but one thing that gripes me is the lack of any waveform visual. I can't easily see where the gaps are in sound to then select split points.

I'm currently using audacity to see the waveform of the mp3 concerned, but obviously it has to import the mp3 file each time....which takes time. Is there a program that will simply let me play and scan through an mp3 file directly displaying a waveform? I don't need an editor, just a 'viewer', I can always jot down the gaps and apply them with mp3splt later.

---

### Post by logos34 on 2007-12-18
I use mp3directcut on wine.  But that assumes you dual boot.

---

### Post by dysphasi on 2007-12-18
I don't dual boot, but if it works in wine, surely I wouldn't have to?

Also just wondering, does mp3directcut support batch processes? Will it then allow you to enter a desired length for segments and subsequently ensure that each segment is cut close to this defined length, whilst ensuring the cut takes place in an area of silence?

Thanks in advance!

---

### Post by logos34 on 2007-12-18
> **dysphasi said:**
> I don't dual boot, but if it works in wine, surely I wouldn't have to?

Also just wondering, does mp3directcut support batch processes? 

It has to be installed on a windows partition before you can run it with wine in linux.  

Not sure about batch.  Check the website.
[http://mpesch3.de1.cc/](http://mpesch3.de1.cc/)

---

### Post by dysphasi on 2007-12-18
> **logos34 said:**
> It has to be installed on a windows partition before you can run it with wine in linux.  

Not sure about batch.  Check the website.
[http://mpesch3.de1.cc/](http://mpesch3.de1.cc/)

Ahh k, I've got a virtualbox/XP setup on my laptop so shall give it a whirl there... as long as I can get the times I'm after easily that'll be grand, I can then use mp3splt to do the actual splitting. Thanks for your help!

---

### Post by logos34 on 2007-12-18
ok, great.  good luck

---

### Post by dysphasi on 2007-12-18
Just to try it out, I installed wine and tried installing mp3directcut.

I made sure to put mpglib.dll in the system32 folder and set it to be used in the mp3directcut settings and hey presto, it works wonderfully :-)

I much prefer mp3splt for the actual splitting, but the pause detection facility in directcut is superb for finding the start of chapters in my recordings, I  can then read off the times and pop them into mp3splt....all in the time it takes audacity to load a single mp3 file!

Just as a sidenote....directcut seems to run smoother and with more stability with wine than within virtualbox.

Thanks for the suggestion! :D

---

### Post by logos34 on 2007-12-18
Glad eveything worked out so well for you.  Sorry for the disinfo--seems I need to read the Wine faqs.  You can tell how much I use it...dbpoweramp, foobar2000, mp3directcut, and recently EAC (now that I've gotten it to recognize my cd/dvd drive)--that's pretty much it as far as windows apps go.  There's an equivalent or better app in linux for everything else.

Have fun chopping up mp3s...Another nice feature of 'directcut is you can add simple fades.

---

