---
title: "Archiving audio CDs: how to deal with weird formats?"
date: 2010-10-31
forum: Multimedia Software
---

### Post by Objekt on 2010-10-31
Recently I've been archiving my audio CD collection to hard drive as *.toc/*.bin file pairs using Brasero.  Getting Brasero working was an ordeal; details here: [http://ubuntuforums.org/showthread.php?p=10032077&highlight=brasero+won%27t+rip+audio+cd#post10032077]("http://ubuntuforums.org/showthread.php?p=10032077&highlight=brasero+won%27t+rip+audio+cd#post10032077")

I have problems with some CDs, because they are not, strictly speaking, standard audio CDs.  One example: Blink 182's Enema of the State.  It is some kind of wacky audio CD + data format, and will not rip with Brasero.  Whether I try to rip it with the "toc" or "cdrdao image" option, I get an error dialog stating "The drive is busy." (?!)  If I try the "Readcd/Readom image" option, I get this error:
```
The image could not be created at the specified location. 
Do you want to specify another location for this session 
or retry with the current location?  
You do not have the required permissions to use this drive.
```

That last is bizarre; I certainly *do* have full read/write permissions in my /home folder.

Any ideas on how to get around this?  Maybe I should use another image ripping program?

I'd also like to rip regular audio CDs to a single file, if possible.  Does any such option exist?  So far I've been ripping to *.toc/*.bin file pairs.

---

