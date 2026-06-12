---
title: "a couple of normalize-audio questions"
date: 2011-07-04
forum: Multimedia Software
---

### Post by mystmaiden on 2011-07-04
I usually put my mp3s for mix cds on my desktop, then cd Desktop and run this 

```
normalize-audio -m -v  *.mp3
```But on the manual pages here [http://manpages.ubuntu.com/manpages/lucid/man1/normalize-audio.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/normalize-audio.1.html)

I found this - 
> MIX MODE

       This mode is made especially for making mixed CD&#8217;s and the  like.   You
       want every song on the mix to be the same volume, but it doesn&#8217;t matter
       if they are the same volume as the songs on some  other  mix  you  made
       last  week.   In  mix mode, average level of all the files is computed,
       and each file is separately normalized to this average volume.What would be the command to run the normalize-audio command in mix mode?

Also, I have a purchased cd I really like but it is So  much louder than any of my other cds (my own mixes and purchased as well) - is there a way to use normalize-audio  to just turn the volume down on all the tracks at once?
 

 EDIT  - I got the answer to the first part.. the -m flag.

The second question- I didn't word it well. I was trying to figure out if I could turn all the tracks down a set amount, rather than having normalize choose the adjustment.

thanks,

mystmaiden

---

### Post by mystmaiden on 2011-07-06
bump...

---

