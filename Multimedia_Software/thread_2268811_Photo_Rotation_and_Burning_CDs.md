---
title: "Photo Rotation and Burning CDs"
date: 2015-03-11
forum: Multimedia Software
---

### Post by jnquick on 2015-03-11
I am relatively new to Ubuntu, 14.04. All the photos I have taken with a Canon Elph are properly oriented with Image Viewer and Shotwell which I used for cropping and minor editing. Apparently this is an automatic feature built into Ubuntu and it is nice. Buttttt, I need to burn a CD to 'play' at a party and those images that were taken rotated, are not oriented correctly. I have well over 250 photos and approxiamtely half need to be rotated when they are burned. 

Any and all suggesstions are appreciated. Thanks in advance.

---

### Post by sudodus on 2015-03-11
There are two ways to do it:

1 - change the rotation data in the pictures (good method for the future)

2 - use a picture viewer at the party, which will orient the pictures correctly (easy if available)

---

### Post by jnquick on 2015-03-12
In my searches, I found that the metadata stored with each photo regarding orientation is EXIF. Two programs to strip tht data, ImageMagick and EXIF tool were mentioned. Anyone have any experience with those?

All the image vieweers I used: gimp, gthumb, shotwell and image Viewer reorient the photos so I don't know which ones to rotate. The cd will be palyed as a slide show on a windows machine, It will not reorient the images.

---

### Post by sudodus on 2015-03-12
I made a script that uses ***jhead*** (lossless) or ***imagemagick convert*** (lossy). You can use it, but you may need to adapt it to your camera's resolution.

```

#!/bin/bash

if [ "$1" == "" ]
then
 echo "Usage: $0 <jpeg-file> [lossy]"
 echo "Auto-rotate *lossless* with jhead,"
 echo "or optionally, if bad image dimensions,"
 echo "auto-orient *lossy* with convert"
 exit
fi
typeset name=$(echo "$1"|sed "s/\..*//")
if [ "$1" == "$name".jpg ] || [ "$1" == "$name".JPG ]
then
 echo hej>/dev/null
else
 echo "Bad! $1 not a jpeg-file"
 exit
fi

typeset dimkonica=2112x2816
typeset dimcanon=3264x2448

typeset dim=$(identify -ping "$1"|sed -e s/.*JPEG\ // -e s/\ .*//)
typeset gw0=$(echo "$dim"|sed s/x.*//)
typeset gw1=$((gw0/16*16))
typeset gh0=$(echo "$dim"|sed s/.*x//)
typeset gh1=$((gh0/16*16))

if [ "$dim" == "$dimkonica" ] || [ "$dim" == "$dimcanon" ]
then
  echo "jhead: Original dimension for jhead: $1: $dim"
  jhead -autorot "$1"
else
 if [ "$gw0" == "$gw1" ] && [ "$gh0" == "$gh1" ]
 then
  echo "jhead: Good dimension for jhead: $1: $gw0"x"$gh0"
  jhead -autorot "$1"
 else
  if [ "$2" == "lossy" ]
  then
   echo "convert: Bad dimension for jhead: $1: $dim"
   while [ "$ans" != "yes" ] && [ "$ans" != "n" ] && [ "$ans" != "no" ]
   do
    echo -n "make a lossy rotation the image? (yes/no) "
    read ans
    if [ "$ans" == "yes" ]
    then
     echo Converted: original saved, rotated copy named "$name"_r.jpg
     convert -auto-orient "$1" "$name"_r.jpg
    fi
   done
  else
   echo "Bad dimension for jhead: $1: $dim"
  fi
 fi
fi

```

It will not work for all cameras. In such cases you might need to rotate the pictures manually, for example with ***gimp*** or ***imagemagick convert***.

---

### Post by SeijiSensei on 2015-03-12
If sudodus's script doesn't work for you, I posted one earlier that might help: [http://ubuntuforums.org/showthread.php?t=1951949](http://ubuntuforums.org/showthread.php?t=1951949)

```

#!/bin/sh

mkdir -p new

for f in *.JPG
do
   # extract the size of the image
   SIZE=$(identify $f | awk '{print $3}')

   case $SIZE in 
     
       480x640|1200x1600|1920x2560)
           # portrait --do nothing
           cp $f new
           ;;

       *)
           # landscape -- rotate file
           convert -rotate 90 $f new/$f   
   
   esac

done

exit 0

```

It creates a subdirectory "new" under the directory where the images are stored and puts the processed items there.  You'll need to install Imagemagick first which provides the "identify" and "convert" commands.

---

### Post by jnquick on 2015-03-13
Thanks for the 'scripts'. As I said I am early on the learning curve, so this will be a good experience for me. Batch file processing is not something I have done since DOS. 

I was actually expecting something like the Picture viewer in Windows, but when I opened the folder in W 8.1, it also oreints the photos the way that they are taken and so I had the same problem there. When I went back to W 7, I could see the photos the way they were saved rather than the way the camera was oriented. I haven't checked the Windows board to see what their solution is for W 8.1. The Windows Live Photo Viewer did work, however.

I suspect that people aren't burning as many photo cds and are mostly just showing them on a tablet or computer where the machine does the orientation automatically.In the instant photo kiosks, you probably can rotate them, or just turn the photo after it was printed. If this was a common problem for people, the software to burn CDs would also be able to make the proper orientation.

Personally, I prefer to have a degree of control and like to check the orientation of each photo individually. I would most like to turn off Image Viewer's automatic orientation of the photos. I will try the above scripts and if they in fact accomplish that, then my routine will be to batch process the entire folder that I download and then just look at the images stripped of the EXIF.

---

### Post by sudodus on 2015-03-13
You can also bring a USB pendrive with Ubuntu (operating system) plus the pictures and a program, that you know works. But then you must check that the particular computer you will use can boot from Ubuntu, or simply bring your own computer (laptop or netbook) and connect to the projector or external screen.

---

