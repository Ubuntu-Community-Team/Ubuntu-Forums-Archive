---
title: "metaflac, utf-8 (and abcde)"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by Klark Kockworth on 2007-08-25
I'm trying to rip my entire CD collection to FLAC and mp3 at the same time. I use abcde for this purpose.

However I've run into some problems when ripping tracknames, which have umlauts (ü,ö,ä, etc.)

When ripping such a CD, abcde gives me errors like this:
```
[ERROR] abcde: The following commands failed to run:
tagtrack-flac-03: returned code 1: metaflac --no-utf8-convert --import-tags-from=- ~/abcde.890ac50b/track03.flac
tagtrack-flac-04: returned code 1: metaflac --no-utf8-convert --import-tags-from=- ~/abcde.890ac50b/track04.flac
tagtrack-flac-06: returned code 1: metaflac --no-utf8-convert --import-tags-from=- ~/abcde.890ac50b/track06.flac
tagtrack-flac-09: returned code 1: metaflac --no-utf8-convert --import-tags-from=- ~/abcde.890ac50b/track09.flac
Finished. Not cleaning ~/abcde.890ac50b.
```

After abcde has finished there are no FLACs or mp3s of the tracks, which have umlauts.

I can't figure out where the problem is? Is it some switch with metaflac or is it my locale settings with Ubuntu?

Btw, my locale is as follows:
```
LANG=en_GB.UTF-8
LANGUAGE=en_GB:en
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=
```

Thanks!

---

### Post by EGR on 2007-08-26
Yep, that is the same problem as me. Your tracks probably do get ripped
though: try looking in your ~/abcde.### folder (~/abcde.890ac50b in the
example you give below). That's where they are in my case, simply
labelled `track#.flac'. So at worst you can manually rename them. 

Hopefully we'll find a solution.

Cheers!

---

### Post by Klark Kockworth on 2007-08-28
I solved the problem by converting the *cddbread.1* file from **[COLOR="DarkRed"]ISO 8859-15[/COLOR]** to **[COLOR="Green"]UTF-8[/COLOR]**.

I'm certain there are more elegant ways to do it, but I used *gedit* to do the conversion. 

First make sure *abcde* is in interactive mode.
ie. add
```
INTERACTIVE=y
```
to your *.abcde.conf*


Then place *gedit* in your $EDITOR (shell variable)
```
$ export EDITOR='gedit'
```


Then run abcde, and everytime you see umlauts in the cddb files, press **y** to launch gedit and save the file as UTF-8.

---

### Post by EGR on 2007-08-28
Ah, works great! Thanks alot!

Incidently, you don't have to resort to gedit here.  You can save as
utf-8 from within vim (say). In this case you would use
```

:set fileencoding=utf-8

```
and then write/exit the file (:wq)

I'm pretty sure you could do the same with other editors as well.

Cheers!

---

