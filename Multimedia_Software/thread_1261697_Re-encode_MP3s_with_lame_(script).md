---
title: "Re-encode MP3s with lame (script)"
date: 2009-09-09
forum: Multimedia Software
---

### Post by tgeer43 on 2009-09-09
I'm formulating a simple 3-line shell script to batch re-encode MP3s to 128bps CBR using lame. The first line is to convert all spaces in the filenames to underscores:
```
for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done
```and it works just fine.

The second line does the actual bitrate conversion:
```
for x in `ls -1 *.mp3`; do lame -b 128 $x NEW-${x}; done
```It works fine too but note that I'm prefixing the output filename with 'NEW-' to avoid the 'Input and output filenames are the same' error. What I'd really like to do is just overwrite the original file with the new one using the original filename if possible.

Lastly I'm attempting to change the underscores in the filenames back to spaces. I thought I could just reverse the two SET parameters (" " and "_") from the first line to reverse the procedure. When I do that I get an error message that I don't understand. For example, if the current filename is:

"NEW-01._Led_Zeppelin_-_Black_Dog.mp3"

and I run the command:
```
for i in *.mp3; do mv "$i" `echo $i | tr '_' ' '`; done
```I get the following error message:

***mv: target `Dog.mp3' is not a directory***

So why is the filename getting truncated to only the last word and why is 'mv' expecting a directory name?

Any help would be appreciated.

tgeer

---

### Post by mc4man on 2009-09-09
If you wish to do this way (you'll lose tags) then this may be more suitable - doesn't care about spaces ect.

```
#!/bin/bash
mkdir save
for f in *.mp3; do lame -b 128 "$f" ./save/"${f%.mp3}.mp3"; done
rm *.mp3


```
You may want to not use the rm and confirm first, then remove .mp3's from prompt.

While not needed here this may work better for the underscore deal

# Rename to remove all strange chars
```
rename 's/ /_/g' *.mp3
```
# Rename to the original names
```
rename 's/_/ /g' *.mp3
```

---

### Post by tgeer43 on 2009-09-09
Thanks, mc4man.

That works just perfectly for me and I've incorporated it.

tgeer

---

