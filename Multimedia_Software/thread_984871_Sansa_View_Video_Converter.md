---
title: "Sansa View Video Converter"
date: 2008-11-17
forum: Multimedia Software
---

### Post by Cheiron on 2008-11-17
I recently purchased a 'Sansa View' media player, and was disappointed to discover that the device required a very specific kind of video format in order to work properly.

After looking around the internet for a while, and reading some man pages, I have created a Ruby script that uses FFMpeg to convert a given video to a 320x240 letterboxed .mp4 video file that can be played on a Sansa View.

I figured that, since there are probably a lot of other people with Sansa View players that would like to use videos, I should share. I have included the script, and a deb package that installs the needed dependancies and places the script in /usr/bin so that you can simply type
```
sansaview-convert original_video converted_video
```
from anywhere on the system and get the desired result.

If anyone finds any bugs, please let me know.

Here is the script:
```

#!/usr/bin/ruby

def usage
	puts "Usage: sansa-convert infile outfile [video-bitrate [audio-bitrate]]"
end

if ARGV.length == 0
	usage
	exit -1
end

fn = ARGV[0]
if not File.exists? fn
	usage
	exit -1
end

newFn = ARGV[1]
if newFn[-4..-1] != ".mp4"
	puts "Output file must be an .mp4 file, appending .mp4 filename extension." 
	newFn += ".mp4"
end

vbr = ARGV[2] || 256

abr = ARGV[3] || 96


#current resolution
hres = `ffmpeg -i '#{fn}' 2>&1 | grep Video: | grep ....x -o`[0.. -2].to_i
vres = `ffmpeg -i '#{fn}' 2>&1 | grep Video: | grep x.... -o`[1.. -1].to_i

#calculate new resolution
scaleRatio = hres / 320.0
hres = 320
vres /= scaleRatio
vres = vres.to_i

blackBars = 240 - vres
vres += 1 if vres % 2 != 0
topPad = blackBars / 2

if topPad % 2 == 0
	bottomPad = topPad
else
	bottomPad = topPad - 1
	topPad = topPad + 1
end

#most of this command courtesy of: http://ubuntuforums.org/showthread.php?t=892971
command = "ffmpeg -i '#{ARGV[0]}' -r 29.97 -vcodec libxvid -b #{vbr}k -acodec libfaac -ab #{abr}k -bufsize 4M -qmax 51 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -ar 44100 -g 300 -s 320x#{vres} -padtop #{topPad} -padbottom #{bottomPad} -ac 2 -f mp4 -y '#{newFn}'"

puts "Command: #{command}"
`#{command}`

```

And the deb file:

---

### Post by Mahinva on 2008-12-20
Would anyone be able to provide a usage example for this script? I'm having trouble figuring it out in Terminal. I think I'm getting stuck on the "[video-bitrate [audio-bitrate]]" part as stated here:

```
def usage
	puts "Usage: sansa-convert infile outfile [video-bitrate [audio-bitrate]]"
end

```

If I look at the desired video's properties, I see that the audio bitrate is 192 kbps and I suppose that is what I should enter into the second bracketed field. However, the video bitrate is shown as N/A. The file is using a DivX MPEG-4 Version 5 codec and is an .avi. Resolution is 528 x 288.

---

### Post by Cheiron on 2008-12-22
I probably should clarify, incase this confuses anyone, that the video and audio bitrates are the bitrates that you would like the resulting video to use, not what the source media file was.

Square brackets in a command's usage specification traditionally indicate an optional value. If you don't enter a value, the default is 256 for video and 96 for audio. I tried to select sane defaults that will strike a balance between quality and size, but a value of 512 for video should be about as high as you'll need to go to get really good quality given the small resolution of the resulting video.

So an example of the programme in use would be:
```
sansa-convert video.avi video-sansa.avi 128 512
```

---

### Post by Miles_Prower on 2009-01-02
Has anyone used this on a sansa e250r? I've run it on a couple of .avi s, and after placing the output mp4s in the sansa's videos directory, the sansa's file browser still suggests that there is no playable video.

---

### Post by Cheiron on 2009-01-02
Sorry, but I think that the older e2x0 models had a somewhat different (and more difficult) video format. I used to have an e280, and from what I could tell at the time, there might have been a way to convert videos to it, but it would have to be in black and white, since the codec didn't support rgb->bgr value switching like it needed - the colours would be wrong otherwise.

---

### Post by awells527 on 2009-01-27
I seem to be having a problem.

```
/home/andrew/bin/sansaview-convert:37:in `to_int': Infinity (FloatDomainError)
	from /home/andrew/bin/sansaview-convert:37
```

If I comment out line 37, the following command gets outputted, and it obviously fails.  I'm thinking that it's dividing by zero somewhere.

```
Command: ffmpeg -i 'movie.mpg' -r 29.97 -vcodec libxvid -b 256k -acodec libfaac -ab 96k -bufsize 4M -qmax 51 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -ar 44100 -g 300 -s 320xInfinity -padtop -Infinity -padbottom -Infinity -ac 2 -f mp4 -y 'movie.mp4'
```

I will try to see what the problem is, but I can't code in Ruby worth a darn. ;)

---

### Post by awells527 on 2009-01-27
Found the problem - when it finds the current resolution on lines 30-31, the grep command was a little off, and when it was passed through '.to_i', it resolved to 0, which caused the divide by 0, which caused 'Infinity' to appear in the final command.

My solution might be more like a workaround, but here is what I did:

`ffmpeg -i '#{fn}' 2>&1 | grep Video:' returned:

```
Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 9800 kb/s, 59.94 tb(r)
```

...so `ffmpeg -i '#{fn}' 2>&1 | grep Video: | grep "...x" -o` returned:

```
.0[0x
 720x
```

...which caused the problem.  A similar problem existed with calculating the vres as well.  I tweaked the grep commands to find the proper resolution.

```
#current resolution
hres = `ffmpeg -i '#{fn}' 2>&1 | grep Video: | grep ", ...x" -o | grep ...x -o`[0.. -2].to_i
vres = `ffmpeg -i '#{fn}' 2>&1 | grep Video: | grep "x... " -o | grep x... -o`[1.. -1].to_i
```

This worked for my specific video stream, but this is probably not a fix-all.

---

