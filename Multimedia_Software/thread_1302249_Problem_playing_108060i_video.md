---
title: "Problem playing 1080/60i video"
date: 2009-10-26
forum: Multimedia Software
---

### Post by tidris on 2009-10-26
I am having trouble playing 1080/60i videos from my brand new Samsung HMX-H100N camcorder. On Totem and VLC the videos show extreme amounts of pixelation and artifacts, and the player crashes after playing a few seconds of video. I uploaded one video to youtube and it shows the same pixelation/artifacts I see when the original video is played on my computer. When the camcorder itself plays these videos they look perfectly normal on its LCD screen.

I am using Ubuntu 9.04 on a 2.4GHz Core2 Duo, 3GB RAM, GeForce8600m GT 256MB. I think that should be powerful enough to play these 1080/60i videos.

No problem with 720p and 480p videos from the same camcorder, except for an aspect ratio issue that is easy to deal with. 

Is anybody else having problems playing 1080/60i videos?

---

### Post by tidris on 2009-10-31
I have posted video samples here:
[http://www.youtube.com/watch?v=0cd5liXf_No](http://www.youtube.com/watch?v=0cd5liXf_No)
[http://www.youtube.com/watch?v=ShBn7wdceiU](http://www.youtube.com/watch?v=ShBn7wdceiU)

I uploaded the raw 1080/60i mp4 files produced by my hmx-h100 into youtube and what you see there is the result after youtube converted them to whatever format they use for public distribution. They look just as bad as when I play the original mp4 files on my Linux computer. Youtube uses Linux so I am not too surprised to see that result.

So I am trying to figure out if this a problem with Linux or a problem with my camcorder model. If you own a different camcorder model/brand please let me know if you have any problems playing its 1080/60i files on Ubuntu.

---

### Post by tidris on 2009-11-11
bump

---

### Post by tidris on 2009-11-14
I found a way to work around my problem. Using the MP4Box tool to extract the video and audio tracks, then using ffmpeg to recombine them using the copy codecs, produces video files that play without the extreme pixelation and artifacts.

However I am still not sure if the original problem is caused by faulty video files from the camcorder, or by a buggy Linux video codec.

---

### Post by MusJet on 2009-11-15
Step to step:

If you have video file "HDV_0001.MP4" with these features:

> mp4info HDV_0001.MP4 
   mp4info version 1.6
   HDV_0001.MP4:
   Track    Type    Info
   1    video    H264 Main@4, 20.560 secs, 17154 kbps, 1920x1080 @ 25.000000 fps
   2    audio    MPEG-4 AAC LC, 20.778 secs, 128 kbps, 90000 Hz

Extracting video track:
mp4creator -extract=1 HDV_0001.MP4 video.264

Extracting audio track:
mp4creator -extract=2 HDV_0001.MP4 audio.aac

Joining video and audio:

MP4Box -fps XX -cat video.264 -cat audio.aac -new video.mp4 -inter 0 -keepsys
where xx = frames per second

Now video.mp4 is ready to play with very clear video.
If you have mplayer installed and vdpau (nvidia video boards) use command:

mplayer -vo vdpau -vc ffh264vdpau video.mp4

and no cpu stress !

Cheers,

   MusJet

---

### Post by tidris on 2009-11-16
I do the same steps you describe but with different tools. I extract the tracks with MP4Box and rejoin them with ffmpeg. I didn't know of mp4info and mp4creator until you mentioned them here.

Initially I tried using MP4Box to rejoin the tracks but it insisted on creating 25 fps video no matter what frame rate I specified. My video is NTSC so 25 fps won't do. I found ffmpeg could join the tracks using the correct frame rate.

I wrote a Ruby language script to automate this. I am posting it here in case it can be of use to anyone. To use it paste the script into a text file, then make the file executable. The Ruby interpreter needs to be installed to run the script. If you save the scrip to a file named fix-1080i, you would use it as follows on a terminal window:

```
fix-1080i my_1080i_video_file.MP4
```

The fixed output file will be the same name as the input file with ".mp4" appended (my_1080i_video_file.MP4.mp4, for example). The output file will be in the same directory as the input file.

```
#!/usr/bin/ruby
# Created by tidris 11-13-09
# This script depends on Ruby, ffmpeg and MP4Box.

ARGV.each do |arg|
	dir = File.dirname(arg)
	s = dir + '/' + File.basename(arg).split('.')[0]
	s1 = s + "_track1.h264"
	s2 = s + "_track2.aac"
	s3 = arg + ".mp4"
	
	info = `MP4Box -info "#{arg}"`
	if !info.include?('1920 x 1080')
		puts "*** Skipping '#{arg}'"
		puts "*** It doesn't appear to be a 1080i video file.\n"
		next
	end
	if !info.include?('File Brand avc1 - version 0')
		puts "*** Skipping '#{arg}'"
		puts "*** It appears to have already been fixed.\n"
		next
	end
	
	`MP4Box -raw 1 "#{arg}"` # extract video track
	if !File.exists?(s1)
		puts "*** Could not extract the video track."
		puts "*** Skipping '#{arg}'."
		next
	end
	`MP4Box -raw 2 "#{arg}"` # extract audio track
	if !File.exists?(s2)
		puts "*** Could not extract the audio track."
		puts "*** Skipping '#{arg}'."
		File.delete(s1)
		next
	end
	
	# combine video and audio track
	#`MP4Box -new -fps 59.94005994 -add "#{s1}" -add "#{s2}" "#{s3}"`
	puts `ffmpeg -r 30000/1001 -i "#{s1}" -i "#{s2}" -vcodec copy -acodec copy "#{s3}"`
	File.delete(s1)
	File.delete(s2)
	puts "*** Success! Output is on '#{s3}' ***" if File.exists?(s3)
end

```

---

### Post by sorceror on 2010-05-24
Ran into this problem with my HMX-H105BN, and this thread was very helpful. I put together a shell script to do the processing for NTSC video, as follows:

```

#!/bin/bash
# Helps handling filenames with spaces
IFS=`printf '\n\t'`

## Set up parameters for encoding

# I tried to set the frame rate from the video, but it played at half speed
#THE_FPS=`mp4info $2 | grep @ | cut -d"@" -f 3 | cut -d" " -f 2`
#Instead I just hardcoded the NTSC "60 fps" value...
THE_FPS=59.940602

# Log file name
TEMP_FILE_DIR=`mktemp -d`

# This is the key parameter we gotta have from the user.
# Spaces in the output file name are probably not a good idea.
if [ -n "$1" ]; then
  NEWNAME=$1
else
  echo Output file name not specified, aborting!
  echo "Usage: " $0 " output-name input-video"
  exit 0
fi

if [ -n "$2" ]; then
  VIDNAME=$2
else
  echo Input file name not specified, aborting!
  echo "Usage: " $0 " output-name input-video"
  exit 0
fi


mp4creator -extract=1 ${VIDNAME} ${TEMP_FILE_DIR}/video.264
mp4creator -extract=2 ${VIDNAME} ${TEMP_FILE_DIR}/audio.aac

MP4Box -fps ${THE_FPS} -cat ${TEMP_FILE_DIR}/video.264 -cat ${TEMP_FILE_DIR}/audio.aac -new ${NEWNAME}.mp4 -inter 0 -keepsys

# Clean up the intermediate stuff
rm -rf ${TEMP_FILE_DIR}

```

Hope this helps someone.

---

### Post by HDave on 2011-01-12
This is awesome...thanks to everyone for the work-around.  But does anyone know why this is necessary?  Why can't I just play the HD MP4 file as it comes out of my camcorder?

---

### Post by wkulecz on 2011-01-12
Where did you find mp4creator and MP4Box Synaptic for 10.04 didn't find anything when searching on either of these.

---

### Post by HDave on 2011-01-12
Another piece of Ubuntu awesomeness is if you type in a command that doesn't exist it'll tell you where to get it.   I entered "mp4creator" and it said:

```

The program 'mp4creator' is currently not installed.  You can install it by typing:
sudo apt-get install mpeg4ip-server
You will have to enable the component called 'multiverse'
```

MP4Box I already had installed.  Another piece of Ubuntu command magic gave me that....  "dlocate MP4Box":

```

gpac: /usr/bin/MP4Box
```

---

