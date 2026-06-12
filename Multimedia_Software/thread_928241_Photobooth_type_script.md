---
title: "Photobooth type script?"
date: 2008-09-23
forum: Multimedia Software
---

### Post by jsully1 on 2008-09-23
I'm wondering if there is a script or plugin that can take 4 or 5 source images and turn them into a photobooth style picture.  I've used metapixel before, so I may be able to use that to tile the images vertically, but then I'd still need something to make them black and white. 

Any ideas?

---

### Post by MsTBWx2c on 2008-09-23
**[[color=red]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=red]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[size=3][color=red]Make money online,now![/color][/size]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by jsully1 on 2008-09-24
Imagemagick turned out to be just what I needed!  Here's my script:

```

#!/bin/bash

SOURCE=/media/pictures
WORKING=/home/user/Pictures
DEST=/home/user/Pictures/slideshow
RESOLUTION="864x574!"

cd $DEST
passnumber=`ls -t *.JPG | head -1 | cut -f1 -d. | sed s/photo//`
echo "First photo is $passnumber"

while true

passnumber=`expr $passnumber + 1`
echo "Pass number $passnumber"

do
	pictures=`ls $SOURCE/*.JPG | shuf | tail -4`
	echo "working set of pictures: $pictures"
	finalpic="photo${passnumber}.JPG"
	echo $sourcefilename
	echo "Resulting picture will be $finalpic"
	/usr/bin/convert -resize $RESOLUTION $pictures $WORKING/resized.JPG
	/usr/bin/convert $WORKING/resized* -append $DEST/$finalpic
	#Uncomment to convert images to gray
	#/usr/bin/convert -colorspace Gray $DEST/$finalpic $DEST/$finalpic
	echo "Picture processing complete.  Next picture will be generated in 30 seconds"
	sleep 30
done

```

This takes four random images out of the source directory and then turns them into this:
[img]http://mr2.phpwerx.net/Photos/Sully/Voxel/Matt/Photobooth/800x600/photo10.JPG[/img]

I also put together this script for showing them:
```

#!/bin/bash

SOURCE=/home/matt/Pictures/slideshow

while true
do
	pictures=`ls $SOURCE/*.JPG`
        /usr/bin/qiv -F $pictures -f -m -i -s -l -r --slide --delay 10 & VIEWERPID1="$!"
	sleep 10
	kill $VIEWERPID2
        sleep 5m
        pictures=`ls $SOURCE/*.JPG`
        /usr/bin/qiv -F $pictures -f -m -i -s -r --slide --delay 10 & VIEWERPID2="$!"
	sleep 10
        kill $VIEWERPID1
	sleep 5m
done
```
This utilizes [QIV](http://www.klografx.net/qiv/).  I spawned a second instance before killing the first to guarantee that there's always an image showing.

---

