---
title: "How to identify 'bad' pictures on 'Picture frame' ?"
date: 2020-03-24
forum: Multimedia Software
---

### Post by susja on 2020-03-24
[COLOR=#2C2C2C][FONT=Verdana]Hello,[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]I'm using Sony picture frame. I use 4Gb SDHC card which has top directory ...DCIM/100MSDCF/ and ~20 subdirectories and around 1500 pictures in those directories.[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]It plays in 'slideshow' mode. Quite often instead of 'picture' I see some icon. It sounds to me that it's either 'bad' picture or simply it  tried to open directory.[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]Honestly ... I have no clue why I see those icons instead of normal picture.[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]My question: how could I found among those 1500 picture 'bad' ones that cause the issue? Maybe they are 'wrong' format or wrong file extension or etc[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=Verdana]Thanks[/FONT][/COLOR]

---

### Post by Holger_Gehrke on 2020-03-24
The first step should obviously be to look in the manual for you picture frame to find out what the icon means. 

If it means 'unsupported file type' you could probably use 'find' to find files which have an extension for a file type the frame does not know. The easiest way would probably to use negated criteria, something like
```

find /media/$USER/UUID_OR_VOLUMENAME_FOR_THE_SDHC_FROM_YOUR_FRAME -type f -a \! -iname '*jpg' -a \! -iname '*png' -a \! -iname '*tif'

```
which would look for normal files (that's what '-type f' means) whose names don't end in jpg, png or tif. Add further supported extensions as needed.

If the icon means 'broken file encountered' things become more complicated. The easiest way to find broken images I can think of would be to use find with '-type f -print0' as options and then use 'xargs' to feed the results into identify from imagemagick and do a bit of scripting to only print out the files identify considers broken.

Holger

---

### Post by susja on 2020-03-25
Well .. I ran your suggestion and it found only one file of 'wrong' format ... which I deleted later.
Not sure I want to follow 'imagemagick stuff because I'm not familiar with photo issues at all.
I checked manufacture of the frame and it states:
--
**icons showing in the image list indicate any of the following. The [B]picture files were edited or modified with a computer, or the file format is not supported. Pictures edited or modified by a computer may not display on the [B]digital photo frame. Ensure the pictures are saved in a compatible file format.**[/B][/B]
--
Maybe I should run 'find' again but this time check for the size of file? Someone told me that files smaller than 10 Kb could cause this issue too.
Does it make sense to you?
Appreciate your help.

---

### Post by susja on 2020-03-25
- [COLOR=#000000]Holger
I ran
 [/COLOR]find . -size -10k
It located a bunch of files. I verified that they were corrupted ( by trying to open it in photo editor ). I deleted it.
Now when I run again with size less than 40 Kb I see only directories where all my files are located.
Could it be that I see 'icon' when it hit 'directory' instead of file?
Maybe I should delete all directories and leave only files? Anyway I use it 'randomly' and in 'slideshow' mode. ..
What do you think?
Thanks

---

