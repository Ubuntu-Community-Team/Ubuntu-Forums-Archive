---
title: "avconv problems for a beginner!"
date: 2013-11-13
forum: Multimedia Software
---

### Post by chrisscott100 on 2013-11-13
I am using avconv to stream a video to a Raspberry Pi video wall using the instructions at [www.piwall.co.uk](www.piwall.co.uk)

They provide a command to send the video over a local network using the following command:

[COLOR=#000000][FONT=Arial]avconv -re -i movie.avi -vcodec copy -f avi -an udp://239.0.1.23:1234

The command works fine for an .avi file with an mpeg4 codec (Big Bucks Bunny to be precise!)

Now I am a bit of a novice to the use of avconv but after many hours of looking over the help pages I am stuck.  I have a load of other video I want to show which I generated using Handbrake so is .m4v or .mp4 with an x264 codec (mp4 is also available).

When I run the command 
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]avconv -re -i movie.**mp4** -vcodec copy -f avi -an udp://239.0.1.23:1234

I get a load of error messages and avconv stops.  The first few messages are:

[/FONT][/COLOR][mov,mp4,m4a,3gp,3g2,mj2 @ 0x885baa0] multiple edit list entries, a/v desync might occur, patch welcome 
 [h264 @ 0x8860400] reference picture missing during reorder 

 [h264 @ 0x8860400] reference count overflow 
 [h264 @ 0x8860400] decode_slice_header error 

I can provide more, it ends up being a few pages.

Just wondered if anyone knows what I am doing wrong.  Can avconv not cope with mp4?

Many  thanks

[COLOR=#000000][FONT=Arial][/FONT][/COLOR]

---

### Post by TheFu on 2013-11-13
Original: avconv -re -i movie.mp4 -vcodec copy -f avi -an udp://239.0.1.23:1234
Try:   avconv -re -i movie.mp4 -vcodec copy -f mp4 -an udp://239.0.1.23:1234

See the diff?

I have not tested this.  the format may need to be h.264 or some other codec. I dunno.

---

### Post by chrisscott100 on 2013-11-15
Thanks, got some improvement, however, still get a message below.

The file I am using is a .mp4 and MediaCoder says that the codec for this one is "avc1".  Any ideas?

scott@scotts-laptop:~$ avconv -re -i movie.mp4 -vcodec copy -f mp4 -an udp://239.0.1.23:1234
avconv version 0.8.8-4:0.8.8-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Oct 22 2013 12:35:42 with gcc 4.6.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'movie.mp4':
  Metadata:
    major_brand     : M4V 
    minor_version   : 0
    compatible_brands: M4V M4A mp42isom
  Duration: 00:25:15.42, start: 0.000000, bitrate: 3493 kb/s
    Stream #0.0(und): Video: h264 (High), yuv420p, 1920x1080, 3227 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 253 kb/s
[mp4 @ 0x95709c0] muxer does not support non seekable output
Output #0, mp4, to 'udp://239.0.1.23:1234':
  Metadata:
    major_brand     : M4V 
    minor_version   : 0
    compatible_brands: M4V M4A mp42isom
    encoder         : Lavf53.21.1
    Stream #0.0(und): Video: ![0][0][0] / 0x0021, yuv420p, 1920x1080, q=2-31, 3227 kb/s, 90k tbn, 90k tbc
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
Could not write header for output file #0 (incorrect codec parameters ?)

---

### Post by TheFu on 2013-11-15
Well - since you asked for "any ideas" ... 
What container does avc1 usually have? I don't know, but I put everything into an MKV container since it is not fussy at all, but many devices ARE extremely fussy.  Fortunately, my media playback devices are not fussy - I was tired dealing with 1-trick-pony devices years ago.

The entire M4V/M4A stuff makes me want to gag.

It is an idea, just probably not too helpful to this situation.

---

### Post by chrisscott100 on 2013-11-16
Thanks, I have methods of transcoding into all manner of different  formats but would rather not have to modify it each time.  The AVC1  codec arrived after a realplayer download from YouTube

I just wondered what the error messages mean and what would be a useful thing to do to get round them?

---

### Post by TheFu on 2013-11-16
I think the error message is saying that you cannot put an avc1 encoded stream into an MP4 container. That is why I suggested a different container that I knew would work.

Please still use realplayer?  Google a little to see how that company screwed almost everyone on the internet without asking in the 1990s. At least that is my recollection, so I could be wrong.

---

