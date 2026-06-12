---
title: "GStreamer queue issue"
date: 2010-03-22
forum: Multimedia Software
---

### Post by jasonme on 2010-03-22
Dear all,

I was trying to use GStreamer(0.10.26) to play a mpg file under the latest version of Ubuntu. 

I used:
gst-launch filesrc location=test.mpg ! mpegdemux ! mpeg2dec ! ffmpegcolorspace ! ximagesink

The video can be perfectly played. Then I tried to use queue to make audio run as the manual of gst-launch told me:
gst-launch filesrc location=test.mpg ! mpegdemux name=demuxer demuxer. ! queue ! mpeg2dec ! ffmpegcolorspace ! ximagesink demuxer. ! queue ! mad ! audioconvert ! audioresample ! alsasink

Then GStreamer told me queue can't link with the decoder, prompting:
WARNING: erroneous pipeline: could not link queue0 to mpeg2dec0.

I wonder why this is not working as the manual said. I suppose it is a pretty normal way to play video with audio together. Or Could I have done something wrong to make GStreamer crazy? If I did, please let me know where I did wrong, so I can make it work. 

Thank you very much for all the replies.

---

### Post by jasonme on 2010-03-22
Anyone in here? Thanks!

---

### Post by pranshu24 on 2011-08-05
Well I had also been facing the same problem and you ll be surprised to hear that it was mere fluke that I succeeded in playing the audio and video simultaneously.

gst-launch filesrc location=<path> mpegdemux name=demuxer demuxer. ! mpeg2dec ! queue ! ffmpegcolorspace ! sdlvideosink demuxer. ! mad ! queue ! audioconvert ! audioresample ! alsasink

Though I understand that** queue should have occured before mpeg2dec **but it worked when I when placed it as above.

The explanation I could give to this as follows:
when I tried and checked the plugins using: gst-inspect-0.10 mpegdemux 
I discovered that gst-plugins were of the type UGLY i.e not checked and verified properly.This might be a reason for this confusion.

Moreover .avi and quicktime files were running smoothly as their plugins were of the type GOOD!

---

### Post by cwurld on 2012-02-26
Thanks! Your post was a lifesaver. I have no idea how I would have figured that out.

---

