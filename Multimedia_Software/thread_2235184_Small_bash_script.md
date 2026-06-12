---
title: "Small bash script"
date: 2014-07-19
forum: Multimedia Software
---

### Post by alfirdaous on 2014-07-19
Hello everybody,

I am having this small script, I do some problems with variables:

```

read -p "Please enter starting area : " areaStart
read -p "Please enter ending area : " areaEnd
read -p "Please enter original file name : " fileName
read -p "Please enter texte size : " textSize
read -p "Please enter output PNG file : " filePNG

for ((i=areaStart;i<=areaEnd;i++));
do
  printf -v f '%03d' $i
n=0; for offset in 200 220 240 260 280 320 340 360 380 400; do n=$((n+1)); ffmpeg -itsoffset -$offset -i "$fileName"_$f.png -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 "$filePNG"_"$f"_$n.png; done
```

I got this result:

```

n=0; for offset in 200 220 240 260 280 320 340 360 380 400; do n=1; ffmpeg -itsoffset - -i FILE_001.png -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 PNG_001_.png; done && ffmpeg -i FILE_001.mp4 -vn -ar 44100 -ac 2 -ab 128 -f mp3 001.mp3

```

So, I have problem with these 2 variables: "-$offset" and "$n.png"

How can I fix it??

Thanks in advance

---

### Post by slooksterpsv on 2014-07-19
You're missing another done for the first for do loop.

---

### Post by alfirdaous on 2014-07-21
this is the full code:

```

#!/bin/bash

read -p "Please enter starting area : " areaStart
read -p "Please enter ending area : " areaEnd
read -p "Please enter original file name : " fileName
read -p "Please enter texte size : " textSize
read -p "Please enter output PNG file : " filePNG



for ((i=areaStart;i<=areaEnd;i++));
do

  printf -v f '%03d' $i

echo "ffmpeg -i Original/$fileName"_"$f-Original.mp4 -strict experimental -vf "drawtext=fontfile='/usr/share/fonts/truetype/freefont/FreeSansBold.ttf':text='www.test.com':x=5:y=30:fontsize="$textSize":fontcolor=white" -vcodec libx264 -preset medium -crf 24 -acodec copy Done/"$fileName"_$f-Done.mp4 && MP4Box -add Done/"$fileName"_$f-Done.mp4 "$fileName"_$f.mp4 && ffmpeg -itsoffset -330 -i "$fileName"_$f.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 "$filePNG"_$f.png && n=0; for offset in 200 220 240 260 280 320 340 360 380 400; do n=$((n+1)); ffmpeg -itsoffset -$offset -i "$fileName"_$f.png -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 "$filePNG"_"$f"_$n.png; done && ffmpeg -i "$fileName"_$f.mp4 -vn -ar 44100 -ac 2 -ab 128 -f mp3 $f.mp3";

 done;

```

I have problem with these 2 variables: "-$offset" and "$n.png"

---

### Post by slooksterpsv on 2014-07-22
Try separating your code a bit, the whole one line to do everything with echo is very perplexing, I think it may be a root issue of the problem:

```

echo "ffmpeg -i Original/$fileName"_"$f-Original.mp4 -strict experimental -vf "drawtext=fontfile='/usr/share/fonts/truetype/freefont/FreeSansBold.ttf':text='www.test.com':x=5:y=30:fontsize="$textSize":fontcolor=white" -vcodec libx264 -preset medium -crf 24 -acodec copy Done/"$fileName"_$f-Done.mp4 
MP4Box -add Done/"$fileName"_$f-Done.mp4 "$fileName"_$f.mp4 
ffmpeg -itsoffset -330 -i "$fileName"_$f.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 "$filePNG"_$f.png 
  n=0 
  for offset in 200 220 240 260 280 320 340 360 380 400 
  do 
    n=$((n+1)); 
    ffmpeg -itsoffset -$offset -i "$fileName"_$f.png -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 "$filePNG"_"$f"_$n.png
 done 
ffmpeg -i "$fileName"_$f.mp4 -vn -ar 44100 -ac 2 -ab 128 -f mp3 $f.mp3"

```

Try outputting your code and see where it breaks at meaning instead of passing all those commands, step through 1 at a time till you figure out what the issue is. ffmpeg isn't being found in my repos so I'll address that, so I'm unable to try out your program to find where it breaks.

---

### Post by sudodus on 2014-07-22
Maybe you can get specific help with ffmpeg in the multimedia & video forum. Do you want me to move the thread to that forum?

---

### Post by alfirdaous on 2014-07-22
@[**[COLOR=#000000]slooksterpsv[/COLOR]**]("http://ubuntuforums.org/member.php?u=38762"): I will try this
@[**[COLOR=#C61919][B]sudodus**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021"): Yes please, go ahead

---

### Post by sudodus on 2014-07-22
Moved to multimedia & video, and a free bump ;-)

---

### Post by alfirdaous on 2014-07-23
this is the result of this line where it causes the problem for me:

```

n=0
  for offset in 200 220 240 260 280 320 340 360 380 400
  do
    n=1;
    ffmpeg -itsoffset - -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 file_001_.png
 done

```

however it should display this:

```

n=0
 for offset in 200 220 240 260 280 320 340 360 380 400
  do
   n=$((n+1)); ffmpeg -itsoffset -$offset -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 file_001_001.png
 done

```

and this, will increment by a

```

file_001_001.png
file_001_002.png
file_001_003.png
file_001_004.png
...


file_002_001.png
file_002_002.png
file_002_003.png

...

and so on
...


```

thanks in advance

---

### Post by steeldriver on 2014-07-23
If you want to auto-increment the output file name, you will need to do something like

```

n=0
for offset in 200 220 240 260 280 320 340 360 380 400
do
  n=$((n+1))
  **printf -v outfile 'file_001_%03d.png' "$n"**
  ffmpeg -itsoffset **-"$offset"** -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 **"$outfile"**
done

```

or

```

n=0
for offset in 200 220 240 260 280 320 340 360 380 400
do
  **printf -v outfile 'file_001_%03d.png' "$((++n))"**
  ffmpeg -itsoffset **-"$offset"** -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 **"$outfile"**
done

```

---

### Post by alfirdaous on 2014-07-23
I am still having problem with outfile for png in this line:

```

  ffmpeg -itsoffset -$offset -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 


```

outfile is empty

and this is the full code:

```

#!/bin/bash

url="site.com"
read -p "Please enter starting area : " areaStart
read -p "Please enter ending area : " areaEnd
read -p "Please enter original file name : " fileName
read -p "Please enter texte size : " textSize
#read -p "Please enter output PNG file : " filePNG

for ((i=areaStart;i<=areaEnd;i++));
do

  printf -v f '%03d' $i  # f is a variable that stores 0-padded 3-digit wide $i.mp3



echo "ffmpeg -i Original/$url"_"$fileName"_"$f-Original.mp4 -strict experimental -vf "drawtext=fontfile='/usr/share/fonts/truetype/freefont/FreeSansBold.ttf':text='www.test.com':x=5:y=30:fontsize="$textSize":fontcolor=white" -vcodec libx264 -preset medium -crf 24 -acodec copy Done/"$url"_"$fileName"_$f-Done.mp4 
MP4Box -add Done/"$url"_"$fileName"_$f-Done.mp4 "$url"_"$fileName"_$f.mp4 
ffmpeg -itsoffset -330 -i "$url"_"$fileName"_$f.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 "$fileName"_$f.png 
n=0
for offset in 200 220 240 260 280 320 340 360 380 400
do
  n=$((n+1))
  printf -v outfile '$fineName_$f_%03d.png' $n
  ffmpeg -itsoffset -\$offset -i $fileName"_"$f.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 $outfile
done
ffmpeg -i "$url"_"$fileName"_$f.mp4 -vn -ar 44100 -ac 2 -ab 128 -f mp3 $f.mp3"
done

```

---

### Post by steeldriver on 2014-07-23
Well that's different isn't it?

1. -\$offset is not the same as -"$offset"

2. '$fineName_$f_%03d.png' will not expand the $fineName or $f variables because they're inside single quotes (also you have a typo - $fi[COLOR=#ff0000]**n**[/COLOR]eName instead of $fi[COLOR=#0000ff]**l**[/COLOR]eName). Try

```

printf -v outfile '**%s**_**%s**_%03d.png' "**$fileName**" "**$f**" "$n"

```

There may be other errors

---

### Post by alfirdaous on 2014-07-24
if I do not put a backslash, the variable will not be defined

---

### Post by sudodus on 2014-07-24
In bash you ***assign a value to a variable*** like this (without $)

```
my_variable="some value"
```

You ***use a variable like this*** (with $ and if a string variable also with double quotes (but not if it should be used as an arithmetic variable (a number)).

ex 1.

```
echo "$my_variable"
```

ex 2.

```
if [ "$my_variable" == "special case" ]
then
   some action
else
   some other action
fi

```

ex 3.

```
if [ $my_variable -lt max ]
then
   some action
else
   some other action
fi
```

---

### Post by alfirdaous on 2014-07-25
I think the problem is coming from this line:

```

  printf -v outfile '%s_%s_%03d.png' "$fileName" "$f" "$n"

```

because I changed outfile variable to f variable and it works

---

### Post by steeldriver on 2014-07-25
It works fine for me (I've added an **echo** just to see what the complete command is - I can confirm it also runs successfully with ffmpeg using a random mp4 file that I renamed as file_001.mp4 however the output is too big to post here)

```

$ n=0
$ for offset in 200 220 240 260 280 320 340 360 380 400
> do
>   **printf -v outfile 'file_001_%03d.png' "$((++n))"**
>   echo ffmpeg -itsoffset -"$offset" -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 **"$outfile"**
> done
ffmpeg -itsoffset -200 -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 **file_001_001.png**
ffmpeg -itsoffset -220 -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 **file_001_002.png**
ffmpeg -itsoffset -240 -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 **file_001_003.png**
ffmpeg -itsoffset -260 -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 **file_001_004.png**
ffmpeg -itsoffset -280 -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 **file_001_005.png**
ffmpeg -itsoffset -320 -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 **file_001_006.png**
ffmpeg -itsoffset -340 -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 **file_001_007.png**
ffmpeg -itsoffset -360 -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 **file_001_008.png**
ffmpeg -itsoffset -380 -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 **file_001_009.png**
ffmpeg -itsoffset -400 -i file_001.mp4 -vcodec mjpeg -vframes 1 -an -f rawvideo -s 640x480 **file_001_010.png**

```

Are you sure you are running it as a **bash** script (not dash or **sh**)?

---

### Post by alfirdaous on 2014-07-25
nice [**[COLOR=#C61919][B]steeldriver**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1627500"), it works perfect

---

