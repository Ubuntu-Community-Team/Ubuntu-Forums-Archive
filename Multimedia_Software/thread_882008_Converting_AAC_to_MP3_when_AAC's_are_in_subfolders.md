---
title: "Converting AAC to MP3 when AAC's are in subfolders."
date: 2008-08-06
forum: Multimedia Software
---

### Post by cmlewin on 2008-08-06
I tried using the built-in sound converter, but all my music is in subfolders within my music folder. So when I add it, it will take forever b/c it wants to convert all the MP3's as well. Is there a way to just select the AAC's simply and quickly? Perhaps through terminal?

Thank you.

---

### Post by cmlewin on 2008-08-07
anyone help?

---

### Post by cozmicharlie on 2008-08-07
PACPL is a great transcoder that will do what you want.  This How To will walk you through installation and use.  It is a terminal based program (unless you are using kde then it integrates in Amarok).  
[http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl](http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl)

An example of the command you would use to convert your aac in subfolders to mp3.

```
$ pacpl --to mp3 --only aac /home/yourname/mymusic/music folder that contains your .aac files
```

This will convert all the .aac files in your music folder to mp3.  Using the --only command means it will only convert files with .aac extension

You can also tag and move the files to a new directory.  Once installed go to $pacpl --longhelp and it will list all the commands.  If you have any problems post back and I can help.

Enjoy

---

