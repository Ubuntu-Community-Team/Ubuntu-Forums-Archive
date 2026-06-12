---
title: "How do I print strings with spaces in imagemagick?"
date: 2010-09-16
forum: Multimedia Software
---

### Post by wwwookie on 2010-09-16
Hi, I've been trying for hours to print string variables with imagemagick to make dvd buttons from a shell script. The basic command is:-
```
~$ convert -size 720x480 xc:transparent -fill red +antialias -pointsize 48 -draw 'text 100,100 "Button"' image.png
```Now to print a string variable I have been using:-
```
~$ string=Button
~$ convert -size 720x480 xc:transparent -fill red +antialias -pointsize 48  -draw 'text 100,100 '"$string"' image.png
```However try as I might, when the string has spaces, as in:-
```
~$ string="Button One"
~$ convert -size 720x480 xc:transparent -fill red +antialias -pointsize 48 -draw 'text 100,100 '"$string" image.png
```Imagemagick strips off the quotes and I get an error:-
```
convert: Non-conforming drawing primitive definition `One' @ draw.c/DrawImage/3140.
```Does anyone know a trick to escape the spaces?




Secret to a long life - Don't forget to breathe.

---

### Post by wwwookie on 2010-09-19
Hi again - I found the solution:- the label:"text" command is much simpler than -draw " <parameters> 'text'", and with only one set of quotes, there's no problem putting in a variable such as

```
$: a="stringy cheese"
$: convert -size 600x400 -background blue -fill red -pointsize 70 -gravity center label:"$a" picture.png
$: display picture.png
```

The exploration coninues...

---

### Post by babixeddu on 2011-07-01
It's too late but can be useful for someone.

You can use the syntax "string '${VAR}' string" with the option "-draw". Like that:

```

#!/bin/bash

WATERMARK="A very very long string that you want to draw"

W=`exiftool -ImageWidth -s -s -s $1`

H=`exiftool -ImageHeight -s -s -s $1`

convert -size $W"x"$H xc:grey30  -gravity center -draw " fill grey70  text 0,0 '${WATERMARk}'"  stamp_fgnd.png

convert -size $W"x"$H xc:black   -gravity center -draw " fill white    text 1,1 '${WATERMARK}' text  0,0 '${WATERMARK}' fill black  text -1,-1  '${WATERMARK}'"  +matte stamp_mask.png

composite -compose CopyOpacity  stamp_mask.png  stamp_fgnd.png  stamp.png

mogrify -trim +repage stamp.png

composite -gravity south -geometry +0+10 stamp.png  $1 new_$1


```If you save it as - for example - watermark.sh, you can execute it specifing the input image file:

# . watermark.sh /path_to/my_image.jpg

:popcorn:

---

### Post by wwwookie on 2011-07-05
Babixeddu, yes my problem was that I had the quotes the wrong way round, it works fine if you use double quotes around the arguments for the -draw option and single quotes for the string intself - Thanks a lot!

---

