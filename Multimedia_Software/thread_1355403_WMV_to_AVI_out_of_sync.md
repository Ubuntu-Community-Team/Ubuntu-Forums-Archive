---
title: "WMV to AVI out of sync"
date: 2009-12-14
forum: Multimedia Software
---

### Post by fonque on 2009-12-14
I have spent the last 2 weeks trying to figure out how to use mencoder to transcode an MSS2 WMV file into a G1 playable file.

I have been successful except the video is faster than the audio. 

In order to successfully do this conversion, I have to fix the wmv file in windows using ASFtools. 
Then I encode the file from WMV to and xvid AVI w/ aac audio:

Then I encode the video portion of the XVID AVI to H.264

Then I use MP4box to combine the aac audio from first conversion and the h264 video from the second conversion into a G1 playing mp4 container


the only issue I am having is the first conversion with the following code:
[PHP]mencoder input.wmv -ovc xvid -xvidencopts bitrate=-1800 -ofps 25 -oac faac -faacopts br=32:mpeg=4:object=2 -channels 1 -srate 48000 -o output.avi[/PHP]

the original WMV is 25:25, the xvid AVI is 25:12
the video is complete but is too fast, the audio has the last 13 seconds truncated.

I am not sure how to get the length of the output video to match the input.

---

### Post by Sin@Sin-Sacrifice on 2009-12-14
Avidemux can fix that. I've found this 
```
# Author: TuTUX
# This script converts FLV/RM/MPEG/... to AVI/MP4 files.
# Dependency: ffmpeg, mencoder, gstreamer...
# ToDo: you tell me.
# Distributed under the terms of GNU GPL version 2 or later
#
# You need to be running Nautilus 1.0.3+ to use scripts.
#
#!/bin/bash

newname="New file name"
title="video convert (flv/avi/mpeg/rm to avi/mpeg-4)"
titlewh="Resolution of input video"
Wide="wide"
High="height"
avi_codec="Choose output codec"
audio_codec="Choose output audio"
bit_rate="Choose the bitrate of video (700 if mp4)"
abit="mp3 bitrate"
audio="audio encode(MPEG-4 will stick to acc)"
wrong="wrong input, skipping"
warning="huh?"
wide=640
high=480
tmp=0
tmp1=0
tmp2=0
bar1=0
bar=0
bar2=0
consw="640"
#encoding functions
iftowide()
{
ffmpeg -i "$1" -target ntsc-dvd  -padtop "$((bar1))" -padbottom "$((bar2))" -s "$wide"x"$high" -aspect 4:3 -b 1152 -padcolor 000000 -acodec copy "`basename "$1"`.mpg"
}
wh()
{
wide=`gdialog --title "$titlewh" --inputbox "$Wide" 200 100 2>&1`
high=`gdialog --title "$titlewh" --inputbox "$High" 200 100 2>&1`
tmp=wide/4
tmp1=tmp*3
tmp2=tmp1-high
if [ $((tmp2%4)) -eq 0 ]; then
bar1=tmp2/2
bar2=bar1
else
bar=tmp2/2
bar1=bar+1
bar2=bar-1
fi
}

DivXmp3_encode()
{
mencoder "$1" -ovc lavc -lavcopts vcodec=mpeg4:vbitrate="$get_bitrate":mbd=2:v4mv:autoaspect -vf pp=lb -oac mp3lame -lameopts cbr:br="$get_audio" -o "`basename "$1"`.avi"
}
DivXAC_encode()
{
mencoder "$1" -ovc lavc -lavcopts vcodec=mpeg4:vbitrate="$get_bitrate":mbd=2:v4mv:autoaspect -vf pp=lb -channels 6 -oac lavc -lavcopts acodec=ac3:abitrate=384 -o  "`basename "$1"`.avi"
}
XviDmp3_encode()
{
mencoder "$1" -ovc xvid -xvidencopts bitrate="$get_bitrate":autoaspect -vf pp=lb -oac mp3lame -lameopts cbr:br="$get_audio" -o "`basename "$1"`.avi"
}
XviDAC_encode()
{
mencoder "$1" -ovc xvid -xvidencopts bitrate="$get_bitrate":autoaspect -vf pp=lb -channels 6 -oac lavc -lavcopts acodec=ac3:abitrate=384 -o  "`basename "$1"`.avi"
}
MP4_encode()
{
ffmpeg -i "$1" -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 160 -ar 48000 -s 640x480 -aspect 4:3 "`basename "$1"`.mp4"
}
MP4()
{
if file "$1" | grep -q "Macromedia Flash Video"; then
     get_audio="64"
     DivXmp3_encode "$1"
     MP4_encode "$1.avi"
     rm -f "$1.avi"
     elif file "$1" | grep -q "RealMedia file"; then
     get_audio="128"
     DivXmp3_encode "$1"
     MP4_encode "$1.avi"
     rm -f "$1.avi"
      else
      MP4_encode "$1"
      fi 
}
MP4w()
{
if [ "$((wide))" -gt "$consw" ] ; then
    if file "$1" | grep -q "RealMedia file"; then
     get_audio="128"
     DivXmp3_encode "$1"
     iftowide "$1.avi"
     rm -f "$1.avi"
     MP4_encode "$1.avi.mpg"
     rm -f "$1.avi.mpg"
     else
     iftowide "$1"
     MP4_encode "$1.mpg"
    rm -f "$1.mpg"
     fi
else
    if file "$1" | grep -q "Macromedia Flash Video"; then
          get_audio="64"
     DivXmp3_encode "$1"
     MP4W_encode "$1.avi"
     rm -f "$1.avi"
     elif file "$1" | grep -q "RealMedia file"; then
     get_audio="128"
     DivXmp3_encode "$1"
     MP4W_encode "$1.avi"
     rm -f "$1.avi"
      else
      MP4W_encode "$1"
      fi 
fi
}
MP4W_encode()
{
ffmpeg -i "$1" -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 160 -ar 48000 -padtop "$((bar1))" -padbottom "$((bar2))" -s "$wide"x"$high" -aspect 4:3 -padcolor 000000 "`basename "$1"`.mp4"
}

#General
get_codec=`zenity --title="$title" --list --radiolist --column="" --column="$avi_codec" FALSE "DivX" TRUE "XviD" FALSE "MPEG-4" FALSE "MPEG-4 from widescreen"`
get_bitrate=`zenity --title="$get_codec" --list --radiolist --column="" --column="$bit_rate" FALSE "2500" FALSE "1800" FALSE "1152" TRUE "700" FALSE "500" `
#todo if mp4 widescreen or not
case "$get_codec" in
DivX)
get_acode=`zenity --title="$audio" --list --radiolist --column="" --column="$audio_codec" FALSE "AC3 5.1" TRUE "mp3lame" `
       case "$get_acode" in
       mp3lame)
       get_audio=`zenity --title="$audio" --list --radiolist --column="" --column="$abit" FALSE "320" FALSE "192" FALSE "160" TRUE "128" FALSE "64" `
       ;;
       esac
;;
XviD)
get_acode=`zenity --title="$audio" --list --radiolist --column="" --column="$audio_codec" FALSE "AC3 5.1" TRUE "mp3lame" `
       case "$get_acode" in
       mp3lame)
       get_audio=`zenity --title="$audio" --list --radiolist --column="" --column="$abit" FALSE "320" FALSE "192" FALSE "160" TRUE "128" FALSE "64" `
       ;;
       esac
;;
"MPEG-4 from widescreen")
wide=`gdialog --title "$titlewh" --inputbox "$Wide" 200 100 2>&1`
high=`gdialog --title "$titlewh" --inputbox "$High" 200 100 2>&1`
tmp=wide/4
tmp1=tmp*3
tmp2=tmp1-high
if [ $((tmp2%4)) -eq 0 ]; then
bar1=tmp2/2
bar2=bar1
else
bar=tmp2/2
bar1=bar+1
bar2=bar-1
fi
#gdialog --title "$((bar1))" --inputbox "$((bar2))" 200 100 2>&1
;;
esac

#General
while [ "$1" ]; do
  case "$get_codec" in        
     MPEG-4)
     MP4 "$1"  
     ;;
     "MPEG-4 from widescreen")
     MP4w "$1"
     ;;
        DivX)
       case "$get_acode" in
       mp3lame)
       DivXmp3_encode "$1"
       ;;
       "AC3 5.1")
       DivXAC_encode "$1"
       ;;
       esac
     ;;
     XviD)
        case "$get_acode" in
        mp3lame)
        XviDmp3_encode "$1"
        ;;
        "AC3 5.1")
        XviDAC_encode "$1"
        ;;
        esac
     ;;
   esac
   shift
done
``` script does a pretty good job. It's technically a nautilus script but, as you may know, it runs like any other script in the terminal.

---

