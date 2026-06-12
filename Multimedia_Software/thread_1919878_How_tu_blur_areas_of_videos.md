---
title: "How tu blur areas of videos?"
date: 2012-02-03
forum: Multimedia Software
---

### Post by Patrunjel007 on 2012-02-03
Hi. I am interesting in blurring areas of a video. The areas have constant coordinates (not like blurring faces, for example, which move all the time).
I have tried OpenShot, but apparently it doesn't support blurring (at least from what i've read online), so I went to LiVES, but that one just tells me that the video format isn't compatible (the video file is a .avi, though).

I just want something simple that can get the job done (i'm not that interested in video editing, I just want to use it this one time for school). Can you please recommend something?

---

### Post by wolfen69 on 2012-02-03
I believe Kdenlive has an *obscure* feature that will work.

---

### Post by pixiq on 2012-02-04
You can use OpenShot to put a picture or video 'in front' covering the main video (or partially covering if semi-transparent). That is a good way to show a signature or some text, and it could also be used to cover something you don't want to show.

---

### Post by pixiq on 2012-02-04
***mplayer*** can remove (or try to remove) logos (or other things on a fixed place), see
```
man mplayer
``````
       delogo[=x:y:w:h:t]
              Suppresses a TV station logo by a simple  interpolation  of  the
              surrounding  pixels.  Just set a rectangle covering the logo and
              watch it disappear (and sometimes something even uglier appear -
              your mileage may vary).
                 <x>,<y>
                      top left corner of the logo
                 <w>,<h>
                      width and height of the cleared rectangle
                 <t>  Thickness of the fuzzy edge of the rectangle (added to w
                      and h).  When set to -1, a green rectangle is  drawn  on
                      the screen to simplify finding the right x,y,w,h parame&#8208;
                      ters.

       remove-logo=/path/to/logo_bitmap_file_name.pgm
              Suppresses a TV station logo, using a PGM or PPM image  file  to
              determine  which pixels comprise the logo.  The width and height
              of the image file must match those of  the  video  stream  being
              processed.   Uses the filter image and a circular blur algorithm
              to remove the logo.

                 /path/to/logo_bitmap_file_name.pgm
                      [path] + filename of the filter image.

```

---

