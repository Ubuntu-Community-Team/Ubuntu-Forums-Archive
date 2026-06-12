---
title: "Streaming with vlc from mms: no sound"
date: 2010-12-07
forum: Multimedia Software
---

### Post by Mariane on 2010-12-07
Hi, 

I'm trying to save the videos from this page:
[http://kemst.hi.is/gods_and_goddesses/](http://kemst.hi.is/gods_and_goddesses/)
(For my personal use, just because they won't stay long online)

DownThemAll does not function. 

I followed one of the links and viewed the page source, I found the address:
mms://media.rhi.hi.is/emissionNoSilverLight/?r=527750db-c5a5-49ef-87f2-0632110f7a22&t=

Then I tried using vlc to stream and transcode it using the instructions there:
[http://www.stufinnis.co.uk/vlcautorecord.html](http://www.stufinnis.co.uk/vlcautorecord.html)

The first try gave me a video file without sound. After several attemps I gave up - for now - on having sound + video and I streamed again, to mp3 format. This gave me a sound file of very bad quality. 

Now I have a video of reasonable quality with no sound and a bad sound file. It's better than nothing but it's not what I wanted  :lol: . 

All suggestions really very very welcome. Possible suggestions include:
- What settings should I use to get better sound
- Is there a way to combine offline a video and a sound file and to synchronise them precisely?
- Are there any settings at all which would give me a file with video AND sound?

Please help

Mariane

---

### Post by ron999 on 2010-12-07
Hi
With VLC > View
Tick the 'Advanced Controls' option.
This will then show some extra buttons.
The [COLOR="Red"]RED[/COLOR] button is for 'record'.

So play the file from the mms link and click the [COLOR="Red"]RED[/COLOR] button.
Use Media > Open Network Stream > Network
Or Media > Open Location From Clipboard

The file is saved something like this:-
> [SIZE="1"]/home/ron/Videos/vlc-record-2010-12-07-14h39m57s-mms:__media.rhi.hi.is_emissionNoSilverLight_?r=527750db-c5a5-49ef-87f2-0632110f7a22&t=-.asf[/SIZE]

The asf file uses WMA2 audio and WMV3 video codecs.

If you're not happy with an asf file it's very easy to losslessly convert it to a wmv file using a command like this:-

```
ffmpeg -i  ***filename***  -vcodec copy -acodec copy output.wmv
```

Test the method by recording just a few minutes of the video first.

Here is my result:-

> General
Complete name                    : /home/ron/output.wmv
Format                           : Windows Media
File size                        : 4.27 MiB
Duration                         : 1mn 53s
Overall bit rate                 : 316 Kbps
Maximum Overall bit rate         : 64.0 Kbps
Encoded date                     : UTC 1970-01-01 00:00:00.000
WM/EncodingSettings              : Lavf52.84.0

Video
ID                               : 1
Format                           : VC-1
Format profile                   : MP
Codec ID                         : WMV3
Codec ID/Info                    : Windows Media Video 9
Codec ID/Hint                    : WMV3
Duration                         : 1mn 53s
Bit rate                         : 230 Kbps
Width                            : 640 pixels
Height                           : 480 pixels
Display aspect ratio             : 4:3
Frame rate                       : 14.926 fps
Resolution                       : 8 bits
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.050
Stream size                      : 3.11 MiB (73%)

Audio
ID                               : 2
Format                           : WMA
Format version                   : Version 2
Codec ID                         : 161
Codec ID/Info                    : Windows Media Audio
Description of the codec         : Windows Media Audio V8
Duration                         : 1mn 53s
Bit rate                         : 64.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Resolution                       : 16 bits
Stream size                      : 887 KiB (20%)



---

### Post by Mariane on 2010-12-07
It works it works it works it works!
Thanks ever so much! 
The file is saved if I stop just by clicking on the stop button and then on the top right 'x'

Complete procedure:
Do as ron999 says to get the advanced control buttons. 
In the "media" menu select "Open Network Stream"
This opens a new window. 
Paste the address beginning with mms:// in the upper text field
Then click on the "Play" button. 

--- WAIT --- WAIT --- WAIT ---

At this point, don't think it has failed because nothing is happening.
vlc hasn't crashed, it is just taking a while.
When the video finally appears click on the little red circle to record.


Mariane

---

### Post by ron999 on 2010-12-07
> **Mariane said:**
> I mean, will the file be saved if I just click on the stop button and then on the top right 'x'?


Yes, and just the 'X' will probably be OK.

---

### Post by Mariane on 2010-12-07
Ron999, may you be blessed to the seventh generation :popcorn: 

Mariane

---

