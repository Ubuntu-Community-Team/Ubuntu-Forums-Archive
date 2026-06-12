---
title: "creating slideshow from .jpg using Mencoder"
date: 2014-09-01
forum: Multimedia Software
---

### Post by rioguia2 on 2014-09-01
I have all my photos in a directory and want to make a simple slide show where each photo displays for three seconds.  My current code provides fine quality but the slides display for less than a second.  Can anyone help me?  Thanks in advance for your help.

```
 mencoder "mf://*.JPG" -mf fps=2.3 -ovc lavc -vf scale=640:480 -o output.avi
```

---

### Post by SeijiSensei on 2014-09-02
I'm going to suggest an alternative route, creating an animated GIF from the jpegs with GIMP.  Open the first slide with GIMP, then use File > Open as Layers and select all the remaining jpegs.  They will be added as layers.  Then use File > Export and create a file with .gif as the extension.  In the dialog box to follow, check the loop box if you want the image to cycle endlessly, and enter a delay of 3000 ms between frames.  Now open the resulting image with an image viewer or a web browser to see the slideshow.

This avoids the need for someone to have a video player with the right codecs to watch your slides.

If you want to change the order of slides, open the Layers dialog with Ctrl-L and use the up and down arrows to rearrange the images.

---

### Post by rioguia2 on 2014-09-02
That's a great idea.  I'll definitely give it a try but i also want to be able to use the video approach.  In this project, I am using over 500 photos from a recent vacation to make into a slideshow.

I've made some progress.  The mencoder timing issue is solved by reducing the fps to 0.50.  

```
mencoder mf://'*.jpg' -mf w=800:h=600:fps=0.50:type=jpg -ovc lavc     -lavcopts vcodec=mpeg4:mbd=2:trell -oac copy -o output.avi 
```

In order to control the order of the slides I had to rename them to  000.JPG, 001.JPG, 002.JPG.  I used Pyrenamer to do this but I'm sure I  can find a command line tool to do the same thing later.

This brings me to the next problem:  rotating the portrait style photos.  The Imagemagick documentation suggested using jhead.

```
jhead -autorot  *.JPG  
```

[B]MY CURRENT QUESTION:

Now I need to figure out how to make the portrait style pictures are 800 in height and 600 in width.  The portrait pictures need to be reduced to 600 height and 450 in width, centered with padding added on each side to maintain consistent dimensions throughout the slideshow.  I think Imagemagick can do this.  I know that the reduced photos will degrade a bit but since I am reducing their size I don't think it will be noticeable.[/B]

---

### Post by rioguia2 on 2014-09-02
Ok resizing and centering the portrait photos is partially solved below.

**MY CURRENT QUESTION:**

  [B]Now i need to figure out how to apply it to the rest of the portrait pictures in the directory.
[/B]
```
convert 019.JPG -resize 800x600 -background black -compose Copy -gravity center -extent 800x600 -quality 92 017.jpg  
```

---

### Post by rioguia2 on 2014-09-03
Ok, I have made some progress on learning how to glob names with Imagemagick convert.  The below renames all the portrait photos (012.JPG, 014.JPG, 018.JPG) to (001.jpg, 002.jpg, 003.jpg) and skips all the standard landscape photos.  This makes the photos out of order.  

```
convert '*.JPG' -resize 800x600 -background black -compose Copy -gravity center -extent 800x600 -quality 92 %03d.jpg 
```

[B]MY CURRENT QUESTION:
[/B]
**I need to get Imagemagick to rename them to their correct number  to maintain order (e.g 012.JPG --> 012.jpg).  Can I do this by using  by using regular expressions?  Any suggestions would be appreciated.**

---

### Post by SeijiSensei on 2014-09-04
I would iterate over the images using a script with a for loop:

```

#!/bin/bash
for IMAGE in *.JPG
do
    # create a lower-cased file name
    NAME=$(echo $IMAGE | tr [A-Z] [a-z])
    # do conversion and store in $NAME
    convert $IMAGE -resize 800x600 -background black -compose Copy -gravity center -extent 800x600 -quality 92 $NAME
done

```

Since not all the images are to be converted, I'm assuming you placed the ones to be transformed into a separate directory.

---

### Post by FakeOutdoorsman on 2014-09-04
Copy the images to a new directory and use mogrify instead of convert. mogrify will overwrite the input while convert makes a new file.

---

### Post by SeijiSensei on 2014-09-05
> **FakeOutdoorsman said:**
> Copy the images to a new directory and use mogrify instead of convert. mogrify will overwrite the input while convert makes a new file.

Mogrify won't make the file names lower-case though.

---

