---
title: "unrar failing to.........unrar ( proof code inside )"
date: 2009-08-10
forum: Multimedia Software
---

### Post by brucezepplin on 2009-08-10
Hi, could I get a bit of help here as to why unrar is failing to extract a .rar file that I want to watch ( torrent of final fantasy advent children ). Here is the code:

[code]
arron@arron-laptop:~/Anime/Final.Fantasy.VII.Advent.Children.Complete.2009.BRRip.XviD-wD.SCENELOVERS$ unrar x ffac1.r00 

unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


Extracting from /home/arron/Anime/Final.Fantasy.VII.Advent.Children.Complete.2009.BRRip.XviD-wD.SCENELOVERS/ffac1.r00

Extracting  Final.Fantasy.VII.Advent.Children.Complete.2009.BRRip.XviD-wD.avi Failed    
[COLOR=Red]1 Failed[/COLOR]
arron@arron-laptop:~/Anime/Final.Fantasy.VII.Advent.Children.Complete.2009.BRRip.XviD-wD.SCENELOVERS$ unrar l ffac1.r00 

unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers
[code]

Am I doing something wrong here? 

Thanks, Arron.

---

### Post by wojox on 2009-08-10
Did you try double clicking the file?

---

### Post by brucezepplin on 2009-08-10
yeah, I'm a native windows user so that was the first thing I tried! I managed to open the file up in archive manager, extract the file, but when I follow on to the extracted file destination it takes me to the unextracted .rar file. So I'm going round in circles : s

---

### Post by andrew.46 on 2009-08-14
Hi brucezeppelin,

> **brucezepplin said:**
> Hi, could I get a bit of help here as to why unrar is failing to extract a .rar file that I want to watch ( torrent of final fantasy advent children ). Here is the code:

```

arron@arron-laptop:~/Anime/Final.Fantasy.VII.Advent.Children.Complete.2009.BRRip.XviD-wD.SCENELOVERS$ unrar x ffac1.r00 
```

I suspect that the file you are attempting to extract is a *section* of a multi-part rar archive. Have a look and you will probably see ffac1.r002, ffac1.r003 etc in the same directory. There will also be a file with the suffix *.rar* only (perhaps ffac1.rar) and this is the one that you need to run the unrar command on. This will join the multi-part archive and then extract it.

All the best,

Andrew

---

