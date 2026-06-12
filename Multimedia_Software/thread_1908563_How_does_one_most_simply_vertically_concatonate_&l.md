---
title: "How does one most simply vertically concatonate &lt;10 differently sized screenshots?"
date: 2012-01-13
forum: Multimedia Software
---

### Post by rocksockdoc on 2012-01-13
I was trying to write a simple Ubuntu DVD-authoring tutorial, but was hampered by the forum limit of 5 screenshots per post:
- [**Newbie learns simple steps to authoring my 1st video DVD disc (+menus, +subtitles)**]("http://ubuntuforums.org/showthread.php?p=11608852#post11608852")

So I figured I'd simply vertically concatonate about ten sequential png screenshots into a single png file (which one can easily accomplish on Windows with Irfanview "Create panorama").

Searching for panorama, I find there is the Imagemagick command:
- [SOLVED]                          [Panorama image as in Irfanview...]("http://ubuntuforums.org/showthread.php?t=1856395&highlight=imagemagick+panorama")

But, I can't get the syntax to work to concatenate vertically without error:
```

$ montage Screenshot.png Screenshot-1.png Screenshot-2.png Screenshot-3.png Screenshot-4.png Screenshot-5.png Screenshot-6.png Screenshot-7.png -mode \ -mode Concatenate -tile Brasero brasero.png
REPORTS:
montage: unrecognized image mode ` -mode' @ montage.c/MontageImageCommand/1184.

```Searching some more, I find the "Hugin" panorama creator exists in Ubuntu by default:
- [automatic panoramic photo "stitcher" for linux?]("http://ubuntuforums.org/showthread.php?t=442425&highlight=hugin+panorama+creator")

But, the very first thing Hugin asks is incomprehensible to me for a screenshot:
"Camera & Lens data: Please enter the horizontal field of view (HFOV) or the focal length and crop factor".

Nothing I type in makes any sense to Hugin to simply vertically concatenate a bunch of differently sized Ubuntu screenshots.

Any suggestions on how best to vertically concatenate a dozen (or so) Ubuntu screenshots?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210785&stc=1&d=1326491174[/IMG]

---

### Post by Basher101 on 2012-01-13
why not upload them at [http://ompldr.org/](http://ompldr.org/) and paste the thumbnail here? this way you can add as many as you want.. (you must copy the text at the very most bottom that is inside a box below the links)

regards

p.s. here is a photo from my computer i made to show another user on UF 

[[img]http://ompldr.org/tYzY5MQ[/img]](http://ompldr.org/vYzY5MQ)

the thumbnail code looks like this ```
[ url=http://ompldr.org/vYzY5MQ][img] http://ompldr.org/tYzY5MQ[/img ][/url] 
``` so you can recognize it. (note that i placed some spaces in there, otherwise it still turns out as a thumbnail...)

---

### Post by shantiq on 2012-01-14
hi rsd    you probably need -append function here not montage


so here  for vertical 

```
convert 1.png 2.png 3.png 4.png   -append  final.png
```


for horizontal

```
convert 1.png 2.png 3.png 4.png   +append  final.png
```




**imagemagick is a bit confusing on that   altho it is such a brilliant prog**

---

### Post by rocksockdoc on 2012-01-15
> **Basher101 said:**
> why not upload them at [http://ompldr.org/](http://ompldr.org/) and paste the thumbnail here?

Being an old guy who has seen many picture sites disappear over time, that's not what the point is for this thread. But thanks for that advice. I generally shun picture sites because I believe a forum post should last as long as the thread lasts, including the pictures.

> **shantiq said:**
>  -append function here not montage

The ±append worked PERFECTLY!

I must add this hint to my file of most-useful non-intuitive conversion commands! :)

[LIST]
[*]PDF to picture for posting to forums:
[LIST]
[*]convert -density 300 file.pdf file.png
[/LIST]
 
[*]Resize JPG:
[LIST]
[*]convert -resize 640x480 -quality 90 big.jpg small.jpg
[/LIST]
 
[*]Add an annotation border:
[LIST]
[*]convert file.jpg -bordercolor white -gravity south -splice 0x100 newfile.jpg
[/LIST]
 
[*]Create an animated GIF:
[LIST]
[*]convert -delay 100 -loop 0 image*.jpg animation.gif
[/LIST]
 
[*]Concatenate pictures horizontally & vertically:
[LIST]
[*]convert 1.png 2.png 3.png 4.png ±append  final.png
[/LIST]
 
[/LIST]

---

### Post by shantiq on 2012-01-15
hi again rsd   i am curious here     how do you manage to stack + and - that way  ```
±append
```      is it a trick on your keyboard or can anyone do that?

ok got it special character from LibreOffice  :KS:KS    neat    ```
 ±
```

---

### Post by rocksockdoc on 2012-01-15
> **shantiq said:**
> ok got it special character

Over the years, whenever I've seen special characters that work for most forums (not all do), I saved them for future use.

Here are the ones I've saved so far that seem to work most of the time:

[LIST]
[*] °  ¢  ±  ÷  ·  µF  § £  &#8364;   ¿
[*] 1st, 2nd, 3rd, 4th, 5th, etc. (darn, superscripts didn't work on this forum)
[*]½  ¼
[*] BIGsmall, X-x[FONT=Arial,  Helvetica,  sans-serif][SIZE=2], H2SO[/SIZE][/FONT]4 (darn, subscripts don't work on this forum apparently)
[*] TM ® (darn, TM didn't work as a superscript, but registered worked. Go figure)
[*] cross out (EDIT: darn, this didn't work on this forum ... it's supposed to have a line through the middle)
[/LIST]
EDIT: Most of these work on most forums - but this particular forum disables a lot of them! :(

---

### Post by rocksockdoc on 2012-01-17
I just used both the horizontal (+) append with the vertical (-) append for this thread:
- **[COLOR=#980101][B][ubuntu]**[/COLOR] [Is this a bug in GNOME Panel 2.30.2 (where buttons go blind on the sides)? ]("http://ubuntuforums.org/showthread.php?p=11617353#post11617353")[/B]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211021&stc=1&d=1326825040[/IMG]

It's interesting that there are no borders in the result; and in looking at Imagemagick options, I can see no sub option to the  ±append command that provides a border.

[LIST]
[*][ImageMagick append options]("http://www.imagemagick.org/script/command-line-options.php")
[*][ImageMagick examples]("http://www.imagemagick.org/Usage/basics/")
[*][ImageMagick command line options]("http://web.njit.edu/all_topics/Prog_Lang_Docs/html/imagemagick/www/command-line-options.html")
[/LIST]
Moving forward, I guess I'll run the 'border' command before running the ±append command to create a border between the concatenated images.
- [COLOR=#980101]**[ubuntu]**[/COLOR]                          [Stringing commands together to manage typical digital photo operations]("http://ubuntuforums.org/showthread.php?t=1839153")

Something like this should work to add a border to the left-most picture when appending two side by side:
```

$ convert leftpic.jpg -bordercolor white -gravity east -splice 0x10 rightpic.jpg +append final.jpg

```

---

### Post by shantiq on 2012-01-17
hi again   rsd    have you seen [**this guide**]("http://www.imagemagick.org/Usage/") here

it is much more thorough and might help you here:KS   



This intrigued me so had a look [**here**]("http://www.imagemagick.org/Usage/crop/")   click on > Border, adding space around the edge of an image link at top of the page

=======================================

So did




```
convert 1.png   2.png   -bordercolor LimeGreen  -border 50x50 +append  final.png &&
convert 2.png    3.png   -bordercolor LimeGreen  -border 50x50  +append  final2.png &&
convert  final.png final2.png -append finalfinal.png
```


and got [ATTACH]211032[/ATTACH]   with only three images gets tricky    maybe add a white one of the same size as a fourth thus

> convert 1.png   2.png   -bordercolor LimeGreen  -border 50x50 +append  final.png &&
convert 3.png    blank.png   -bordercolor LimeGreen  -border 50x50  +append  final2.png &&
convert  final.png final2.png -append finalfinal.png

[CENTER][ATTACH]211033[/ATTACH][/CENTER]

---

### Post by shantiq on 2012-01-17
also here montage is useful too [maybe not as easy tho]


> montage *  -bordercolor red -border 20x20   -geometry 500x500+2+2  bloc.png


-geometry modifies the size of each image if omitted 500x500 here the original size of images  is retained

> montage *  -bordercolor red -border 20x20   -geometry +2+2   bloc.png

[CENTER][ATTACH]211042[/ATTACH][/CENTER]

---

### Post by rocksockdoc on 2012-01-17
> **shantiq said:**
> 
```
convert 1.png   2.png   -bordercolor LimeGreen  -border 50x50 +append  final.png &&
convert 2.png    3.png   -bordercolor LimeGreen  -border 50x50  +append  final2.png &&
convert  final.png final2.png -append finalfinal.png
```

Thanks for going the extra mile to help someone!

Given the three 128x128 pixel images below {1.jpg, 2.jpg, & 3.jpg} ... I duplicated your command sequence and it worked just fine:
```
$ convert 1.jpg 2.jpg -bordercolor LimeGreen -border 10x10 + append final.jpg
$ convert 2.jpg 3.jpg -bordercolor LimeGreen -border 10x10 +append final2.jpg
$ convert  final.jpg final2.jpg -append finalfinal.jpg
```Here's what that sequence of commands resulted in:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211054&stc=1&d=1326854232[/IMG]


> **shantiq said:**
> also here montage is useful too 

The ImageMagick montage command does seem to end up with a more elegant result:
```
montage 1.jpg 2.jpg 3.jpg  -bordercolor red -border 10x10   -geometry +2+2   bloc.jpg
```Here's what that command resulted in:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211055&stc=1&d=1326854618[/IMG]

---

### Post by shantiq on 2012-01-18
Nice.   So if you use 3 images with Montage it ignores the +2+2 and lines them up


If 3 lined up was your wish again +append is probably better since it retains original size of images whereas Montage requires added info   so


> convert 1.jpg 2.jpg 3.jpg  -bordercolor brown -border 20x20    +append  final.jpg

[CENTER][ATTACH]211067[/ATTACH]
[/CENTER]

**But** and more elegantly Montage [COLOR="DarkRed"]will leave a little gap in between[/COLOR]

so we get   > montage -geometry +2+2  1.jpg 2.jpg 3.jpg  -bordercolor brown -border 20x20    final2.jpg


[CENTER][ATTACH]211068[/ATTACH][/CENTER]

---

### Post by rocksockdoc on 2012-01-18
> **shantiq said:**
> Nice.   So if you use 3 images with Montage it ignores the +2+2 and lines them up

Yea. And, montage seems to have added a space (so maybe the border wasn't needed to be specified after all).

> **shantiq said:**
> **But** and more elegantly Montage [COLOR=DarkRed]will leave a little gap in between[/COLOR]

Yeah. I had noticed that little gap. That's convenient. So Imagemagick montage is a bit more elegant than is ±append.

Thanks for taking the time and effort to help me!

Example:
Given these three separate screenshots: 1.jpg 2.jpg 3.jpg, this is what they look like individually added in this forum:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211081&stc=1&d=1326910931[/IMG][IMG]http://ubuntuforums.org/attachment.php?attachmentid=211082&stc=1&d=1326910931[/IMG][IMG]http://ubuntuforums.org/attachment.php?attachmentid=211083&stc=1&d=1326910931[/IMG]

Here's the result from this montage command:
```
montage -geometry +2+2  1.jpg 2.jpg 3.jpg  -bordercolor brown -border 20x20    final2.jpg 			 		
```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211084&stc=1&d=1326911062[/IMG]

And, here's the result without the border being specified:
```
montage -geometry +2+2 1.jpg 2.jpg 3.jpg -bordercolor brown
```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211085&stc=1&d=1326911138[/IMG]

Since I can only upload 5 items per post, I'll continue in the next post.

---

### Post by rocksockdoc on 2012-01-18
Since the montage bordercolor apparently was meaningless without a border, here's the resulting montage command on the three images 1.jpg, 2.jpg, and 3.jpg:
```
montage -geometry +2+2 1.jpg 2.jpg 3.jpg final4.jpg
```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211086&stc=1&d=1326911326[/IMG]

Here's your nice example with the append command:
```
convert 1.jpg 2.jpg 3.jpg  -bordercolor brown -border 5x5    +append  final.jpg 
```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211088&stc=1&d=1326911508[/IMG]

Personally, I like the results from montage ... but it's harder to use than ±append.

---

