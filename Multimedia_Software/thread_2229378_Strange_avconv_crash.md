---
title: "Strange avconv crash"
date: 2014-06-12
forum: Multimedia Software
---

### Post by SimonHGR on 2014-06-12
I have a workaround for this problem, so I don't need ti fixed, but it seems odd enough that I'd like to a) report it, and b) understand it if it's something I'm doing wrong...

I have been using avconv to do screen and audio capture. While using Ubuntu 13.04 I came up with this command:

avconv -f alsa -i pulse -f x11grab -r 30 -s 1280x720 -i :0.0+50,75 -acodec ac3 -vcodec libx264 -pre:0 lossless_ultrafast -threads 0 video-$(date +%F-%H-%M-%S).mkv

to do my grabs.

Somehow, since upgrading to 14.04, this now causes an really bizarre crash. Specifically, if the volume level of the input goes past some point (I have no way to determine what point) it crashes out. I can talk quietly, but if I clap my hands, it dies.

(Yeah, I know you think I'm insane, but really. It's consistent).

The crash report only seems to show up in google searches as having to do with subtitles when converting formats, neither of which is relevant to me. The message is:

Application provided invalid, non monotonically increasing dts to muxer in stream 1: 1405 >= 1400
av_interleaved_write_frame(): Invalid argument

I seem to be able to get around it by adding

-acodec ac3

to the command, and I'm happy with that 

Any thoughts anyone?

---

