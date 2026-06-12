---
title: "trying to write a bash script to batch convert to mp3hd need help"
date: 2010-10-23
forum: Multimedia Software
---

### Post by shantiq on 2010-10-23
ok so i am trying to write a batch convert script for mp3hd

(do not snigger:KS)


my starting point is a script i know works i got elsewhere


```
for f in *.m4a; do ffmpeg -i "$f" "${f%.m4a}.wav"; done

``` [from here]("http://ubuntuforums.org/showthread.php?t=1500430&page=2")

and the instructions for mp3hd are as follows


mp3hdEncoder [-if infile] [-of outfile] [-br Bitrate] [options]


so trying to fuse those 2 i got to

```
for f in *.wav; do mp3hdEncoder "$f" -if .wav -of .mp3 -br 320000 "${f%.wav}.mp3"; done
```


and surprise surprise :KS it did not work

gives me   can't open or read input file .wav





any ideas?    mp3hd can be found [here]("http://www.all4mp3.com/SoftwareHD.aspx")


NB  Please i am not seeking a lecture on the plusses and minuses of mp3hd simply help on script writing   thank you

---

### Post by andrew.46 on 2010-10-23
Hi Shantiq,

Perhaps something like the following might work better:

```

for f in *.wav; do
   mp3hdEncoder -if "$f" -of "${f%.wav}.mp3" -br 320000 ; 
done

```

All the best,

Andrew

---

### Post by shantiq on 2010-10-23
thank you for that andrew but still not


what this does is loop the first track in an encode and then start again at the beginning with no resulting mp3 file being created

puzzling    i am new to this so all help is welcome


shan

---

### Post by mc4man on 2010-10-23
Seems to work ok here, do note that you can put your options first.

Ex. to vbr (high

```
#!/bin/bash
for f in *.wav; do
   mp3hdEncoder -mode 1 -if "$f" -of "${f%.wav}.mp3";
done
```

---

### Post by shantiq on 2010-10-23
thank you mc4  this works    as i said just started to look at this marvellous stuff

does one have to write #!/bin/bash

or does it not make a difference? seems not to mind either way


so  ```
for f in *.wav; do
   mp3hdEncoder -br 320000  -if "$f" -of "${f%.wav}.mp3";
done
```    gives me the 320 lossy i wanted 


syntax is totally crucial here    this is of course what i am struggling with :KS:KS     but hey gotta try

---

### Post by mc4man on 2010-10-23
> does it not make a difference? seems not to mind either way
Probably not, I tend to work from if an action produces a result that's a good thing, (even if the result is wrong),  if it produces the exact result desired then that's what I'll use.

Anyway, at some point you may wish to use a ~/bin for your scripts, some outside exec's, ect.

It can make things easier, the command to call the script simply becomes the script's name.

(if so, do make sure your chosen name isn't a 'taken' linux command of which there are 10's of thousands. Usually adding a number will prevent that.

Also by default a ~/bin will become 'first in PATH', can be useful, just keep that in mind.

To use simply create a folder in your home folder named bin and restart
mkdir bin

giving you a screen to illustrate from my desktop mav., in the case of your above script I named it hdmp3

So to use I'd just cd to the folder with tracks and  enter 
hdmp3
and it would run.

(also very useful to store scripts to be used as the Exec= for alternate .desktops and alt. or outside binaries.

---

### Post by andrew.46 on 2010-10-23
Hi shantiq,

Must be a very valuable piece of software, I felt almost worried when I read the following:

```

*       This software and/or program is protected by copyright law and       *
*         international treaties. Any reproduction or distribution of        *
*        this software and/or program, or any portion of it, may result      *
*       in severe civil and criminal penalties, and will be prosecuted       *
*                 to the maximum extent possible under law.                  *

```

:). BTW I use the same strategy as mc4man with a $HOME/bin folder for scripts and a few bits and pieces, it makes life much easier and I would highly recommend it.

Andrew

---

### Post by shantiq on 2010-10-23
thanx to you both for all info

mc4   nice collection of scripts there

those scripts are so useful


andrew   yes:KS:KS one would think it was more valuable than gold   or a state secret      that is why open source/free design intelligence is always better          coz the guys/lawyers who work for frauenhofer take it a little too seriously   


hope writng a script does not take us to

and will be prosecuted       *
*                 to the maximum extent possible under law.

 but having said that they have made the whole thing free and really easily available to us all    so kudos there       and the whole hybrid lossy /lossless i find interesting and original    shame it **does not work**
in my Samsung mp3player    but still i cherish it


knocked up a couple more to practice
which i always wanted


wav to shorten    and shorten to wav   


```
for f in *.wav; do shorten "$f" "${f%.wav}.shn"; done
```

```
for f in *.shn; do shorten -x "$f" "${f%.shn}.wav"; done
```

---

### Post by andrew.46 on 2010-10-23
Hi shantiq,

> **shantiq said:**
> hope writng a script does not take us to

and will be prosecuted       *
*                 to the maximum extent possible under law.


I have alerted the FBI :)

Andrew

---

### Post by mc4man on 2010-10-23
shantiq
if you have some wmal (lossless), a 32 bit mplayer that can play them and want to fool around a bit I'll give you a different method - batch convert with named pipes - kinda interesting

---

### Post by shantiq on 2010-10-24
> **andrew.46 said:**
> Hi shantiq,



I have alerted the FBI :)

Andrew


thank you it had to be done.

---

### Post by shantiq on 2010-10-24
> **mc4man said:**
> shantiq
if you have some wmal (lossless), a 32 bit mplayer that can play them and want to fool around a bit I'll give you a different method - batch convert with named pipes - kinda interesting

i am intrigued sounds like fun


do not currently have any wmal    i forget how to make them here on linux   had some once once


my totem movie player is 2.32.0 if that is the one you mean using gstreamer 0.10.30
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team




if you have the patience sure always keen to learn a few new tricks    thanks

---

