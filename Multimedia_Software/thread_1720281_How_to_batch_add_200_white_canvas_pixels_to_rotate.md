---
title: "How to batch add 200 white canvas pixels to rotated JPEG bottom edge"
date: 2011-04-03
forum: Multimedia Software
---

### Post by rocksockdoc on 2011-04-03
In the Windows side, with Irfanview freeware, I would open a directory of, say, 500 JPG digital photos, and simply click the buttons to add, say, 200 white pixels to the 'bottom' edge of the (properly rotated) JPEG files. That would kick off a batch job which does the task.

On Ubuntu 10.04 lucid, I can auto-rotate these pictures running "exiftran -ai *.jpg" in the terminal window (which rotates based on EXIF orientation information) - but how do I add 200 white pixels to the bottom of each photo in Ubuntu?

I can easily "resize" the photos but what I want to do is ADD a white canvas (for later manual text caption editing with KolourPaint) to the bottom of each photo.

Gimp can add that canvas manually:

[LIST]
[*]Open the photo in GIMP 2.6 on Ubuntu 10.04 lucid
[*]Image -> Canvas size -> break the chain
[*]Add 200 pixels the the height figure & press "Resize"
[*]Colorize to white (from the checkered layer)
[*]Save the results
[/LIST]
Then KolourPaint will easily annotate the canvas with text & arrows as needed:

[LIST]
[*]Open the photo in KolourPaint 4.4.5 on Ubuntu 10.04 lucid
[*]Add text as desired
[*]Manually draw arrows and circles as desired
[*]Save the results
[/LIST]
But is there a batch program which can simply append 200 white pixels to the canvas on the bottom of each photo in a directory of, say, 500 JPEG photos?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=187938&stc=1&d=1301818104[/IMG]

---

### Post by SeijiSensei on 2011-04-03
I suggest you look into [ImageMagick]("http://www.imagemagick.org/") and, in particular, its immensely powerful [convert]("http://www.imagemagick.org/script/convert.php") program.  It might take you a bit of time to find the right set of options to do what you want, but, being a command-line program, once you figure it out for one image, you can write a bash script to apply the conversion to all the images in a directory.

---

### Post by rocksockdoc on 2011-04-03
> **SeijiSensei said:**
> I suggest you look into [ImageMagick]("http://www.imagemagick.org/") and, in particular, its immensely powerful [convert]("http://www.imagemagick.org/script/convert.php") program. 

I had already looked at ImageMagick (as it's the second program, after The Gimp that anyone would use); but I couldn't find the canvas option that I needed (I was looking at "mongage", for example) to just expand the canvas on a desired edge by, say, 200 pixels of white border. 

The ImageMagick "border" and "bordercolor" options seem to 'surround' the picture with pixels; but what I want is only one edge (so that I can annotate without writing on the picture itself).

I do appreciate the links you posted (very few people take the time to pitch in with that extra effort) - and I remember having been there in my searches to both of them ... and I haven't 'yet' found out how, with Imagemagick, to resize just the canvas with a white color.

If I knew what caption string I'd use, ahead of time, I guess the "caption string" option would work; but I don't know for every picture what the caption will be until I open the picture and think about it a bit (so I just want to be 'caption ready' by adding a border on one side only).

I agree though, since ImageMagick does everything most people need, and since this would be a very common need, I'll have to dig deeper into the 'montage' options to see why I'm missing it in the first pass.

---

### Post by FakeOutdoorsman on 2011-04-03
Perhaps this will work for you:
```
convert input -bordercolor white -gravity south -splice 0x200 output
```

---

### Post by rocksockdoc on 2011-05-06
> **FakeOutdoorsman said:**
> 
```
convert input -bordercolor white -gravity south -splice 0x200 output
```

Sorry I hadn't responded sooner; I only just now saw this Imagemagick answer. Thanks. Your example worked fine, and gave me additional search clues.

```

$ /usr/bin/convert source.jpg -bordercolor white -gravity south -splice 0x100 destination.jpg

```I actually want the source to 'become' the destination ... so I'll have to add a move - and I will be doing this for an entire directory - so I guess I need a 'foreach' script.
```

$ foreach picture *.jpg, convert *.jpg -bordercolor white -gravity south -splice 0x100 *.jpg

```Interestingly, the "convert --help" page isn't as much help as your example was so I can't imagine someone just coming up with this from just the man pages.

[LIST]
[*] -bordercolor color = border color
[*] -gravity type = horizontal and vertical text placement
[*] -splice geometry = splice the background color into the image
[/LIST]
  For example, in the help, there is no mention of what colors are acceptable (although I'm OK with 'white'); and no list for the fields for the "type" for gravity, e.g., ",north,south,east, or west" are nowhere in the help result; and no mention of the syntax for the splice "geometry".

Looking at this [ImageMagick convert help page]("http://www.imagemagick.org/script/convert.php") gives the same results; however [these Imagemagick example pages]("http://www.imagemagick.org/Usage/") are vastly more extensive and show a previously unlisted 'canvas' option - but of course, the canvas option doesn't actually exist even though they document its use:
> convert -size 100x100 canvas:khaki  canvas_khaki.gifDigging more, I find there is a border command:

[LIST]
[*] [Add border to top of image using imagemagick]("http://stackoverflow.com/questions/2313206/add-border-to-top-of-image-using-imagemagick")
[*] See also [Cutting and Bordering]("http://www.imagemagick.org/Usage/crop/") for more examples.
[/LIST]
Notable examples ... 

> 
```

$ convert source.jpg -splice 0x100 destination.jpg
  If you want to add the border only *at the bottom*, use -gravity as well: 

$ convert source.jpg -gravity south -splice 0x100 destination.jpg 
  Note that the border will be transparent, unless you use -background, too.

```> ```

$ convert source.jpg -gravity south -extent 100x50 destination.jpg
  -gravity tell it which direction to move the original image.

```

---

### Post by rocksockdoc on 2011-05-06
Now that we've solved the problem for one file, it behooves us to script it for a batch file handling an entire directory of photos as the title implies.

I've never done scripting but here's my first attempt after reading the bash help files:

```

for f in *.jpg; do convert $f -bordercolor white -gravity south -splice 0x100 $f_new; mv $f_new $f; done

```

It's ugly.

There must be some way for convert to make the output file the same as the input file name.

---

