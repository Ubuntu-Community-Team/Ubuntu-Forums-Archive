---
title: "a question for coders ..."
date: 2012-09-01
forum: Multimedia Software
---

### Post by shantiq on 2012-09-01
Not sure where to put this so i put it here since they are audio files



how can i do this from command line?


create new folders within a folder with same name... and move files into new folder



here a picture will explain it better[ATTACH]223497[/ATTACH]



i want  folders each containing relevant flac and cue & bearing the same name


i had a go but yyyyyyyyyesss   i need help on this thanx

---

### Post by m_duck on 2012-09-01
Note that there is no error checking in this script and has only been tested quickly, so I **strongly advise you make a backup of the directory you are applying this to [COLOR=Red]first [/COLOR]**just in case this deletes, moves or just generally messes up stuff that it shouldn't. In fact it is possibly worth waiting for someone better to have a quick look at this first before you run it (sorry, I get paranoid working with files, particularly other people's!)

Assuming your files are always named as <thing1>.cue, <thing1>.flac and <thing2>.cue, <thing2>.flac etc., the following should work:
```
#!/bin/bash
for i in *.cue; do
   name=$(basename "${i}" ".cue")
   mkdir "${name}"

   mv -v "${name}.cue" "${name}/"
   mv -v "${name}.flac" "${name}/"
done
```This looks for all of the cue files in the directory from which it is run, and stores the base of that name (i.e. no path or file extension) into the variable ***name***. It then makes new directories with that name, and moves the corresponding cue and flac file into it. It does this sequentially for each cue file in the directory.

Paste it into a text editor, save it (in the directory where the stuff to sort is, i.e. the directory shown in your screenshot). Make it executable and run it with:```
cd /path/to/dir
chmod u+x scriptname.sh
./scriptname.sh
```Just to say again, make a backup first! My BASH skills aren't the best. If nothing else, it should give you a reasonable starting point.

---

### Post by shantiq on 2012-09-01
thank you m_duck . Perfection !!  :KS

please what does the -v do? in  mv -v  ...   i kinda understand the rest [more or less] but do not know what the -v is for

---

### Post by TheFu on 2012-09-01
> **shantiq said:**
> thank you m_duck . Perfection !!  :KS

please what does the -v do? in  mv -v  ...   i kinda understand the rest [more or less] but do not know what the -v is for


**man mv**
This will explain everything!  -v usually means the same thing for most CLI commands, either verbose or version.

---

### Post by m_duck on 2012-09-01
Yeah, TheFu is correct - it means verbose in this case. It says what the command is currently doing. I just use it out of habit from when copying e.g. a lot of videos. It just gives some indication of the progress of the move.

I'm glad it worked!

---

### Post by shantiq on 2012-09-01
-v   verbose    der!     well sometimes i can be a bit slow:KS:KS:KS



thanx again

---

