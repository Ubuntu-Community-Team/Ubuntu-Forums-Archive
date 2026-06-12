---
title: "explain code"
date: 2009-11-17
forum: Multimedia Software
---

### Post by littlepeon on 2009-11-17
hey there...new to command line batch files...
have a line of code:

rename -v 's/\.flv.avi/\.avi/' *.flv.avi

could some1 please break this down (all the switches) as to what it is doing (i know it is renaming the files and taking away the .flv--what i don't know is what the -v switch is/does 'yes i have goggle-no luck'--do i have to include the /\ if my files don't have spaces-i assume that is what that is for.....is the 's' a variable?)
i would like to change/use this code for another batch file.....like i said i'm new to command line.......

txs
-Peon

---

### Post by mobilediesel on 2009-11-17
> **littlepeon said:**
> hey there...new to command line batch files...
have a line of code:

rename -v 's/\.flv.avi/\.avi/' *.flv.avi

could some1 please break this down (all the switches) as to what it is doing (i know it is renaming the files and taking away the .flv--what i don't know is what the -v switch is/does 'yes i have goggle-no luck'--do i have to include the /\ if my files don't have spaces-i assume that is what that is for.....is the 's' a variable?)
i would like to change/use this code for another batch file.....like i said i'm new to command line.......

txs
-Peon

```
rename -v 's/\.flv.avi/\.avi/' *.flv.avi
```
**rename** - self-explanatory.
**-v** - verbose, shows exactly which files it renamed.
**'s/** - start a regular expression
**\.flv.avi** - matches filenames containing *.flv.avi*
**/** - separates the find and replace
**\.avi** - replacement for the filenames matched
**/'** - end of the regular expression
***.flv.avi** - all files ending with *.flv.avi*

It could be rewritten as ```
rename -v 's/\.flv//' *.flv.avi
```
so that it simply removes the *.flv* from the filenames.

---

### Post by littlepeon on 2009-11-18
hey there....
thanks!!!!
am just getting used to simple bash commands (am from a simple dos world) and pipes/regex confuse the snot outta me.....

was thinking that there was to many .avi's there--so i knew something was going on...

am glad anytime someone talks something out instead of the RTFM/use google reply...

-Peon

p.s.
just noticed your coordinates--glad to see Ann Arbor's influence hasn't contaminated everyone in MI.-go Buckeyes! :lolflag:

---

### Post by mobilediesel on 2009-11-18
> **littlepeon said:**
> hey there....
thanks!!!!
am just getting used to simple bash commands (am from a simple dos world) and pipes/regex confuse the snot outta me.....

was thinking that there was to many .avi's there--so i knew something was going on...

am glad anytime someone talks something out instead of the RTFM/use google reply...

-Peon

p.s.
just noticed your coordinates--glad to see Ann Arbor's influence hasn't contaminated everyone in MI.-go Buckeyes! :lolflag:

I only left Windows/DOS about a year and a half ago. When you start getting used to the Unix/Linux way of doing it, you wonder why you didn't switch sooner! I try to give at least a partial answer before pointing to Google.

Originally from Flint, lived in Texas awhile and now back in Michigan to freeze my rear end off! Half my wife's family lives on Ohio so that's always fun to go there for thanksgiving. One side of the room laughing at the other every time there's a touchdown on the tv.

---

