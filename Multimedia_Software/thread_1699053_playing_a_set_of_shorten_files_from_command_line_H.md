---
title: "playing a set of shorten files from command line Help needed..."
date: 2011-03-03
forum: Multimedia Software
---

### Post by shantiq on 2011-03-03
ok i have a bunch of shorten files i want to play from the command line and ffplay will play them one at a time but i want to play them one after the other (the whole album)

using this

```
for f in *.shn; do ffplay  "$f"; done
```

does not work i must have forgotten something as it plays one track then stops    how can i remedy that


see image attached for setup

---

### Post by shantiq on 2011-03-03
if anyone wants to test this but does not have a shorten (.shn) file flac will do just as well

the extension is not the issue here but the moving on to the next track   i think the technical term is iteration


=================================================================

found an alternative route from command line so easy i wish i had thought it before   would still like to know if ffplay can do this too

```
mplayer *
```   to move to next track press enter


of course you need to have shorten to do this and it is easily got from [here]("http://ubuntuforums.org/attachment.php?attachmentid=174028&d=1288481430")

---

