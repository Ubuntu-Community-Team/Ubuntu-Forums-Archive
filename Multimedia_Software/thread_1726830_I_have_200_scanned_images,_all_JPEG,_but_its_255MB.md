---
title: "I have 200 scanned images, all JPEG, but its 255MB......"
date: 2011-04-11
forum: Multimedia Software
---

### Post by sleeper414 on 2011-04-11
I would like them to be compressed to smaller sizes for web upload.
is there a simple program that will compress all the photos at once?:confused:
like soundconverter for audio, but for pictures?:)

any help of any kind is appreciated.

---

### Post by 741Baus on 2011-04-11
Hi sleeper414 , nautilus has an image resizer add-on that will resize your images to what you want open up a terminal ,
```
sudo apt-get install nautilus-image-converter
```
After installing right click on the image to be resized and go to resize image -ok . The only problem is that images will be resized in the original folder along side your original images.

---

### Post by rosencrantz on 2011-04-11
Do you have ImageMagick?
Large batch conversions work best from the command line:
e.g. (warning! this replaces the original pictures)
for file in *.jpg; do convert $file -quality 80 -resize 50% $file; echo $file; done
here's some of ImageMagick's documentation for more options:
[http://www.imagemagick.org/script/command-line-options.php](http://www.imagemagick.org/script/command-line-options.php)

---

### Post by sleeper414 on 2011-04-11
i got a recommendation for phatch. gonna try that. thanks everyone!

---

### Post by ufugu on 2011-04-11
I was going to suggest Phatch.  It's awesome.  Hope it does the trick for you.

---

