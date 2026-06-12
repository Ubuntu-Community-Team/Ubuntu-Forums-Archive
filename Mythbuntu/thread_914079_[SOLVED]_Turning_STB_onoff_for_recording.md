---
title: "[SOLVED] Turning STB on/off for recording?"
date: 2008-09-08
forum: Mythbuntu
---

### Post by LorenzoS on 2008-09-08
How do people manage the powering on / off of their Cable Boxes when scheduling a show to record?

I have recording working nicely with Composite video input from my Scientific Atlanta 4250 cable box.  LIRC is working and changing channels on the STB.  Also, I can manually power the box on or off at the command line ```
irsend SEND_ONCE blaster POWER
```
My problem is this STB has only a single POWER code instead of separate POWER_ON and POWER_OFF.  And there is no way to predict if somebody left the STB powered on or off when a scheduled recording starts.  So often when a show is set to record, I get nothing because the STB is off.

So my questions are: 
[LIST=1]
[*]Is there a way to handle this other than always making sure the STB is powered on?
[*]What about a way to detect if Composite video or audio signal is being received by the PVR-500 card, as a way to know if the STB needs to be powered on? 
[*]Is there a different STB with separate power on/off codes that I should try to get from my cable company (Time Warner NYC)?
[/LIST]

---

### Post by LorenzoS on 2008-09-09
I found this excellent solution from Evuraan over here: [http://evuraan.blogspot.com/2008/01/how-to-ensure-set-top-box-stb-is.html](http://evuraan.blogspot.com/2008/01/how-to-ensure-set-top-box-stb-is.html)

After a few changes to work for my STB it works great.  Here is my channel changing script that first checks to see if the PVR-500 is receiving a picture and turns on the STB if needed before changing the channel.
```
# check STB to see if powered on and turn on if needed
# then change channel

#set working variables
REMOTE_NAME=SAE8000
pvr="/dev/video1"
t="$RANDOM-$RANDOM"
out="/tmp/$t.mpg"
mark="1727"
blank="0"
POWEROFF="0"
POWERON="0"

# function to search for video from STB and turn it on if it is off
scan_images(){
for i in `echo /tmp/$t*.jpeg`
do
if [ -s "$i" ]
then
#blank="`jp2a $i --invert --size=72x24 | sed -e 's/./& \n/g'|grep -c "M"`"
blank="`jp2a $i --invert --size=72x24 | sed 's/W/M/g' | sed -e 's/./& \n/g'|grep -c "M"`"
 rm -f "$i" 1>/dev/null 2>/dev/null || :
fi
[ "$blank" -gt "$mark" ] && export POWERON="100"
[ "$blank" -le "$mark" ] && export POWEROFF="100"
done
if [ "$POWERON" -eq "100" -a "$POWEROFF" -ne "100" ]
then
# STB is off so turn it on
send_power_on
irsend SEND_ONCE $REMOTE_NAME power
sleep 2
fi
}

# switch to the temp directory
cd /tmp
dd if="$pvr" of="$out" bs=64K count=2  1>/dev/null 2>/dev/null

# make sure the STB is on
if [ -s "$out" ]
then
ffmpeg -i $out -f image2 -vcodec mjpeg /tmp/$t%d.jpeg 1>/dev/null 2>/dev/null
[ -s "/tmp/${t}1.jpeg" ] && scan_images
fi

# change the channel
# send exit code in case onscreen guide is active
sleep 0.1
irsend SEND_ONCE $REMOTE_NAME exit 
# send channel digits
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $digit
sleep 0.1
done
# send select code instead of waiting for STB 
irsend SEND_ONCE $REMOTE_NAME select
sleep 0.1

# delete the temp files
[ -f "$out" ] && rm -f "$out" 1>/dev/null >/dev/null || :
```

---

