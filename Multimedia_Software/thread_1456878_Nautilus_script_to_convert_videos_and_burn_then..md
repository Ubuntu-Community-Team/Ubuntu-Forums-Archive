---
title: "Nautilus script to convert videos and burn then."
date: 2010-04-17
forum: Multimedia Software
---

### Post by Boondoklife on 2010-04-17
I have been trying out different DVD-Video creation utilities and they are just way to complex for my needs so I wrote a nautilus script that will do it for me.

This will allow you to process more than one file (sequentially). Let me know if you run into any issues. The script takes the video file(s) and converts them to a MPG file, builds the dvd structure, and finally burns it. It does not allow for menu customization etc, but then again that is not what the script was meant for.

I personally have used it on divx encoded videos and they work in my wii and another set top dvd player.

```

#!/bin/bash
#
#
#    Requires: zenity, mencoder, dvdauthor, awk, dvd+rw-mediainfo, growisofs
#
#
IFS=$'\n'
TEMP_DIR='/tmp'

#zenity --info --text="$@"
#zenity --info --text=`pwd`

if [ "$1" == "" ]; then
    zenity --error --text="No files were specified"
    exit
fi

for FILE in $@
do
    MPEG="${FILE##*/}"
    MPEG="$TEMP_DIR"'/'"${MPEG%.*}.mpg" 
    #zenity --info --text="$MPEG"

    nice -n 19 mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:480,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=16/9:acodec=ac3:abitrate=192 -ofps 30000/1001 -o "$MPEG" "$FILE" 2>&1 | awk -vRS="\r" '$1 ~ /Pos/ {gsub(/Pos:/," ");gsub(/%\)/," ");gsub(/ \(/," ");print $3"\n#Position :\\t"$1"\\nFrame :\\t"$2"\\nPercentage :\\t"$3"%\\nFrame Rate :\\t"$4"\\nTime Remaining :\\t"$6; fflush();}' | nice -n 19 zenity --progress --auto-kill --auto-close --title="Converting ${FILE##*/}" --width=450


    #Create an xml file for dvdauthor
echo '<dvdauthor dest="'"$TEMP_DIR"'/DVD">
<vmgm />
<titleset>
<titles>
<pgc>
<vob file="'"$MPEG"'" />
</pgc>
</titles>
</titleset>
</dvdauthor>' > "$TEMP_DIR"'/dvdauthor.xml'



    #Create dvd file structure
    nice -n 19 dvdauthor -x "$TEMP_DIR"'/dvdauthor.xml' 2>&1 | nice -n 19 awk '{ print $1; fflush() }'| nice -n 19 zenity --progress --pulsate --auto-close --text="Creating dvd file structure" --title="Creating ${FILE##*/}" --width=450

    ANOTHER_DISC=1

    while [ $ANOTHER_DISC -eq 1 ]
    do

        ANOTHER_DISC=0

        #Get DVD Location
        dvd+rw-mediainfo /dev/dvd
        if [ $? -eq 0 ]
        then
            dev=/dev/dvd
        else
            dev=/dev/dvd1
        fi

        DISC_CHECK=$(dvd+rw-mediainfo /dev/dvd | grep -o 'no media mounted')
        if [ "$DISC_CHECK" = 'no media mounted' ]
        then
            DISC_CHECK=0
        else 
            DISC_CHECK=$(dvd+rw-mediainfo /dev/dvd | grep -o ' Disc status:           blank')
            if [ "$DISC_CHECK" = ' Disc status:           blank' ]
            then
                DISC_CHECK=1
            else
                DISC_CHECK=0
            fi
    
        fi

        while [ $DISC_CHECK -eq 0 ]
        do

            eject "$dev"
            zenity --info --title="Ready to burn DVD" --text="Please make sure there is a blank DVD in the drive."

            DISC_CHECK=$(dvd+rw-mediainfo /dev/dvd | grep -o 'no media mounted')
            if [ "$DISC_CHECK" = 'no media mounted' ]
            then
                DISC_CHECK=0
            else
                DISC_CHECK=$(dvd+rw-mediainfo /dev/dvd | grep -o ' Disc status:           blank')
                if [ "$DISC_CHECK" = ' Disc status:           blank' ]
                then
                    DISC_CHECK=1
                else
                    DISC_CHECK=0
                fi
            fi

        done

        #Burn DVD
        growisofs -dvd-compat -Z "$dev" -dvd-video "$TEMP_DIR"'/DVD' 2>&1 | awk '{ print $1; fflush() }' | zenity --progress --auto-close --text "Burning DVD" --title="Burning ${FILE##*/}" --width=450
        eject "$dev"
        zenity --question --text="Do you want to burn another copy of ${FILE##*/}" --ok-label="Yes" --cancel-label="No" --title="Burning ${FILE##*/}" --width=450
        if [ $? == 0 ]; then
            ANOTHER_DISC=1
        fi
    done

    #cleanup
    rm "$TEMP_DIR"'/dvdauthor.xml' & rm "$MPEG" & rm -r "$TEMP_DIR"'/DVD'
done

```

---

