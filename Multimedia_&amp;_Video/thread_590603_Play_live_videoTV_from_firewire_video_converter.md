---
title: "Play live video/TV from firewire video converter"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by stuporglue on 2007-10-24
I have a Canopus video converter, which takes in composite video and spits out firewire. When I had  a Mac, I could hook up a VCR to my computer through the converter, and watch TV on my computer. I'd like to do the same thing now on Ubuntu. 

Kino lets me watch the video, but doesn't do full screen that I can tell. I don't need to record it, just want to watch it llive. 

Here's the converter. [http://www.canopus.com/products/ADVC110/index.php](http://www.canopus.com/products/ADVC110/index.php)

Thanks, 
Michael

---

### Post by aprete on 2007-12-07
Michael,

I have the same question.  I have a Canopus ADVC-50 and I want to do the same thing.  In Window$ the DVD player software that came bundled with my DVD burner, Ulead DVD Player, can play DVD's, video files, or directly from the capture card.

Under Ubuntu (Gutsy) my preferred player is VLC.  It has a fullscreen option.  It also has an option to play from the capture card but I still haven't figured out how to do it.  I'm guessing I have to play with the device name in VLC.  It defaults to /dev/video but I suspect that's for a video card/capture card combo.

Hope this helps a little and if you get it to work, help me back.

Al

---

### Post by stuporglue on 2007-12-07
aprete, I actually did get it to work, and I think it was with VLC, or possibly ffmpeg.  I gave up on it because what I really wanted was to play the Wii on my computer monitor (which is bigger than our tiny 12 inch TV), and the process induced about a 3-5 second lag which made it impossible to play games. 

It would've worked fine for watching live TV though. :-) 

I might not get to it till next week, but I'll see if I can't figure it out again. 

Thanks, 
Michael

---

### Post by aprete on 2007-12-11
Michael,

I got a little further with it, but I'm still not quite there.

First, I have to enter the following command:

sudo chmod 666 /dev/raw1394

I have to do this every time I boot.  Then I enter vlc from the command line:

vlc dv/rawdv:///dev/raw1394

This gives me video and audio, but both the video and audio are garbled.  I think I saw somewhere in these forums that this is a bug in the latest version of vlc.

I'm able to watch with kino, but like you say, it's not fullscreen.  And to get sound in kino, I have to start capturing, which means I'll have a large file on my hard drive pretty fast.

Al

---

### Post by aprete on 2008-02-07
I got it to work.

After executing the chmod command above, I do it like this:

dvgrab - | vlc - --no-sub-autodetect-file :demux=rawdv

This pipes the output of dvgrab into vlc.  This didn't work before because of a bug in dvgrab 3.0 that prevented it from streaming to stdout.  The author of dvgrab recently posted release 3.1; I downloaded it and installed it and it works now.  There's no package yet for dvgrab 3.1, so I had to compile it.

---

