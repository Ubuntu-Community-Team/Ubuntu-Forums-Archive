---
title: "Screen Capture (Audio and Video)"
date: 2009-03-18
forum: Multimedia Software
---

### Post by IGM0937 on 2009-03-18
Hi...

I'm looking into doing some screen capture in ubuntu, but im having a hard time finding the right software to do this. Im trying to find something that's going to record whats on screen and also record audio like speech from a microphone!

I also need some video editing software, nothing advanced, just something that's going to cut and paste and do some small transitions.

So far i found a program called Istanbul, Is there any other programs that could be as good or even better?

---

### Post by batharoy on 2009-03-18
recordMyDesktop

Can be found in Add/Remove or Synaptic.

---

### Post by ajgreeny on 2009-03-18
> I also need some video editing software, nothing advanced, just something that's going to cut and paste and do some small transitions.
Have a look at avidemux.  I've used it a bit and it seems to work quite well for simple stuff like you seem to need.

---

### Post by binbash on 2009-03-24
gtk-recordmydesktop

---

### Post by wsherliker on 2011-06-14
Not sure if this will help others but I needed to grab sound and video. Tried all the suggested options but they were fiddly or didn't allow areas of the screen to be grabbed. 

Came up with this simple script which could easily have a gui added if someone has time. Just save as a bash script:

```
#/bin/bash

echo "CAPTURE - Record a portion of the screen with sound"
echo "Script by Warren Sherliker - The SmartTHING Limited"
echo ""
echo "NOTE: Ensure you have to set ffmpeg to capture from the monitor of your computers audio otherwise you will get silence"
echo "(see http://openubuntu.com/index.php?topic=690.0 and ensure you have unmuted the monitor)"
echo ""
echo "PREREQUISITES: ffmpeg and xdotool (both availabel by sudo apt-get install ....)"

echo "Please position your mouse in the top left of the capture area"
for i in `seq 1 5`; do
    echo -n "Pausing for 5 seconds: $i second(s)"
    echo -n $'\r'
    sleep 1
done
echo ""

POS=`xdotool getmouselocation`
X=`echo $POS | cut -d\  -f1`
Y=`echo $POS | cut -d\  -f2`

echo "Found $X and $Y"

echo "Please position your mouse in the bottom right of the capture area"
for i in `seq 1 5`; do
   echo -n "Pausing for 5 seconds: $i second(s)"
   echo -n $'\r'
   sleep 1
done
echo ""

POS=`xdotool getmouselocation`
X2=`echo $POS | cut -d\  -f1`
Y2=`echo $POS | cut -d\  -f2`

echo "Found $X2 and $Y2"

echo "Please start your video"
for i in `seq 1 5`; do
   echo -n "Pausing for 5 seconds: $i second(s)"
   echo -n $'\r'
   sleep 1
done
echo ""

if [ -e "output.mkv" ]; then
   echo "Removing previous recording (output.mkv)"
   rm "output.mkv"
fi

# Not much error checking here but should work in most cases
X=${X:2}
Y=${Y:2}
X2=${X2:2}
Y2=${Y2:2}

width=$(($X2 - $X))
width=$(($width / 2 * 2)) # Round to nearest multiple of 2 for ffmpeg
width=${width#-} # Ensure it is not negative (should really swap X and X2, Y and Y2 if so)
height=$(($Y2 - $Y)) 
height=$(($height / 2 * 2)) # Round to nearest multiple of 2 for ffmpeg
height=${height#-} # Ensure it is not negative (should really swap X and X2, Y and Y2 if so)

echo "Capturing ${width} by ${height} at position ${X} ${Y} to output.mkv in the current directory"

CMD="ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s ${width}x${height} -i :0.0+${X},${Y} -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv"

echo "RUNNING $CMD"
$CMD

echo "Output saved to output.mkv"
echo ""
echo "NOTE: You can perform basic cuts to the video using: "
echo " ffmpeg -sameq -ss <start in seconds> -i output.mkv output-cut.mkv"
echo "        add the -t <duration in seconds> parameter if needed"

```

---

### Post by raiden82 on 2011-07-29
Hi guys, i've tried every software available and none works! video and audio, any suggestions?

checked the developers websites and couldn't find any help there..

Ubuntu 11.04

Thanks

---

