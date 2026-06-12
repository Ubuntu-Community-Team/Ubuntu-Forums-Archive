---
title: "bulk convert in ffmpeg?"
date: 2010-06-20
forum: Multimedia Software
---

### Post by shantiq on 2010-06-20
[B][COLOR="Blue"]hi there 


recently developed a taste for the Alac format and ffmpeg will oblige with this line of code

```
ffmpeg -i <input> -acodec alac <output>.m4a

```


and this worked beautifully one file at a time and

my question is : how does one do all the files in a given folder?

is there an asterisk one adds as in shntool    do any of you know Thanx in advance shan[/COLOR][/B]

---

### Post by lykeion on 2010-06-20
You can use the find command to find for example all avi files in the current folder and convert them using ffmpeg like this:
```
find . -name '*.avi' -type f -exec ffmpeg -i '{}' -acodec alac '{}'.mp4 \;
```

BTW Andrew has written a very nice introduction to the find command here:
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

---

### Post by shantiq on 2010-06-20
[COLOR=Blue]**thanx man will try it**[/COLOR]

---

