---
title: "Watermarking photos"
date: 2006-11-21
forum: Multimedia &amp; Video
---

### Post by cchevy on 2006-11-21
is there a program that can automaticaly watermark images or place a photo(logo) on them?

---

### Post by eeGhoong0ais on 2006-11-21
> **cchevy said:**
> is there a program that can automaticaly watermark images or place a photo(logo) on them?

The Imagemagick suite can automate pretty much any image-processing task you can think of, but its documentation isn't very good, so you might want to check out Anthony Thyssen's [examples of Imagemagick usage]("http://www.cit.gu.edu.au/%7Eanthony/graphics/imagick6/").

---

### Post by eeGhoong0ais on 2006-11-21
... and here's some specific [watermarking]("http://www.cit.gu.edu.au/%7Eanthony/graphics/imagick6/annotating/#wmark_image") info.

---

### Post by cchevy on 2006-11-21
isn't there a gui version or other program with gui?

this doesnt look complicated when u have instructions, but i would prefer a gui version

---

### Post by eeGhoong0ais on 2006-11-21
> **cchevy said:**
> isn't there a gui version or other program with gui?

Ah ... I misunderstood what you meant by "automatic" - for me, it isn't automatic unless I can get a program to do it unattended.

The mother of all Free GUI image manipulation programs is The GIMP. If there isn't already a watermark plugin hiding somewhere in its menus, I should think a little googling around will find one for you.

---

### Post by cchevy on 2006-11-21
thanks man

i really appreciate your effort

this whole ubuntu thing is the best thing that happeed lately

i feel like i got a new pc, all excited

and i like the challenge

---

### Post by malico on 2007-12-09
cchevy,

There are a few good GUI's around there, but if you're looking for speed, CLI is the only way to go. Here's a nice thing for you to try.

Create a Launcher on your Desktop with the command:

mogrify -font /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf pointsize 22 -verbose -draw "gravity south fill black text 0,33 'www.ianmurphyphotography.com' fill white text 1,32 'www.ianmurphyphotography.com' " *.jpg

Save it, and you can select 1 or multi photos and drag and drop them onto the icon. The images will now have your watermark on them!

---

