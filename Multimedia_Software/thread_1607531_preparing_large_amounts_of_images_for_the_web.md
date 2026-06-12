---
title: "preparing large amounts of images for the web"
date: 2010-10-27
forum: Multimedia Software
---

### Post by bobdobbs on 2010-10-27
Hi all.

I've been using GIMP's 'save for the web' tool to reduce the file sizes of images.

I now have a directory with about 50 images. I'd like to avoid processing them all by hand.

I have a (very) basic knowledge of programming, and I'm comfortable with the commandline. I don't mind doing some homework on how to use new tools.

All I'm really concerned with here is reducing the file sizes of the images I have.

What possible pathways are there for me to prepare large amounts of images for the web?

Thanks.

---

### Post by Enigmapond on 2010-10-27
If you have FFmpeg installed, there is a very simple terminal command to resample the images. For example if I had a folder of .jpgs and wanted them all half the size, (not aspects but just kb's)...open the folder in the terminal and type:

```
ffmpeg -resample -50 *.jpg
```The variables here are the (-50) and the extension as you may have gif's or png's...

hope this helps.

Cheers!

---

### Post by SeijiSensei on 2010-10-29
I prefer [ImageMagick]("http://www.imagemagick.org/script/index.php") for graphics processing.  The range of available [options]("http://www.imagemagick.org/script/convert.php") is incredible.  ImageMagick is available from the Ubuntu repositories.

Suppose your files are stored in /home/bob/webimages.  Let's make a new directory /home/bob/webimages/small and put the rescaled images there:

```

cd /home/bob/webimages
mkdir small
for f in *.jpg
do convert $f -resize 50% small/$f
done

```

This script reads all the *.jpg files in the webimages directory and places half-sized copies in the webimages/small directory.  (Remember that Unix is case-sensitive, so if the files are called *.JPG, you need to change the entry in the "for" line above.)

ImageMagick is blazingly fast; for fifty images, the whole task should only take a minute or so.

---

### Post by FakeOutdoorsman on 2010-10-29
> **Enigmapond said:**
> If you have FFmpeg installed, there is a very simple terminal command to resample the images. For example if I had a folder of .jpgs and wanted them all half the size, (not aspects but just kb's)...open the folder in the terminal and type:

```
ffmpeg -resample -50 *.jpg
```The variables here are the (-50) and the extension as you may have gif's or png's...

hope this helps.

Cheers!

I think you mean *convert* instead of *ffmpeg*. These options are not valid for FFmepg and it also does not use *****.

---

### Post by Enigmapond on 2010-10-31
> **FakeOutdoorsman said:**
> I think you mean *convert* instead of *ffmpeg*. These options are not valid for FFmepg and it also does not use *****.

I'm sorry...that was my error...mogrify which is part of imagemagick...not ffmpeg.

```
mogrify -resample -50 *.jpg
```

> **SeijiSensei said:**
> I prefer [ImageMagick]("http://www.imagemagick.org/script/index.php") for graphics processing.  The range of available [options]("http://www.imagemagick.org/script/convert.php") is incredible.  ImageMagick is available from the Ubuntu repositories.

Suppose your files are stored in /home/bob/webimages.  Let's make a new  directory /home/bob/webimages/small and put the rescaled images there:

```

cd /home/bob/webimages
mkdir small
for f in *.jpg
do convert $f -resize 50% small/$f
done

```This script reads all the *.jpg files in the webimages directory  and places half-sized copies in the webimages/small directory.   (Remember that Unix is case-sensitive, so if the files are called *.JPG,  you need to change the entry in the "for" line above.)

ImageMagick is blazingly fast; for fifty images, the whole task should only take a minute or so.

I think he wants to change that file size and not the dimensions...so instead of -resize he would need to use -resample...at least that was my understanding of the OP...:)

---

