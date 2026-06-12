---
title: "HOWTO: Fix Aspect ratio of Divx,etc for DVD with ffmpeg"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by ish4269 on 2007-09-25
I have created a simple bash script to calculate the aspect ratio when using ffmpeg for DivX->DVD-Video ready mpeg. So when watching the finished DVD on a stand alone DVDplayer, the image should  not be squashed or squeezed.

Burning DVD Videos is described elsewhere.

The script calculates the correct amount of (top and bottom) padding required to maintain the AVi,etc Display Aspect Ratio. I exclusively use PAL so the resulting ratio will be 720X576. For NTSC (not tested) changing the variable dh=480 "should" work.

For details on the how the calculation is made go [here]("http://www.transcoding.org/cgi-bin/transcode?Calculating_Frame_Size_And_Aspect_Ratio")

Copy the script to whatever name your want, chmod u+x script_name, to make it executable 

**First**
Get the Display Aspect Ratio of the AVI,etc video file from the file properties, if for example AVI is 592x320, 
**usage:** script_name 592 320
Some input error checking is included as well.
**OUTPUT will be**
#put the folowing into ffmpeg options assuming its a PAL dvd you want:
-target pal-dvd -s 720x554 -padtop 10 -padbottom 12

copy the above flags to the ffmpeg command line options, I would also use the flag **-aspect 16:9** to be safe.
**e.g.**
ffmpeg -i <input_file.avi> -target pal-dvd -s 720x554 -padtop 10 -padbottom 12 -aspect 16:9 <output.mpg>

```

#!/bin/bash
#
# A script to correct the resolution of an AVI file and
# make a DVD without any stretching or squashing
#
if [ "$1" == help ]
then
  echo "When encoding to a 16:9
Aspect MPEG (*see note below*)
Source Aspect   NTSC/PAL CVD    NTSC/PAL SVCD   NTSC/PAL DVD
1.33    1.33 Not Applicable: See above table for 1.33 resolutions

1.78    *352x480 / *352x576     *480x480 / *480x576     352x480 / 352x576 704x480 / 704x576 720x480 / 720x576

1.85    *352x460 / *352x552     *480x460 / *480x552     352x460 / 352x552 704x460 / 704x552 720x460 / 720x552

2.20    *352x388 / *352x432     *480x388 / *480x464     352x388 / 352x464 704x388 / 704x464 720x388 / 720x464

2.35    *352x360 / *352x432     *480x360 / *480x432     352x360 / 352x432 704x360 / 704x432 720x360 / 720x432
See http://www.transcoding.org/cgi-bin/transcode?Calculating_Frame_Size_And_Aspect_Ratio"
  exit
fi


# dw = dvd_width see above table for allowed widths I use 720x576
# dh = dvd_height see table above for allowed heights
dw=720
dh=576

if [ ! -n "$1" ]
then
  echo "Usage: `basename $0` <avi_width> <avi_height>"
  exit
fi

if [ ! -n "$2" ]
then
  echo "Usage: `basename $0` <avi_width> <avi_height>"
  exit
fi

# aw = avi_width; ah = avi_height, dar is the aspecraation of avi
aw=$1
ah=$2
dar_avi=`echo "scale=5; $aw/$ah" | bc`

#dvd_dar this is either 16:9 or 4:3 the Display Aspect Ratio

dvd_dar=1.77778
par=`echo "scale=5; ($dh*$dvd_dar)/$dw" | bc`

# when width of DVD is going to be 720
# And working out height is even if not +1 to make even

h=`echo "scale=0; $par*$dw/$dar_avi" | bc`
h22=`echo "scale=0; ($h/2)*2" | bc`

if [ $h != $h22 ]
then
  h=`expr $h + 1`
fi

#Padding needed
#And test if even pixels

p=`echo "scale=0; ($dh-$h)/2" | bc`
p22=`echo "scale=0; ($p/2)*2" | bc`

if [ $p != $p22 ]
then
  p_top=`expr $p - 1`
  p_bottom=`expr $p + 1`
else
  p_bottom=$p
  p_top=$p
fi

# if [ $p == $p22 ]
# then
#   p_top=`echo "scale=0; ($dh-$h)/2" | bc`
#   p_bottom=`echo "scale=0; ($dh-$h)/2" | bc`
# fi

echo "#put the folowing into ffmpeg options assuming its a PAL dvd you want:"
echo "    -target pal-dvd -s "$dw"x"$h" -padtop "$p_top" -padbottom "$p_bottom

exit

```

---

### Post by ahaslam on 2008-03-13
This is just what I was looking for. Thank you, much appreciated. ;)

---

