---
title: "[SOLVED] PSP Video Script"
date: 2008-09-12
forum: Multimedia Software
---

### Post by xXZeroXx on 2008-09-12
Well, before I changed to Kubuntu, I used Ubuntu, but now, I can't use the script I used before, any idea about how to modify it, so I can use it in kubuntu?

> #!/bin/bash
## Script for converting videos to a PSP compliant format in
## Gnome.
## Created by KMC, March 6th, 2007
## Released under GPL.  Have at it.

gui=1
ffmpeglog="$HOME"/PSPVid.log
DSTNAME=M4V$(printf '%05d' ${RANDOM})
maxthm=200
aspect="16:9"

# die function
die () {
  if [ $gui ]; then
    zenity --error --title="PSPVid" --text "PSPVid has encountered an error - Ending now."
  else
    echo "PSPVid has encountered an error - Ending now." >/dev/stderr
  fi
  exit 1
}

# dienice function
dienice () {
  if [ $gui ]; then
    zenity --info --title "PSPVid" --text "${newtitle}.MP4 and ${newtitle}.THM were successfully created."
  else
    echo "Task complete" >/dev/stderr
  fi

  exit 1
}

# progress bar equations.
DisplayEncodingProgress () {
    progresstext="Now Encoding $SRCFILE [ pass $pass of 2 ]"
  if [ $gui ]; then
    (
      while ps | grep "$pid " >/dev/null
      do
        secondsCompleted=`tail -c 90 "$ffmpeglog" | awk -F"time=" {'print $2'} | cut -d"." -f 1`
        [ -n "$secondsCompleted" ] || secondsCompleted=0
        percentage=$((100*$secondsCompleted/$inputlength))
        echo "$percentage"
        sleep 1
      done
      echo 100
    ) | zenity --progress --title="$appname" --text="$progresstext" --auto-close
  else
    echo "$progresstext"
    lastpercentage=0
    while ps | grep "$pid " >/dev/null
    do
      secondsCompleted=`tail -c 90 "$ffmpeglog" | \
                        awk -F"time=" {'print $2'} | cut -d"." -f 1`
      [ -n "$secondsCompleted" ] || secondsCompleted=0
      percentage=$((100*$secondsCompleted/$inputlength))
      if [ $percentage -gt $lastpercentage ]; then
        echo -ne "$percentage%\r"
        lastpercentage="$percentage"
      fi
      sleep 1
    done
  fi
}

# quick dependency check
if [ $gui ]; then
  [ -z "$(which zenity)" ] && gui=
fi
[ -n "$(which mplayer)" ] || zenity --error --title "PSPVid" --text "Mplayer not installed, see [http://www.mplayerhq.hu](http://www.mplayerhq.hu) for more information."
[ -n "$(which mplayer)" ] || die 'mplayer not installed, see [http://www.mplayerhq.hu/](http://www.mplayerhq.hu/)'
[ -n "$(which ffmpeg)" ] || zenity --error --title "PSPVid" --text "FFmpeg not installed, see [http://ffmpeg.mplayerhq.hu/](http://ffmpeg.mplayerhq.hu/) for more information."
[ -n "$(which ffmpeg)" ] || die 'ffmpeg not installed, see [http://ffmpeg.mplayerhq.hu/](http://ffmpeg.mplayerhq.hu/)'
if [ -z "$(ffmpeg -formats | grep aac)" ]; then
  zenity --error --title "PSPVid" --text "No AAC audio codec support found.  Please recompile ffmpeg with faac support.";  die 'ffmpeg can not encode AAC audio, please recompile with faac support'
fi
if [ -z "$(ffmpeg -formats | grep xvid)" ]; then
  zenity --error --title "PSPVid" --text "No xvid video codec support found.  Please recompile ffmpeg with xvid support."; die 'ffmpeg can not encode xvid video, please recompile with xvid support'
fi
if [ -z "$(ffmpeg -formats | grep h264)" ]; then
  zenity --error --title "PSPVid" --text "No h264 video codec support found.  Please recompile ffmpeg with h264 support."; die 'ffmpeg can not encode h264 video, please recompile with h264 support'
fi

# select file to be converted.
appname=$(zenity --title="PSPVid - What file would you like to convert?" --file-selection $appname) 

  if [ -r "$appname" ]
    then SRCFILE="$appname"
  else zenity --error --title "PSPVid" --text "File is unreadable"
  die "File unreadable"
  fi

# select a title for saved file.
newtitle=$(zenity --title "PSPVid" --text "Enter a name for your new file" --entry $newtitle)

# select a number for saved file.
newnumber=$(zenity --title "PSPVid" --text "Enter a 5 digit number - (Used for file name creation)" --entry $newnumber)

# select destination directory, use last selected.
savedir=$(zenity --title "PSPVid - Where would you like your file to be saved?" --file-selection --directory $savedir) 

  if [ -w "$savedir" ]
    then ENCDIR="$savedir"
  else zenity --error --title "PSPVid" --text "You do not have permission to write to this directory."
  die "Directory permission error"
  fi

aspect=$(zenity --list --title "PSPVid" --text "Choose an aspect ratio" --radiolist --column "" --column "Aspect ratio" TRUE "Default" FALSE "4:3" FALSE "16:9" $aspect)

  if [ ${aspect} = "Default" ]
	then aspectr="4:3"
  
  elif [ ${aspect} = "4:3" ]
	then aspectr="4:3"
  
  elif [ ${aspect} = "16:9" ]
	then aspectr="16:9"
  
  else zenity --error --title "PSPVid" --text "No aspect ratio selected."
  die "No aspect ratio selected"
  fi

resol=$(zenity --list --title "PSPVid" --text "Choose a conversion method (Video codec --- Scr. Ratio / VBR / ABR)" --radiolist --column "" --column "Video Conversion method" TRUE "AVC---480x272/VBR-768K/ABR-128K" FALSE "MPEG4---368x208/VBR-768k/ABR-128k" FALSE "MPEG4---368x208/VBR-512k/ABR-64k" $resol)

  if [ ${resol} = "AVC---480x272/VBR-768K/ABR-128K" ]
	then RES="480x272"
frate="30000/1001"
vbitrate="768k"
audbitrate="128k"
vcode="h264"
filenam="MAQ"
arate="48000"
  
  elif [ ${resol} = "MPEG4---368x208/VBR-768k/ABR-128k" ]
	then RES="368x208"
frate="30000/1001"
vbitrate="768k"
audbitrate="128k"
vcode="xvid"
filenam="M4V"
arate="24000"
  
  elif [ ${resol} = "MPEG4---368x208/VBR-512k/ABR-64k" ]
	then RES="368x208"
frate="30000/1001"
vbitrate="512k"
audbitrate="64k"
vcode="xvid"
filenam="M4V"
arate="24000"
  
  else zenity --error --title "PSPVid" --text "No conversion method selected."
  die "No conversion method selected"
  fi

inputlength=`mplayer -identify -frames 0 -vc null -vo null -ao null \
               "${SRCFILE}$device" 2>/dev/null | \
               grep ^ID_LENGTH | \
               sed -e 's/^.*=//' -e 's/[.].*//'`
  [ -n "$inputlength" ] || die "Unable to determine video length."

nice -10 ffmpeg -i "${SRCFILE}" -pass 1 -passlogfile "${DSTNAME}" -title "${newtitle}" -acodec aac -ab "${audbitrate}" -vcodec "${vcode}" -s "${RES}" -b "${vbitrate}" -ar "${arate}" -coder 1 -r "${frate}" -f psp -aspect "${aspectr}" "${ENCDIR}/${filenam}${newnumber}.MP4" 2>"$ffmpeglog" &
	pid=$!
	pass=1
	DisplayEncodingProgress
	pid=

nice -10 ffmpeg -i "${SRCFILE}" -pass 2 -passlogfile "${DSTNAME}" -title "${newtitle}" -acodec aac -ab "${audbitrate}" -vcodec "${vcode}" -s "${RES}" -b "${vbitrate}" -ar "${arate}" -coder 1 -r "${frate}" -f psp -aspect "${aspectr}" "${ENCDIR}/${filenam}${newnumber}.MP4" 2>>"$ffmpeglog" &
	pid=$!
	pass=2
	DisplayEncodingProgress
	pid=

rm "${DSTNAME}-0.log"
  if [ -e "$ffmpeglog" ] 
    then
	rm "$ffmpeglog"
  fi

# select a thumbnail capture point.
thumbnail=$(zenity --title "PSPVid" --text "Enter a thumbnail capture point, in seconds. (between 1 and 200) " --entry $thumbnail)

  if [ -z $thumbnail ]
    then zenity --error --title "PSPVid" --text "No thumbnail capture point selected"
  die "No thumbnail capture point selected"
  
  elif [ $maxthm -lt $thumbnail ]
    then zenity --error --title "PSPVid" --text "Invalid capture point selected"
  die "invalid capture point selected"
  fi

nice -10 ffmpeg -y -i "${SRCFILE}" -f mjpeg -ss "${thumbnail}" -vframes 1 -s 160x120 -an "${ENCDIR}/${filenam}${newnumber}.THM" 2>/dev/null

  if [ -e "gmon.out" ] 
    then
	rm "gmon.out"
  fi

dienice "Process complete"

Can anyone help me?
PD: If you are wondering why do I like this script is because it also makes thumbnails of my videos, and there is not any other program for psp that does that.

---

### Post by ju2wheels on 2008-09-12
1. Make sure you give the script execute permission: sudo chmod +x scriptname.sh

2. What errors are you getting?

3. Do you have the dependencies resolved? (ffmpeg, mplayer) sudo apt-get install mplayer mencoder ffmpeg

---

### Post by xXZeroXx on 2008-09-13
Yeah, you were right, I forgot to give it the necesary permissions, Thanks.

---

