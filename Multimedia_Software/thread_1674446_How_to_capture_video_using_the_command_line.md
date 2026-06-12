---
title: "How to capture video using the command line"
date: 2011-01-23
forum: Multimedia Software
---

### Post by skullmunky on 2011-01-23
I wanted to share this nifty technique I came across for capturing video using the command line.  

The problem: I have a bunch of old VHS tapes (remember those...?) and need to get them digitized.

I have a VCR, and a Dazzle Hollywood DV Bridge which captures video to DV over Firewire (IEEE1394).  

I first tried using Final Cut Pro, but it wouldn't capture, perhaps because it expects a controllable DV camera, and the Dazzle isn't a DVC device.

I then tried my other favorite video editing app, Kdenlive, but it seemed to have the same problem. 

I took a quick stab at the other common editors in the repositories (Kino, Openshot, etc.), but no luck with any of them.

Then I remembered the dvgrab command, and gave that a shot and it worked, giving me a nice .dv file.

However, DV makes pretty big files, which I wanted to compress down to something more manageable.  Since I was going to be digitizing hours and hours of tapes, it would be great if I could compress while capturing.  A little more googling and I had the answer - you can pipe dvgrab directly into ffmpeg!  Here's the command:

```

dvgrab -format dv1 - | ffmpeg -f dv -i - -b 2000k -ab 512k -y output.mov

```

the first part starts the capture, in DV1 format, and outputs it to a pipe file.  usually you give dvgrab a filename, like ```
dvgrab -format dv1 capture.dv
```

the second part does the encoding:

-f dv: use DV format
-i -: input from the pipe 
-b 2000k: video encoding bitrate of 2000k/sec, high quality
-ab 512k: audio encoding bitrate
-y: overwrite file if it exists

I didn't set the codec explicitly, for Quicktime it defaults to MPEG4.

This worked great, capturing a 2-hour tape into a high-quality quicktime around 2GB.  

But I also wanted to be able to view the capture while it was going.  Since I left the field monitors and audio splitters at the office, I had to figure out how to do this in software.  Turns out that the "tee" command does exactly what I needed - the shell never ceases to amaze!  Here's the full command:

```
dvgrab -format dv1 - | tee >(ffmpeg -f dv -i - -b 2000k -ab 512k output.mov) >(playdv --disable-audio --no-mmap)
```

tee uses the ```
>(command)
``` syntax to pipe simultaneously to multiple processes.  The only thing that didn't work was audio playback, which was choppy and introduced errors in the capture file.  I think a little tweaking with the capture rates could fix that.  
:popcorn:

---

### Post by BicyclerBoy on 2011-01-24
FYI
mplayer & ffmpeg will capture directly from webcams, video cameras, capture cards & tuners (analogue & dvb)

So will VLC .

AFAIK Can just "cat" the video stream into a file as well..

---

### Post by skullmunky on 2011-03-02
True, though when I tried those I couldn't get them to work because they only seemed to have options for video4linux, rather than dv1394.  cat works of course but makes a raw file, which is why I wanted to encode on the fly.

---

