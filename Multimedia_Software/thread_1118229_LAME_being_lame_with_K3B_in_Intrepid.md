---
title: "LAME being lame with K3B in Intrepid"
date: 2009-04-06
forum: Multimedia Software
---

### Post by dbsoundman on 2009-04-06
I'm running Ubuntu 8.10, and I want to use K3B to import CDs to mp3 files on my computer. I initially had trouble because I forgot to install the ubuntu-restricted-extras, but now everytime I try to use the LAME encoder, whether it be with K3B or in the command line, this is what happens (this is a command-line example):
```
dan@blackdiamond:~$ lame -h --tt Cissy Strut --ta The Meters --tl The Very Best of the Meters --ty 1997 --tc - /home/dan/Organized Music//The Meters - The Very Best of The Meters
lame: excess arg Very
```

I'm not really sure why it's giving me this error, but it happens with any CD I try, and while K3B doesn't actually tell me the error like that, I just copied the error message for the LAME command in K3B and tried running it, and that is what I got. Any ideas on how to fix this?

Thanks,
Dan

---

### Post by logos34 on 2009-04-06
you need libk3b2-extracodecs too:

> sudo apt-get install libk3b2-extracodecs

try the fix [here]("http://www.linuxquestions.org/questions/showthread.php?p=3351983#post3351983")

or

[http://ubuntuforums.org/showthread.php?t=38486](http://ubuntuforums.org/showthread.php?t=38486)

Here's my k3b lame line in case you're interested:

> lame -V2 --vbr-new -q0 --ta %a --tl %m --ty %y --tc %c - %f

(options 'swap byte order' and 'write wav header' both UNchecked)

---

### Post by dbsoundman on 2009-04-06
Interesting...the first fix after the package download seems to have fixed it! Weird problem, but at least it works! Thanks!

-Dan

---

