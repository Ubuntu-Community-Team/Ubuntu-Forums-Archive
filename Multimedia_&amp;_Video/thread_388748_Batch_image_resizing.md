---
title: "Batch image resizing?"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by xSauronx on 2007-03-19
Is there a package available that can down-convert my camera images easily? Im using Xubuntu 6.10 and havent found anything yet. Gthumb converts between formats, but i want to downsize a number of images easily to save a little space for when I upload them to a website. 

I have 600 meg to use, and nowhere near so many pictures, but, am thinking of the future as i want to have *alot* of galleries up at once :)

thanks

---

### Post by jabeez on 2007-03-19
I use digikam and know there are many batch processes, image sizing among them, although I've never used any besides rename.

---

### Post by xSauronx on 2007-03-19
i dont have teh kde stuff installed, and would rather not install all thats necessary to use digikam :/

thanks for the idea though, ill keep it in mind if i switch desktops

---

### Post by pteglia on 2007-04-30
You could use the ImageMagic function:

```
mogrify -resize 450x338 *.jpg
```

for example, with 450x338 being the resulting image size you want (change to your preference, it will resize up to the largest diameter without distorting) and the *.jpg being all the current files in a directory.

Be sure to have a copy of the directory that you are doing this too as it will alter the files that are there, it will not copy them to another directory (although putting something like > ~/newimagesdirectory/ might do it, don't know never tried that, I always just make a copy of the directory then run the line above)

Hope that helps,

Pat

---

### Post by bashologist on 2007-04-30
Maybe someone will find this useful:
```
#!/bin/bash
imgdir="/path/to/images/"
dimensions="600x600"
tmpd="$(mktemp -dt)"; count=1

if ! which mogrify > /dev/null; then
	echo "$0: install imagemagick first"
	exit 1
fi

if [ -n "$2" ]; then
	dimensions="$2"
fi

if [ -d "$1" ]; then
	imgdir="$1"
fi

if [ ! -d "$imgdir" ]; then
	echo "$0: please specify a directory"
	echo "$0: usage: $0 /path/to/images 400x400"
	exit 1
fi

find "$imgdir" -type f -iname '*.jpg' -print | while read line; do
	cp --parents "$line" "$tmpd"
	printf "\r$0: resizing image #$count ..."
	mogrify -resize "$dimensions" "$tmpd$line"
	((count++))
done

printf "\n$0: your resized images are in $tmpd\n"
```This script comes with no warranty. If it destroys thousands of files don't blame me! It looks safe in my opinion tho.

---

### Post by pteglia on 2007-04-30
Lol, a simple one-liner wasn't good enough for ya?  Hehehehehe, nice script, looks like it covers all of the bases.

Pat

---

### Post by TomFumb on 2007-05-07
any idea where I can get mogrify? it doesn't appear to be in my repos (with everything enabled)

thanks

---

### Post by pteglia on 2007-05-07
Yep, it is part of the ImageMagick package.

Probably already installed, by the way.

Pat

---

### Post by michux on 2007-05-11
More such tricks: [Enchanting Pictures with ImageMagick](http://polishlinux.org/apps/graphics/enchanting-pictures-with-imagemagick/)

---

### Post by Merdyn on 2007-05-11
I'm too accustomed to **Irfanview** ([www.irfanview.com](www.irfanview.com) - free for non-commercial use), so I have installed wine and still use it.

---

