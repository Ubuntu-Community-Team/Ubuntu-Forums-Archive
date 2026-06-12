---
title: "Create a movid DVD from avi files?"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by johann_p on 2007-04-29
I have a couple of AVI files laying around and I would like to burn a DVD from them that I can play on any DVD player. I do not need fancy menus or anything, just a dvd where each chapter corresponds to one AVI file.

How can I do this? What kind of media should I use so that I can play them in any consumer DVD player? 

I expected to run k3b and drag'n'drop my files to a DVD movie project just like I would do it with mp3s and an audio project, but that option is not available.

---

### Post by Scruffynerf on 2007-04-29
johann_p, I'm trying to do the same thing in this thread: [Burning DVD's shouldn't be this hard]("http://ubuntuforums.org/showthread.php?t=426920")

Am waiting and seeing.

---

### Post by Teamgeist on 2007-04-29
Ever heard of DeVeDe?
You should try that. It work great for me.
[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)
or look for it on 
[www.getdeb.net](www.getdeb.net)

---

### Post by ianhaycox on 2007-04-29
I've had really good results from tovid, [ToVid Wiki]("http://tovid.wikia.com/wiki/Main_Page") It just worked for me.

---

### Post by Scruffynerf on 2007-04-29
> **Teamgeist said:**
> Ever heard of DeVeDe?
You should try that. It work great for me.
[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)
or look for it on 
[www.getdeb.net](www.getdeb.net)

It converts fine, just won't burn. Also, when attempting to play the dvd on a normal dvd player, your dvd player won't recognise the disk.

---

### Post by johann_p on 2007-04-29
Just tried DeVeDe [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html) which is available in Synaptic from the multiverse/utils repository. This program looks extremely good, easy to use and it converted my files to an iso file without problems. 
I then burned that ISO to DVD using k3b. The DVD played fine, but there was no menu and the order of the files was odd ... I'll have to check that.

Tovid does not seem to be available from the Ubuntu repositories and since I try to avoid installing software from other sources, I did not bother testing it.
EDIT: installed tovid from its homepage and the first I got when I run "tovidgui" is an error message :(

---

### Post by fakie_flip on 2007-04-30
Post the error message here. You may be missing some dependencies.

---

### Post by johann_p on 2007-04-30
> **fakie_flip said:**
> Post the error message here. You may be missing some dependencies.
I installed from the tar.gz (there is no Ubuntu package) with configure/make/install and there was no complaint about anything missing.

When I run "tovidgui" I get:
```

Traceback (most recent call last):
  File "<Installprefix>/bin/tovidgui", line 43, in <module>
    from libtovid.gui.frames import TovidFrame
ImportError: No module named libtovid.gui.frames

```

---

### Post by fakie_flip on 2007-04-30
All you have to do is put your error or part of your error in google and start searching. Yes, there is a deb, but others here were getting the same error from it as you were. Look at post #355. A guy found the cause of the problem and a fix. Another guy tried the suggestion in post #359 and said it worked too, so you should give it a try, or you can get the newest deb that is supposed to not have any problems in Feisty.

[http://ubuntuforums.org/showthread.php?t=183936&page=36](http://ubuntuforums.org/showthread.php?t=183936&page=36)

---

### Post by johann_p on 2007-04-30
I found the deb package now and managed to run the tovid GUI. The program looks very nice and I like the clear layout of the GUI and the instructions page.

My biggest concern is that there seems to be no indication whatsoever about how much DVD space the movies I add already use up -- how am I supposed to figure out when to stop? Surely it cannot be that only after a long time of encoding I will see if this is bigger than 4.7GB or not? Am I missing anything here?

---

