---
title: "Watch &amp; Record TV with Mplayer"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by Jose Catre-Vandis on 2007-02-24
This is a half howto and half how do I, as I have some of the pieces, but not the whole jigsaw!

This is poorly documented from what I can find, so I will list below the solutions I have found to enable, in one way or another, how you can go about watching what you are recording. It is evidently possible using VLC, MythTV and Freevo, but if you don't want the hassle of the Media Centre configurations, and need the configurability of mplayer, then this might help. I want control over these actions, and the ease of just using the command line or short scripts with zenity

Assumes you have mplayer/mencoder installed, and all suitable codecs and plugins you might need
Assumes you have a working dvb card and a channels.conf in your .mplayer directory

**1. The simplest solution**

You know that:
```
 mplayer dvb://
```
plays the first dvb channel in your list

You can then add a channel name like so:
```
 mplayer dvb://BBC1
```
Plays BBC1

You can then extend this to dump the ts stream to your hard drive (@ 1mb a second)
```
 mplayer dvb://BBC1 -dumpstream -dumpfile myBBC1recording.ts
```
(the file will be saved from wherever you run the terminal from)

So how do you watch this?

Well wait about 30 seconds after you have run the dumping command, open up a new terminal if needs be, and:
```
mplayer myBBC1recording.ts
```
and you should start viewing the recording, but a bit behind real time so that you don't crash things.

OK, this isn't perfect, and means a lot of work at the command line, and you have to manually shut down each instance of mplayer to stop viewing and recording. So you can write a script to automate  this:
```
#!/bin/bash
##
#dump the stream
mplayer  -dumpstream -dumpfile myBBC1recording.ts dvb://BBC1 &

#watchit
sleep 30 | zenity --progress --title="Recording" --text="Waiting for Cache before Mplayer starts..."
mplayer myBBC1recording.ts
#(to close the mplayer viewing window just close it)

#dialog to close down the recording mplayer
zenity --info --title "Watching & Recording TV" --text "Click OK to Finish Recording"

#finds the process id for the "recording" mplayer
mypid=`pidof -s mplayer`

#kills the process
kill -9 "$mypid"
```
(copy this code and save it to a text file called mytv.sh and make it executable. You need zenity installed as well, so that the pop up progress bar comes up while you wait the 30 seconds, just to let you know its happening), and to put up the second dialog to help you shut down the "recording" instance of mplayer.

To make the saved ts file usable, you will have to use mencoder again to force an index onto it, or use ProjectX, then you can encode to a format you wish.

**2. Using mencoder and tee**

You can set your own encoding options for this. 

To simply save the ts file, use the following syntax:
> mencoder dvb://BBC1 -o >( tee test.ts | mplayer -) -cache 8192 -oac copy -ovc copy -endpos 00:01:00

To encode to your preferred format, use this syntax, but note, you will see the encoded output in mplayer and not the raw dvb footage. Also note that I have included a 60 second endpos, for testing. You can edit this as you wish in HH:MM:SS format
> mencoder dvb://BBC1 -cache 8192 -oac copy -ovc lavc -lavcopts vcodec=mpeg4:mbd=1:vbitrate=500:aspect=16/9 -vf crop=700:570:10:0 -endpos 00:01:00 -o >( tee test.avi | mplayer -)

Also note that I have included a 60 second endpos, for testing. You can edit this as you wish in HH:MM:SS format. You will also note I have an 8mb cache set, this seems to help my PC cope with poor signal or drops in signal. You will need at least 30 seconds of recording to allow your PC to play what has been recorded without it getting all tangled up and crashing! If you have a slow PC, you might need longer?


I would be interested to hear from others who have code or scripts that do this seemingly simple thing, or if anyone knows what goes on inside MythTV or Freevo. I would like to try to get the raw footage as viewable and the recorded footage encoded, so a reverse of 2 in effect. Any help on improving my commands or scripts would be great, and I am happy to help others (with my limited experience) who are trying to do the same. Apparently the mplayer devs like to use "mkfifo" (names pipes) to do this, but I can't see how it helps.

Credits: mplayer FAQ, bash scripting guides,
Tested on: 6.0.6 /6.10 i386
Reqs: mplayer/mencoder, zenity, bash, [codecs?]
Guide and info caused no ill effects on my machines, and can't see how they could,but if you choose to use them, I can't be responsible if something goes horribly wrong!

---

### Post by gmc on 2007-02-28
> **Jose Catre-Vandis said:**
> ...I would be interested to hear from others who have code or scripts that do this seemingly simple thing, or if anyone knows what goes on inside MythTV or Freevo. I would like to try to get the raw footage as viewable and the recorded footage encoded, so a reverse of 2 in effect. Any help on improving my commands or scripts would be great, and I am happy to help others (with my limited experience) who are trying to do the same. Apparently the mplayer devs like to use "mkfifo" (names pipes) to do this, but I can't see how it helps.


I'm in the process of working out a pvr script to record shows for later viewing with my pvrusb2. Originally I was using mencoder to encode the mpeg-2 stream from /dev/video in realtime, and although I was reasonably happy with the quality of the recordings, the file sizes left something to be desired. A 30 minute show in mpeg-2 format clocks out at about 1.4GB, when I encoded then with mencoder, I could cut that down to about 400MB.

Still not satisfied, I've come up with a better way (see script below)

```

#!/bin/bash

# Configure WinTV USB2 Parameters
  echo false     > /sys/class/pvrusb2/sn-8206665/ctl_mute/cur_val
  echo 58980     > /sys/class/pvrusb2/sn-8206665/ctl_volume/cur_val
  echo composite > /sys/class/pvrusb2/sn-8206665/ctl_input/cur_val
  echo 6000000   > /sys/class/pvrusb2/sn-8206665/ctl_video_bitrate/cur_val
  echo 720       > /sys/class/pvrusb2/sn-8206665/ctl_resolution_hor/cur_val
  echo 480       > /sys/class/pvrusb2/sn-8206665/ctl_resolution_ver/cur_val

input=/dev/video1
outtmp=/home/gord/Desktop/pvr/.tmp/`date +%d%m%y%H%M`.mpeg
output=/home/gord/Desktop/pvr/$1-`date +%d%m%y`.avi
quiet=-really-quiet

# Record show
mencoder $quiet -ovc copy -oac copy -demuxer 2 -of mpeg -mpegopts format=dvd -endpos $2 $input -o $outtmp &
sleep 15
nice -n 19 mencoder $quiet -ovc lavc -oac mp3lame -demuxer 2 -lavcopts vcodec=mpeg4:mbd=2:trell:v4mv -vf crop=704:480:6:0,spp,scale=704:480,pp=lb,hqdn3d=2:1:2 -lameopts abr:br=92 $outtmp -o $output

# Clean up temporary
rm -rf $outtmp

exit 0

```Since the pvrusb2 is not a true dvb device and because I'm recording from satellite, I have my satellite receiver take care of changing the channels at the appropriate times and use crontab to execute the above script with the name of the show and length of time to be recorded.

Because I'm saving the mpeg-2 stream in realtime and then after a short delay, begin encoding that, I can compress a 30 minute show down to 195MB. And this works out well for me daily dose of Coronation St :-)

Regard
Gord

---

### Post by Jose Catre-Vandis on 2007-02-28
So real time encoding (say using the same parameters) results in a bigger file than if you encode a file saved to disk? (This is what I think you are syaing?)

Also, can you watch as well (while all this saving and encoding is going on!) ?

Nice script :-)

---

### Post by gmc on 2007-03-01
Hi Jose,

Yes, that's exactly what I'm saying. Realtime encoding will result in a larger file, than capturing the unencoded stream and then encoding after the fact.

It is possible to modify my script, so that you can watch the show while it's being encoded, specifically, by replacing the first instance of mencoder in my script, with the method your script uses, or simply tell <insert your favorite video veiwing program> to use the  output from the first instance of mencoder in my script.

Personally, since I'm more of a time shifting viewer, I prefer to record the show, by saving the stream coming from my WinTV PVR USB2 to a temporary file (which I can watch if I want), and then begin encoding to the best video/smallest file I can, and watch the show when it's more convenient.

I'm at work right now, but I've modified my original script to add more flexibility to it. I'll post it when I get home. Specifically, now I can control the channel, volume, choose between two different encoding methods.

In my experimentation with mencoder, fast action shows require a considerably higher bitrate than non-action shows, so I added a second encoding method to allow me to capture either based on what show I'm recording.

Regards,
Gord

---

### Post by Jose Catre-Vandis on 2007-03-01
Sounds good. Let me point you my other efforts on this which is simply about recording

[http://www.ubuntuforums.org/showthread.php?p=2009744#post2009744](http://www.ubuntuforums.org/showthread.php?p=2009744#post2009744)

---

### Post by gmc on 2007-03-02
HI Jose,

Sorry for the delay in responding, there's a big snow/ice/freezing rain storm that knocked out my internet access. 

Nice scripts you've come up with there, they've given me a few ideas on which direction I'm going to modify mine in. Speaking of which, here's what I've come up with so far...

```

#!/bin/bash

usage() {
    echo "pvcr -s[howname] -l[ength] hh:mm:ss -c[hannel] -v[olume] -t[ype] slow|fast"
    echo
}

nonaction() {
#  zenity --info --title "ATTENTION" --text "Video Encoding in progress"
   nice -n 19 mencoder $quiet -ovc lavc -oac mp3lame -demuxer 2 \
        -lavcopts vcodec=mpeg4:mbd=2:trell:v4mv \
        -vf crop=704:480:6:0,spp,scale=704:480,pp=lb,hqdn3d=2:1:2 \
        -lameopts abr:br=92 $outtmp -o $output >/dev/null
}

action() {
#  zenity --info --title "ATTENTION" --text "Video Encoding in progress"
   nice -n 19 mencoder $quiet -ovc lavc -oac mp3lame -demuxer 2 \
        -lavcopts vcodec=mpeg4:vbitrate=1400:keyint=30 \
        -vf crop=704:480:6:0,spp,scale=704:480,pp=lb,hqdn3d=2:1:2 \
        -lameopts abr:br=92 $outtmp -o $output >/dev/null
}

# Parameter Defaults
show=test
length=00:01:00
channel=0
volume=95
type=slow

# Parse Parameters
while getopts ":s:l:c:v:t:" param; do
    case $param in
        s) show=$OPTARG ;;
        l) length=$OPTARG ;;
        c) channel=$OPTARG ;;
        v) volume=$OPTARG ;;
        t) type=$OPTARG ;;
        *) usage; exit 1;;
    esac
done

# WinTV PVR USB2 Parameters
pvrctl=/sys/class/pvrusb2/sn-8206665
input=/dev/video1
outtmp=/home/gord/Desktop/pvr/.tmp/`date +%d%m%y%H%M`.mpeg
output=/home/gord/Desktop/pvr/$show-`date +%d%m%y`.avi
quiet=-really-quiet

# Configure WinTV USB2 Parameters
echo false     > $pvrctl/ctl_mute/cur_val
echo "620 * $volume" | bc > $pvrctl/ctl_volume/cur_val

if [ "$channel" = "0" ]; then 
   echo composite > $pvrctl/ctl_input/cur_val
else
   echo television > $pvrctl/ctl_input/cur_val
   ivtv-tune --channel=$channel
fi

# Record mpeg-2 stream
# zenity --info --title "ATTENTION" --text "Video Recording in progress"
mencoder $quiet -ovc copy -oac copy -demuxer 2 -of mpeg -mpegopts format=dvd -endpos $length $input -o $outtmp >/dev/n
ull

if [ "$type" == "slow" ]; then
    nonaction
else
    action
fi

# Clean up temporary
rm -rf $outtmp

exit 0


```One thing I noticed is you're simply copying the audio output as opposed to compressing it. I've found that by compressing audio down to 92kbps, I don't lose much in the audio quality and use the bits that are not used to encode audio to improve the video quality and file size, when I do use the vbitrate option.

Gord

---

### Post by panch0 on 2007-03-02
Just as a side note, both KPlayer and Kaffeine have a very nice interface for playing from DVB devices. Recording is still best done from the command line of course.

---

### Post by Jose Catre-Vandis on 2007-03-03
> **panch0 said:**
> Just as a side note, both KPlayer and Kaffeine have a very nice interface for playing from DVB devices. Recording is still best done from the command line of course.

Yep, and vlc is pretty good too, but I wanted to acheive something using mplayer and I started to have trouble with kaffeine recording, it borked on a couple of recordings I tried to make, so started looking for alternatives. I find using a large cache in mplayer has helped considerably avoid broken recordings.

I have not tried Kplayer (being on Gnome) but will take a look.

Mentioning vlc, I love the ability to stream live tv around the lan, this helps to reduce fighting in the house when there are five things to watch at the same time!:)

---

### Post by gmc on 2007-03-03
Hi Jose,

Umm? "large cache". Can you elaborate on that one? I haven't seen anything in mencoder that talks about caches, or is that something specific to mplayer.

Regards,
Gord

---

### Post by Jose Catre-Vandis on 2007-03-03
> **gmc said:**
> Hi Jose,

Umm? "large cache". Can you elaborate on that one? I haven't seen anything in mencoder that talks about caches, or is that something specific to mplayer.

Regards,
Gord

You are right Gord, not to do with mencoder, but is an mplayer option, but it seems to work as a mencoder option as well? So if I am going to record something, I set the cache to say 8192 in my options, then until the cache is filled things don't start recording. if I get a weak signal at any point then the cache is sufficient to overcome any recording problems. Kaffeine would just stall.

---

### Post by david_2001 on 2007-03-03
What I've found is that though kaffeine will stall or sometimes hang completely if the signal gets weak/corrupted it will carry on streaming the dvb ts to file (the recording is done by a separate process).  And, most of the time, just clicking on the stop button and then the play button will get playback going again after kaffeine has stalled.

---

### Post by gmc on 2007-03-04
> **Jose Catre-Vandis said:**
> You are right Gord, not to do with mencoder, but is an mplayer option, but it seems to work as a mencoder option as well? So if I am going to record something, I set the cache to say 8192 in my options, then until the cache is filled things don't start recording. if I get a weak signal at any point then the cache is sufficient to overcome any recording problems. Kaffeine would just stall.


Oh! I thought maybe you were saying you'd found a way to eliminate missing/duplicate frames when recording a show. I find that with my setup, it usually takes a minute or two for mencoder to settle down and captures frames without the frames being mangled by using some sort of caching option.

Gord

---

