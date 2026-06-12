---
title: "Question about creating a mencoder script"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by DigitalDuality on 2007-11-15
Basically i created a script, and i probably went the long way about doing it.  Basically all it did was run the following command.

```
mencoder infile.wmv -ofps 23.976 -ovc lavc -oac copy -o outfile.avi && rm infile.wmv 
```

On a bunch of wmvs.  I found this on another site and it worked like a charm.   Now as mentioned in another thread ( [http://ubuntuforums.org/showthread.php?t=613986](http://ubuntuforums.org/showthread.php?t=613986) ) I have a bit of a problem.

I did **23.976** -ovc lavc -oac copy -o outfile.avi  where i should've done **23.97**.   The more i think about it, the more i kind of want to avoid going the linux route to play downloaded movies on my television with.  The machine the drive is in now is a Windows machine.  

All the files played perfectly in Linux.  They don't play so perfectly in Windows.  There's  lines all over the video, both on the computer screen.. and the television.   It doesn't matter what i play them in.   Windows Media Player simply won't play them.  VLC plays them with the lines.

So my two questions:

1. If i mount the drive on a live disc and run another script to correct the error... would the following work?

```
mencoder infile.avi -ofps 23.97 -ovc lavc -oac copy -o outfile.avi && rm infile.avi 
```

2.  It was a giant pain in the rear to copy all those file names into the script.  Is there a way (say all the files were isolated in their own directory) to just maintain the file names or at least rename them sequentially (1.avi, 2.avi, 3.avi, etc)  ?  Copying and pasting file names for over an hour isn't my idea of fun.

---

