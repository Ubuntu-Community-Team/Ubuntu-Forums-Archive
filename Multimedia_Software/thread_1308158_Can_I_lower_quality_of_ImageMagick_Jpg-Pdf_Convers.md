---
title: "Can I lower quality of ImageMagick Jpg-Pdf Conversion?"
date: 2009-10-31
forum: Multimedia Software
---

### Post by rob86 on 2009-10-31
I asked this question on IM forums, but haven't had a reply (yet) so I thought I'd ask here. I'm trying to convert multiple jpg files into one pdf. For one or two jpg, it works excellent and hardly takes any time at all, less than a min. When I do 10, my swap memory is all used up and it takes a long time and my mouse and kbd are unresponsive (even with niceness at 19).  I have over 100 jpg to convert, each about 1.5mb in size. I have no idea how long that would take even running over night. I know I.M. says something like "our goal was never speed", but it seems like such an excessive amount of time, I don't have the newest computer around but on Windows I could do this same thing and it worked in 10 min or less. 

I don't need these to be converted with such high quality, I just want the black and white text readable, and I was thinking if I could lower the quality, would it speed up the conversion? I don't know.

I was just using the basic convert *.jpg output.pdf  and/or convert *.jpg -adjoin output.pdf -- not sure if they produce the same result or not, I've never finished a conversion with more than a few images.

I LOVE the ease of use ImageMagick offers, but I wish it could do this conversion faster...

---

### Post by kaibob on 2009-10-31
Creating a PDF document from multiple JPEG images can take some time. I've found the best option is to create a copy of the JPEG files in a temporary directory and to reduce their resolution first. Then use Imagemagick, and things are much quicker. 

To batch convert the JPEG files to a lower resolution, the Nautilus image converter--which is in the repo's--is a good tool. 

[http://www.bitron.ch/software/nautilus-image-converter.php](http://www.bitron.ch/software/nautilus-image-converter.php)

I was curious and just ran a test with twenty 2.8-MB JPG files. It took less than a minute to resize the photos to 640x480 with Nautilus Image Converter. Converting them to a PDF with Imagemagick also took less than a minute. This is on a 6-year-old computer.

As an aside, there is a bug in convert which can give a segmentation fault when converting a number of JPEG files to one PDF file. The following appears to avoid this:

```
convert *.JPG -compress Zip output.pdf
```

---

### Post by rob86 on 2009-10-31
Thanks for the reply kaibob. I bet Nautilus converter works good, but I'm looking for a command line way to do it all.

I managed to resize and lower the quality (of temporary copies - 10 files!) with this command.

mogrify -resize 50% -quality 25 

This overwrites the originals, but I wasn't sure how to process multiple jpgs and produce multiple output files. There's probably a way, but ImageMagick has a lot of options to read through. 25 quality seems like a low number, but it appeared to be more than adequate for reading text.

The result was files that had a significant drop in file size (about 50-100k compared to ~1000kb (I guess I exaggerated a bit when I said 1.5mb).

I then ran convert *.jpg output.pdf and the conversion seemed to be very fast, maybe a minute or less. So the jpg to pdf conversion was definitely faster with lower resolution images.

I thought maybe I could combine this command into...

convert -quality 25 -resize 50% *.jpg -adjoin output.pdf

This command worked, but it seemed to take a bit  longer than doing the resize and convert2pdf seperately, though it only took a couple minutes. I haven't experimented much to really compare. I'm only assuming the quality and resize options took affect before somewhere in there. 

I haven't experienced the seg fault yet,  but thanks for letting me know about it.

---

### Post by kaibob on 2009-11-01
I'm glad you got things working. With Imagemagick, it's often best to experiment and see what works. 

You raised the issue of resizing images without overwriting the originals. This can be done as in the following command line. The converted images have the names newfile001.jpg, newfile002.jpg, and so on. 

```
convert '*.JPG' -resize 640x480 newfile%03d.jpg
```

Or, if you want to retain the original file name and prepend new, you could use the following:

```
for file in *.JPG ; do convert "$file" -resize 640x480  "new-${file}" ; done
```

I only began receiving the segmentation fault error after upgrading to Karmic, so I assume this has something to do with a new version of Imagemagick. I hope they fix this soon, as the zip compression results in huge file sizes.

---

### Post by lipinski on 2010-03-22
> **kaibob said:**
> 

As an aside, there is a bug in convert which can give a segmentation fault when converting a number of JPEG files to one PDF file. The following appears to avoid this:

```
convert *.JPG -compress Zip output.pdf
```

kaibob - Thanks for this..  I ran into this and could not get around the segfault.  All googling around pointed to upgrading imagmagick, but I was on the latest "ubuntu" version per synaptic.

---

### Post by kaibob on 2010-03-23
> **lipinski said:**
> kaibob - Thanks for this..  I ran into this and could not get around the segfault.  All googling around pointed to upgrading imagmagick, but I was on the latest "ubuntu" version per synaptic.

I just tried the command line with the zip compression option, and it worked fine, although the size of the output file was too large to be useful (140 MB output PDF file with 30 MB of source JPG files). 

I then tried the following command line--which previously had seg faulted--and it also worked fine. Also, the output file size was quite reasonable (11 MB output PDF file with the same 30 MB of source JPG files).

```
convert *.JPG -compress JPEG output.pdf
```

If the above doesn't work, I suggest you try graphicsmagick, which is a small install that's in the repo's. I've switched to it for most of the stuff I do and have found it to be much more reliable with quality output and good file sizes (7 MB with the same source files). The command line with graphicsmagick is:

```
gm convert *.JPG -compress JPEG output.pdf
```

For more information on graphicsmagick:

[http://www.graphicsmagick.org/](http://www.graphicsmagick.org/)

BTW, I'm running jaunty, which may have a version of imagemagick without some bug.

---

