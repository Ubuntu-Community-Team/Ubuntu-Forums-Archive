---
title: "Extract audio from many .flv video"
date: 2009-07-09
forum: Multimedia Software
---

### Post by afeasfaerw23231233 on 2009-07-09
From this thread [http://ubuntuforums.org/showthread.php?t=1101022](http://ubuntuforums.org/showthread.php?t=1101022)
 I use ffmpeg to extract audio from a download .flv. However I have 30 .flv files in this folder. How can I extract audio from all files in this folder by ffmpeg using a single command? Also I would like to know how to display the audio information of multiple files by the **ffmpeg -i** command. Thanks!

---

### Post by amauk on 2009-07-09
cd to the directory containing the flash files, and type in
```
for FILE in *.flv
do
ffmpeg -i "$FILE" -vn "${FILE}.mp3"
done
```
this will loop over all the flv files

---

### Post by afeasfaerw23231233 on 2009-07-09
thanks!

---

