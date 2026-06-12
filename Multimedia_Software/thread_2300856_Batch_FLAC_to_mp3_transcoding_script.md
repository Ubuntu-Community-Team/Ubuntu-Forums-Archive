---
title: "Batch FLAC to mp3 transcoding script"
date: 2015-10-28
forum: Multimedia Software
---

### Post by nekoc4se on 2015-10-28
I've been using this script to trancode single albums.

```
for file in ./*.flac; do
[ -e "$file" ] && flac -cd "$file" | lame -V0 --vbr-new - "${file/.flac/.mp3}"
done
```

But I need a script that will trancode all albums in a directory.

---

### Post by ian-weisser on 2015-10-29
dir="/home/me/music/yes 90215"
for file in $dir/*.flac; do

---

### Post by shantiq on 2015-10-29
[also added optional removal of flac in red after the event OMIT if you do want to keep the original file in folder]
It goes to each folder does the conversion gets out goes to next folder and repeats

simply cd to the directory where all these music folders are and run as one block >>


```
for i in */
do 
cd "$i"
for file in ./*.flac; do
[ -e "$file" ] && flac -cd "$file" | lame -V0 --vbr-new - "${file/.flac/.mp3}"
done [COLOR=#ff0000]**&& rm *.flac**[/COLOR]
cd ..
done
```

---

### Post by andrew.46 on 2015-10-29
It is a small point but *--vbr-new* is only required if you are using LAME 3.97 or older. Test as follows:

```

andrew@ilium~$ **[COLOR="#FF0000"]lame --version | head -n 1[/COLOR]**
LAME 64bits version 3.99.5 (http://lame.sf.net)

```

---

### Post by nekoc4se on 2015-11-10
> **shantiq said:**
> [also added optional removal of flac in red after the event OMIT if you do want to keep the original file in folder]
It goes to each folder does the conversion gets out goes to next folder and repeats

simply cd to the directory where all these music folders are and run as one block >>


```
for i in */
do 
cd "$i"
for file in ./*.flac; do
[ -e "$file" ] && flac -cd "$file" | lame -V0 --vbr-new - "${file/.flac/.mp3}"
done [COLOR=#ff0000]**&& rm *.flac**[/COLOR]
cd ..
done
```

This worked well thanks! However it did not convert sub directories.

---

### Post by shantiq on 2015-11-10
i too would like to know but do not :]
maybe a programmer could help us here please
i am guessing the first line must change

---

