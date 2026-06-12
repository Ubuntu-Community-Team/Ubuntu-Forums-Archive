---
title: "Returning to Ubuntu to convert DVD to MP4"
date: 2008-05-25
forum: Multimedia Software
---

### Post by the lemming on 2008-05-25
Hello

I am returning to Ubuntu after building a new PC from scratch.  My last shop bought system did not like Ubuntu at all and crashed spectacularly.

However enough of all that, I am in the process of transferring my DVD collection onto my hard drive by using MP4 H264 encoding.  So far all this has been done using Vista but as I say I want to start using Linux again because of how safe it is to use on the net which means I would love to learn how to convert my collection using Ubuntu.

Any recommendations on what programs I need to use to accomplish all this?

Cheers

---

### Post by the lemming on 2008-05-29
Bumpity bump.

Anybody please?

I just want to convert VOB to MP4 (H264)

Cheers

---

### Post by Kevbert on 2008-05-29
Have a look at this: [http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/52379-mpeg-dvd-vob-format-conversion.html]("http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/52379-mpeg-dvd-vob-format-conversion.html")
Also Mplayer ([http://www.mplayerhq.hu]("http://www.mplayerhq.hu"))is supposed to be able to do this but I couldn't find anything relating to it.
Let me know if you have any luck.

---

### Post by JEDIDIAH on 2008-05-29
Here's one of the batch processing scripts I use once my DVDs are ripped
as VOB files. This uses mencoder with x264 for video and mp3 for audio.

The main h264 are just something I found on a website when I was first
exploring this idea myself. You don't need to set the bitrate. I do that
because I worry that the encoder will set it too low. You can get some
really small files with h264.

This is for TV viewing. I use a conventional SD set as well as a large
HDTV. These options won't work for something like an Archos (which I
have a separate script for). For an Archos, you can just use the default
options for x264.

There's a cropping option in here for letterbox stuff. 

This will convert from vob to avi and will make sure that the
target file doesn't already exist. If you run this without args
it will try to convert every vob in the current directory.

###-----------------------------------------------------------------###
#!/bin/bash


if [ "$1" != "" ]; then
    FROM="$1"
else
    FROM=$( ls *vob )
fi

CROP_ME="TRUE"
CROP_ME="FALSE"

cp /dev/null convert.log

#####################################################################
###---------------------------------------------------------------###


###--- xvid defaults

OPTIONS="-xvidencopts bitrate=800"
MAIN_OPTS="-ovc xvid -oac mp3lame -alang en -slang en"


###--- h.264 high quality


BITRATE=800
BITRATE=1200
BITRATE=1500

### subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b
### subq=5:8x8dct:frameref=2:bframes=3:b_pyramid:weight_b
### subq=4:bframes=2:b_pyramid:weight_b

###OPTIONS="-x264encopts subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:bitrate=$BITRATE "


### h264 High Quality options, 2 pass
### This is the default setting
X264_PASS1="-ovc x264 -x264encopts subq=4:bframes=4:b_pyramid:weight_b:pass=1:psnr:bitrate=$BITRATE:turbo=1"
X264_PASS2="-ovc x264 -x264encopts subq=5:partitions=4x4:8x8dct:frameref=3:me=hex:bframes=4:b_pyramid:pass=2:psnr:bitrate=$BITR
ATE" 

### h264 basic options, 1 pass
### This is for problem content like Forever Knight
#X264_PASS1=""
#X264_PASS2="-ovc x264 -x264encopts bitrate=$BITRATE" 
##X264_PASS2="-ovc x264 " 


CROP_OPTS=" -vf crop=720:360 -lavcopts aspect=16/9"

LANG="-alang en -slang en -aid 128"

MP3_AMP=":vol=8"
MP3_AMP=":vol=6"
MP3_AMP=""

MP3_OPTS="-oac mp3lame -lameopts br=128${MP3_AMP}"


OPTIONS=""

###---------------------------------------------------------------###
#####################################################################



for from in $FROM; do
    echo "Converting $from..."

    flag=$(file $from | sed 's/.*: //g' | grep ^MPEG | wc -l)
    if [ $flag -eq 1 ]; then

        ####---- Create the destination filename ----####
        to=$( echo $from | sed 's/[.]vob$/.avi/g' )


        #########################################################
        ###---------------------------------------------------###
        flag=$(echo "$EXCLUDE" | tr ' ' '\n' | grep $from | wc -l  )
        exclude=0
        ###---------------------------------------------------###
        if [ $flag -gt 0 ]; then
            echo "$to"
            echo "Source File on Exclusion List! Skipping..."
            exclude=1
        fi
        ###---------------------------------------------------###
        if [ -f $to ]; then
            echo "$to"

...back 1 page
### This is for problem content like Forever Knight
#X264_PASS1=""
#X264_PASS2="-ovc x264 -x264encopts bitrate=$BITRATE" 
##X264_PASS2="-ovc x264 " 


CROP_OPTS=" -vf crop=720:360 -lavcopts aspect=16/9"

LANG="-alang en -slang en -aid 128"

MP3_AMP=":vol=8"
MP3_AMP=":vol=6"
MP3_AMP=""

MP3_OPTS="-oac mp3lame -lameopts br=128${MP3_AMP}"


OPTIONS=""

###---------------------------------------------------------------###
#####################################################################



for from in $FROM; do
    echo "Converting $from..."

    flag=$(file $from | sed 's/.*: //g' | grep ^MPEG | wc -l)
    if [ $flag -eq 1 ]; then

        ####---- Create the destination filename ----####
        to=$( echo $from | sed 's/[.]vob$/.avi/g' )


        #########################################################
        ###---------------------------------------------------###
        flag=$(echo "$EXCLUDE" | tr ' ' '\n' | grep $from | wc -l  )
        exclude=0
        ###---------------------------------------------------###
        if [ $flag -gt 0 ]; then
            echo "$to"
            echo "Source File on Exclusion List! Skipping..."
            exclude=1
        fi
        ###---------------------------------------------------###
        if [ -f $to ]; then
            echo "$to"
            echo "Destination file already exists! Skipping..."
            exclude=1
        fi
        if [ -f x264/$to ]; then
            echo "x264/$to"
            echo "Destination file already exists! Skipping..."
            exclude=1
        fi
        ###---------------------------------------------------###
        #########################################################


     
        ######################################################################
        ###--- Determine if this is a letterboxed video by the filename ---###
        flag=$(echo "$from" | grep 'LB.vob' | wc -l )
        echo "<crop_flag> $flag"
        if [ $flag -eq 1 ]; then
            CROP=" -vf crop=720:360 -lavcopts aspect=16/9"
            OPTIONS="$CROP"
        else
            OPTIONS=""
            CROP=""
        fi
        ###--- Determine if this is a letterboxed video by the filename ---###
        ######################################################################



        #####################################################################
        ###------------- Make sure we haven't converted it already -------###
        if [ $exclude -eq 0 ]; then
            echo "Converting $to..."

            basename=$(echo $from | sed 's/[.].*$//g' )

            if [ "$X264_PASS1" != "" ]; then
                ###--- Pass #1 
                nice -20 mencoder -v $from $X264_PASS1 $OPTIONS \
                    -oac copy $LANG \
                    -o /dev/null
                    ## -vobsubout $basename -vobsuboutindex 0 \
             fi

             ###--- Pass #2
             nice -20 mencoder -v $from $LANG \
                $MP3_OPTS $X264_PASS2 $OPTIONS \
                -o $to

        fi

     else
         echo "$from is NOT an MPEG file! Skipping..." | tee -a convert.log
     fi

done

exit


         nice -20 mencoder $from -o $to -oac mp3lame -ovc lavc \
             -lavcopts vcodec=xvid:vpass=1:vbitrate=${BITRATE} $CROP
         nice -20 mencoder $from -o $to -oac mp3lame -ovc lavc \
             -lavcopts vcodec=xvid:vpass=2:vbitrate=${BITRATE} $CROP

---

