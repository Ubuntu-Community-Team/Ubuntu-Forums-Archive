---
title: "record tv capture card to file"
date: 2006-03-24
forum: Multimedia &amp; Video
---

### Post by Michael Matthews on 2006-03-24
I have an old ATI tv card with bt. tvtime, zapping work great for viewing.
I would like to record to a file with same quality.  Tv signal is us-cable.
Sound comes in via sound card line input NOT from card.

Using ffmpeg:

/usr/bin/ffmpeg  -r 24 -t 30 -s 720x480 -vd /dev/video0 -ad /dev/dsp -tvstd NTSC  -deinterlace tvout.avi

Quality is decent but not as good as tvtime. Image is little blotchy. No sound.
I do not know enough about video capture, ffmpeg and find documentation to be video expert level and not very helpful.

Anyone have any ideas how I get some sound or improve quality? Any capture card ffmpeg howtos more 

There is a very specific transcode example for this operation but apparently transcode pkg is broken on ubuntu and I have problem building from source. transcode build does not like ubuntu libavcodec (ffmpeg lib). 

Any other alternatives for tv video capture?

thanks

---

### Post by pooler on 2006-03-24
I use xawtv, but it doesn't have many video codecs. You could also try xdtv...

---

### Post by Michael Matthews on 2006-03-30
And the answer is:  use mencoder

mencoder -tv driver=v4l2:device=/dev/video0:fps=29.97:norm=ntsc:width=720:height=480:adevice=/dev/dsp:amode=1  \
  -ovc lavc -oac lavc -lavcopts vcodec=mpeg4:vbitrate=900:acodec=mp3:abitrate=256 \
  -o output.avi tv://1 5

output is better, not perfect or as good tvtime direct off card. Still no sound.

mencoder docs are coherent and there a few howtos available on the web.

Anyone have any ideas how to get sound from mixer? Tweak quality?

thanks in advance...

---

