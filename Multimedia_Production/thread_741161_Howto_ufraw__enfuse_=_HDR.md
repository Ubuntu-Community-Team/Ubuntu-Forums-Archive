---
title: "Howto: ufraw | enfuse = HDR"
date: 2008-03-31
forum: Multimedia Production
---

### Post by sillyxone on 2008-03-31
**Intro**
A brief introduction to High Dynamic Range (HDR) imaging in case you haven't heard of it. A JPEG file can only store 256 levels (8 bits) of brightness. Thus, in scenes with high contrast, the highlights and/or shadows are clipped off. People usually cope with this by bracketing: taking photos of the same scene at different exposures, then combine them together using software to create composite HDR photos. However, bracketing is difficult when the scene changes in between frames. Besides, my Nikon D40 doesn't have AEB.

An alternative is the RAW file. A RAW file stores brightness as 12 bits values (4096 levels). When the camera creates the JPEG file, it has to select a small window of brightness levels within that 4096 levels to export (down convert from 12 to 8 bits). If you look at a RAW file, you can get from -3EV to 3EV of what a JPEG of the same scene sees. So, basically, this is somewhat bracketing. For more information on RAW, look here:
[http://www.luminous-landscape.com/tutorials/understanding-series/u-raw-files.shtml]("http://www.luminous-landscape.com/tutorials/understanding-series/u-raw-files.shtml")

There are commercial software such as Photomatix that can combine multiple-exposures photos into an HDR one. However, we are all about software freedom, so here are Ufraw (or Rawstudio) and Enfuse. Enfuse is a new addition to the Enblend package in panorama tools. For more information on Enfuse:
[http://wiki.panotools.org/Enfuse](http://wiki.panotools.org/Enfuse)

**Install**
To get Ufraw, you can use the version in Synaptic or the latest deb package:
[http://www.getdeb.net/app.php?name=UFRaw](http://www.getdeb.net/app.php?name=UFRaw)

Enfuse is part of the latest Enblend package and is not in the Repo yet, so follow the instruction here to compile it:
[http://wiki.panotools.org/Hugin_Compiling_Ubuntu#Building_Enblend](http://wiki.panotools.org/Hugin_Compiling_Ubuntu#Building_Enblend)

**Usage**
I tested Ufraw and Enfuse by exporting 7 images with different exposures from a single RAW file using Ufraw: -3, -2, -1, 0, 1, 2, 3EV. Then just like this article ([http://www.linux.com/feature/127062](http://www.linux.com/feature/127062)), I fed those 7 images into Enfuse. The result is that both shadows and highlights that normally clipped out of a JPEG file is included, just like other HDR photos without going through tone mappping.

Also, a little shell script to automate the process is handy too. The scripts take 3 parameters (only the first one is required):

- first param (required): filename of the RAW file (tested with NEF and CR2, Ufraw can handle most RAW formats)
- second param (optional): the lower limit of exposures, default to -3
- third param (optional): upper limit of exposures, default to 3
EDITED:  fourth, fifth .. ninth param are passed directly to Enfuse for more tweaking. I usually pass --WContrast --wSaturation --wSigma --wExposure to Enfuse.

for example:

```
enfuse_raw.sh DSC_1001.NEF 
```
or
```
enfuse_raw.sh DSC_1001.NEF -1 2
```

It will generate up to 7 photos at different exposures (-3. -2, -1, 0, 1, 2, 3) depending on the range you entered. The temporary TIFF files are not removed so that it doesn't have to regenerate again in case you want to experiment with different ranges. 

Of the two attached sample photos, one is JPEG straight from the camera, one is the result of ufraw | enfuse from -3 to 3. Notice that it's a high contrast scene, so the sky is washed out and shadow is too dark, but the RAW file can see them all and enfuse blends them together beautifully.

UPDATED: here is a follow up: [Using Enfuse, Ufraw and Hugin to create (pseudo) HDR Panorama]("http://ubuntuforums.org/showthread.php?t=745894")

Here is the little script (enfuse_raw.sh). I'm not experienced with shell scripting so there is lots of repetition in it.

```

#!/bin/bash

if [ ! "$1" ]
then
	echo "Please specify filename."
	exit 1
fi

if [ ! -f "$1" ]
then
	echo "Error: file does not exist"
	exit 1
fi


# extract the filename without extension
filename=`basename "$1" | sed 's/\.\([^\/\.]*$\)//'`


# check lower limit param
if [ $2 ]
then
	lower_limit="$2"
else
	lower_limit=-3
fi

# check upper limit param
if [ $3 ]
then
	upper_limit="$3"
else
	upper_limit=3
fi

# make sure lower limit < upper limit
if [ $upper_limit -le $lower_limit ]
then
	echo "Error: upper limit is smaller than lower limit."
	exit 1
fi


echo "Processing from $lower_limit to $upper_limit."


file_list=""

# should we use -3 exposure from RAW
if [ $lower_limit -lt -2 ]
then
	if [ ! -f "${filename}_N3.tiff" ]
	then
		ufraw-batch  --wb=camera --exposure=-3 --out-type=tiff8  --output=${filename}_N3.tiff "$1"
	fi
	file_list="${filename}_N3.tiff"
fi

# should we use -2 exposure from RAW
if [ $lower_limit -le -2 -a $upper_limit -ge -2 ]
then
	if [ ! -f ${filename}_N2.tiff ]
	then
		ufraw-batch  --wb=camera --exposure=-2 --out-type=tiff8  --output=${filename}_N2.tiff "$1"
	fi
	file_list="${file_list} ${filename}_N2.tiff"
fi


# should we use -1 exposure from RAW
if [ $lower_limit -le -1 -a $upper_limit -ge -1 ]
then
	if [ ! -f ${filename}_N1.tiff ]
	then
		ufraw-batch  --wb=camera --exposure=-1 --out-type=tiff8  --output=${filename}_N1.tiff "$1"
	fi
	file_list="${file_list} ${filename}_N1.tiff"
fi

# should we use 0 exposure from RAW
if [ $lower_limit -le 0 -a $upper_limit -ge 0 ]
then
	if [ ! -f ${filename}_0.tiff ]
	then
		ufraw-batch  --wb=camera --exposure=0 --out-type=tiff8  --output=${filename}_0.tiff "$1"
	fi
	file_list="${file_list} ${filename}_0.tiff"
fi

# should we use +1 exposure from RAW
if [ $lower_limit -le 1 -a $upper_limit -ge 1 ]
then
	if [ ! -f ${filename}_P1.tiff ]
	then
		ufraw-batch  --wb=camera --exposure=1 --out-type=tiff8  --output=${filename}_P1.tiff "$1"
	fi
	file_list="${file_list} ${filename}_P1.tiff"
fi

# should we use +2 exposure from RAW
if [ $lower_limit -le 2 -a $upper_limit -ge 2 ]
then
	if [ ! -f ${filename}_P2.tiff ]
	then
		ufraw-batch  --wb=camera --exposure=2 --out-type=tiff8  --output=${filename}_P2.tiff "$1"
	fi
	file_list="${file_list} ${filename}_P2.tiff"
fi

# should we use +3 exposure from RAW
if [ $upper_limit -gt 2 ]
then
	if [ ! -f ${filename}_P3.tiff ]
	then
		ufraw-batch  --wb=camera --exposure=3 --out-type=tiff8  --output=${filename}_P3.tiff "$1"
	fi
	file_list="${file_list} ${filename}_P3.tiff"
fi

# run enfuse with default parameter, edit this line for more advance enfuse options
enfuse ${file_list} -o ${filename}_enfused.tiff $4 $5 $6 $7 $8 $9

# uncomment the next line to auto clean up, else just leave the temp files to experiment more
#rm ${file_list}

echo "Done: final output file is ${filename}_enfused.tiff"
exit 0

```

---

