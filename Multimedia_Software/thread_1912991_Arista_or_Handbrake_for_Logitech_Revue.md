---
title: "Arista or Handbrake for Logitech Revue"
date: 2012-01-21
forum: Multimedia Software
---

### Post by shanepardue on 2012-01-21
I've always used Handbrake for transcoding videos for use with my Logitech Revue, but I recently heard about Arista (via Linux Outlaws). Since I'm always looking for better video quality, I thought I'd check it out.

Can someone to speak to the differences between Handbrake and Arista or maybe even specific settings that might make for the best transcoding on a Logitech Revue? I've been just using the "high quality" preset on Handbrake.

Thanks!

---

### Post by lukeiamyourfather on 2012-01-22
Both are just a front end for other utilities like FFmpeg so they are both capable of the same quality. The quality will be dependent on the encoder settings which are under the control of the user.

Personally I'd setup a shell script or Python script to encode the media with FFmpeg directly. It would take a few hours to figure out and setup but then you could encode new stuff very easily by just running a single command from the terminal instead of fiddling around with a GUI like Handbrake or Arista.

---

### Post by ben2talk on 2012-03-08
The problem here is that it would take so much time to set up a script - which would probably only work for a single kind of job... what happens if you just wanna drop an odd wmv file (maybe 640x480) or an flv (maybe 540x480) and choose some kind of decent output for streaming to a 1080p widescreen TV?

I'm using Arista - flexible, and simple drag 'n drop - and will be looking at Handbrake again to see how well it has improved since I last played with it.

After all, aren't they simply a more complex set of advanced scripts?

---

### Post by JohnAStebbins on 2012-03-08
> **lukeiamyourfather said:**
> Both are just a front end for other utilities like FFmpeg...
Not true.  I can't speak for Arista, but HandBrake is not just a front end to ffmpeg.  HandBrake does not make calls to external commands at all.  It is directly linked to a collection of video and audio decoding, encoding, and muxing libraries.  libav is one of them.  Others are libswscale, libx264, libfaac, liba52, libdca, libass, libbluray, libdvdread, libdvdnav, libmkv, libmp3lame, libmp4v2, libmpeg2, libtheora, libsamplerate, and libvorbis.  HandBrake interacts with all these libraries directly and not through another tool like ffmpeg.  Doing things this way offers greater control and flexibility to the developers. The core HandBrake library libhb sees every packet and routes it from demuxer to decoder, to filters, to renderer, to encoder to muxer.  libhb implements it's own track synchronization logic, demuxers for several file formats, several video filters, subtitle rendering, audio downmixing and a variety of other things.
[quote=ben2talk]
After all, aren't they simply a more complex set of advanced scripts?
[/quote]
See above.  There are no scripts involved in HandBrake's operation.

---

