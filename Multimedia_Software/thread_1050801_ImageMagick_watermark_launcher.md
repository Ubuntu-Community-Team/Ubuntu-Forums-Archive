---
title: "ImageMagick watermark launcher"
date: 2009-01-26
forum: Multimedia Software
---

### Post by anyusername on 2009-01-26
Hi,

I found a post in the archive on how to make a desktop launcher using ImageMagick which allows an image to be dragged onto it to apply a watermark. The post is [HERE]("http://ubuntuforums.org/showthread.php?t=303962") and the command for the launcher is ```
mogrify -font /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf pointsize 22 -verbose -draw "gravity south fill black text 0,33 'www.ianmurphyphotography.com' fill white text 1,32 'www.ianmurphyphotography.com' " *.jpg
```

I'd like to use this but have the watermark as embossed, as detailed [HERE]("http://www.imagemagick.org/Usage/annotating/#wmark_text"). The code is:
```

  convert -size 300x50 xc:grey30 -font Arial -pointsize 20 -gravity center \
          -draw "fill grey70  text 0,0  'Copyright'" \
          stamp_fgnd.png
  convert -size 300x50 xc:black -font Arial -pointsize 20 -gravity center \
          -draw "fill white  text  1,1  'Copyright'  \
                             text  0,0  'Copyright'  \
                 fill black  text -1,-1 'Copyright'" \
          +matte stamp_mask.png
  composite -compose CopyOpacity  stamp_mask.png  stamp_fgnd.png  stamp.png
  mogrify -trim +repage stamp.png
```
```

  composite -gravity south -geometry +0+10 stamp.png  logo.jpg \
            wmark_text_stamped.jpg
```

Is it possible to apply the above into a launcher? I've tried but don't seem to be able to get it to work.

Thanks in advance.

---

### Post by anyusername on 2009-01-26
Been messing around with it for a couple of hours tonight and can get it to work as a script using the above code but I can't figure out how to change the 'composite -gravity south -geometry +0+10 stamp.png  logo.jpg \   wmark_text_stamped.jpg' into a launcher. Ideally I want to be able to drag an image onto the launcher and have it processed and saved back, maybe with something appended to the filename so that it doesn't overwrite the original.

---

