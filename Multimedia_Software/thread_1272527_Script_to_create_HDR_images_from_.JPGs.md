---
title: "Script to create HDR images from .JPGs"
date: 2009-09-22
forum: Multimedia Software
---

### Post by mmcmonster on 2009-09-22
This script is to create High Dynamic Range (HDR) images on the cheap.  It is a slight modification of [the excellent script]("http://photoblog.edu-perez.com/2009/04/script-hdr-with-linux.html") I found on a blog about Linux and HDR imaging.  It's been modified to take .JPG images as input, for those of us that cannot afford a camera which gives us good quality RAW files.

Prerequisites:
  You will have to install pfstools (apt-get install pfstools libpfs-dev).  You will also have to compile [pfscalibration]("http://pfstools.sourceforge.net/pfscalibration.html") (as it is not included in Ubuntu repositories).  pfscalibration is required to create the dcraw2hdrgen binary used in the script.   The libpfs-dev package is installed so that pfscalibration can be compiled with minimal hassel.  

To use:
Run the script in a directory with a bunch of JPG images (at least three, to get reasonable results).  The images should be of exactly the same scene, with different camera exposures.  (Setting exposure to -2EV, 0EV, +2EV, or other ways to adjust lighting of the image.)

Once the script runs, it will create an enfuse.tif file and two .jpg files (pfstmo_mantiuk06.jpg and pfstmo_fattal02.jpg) in a HDR subdirectory.

Open up Gimp, and then "File->Open As Layers", to open up the three files as separate layers of a single image.  Then, in the Layers tab, move the enfuse.tif layer (the one that looks most like a normal image) to the bottom, making it the background layer (though it won't change the name to background).  Change the mode of the other two layers from normal to overlay.

Other effects can be produced by using the original .jpg with a "normal" exposure (0EV) instead of the generated enfuse.tif file as the background layer, or changing transparencies or modes of the other layers.  Also, the generated pfs.hdr file can be run through the tonemapping option in [qtpfsgui]("http://qtpfsgui.sourceforge.net/") to create other images that can be added as layers.

QED.
```

#! /bin/bash

set -e

SELF=`basename $0`

DIR=.
ALIGN=Y
ENFUSE=Y
TONEMAP=Y

echo "$SELF: `date`"

while [ "$1" != "" ]; do
 case "$1" in
  "-a")
   ALIGN=Y
   ;;
  "-e")
   ENFUSE=Y
   ;;
  "-t")
   TONEMAP=Y
   ;;
  "-d")
   DIR="$2"
   shift
   ;;
  *)
   echo "$SELF: Parameters"
   echo "$SELF:  -d      -> Directory"
   echo "$SELF:  -a      -> Align images"
   echo "$SELF:  -e      -> Create enfuse"
   echo "$SELF:  -t      -> Create and tonemap HDR"
   exit
   ;;
 esac

 shift
done

HDR="$DIR"/HDR
FILES=("$DIR"/*.[Jj][Pp][Gg])
COUNT=${#FILES[@]}

echo "$SELF: Options:"
echo "$SELF:  Directory  = $DIR"
echo "$SELF:  Output     = $HDR"
echo "$SELF:  Align      = $ALIGN"
echo "$SELF:  Enfuse     = $ENFUSE"
echo "$SELF:  Tonemap    = $TONEMAP"
echo "$SELF:  Files      = ${FILES
[*]}"

if [ $COUNT -eq 0 ]; then
 echo "$SELF: No files found!!!"
 exit 1
fi

echo "$SELF: Creating output directory:"
mkdir "$HDR"

echo "$SELF: Parsing EXIF information:"
dcraw2hdrgen ${FILES
[*]} > "$HDR"/pfs_raw.hdrgen

echo "$SELF: Generating TIFFs"
mogrify -path "$HDR" -format tif ${FILES
[*]}

FILES=("$HDR"/*.tif)

if [ "$ALIGN" = "Y" -a $COUNT -gt 1 ]; then
 echo "$SELF: Aligning images"
 align_image_stack -a "$HDR"/AIS_ ${FILES
[*]} > "$HDR"/align_image_stack.log
 rm -f ${FILES
[*]}
 FILES=("$HDR"/AIS_*.tif)
fi

if [ "$ENFUSE" = "Y" ]; then
 if [ $COUNT -gt 1 ]; then
  echo "$SELF: Generating enfuse:"
  enfuse -o "$HDR"/enfuse.tif ${FILES
[*]} > "$HDR"/enfuse.log
 else
  echo "$SELF: By-passing enfuse:"
  ln ${FILES
[*]} "$HDR"/enfuse.tif
 fi
fi

if [ "$TONEMAP" = "Y" ]; then
 echo "$SELF: Parsing hdrgen"
 i=0
 > "$HDR"/pfs_tif.hdrgen
 cat "$HDR"/pfs_raw.hdrgen | while read LINE; do
  echo "${FILES[$i]} $LINE" | cut -d' ' -f1,3- >> "$HDR"/pfs_tif.hdrgen
  i=`expr $i + 1`
 done

 echo "$SELF: Generating HDR:"
 pfsinhdrgen "$HDR"/pfs_tif.hdrgen | pfsout "$HDR"/pfs.hdr

 echo "$SELF: Tone-mapping HDR:"

 echo "$SELF:  Operator = mantiuk06"
 pfsin "$HDR"/pfs.hdr | pfstmo_mantiuk06 -e 1 -s 1 | pfsgamma -g 2.2 | pfsout "$HDR"/pfstmo_mantiuk06.jpg

 echo "$SELF:  Operator = fattal02"
 pfsin "$HDR"/pfs.hdr | pfstmo_fattal02 -s 1 | pfsout "$HDR"/pfstmo_fattal02.jpg
fi

echo "$SELF: Cleanning:"
rm -f ${FILES
[*]}

```

---

### Post by Rodney9 on 2009-11-03
Qtpfsgui does High Dynamic Range (HDR) images

Tips and instructions on how to it use here - [http://garmahis.com/tutorials/hdr-tutorial-free-software/](http://garmahis.com/tutorials/hdr-tutorial-free-software/)

Rodney

PS: Also found this terrific tutorial - [http://shootingubuntu.blog.com/2009/09/01/single-hdr-image-creation-in-ubuntu/](http://shootingubuntu.blog.com/2009/09/01/single-hdr-image-creation-in-ubuntu/)

---

