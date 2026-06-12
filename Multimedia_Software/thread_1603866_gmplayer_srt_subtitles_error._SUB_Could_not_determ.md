---
title: "gmplayer srt subtitles error. SUB: Could not determine file format"
date: 2010-10-23
forum: Multimedia Software
---

### Post by luvshines on 2010-10-23
I installed mplayer GUI today on Ubuntu 10.04, had been using command line only for long :)

When I tried to open Video file it gave /dev/mag_vo error. I googled and found that I have to select some other driver for playing since that one is broken.
**I then selected gl2 and now video is working fine**

**But when I try to load subtitles, I get the following error on the terminal**:
```

[GUI] Loading subtitles: /home/scoobydo/movies/lotr.fotr.srt
SUB: Could not determine file format
Cannot load subtitles: /home/scoobydo/movies/lotr.fotr.srt
```

It is simple srt file and VLC is able to show the subtitles without any hitch. But I want to run gmplayer only :D
I also noticed that mplayer also was not able to pick these subtitles(it's same as avi file name and in same directory)

Any ideaz ??

---

### Post by andrew.46 on 2010-10-23
Hi luvshines,

Sounds a little odd. Can you force the subtitle from the commandline as follows:

```
mplayer -sub lotr.fotr.srt lotr.fotr.avi
```

although this may simply give the error you have seen with GMPlayer :(. BTW GMPlayer is almost abandoned by the MPlayer developers and perhaps you should to? Best replacement is SMPlayer:
```

sudo apt-get smplayer
```

Andrew

---

### Post by luvshines on 2010-10-24
When I run mplayer with -sub option, it still displays the same error.
Even smplayer won't show it :(

I tried some things and have some interesting result
When I do cat -t for any other srt file it shows me
```

## cat -t output
1011
01:33:28,920 --> 01:33:31,763
DAWN: # Bye-bye, bye-bye #

## Actual line from srt
1011
01:33:28,920 --> 01:33:31,763
DAWN: # Bye-bye, bye-bye #

```

But this one shows
```

## cat -t output
^@1^@6^@6^@4^@^M^@
^@0^@1^@:^@5^@0^@:^@5^@0^@,^@8^@4^@4^@ ^@-^@-^@>^@ ^@0^@1^@:^@5^@0^@:^@5^@1^@,^@8^@3^@3^@^M^@
^@E^@n^@g^@l^@i^@s^@h^@ ^@-^@ ^@U^@S^@ ^@-^@ ^@S^@D^@H^@^M^@

## Actual line from file
1664
01:50:50,844 --> 01:50:51,833
English - US - SDH
```

So, for any other srt, output is same as actual line, but for this one, it is loaded with lots of ^@ and ^M character

I also tried fromdos, but no success :(

---

### Post by luvshines on 2010-10-24
Well, I downloaded another srt file and that one is running fine
I guess, the earlier one had some unknown characters which were not visible in 'vim' but cat -t revealed them :D, and mplayer was not able to understand what was going, poor mplayer.
VLC was smart enuf to read though ;)

Any idea what those characters were. Unicode ??
I'll mark this SOLVED newayz

Thanx for your responses :)

---

### Post by Jercos on 2010-11-09
To invoke some very minor necromancy in the name of setting things right for potential future users without an alternate subtitle file to use, the file looked to be in UTF-16 (or UCS2). Running 
```
iconv -f UTF-16 -t UTF-8 filename.srt
```
Worked for me in a similar case.

---

