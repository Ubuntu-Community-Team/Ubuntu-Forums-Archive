---
title: "Convert mp3 to avi"
date: 2009-08-19
forum: Multimedia Software
---

### Post by cudjoe on 2009-08-19
Hi,

I need to convert a mp3 to avi because my Upnp player (freebox-tv) does not read mp3 but supports well xvid videos. I thus will transcode my music as blank videos.

With ffmpeg, the conversion is easy :
```
ffmpeg -i input.mp3 -vn -acodec copy -f avi output.avi
```
**Problem** : the output does not have any video stream. 

I made a small blank video (attached as txt), 1 black frame.

With mencoder, I managed to have both video and audio : 
```
mencoder black.avi -o output.avi -ovc xvid -oac copy -audiofile input.mp3
```
**Problem** : the output file is 1 frame long.

How can I specify to loop over the blank video accordingly to audio stream length ?

Thank you guyz for any ideas!

---

### Post by FakeOutdoorsman on 2009-08-20
Create blank black image (*convert* is part of the *imagemagick* package):
```
convert -size 320x240 xc:black black.png
```
Or create black image with white text:
```
convert -size 320x240 xc:black -fill white -draw "gravity Center text 0,0 'The Pogues'" black.png
```
Combine audio and black video:
```
ffmpeg -loop_input -i black.png -i fairytale_of_new_york.mp3 -shortest -acodec copy output.avi
```
You will need to enable restricted encoders in FFmpeg to encode with mpeg4:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Locutus_of_Borg on 2009-08-20
save this python script, name it script.py (or whatever you want)
```
import os, sys                                           

fps = 30

if len(sys.argv) != 4:
    print "Usage: makevid.py imagefile audiofile seconds"
    sys.exit(1)                                          

secs = int(sys.argv[3])
if secs < 0:
    print "Please pass a positive amount of seconds"
    sys.exit(1)
secs = 1 / float(secs)

filesexist = True
for each_file in sys.argv[1:2]:
    if not os.path.exists(each_file):
        print "%s doesn't exist" % each_file
        filesexist = False
if not filesexist: sys.exit(1)

mencoder_cmd = ('mencoder "mf://%s" -mf fps=%f -vf harddup -ovc lavc'\
    ' -lavcopts vbitrate=100 -audiofile "%s" -oac copy -ofps %d'\
    ' -o output.avi') % (sys.argv[1], secs, sys.argv[2], fps)

print "Starting mencoder"
os.system(mencoder_cmd)
print "Video is complete, output written to output.avi"
```
open a terminal execute the script with```
python script.py [imagefile] [audiofile] [length in seconds]
```

this will create a video of a still image that will play your audio for however many seconds you specify

---

### Post by cudjoe on 2009-08-21
Thanks Locutus_of_Borg.
With the information of Fakeoutdoorsman, I made this small shell script (ffmpeg instead of mencoder) :

```

input=$1
output=$2

background=/tmp/bng-black.jpg
convert -size 320x240 xc:black $background
duration=`ffmpeg -i $input 2>&1 | grep Duration | cut -f1 -d, | cut -f2,3,4,5 -d:`
ffmpeg -loop_input -i $background -i $input -vcodec mpeg4 -acodec copy -t $duration $output

```

Thank you very much for your assistance !

---

### Post by Kilarin on 2010-01-21
Thanks!  I just used your shell script, replacing the background.jpg with an image I wanted to use, and converted an mp3 file into an avi!  It was EASY with the script.  thank you VERY much!

---

### Post by FakeOutdoorsman on 2010-01-22
I updated my first post to now use the *-shortest* option which will automatically finish encoding the video when the music ends.  Much easier than getting the audio duration and then using that number to determine the encoding length.  So now cudjoe's script can look like this:
```
#!/bin/bash
# Usage: mp32avi.sh input.mp3 output.avi
input=$1
output=$2

background=/tmp/bng-black.jpg
convert -size 320x240 xc:black $background
ffmpeg -loop_input -i $background -i $input -vcodec mpeg4 -acodec copy -shortest -qscale 5 $output
```

What would be interesting is to get the artist and/or title tag from the audio metadata and feed that to the "create black image with white text" (post #2) example for *convert*.

**Update:** I also added *-qscale 5* to cudjoe's script so the output quality should be better for more complicated backgrounds other than just a solid color.

---

### Post by Lars Noodén on 2010-01-22
@ FakeOutdoorsman : That looks useful.  Sorry for a dumb question: Does that method wrap the MP3s as AVI as is, or does it transcode them and reduce the sound quality further?

---

### Post by FakeOutdoorsman on 2010-01-22
> **Lars Noodén said:**
> @ FakeOutdoorsman : That looks useful.  Sorry for a dumb question: Does that method wrap the MP3s as AVI as is, or does it transcode them and reduce the sound quality further?

There is no re-encoding of the audio in the script because it is using the *-acodec copy* option.  It is basically copying the audio from the MP3 file and pasting it into an AVI file.

There is a *-vcodec copy* option as well which is quite useful.  Both of these options are good for trimming a video without re-encoding or adding/removing audio/video to a file without any need to re-encode.

---

### Post by FakeOutdoorsman on 2010-01-22
Here's a new version:
[list][*] add the title to the black background
[*] use gif because it is faster to decode than png apparently
[*] set frame rate
[*] add requirements
[*] make background randomly named and then delete it[/list]
```
#!/bin/bash
# Requires: imagemagick, ffmpeg
# Usage: ./mp32avi.sh input.mp3 output.avi

background=/tmp/$RANDOM.gif

title=`ffmpeg -i $1 2>&1 | grep TIT2 | cut -d: -f 2`

convert -size 320x240 xc:black -fill white -draw "gravity Center text 0,0 '$title'" $background

ffmpeg -loop_input -r ntsc -i $background -i $1 -acodec copy -shortest -qscale 5 $2

rm $background

exit
```

---

### Post by Kilarin on 2010-01-24
this scrip creates the avi just fine, but the background is plain black.  For some reason its not grabbing the mp3 title info.

I made certain the title was populated in both v1 and v2 tags.  Am I missing some component?

thanks again!

---

### Post by FakeOutdoorsman on 2010-01-24
> **Kilarin said:**
> this scrip creates the avi just fine, but the background is plain black.  For some reason its not grabbing the mp3 title info.

I made certain the title was populated in both v1 and v2 tags.  Am I missing some component?

thanks again!

I forgot to mention that you'll need a relatively recent version of FFmpeg for the title grabbing part of the script to work.  I'll have to check if Karmic uses a recent enough FFmpeg, but I'm out of town right now.

It might be easier to just install the **id3v2** package and run this (untested) version of the script:

```
#!/bin/bash
# Requires: imagemagick, id3v2, ffmpeg
# Usage: ./mp32avi.sh input.mp3 output.avi

background=/tmp/$RANDOM.gif

title=`id3v2 -l $1 | grep TIT2 | cut -d: -f 2`

convert -size 320x240 xc:black -fill white -draw "gravity Center text 0,0 '$title'" $background

ffmpeg -loop_input -r ntsc -i $background -i $1 -acodec copy -shortest -qscale 5 $2

rm $background

exit
```

---

### Post by Kilarin on 2010-01-24
That works, thanks.

---

