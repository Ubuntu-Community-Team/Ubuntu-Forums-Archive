---
title: "[SOLVED] abcde throws new flac error"
date: 2009-01-07
forum: Multimedia Software
---

### Post by logos34 on 2009-01-07
I just got this error trying to rip a cd to flac:

> Encoding track 17 of 23: Dialogue de l'ombre double - Transition III à IV...
flac 1.2.1
Tagging track 17 of 23: Dialogue de l'ombre double - Transition III à IV...
/home/user/abcde.4e0e4917/track17.flac: [COLOR="Red"]ERROR: reading metadata, status = "FLAC__METADATA_CHAIN_STATUS_ERROR_OPENING_FILE"[/COLOR]

[COLOR="Red"]The FLAC file could not be opened.  Most likely the file does not exist
or is not readable.[/COLOR]
[ERROR] abcde: [B][COLOR="Red"]The following commands failed to run:
tagtrack-flac-17: returned code 1: nice -n 10 metaflac --no-utf8-convert --import-tags-from=- /home/user/abcde.4e0e4917/track17.flac[/COLOR][/B]
Finished. Not cleaning /home/user/abcde.4e0e4917.

Been maybe a couple months since I ripped to flac, so I'm not sure exactly when this problem cropped up.

I've tried reinstalling flac.  No diff.  

Why is it not finding the track.flac file?

why is it trying to run 'metaflac --no-utf8-convert' ... etc?  I have metaflac option hashed out in abcde,conf

---

### Post by logos34 on 2009-01-07
I even saved the .wav and converted it with 

flac -8 track17.wav

produced a 'track17.flac' that plays fine

hmm...

apparently a problem reading the tag is throwing it for a loop

Edit: oh, and I tried two other cds--same thing

I googled it but only found [this ]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=415635")from the abcde dev clement.  The svn trunk site is dead atm so I can't try the newer version

---

### Post by logos34 on 2009-01-13
ok, it turns out this is the problem:

FLACOPTS="-v -8"

Should be:

FLACOPTS="-[COLOR="Red"]**V**[/COLOR] -8"

("-V"  --Verify option)

Somehow it got changed.  To think it all came down to a letter in the wrong case!

---

### Post by andrew.46 on 2009-01-14
Hi logos,

Loved the story :-). And I have also purloined this setting to my own .abcde.conf, thanks for bringing this one to my attention! It is a great shame that this script appears to be slowly withering away with no developer at the moment, hopefully somebody will pick it up soon.

All the best,

Andrew

---

