---
title: "twinview and wallpaper"
date: 2009-07-20
forum: Multimedia Software
---

### Post by munruh on 2009-07-20
I am using twinview on a dual monitor configuration. I did not like
the wallpaper split with half on each screen. I found examples on
using Gimp to mirror and combine images into one to fill both
monitors. That seemed like a lot of hand work for only one image and a
whole lot of work if you wanted very many. I use cron and a bash
script to randomly select wallpaper out of a directory and change it
hourly. I added one line to the script that creates a mirror image of
an original image. The mirror and the original are combined into a tmp.file
that is applied as the wallpaper. I do not need to modify the pictures
I want for desktop backgrounds, just drop them into the directory
containing my wallpaper. I used ImageMagick to do the heavy lifting.
Following is the line I added:

convert orig.jpg \( +clone -flop \) +append +clone +delete tmp.jpg

Example: [Screen Shot]("http://img136.imageshack.us/i/twinviewpng.jpg/")

Hope someone finds this helpful.

---

