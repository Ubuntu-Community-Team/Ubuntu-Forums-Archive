---
title: "Encoding Video for Emerson / Phillps / Funai LF391EM4 TV set"
date: 2014-05-31
forum: Multimedia Software
---

### Post by timothylegg on 2014-05-31
After tinkering around for a few hours, I figured out a way to encode video for the LF391EM4 television set designed by Funai and sold as Emerson or Phillips.

The TV set specifies MJPEG 320x240 at 30FPS.  It states that it expects a .avi file extension, but I haven't tested this limitation.

```
mencoder inputfile.mp4 -o output.avi -ovc lavc -lavcopts vcodec=mjpeg -oac pcm -vf scale=320:240
```

I found the documentation and usage for mencoder to be a confusing mess.  Most of the time spent was trying to understand the parameters of the tool.  I included the descriptions below to aid novices to the structure of this tools parameters.


[LIST]
[*]The first parameter is the input file. 
[*]**-o** is the output filename.  Ensure this ends with .avi as per manufacturer's specification. 
[*]**-ovc** is the output video codec. **lavc** is selected so the libavcodec library is used. 
[*]**-lavcopts** sets the options for libavcodec.  Within this, vcodec will be assigned
[LIST]
[*]**vcodec=mjpeg** to assign the correct codec. 
[/LIST]
  
[*]**-oac** is the output audio codec and it is set to **pcm** 
[*]**-vf** is for video filters, amongst those, the scale tool will be applied
[LIST]
[*]**scale=320:240** 
[/LIST]
     
[/LIST]

Please comment below if you have improvements to suggest for future viewers.  Have fun and hope this helps.

Timothy D. Legg

---

### Post by ajgreeny on 2014-05-31
Just out of interest (mine, at any rate) try the command
```
avconv -i infile.mp4 -vcodec mpeg2video -q 6 -ab 128k outfile.mpg
```
which is what I use to convert mp4 files from get-iplayer to mpeg-2 files for playing on usb thumb drives on my TVs here in the UK.

You may need to deal with the resolution which in your case is lower than I use, and you may also need to use the .avi filetype in the outfile.avi name instead of outfile.mpg.

---

### Post by timothylegg on 2014-08-20
Sorry about this, but I just upgraded to 14.04 LTS and neither one of these work any more.  Gives unclear error messages.  They need a technical writer to translate such dialog into statements with actual meaning.  Unsupported AVPixelFormat 53?  What the hell is that supposed to mean?

You never really know what's broken on an upgrade until you make that leap up.  Annoying.  I wish the Ubuntu people would test these things out before releasing their new distributions, especially since they are competing against heavily funded competition.  Stuff like this really makes us look like a bunch of goofballs.

---

### Post by coldraven on 2014-08-21
> **timothylegg said:**
> Sorry about this, but I just upgraded to 14.04 LTS and neither one of these work any more.  Gives unclear error messages.  They need a technical writer to translate such dialog into statements with actual meaning.  Unsupported AVPixelFormat 53?  What the hell is that supposed to mean?

You never really know what's broken on an upgrade until you make that leap up.  Annoying.  I wish the Ubuntu people would test these things out before releasing their new distributions, especially since they are competing against heavily funded competition.  Stuff like this really makes us look like a bunch of goofballs.

I'm guessing that you will need to install the restricted extras 
[http://en.wikipedia.org/wiki/Ubuntu-restricted-extras](http://en.wikipedia.org/wiki/Ubuntu-restricted-extras)
```
***sudo apt-get install ubuntu-restricted-extras ***
```

---

### Post by timothylegg on 2015-03-16
> **coldraven said:**
> I'm guessing that you will need to install the restricted extras 
[http://en.wikipedia.org/wiki/Ubuntu-restricted-extras](http://en.wikipedia.org/wiki/Ubuntu-restricted-extras)
```
***sudo apt-get install ubuntu-restricted-extras ***
```

Did that install.  Maybe this version of mencoder is broken.  It seems that av converters like to exist on a works-today broken-tomorrow sort of existence.  I might try this again when a new version of Ubuntu comes out. 

Unsupported AVPixelFormat 53
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
[swscaler @ 0x7f0325e4d640]BICUBIC scaler, from yuv420p to yuv420p using MMXEXT
videocodec: libavcodec (320x240 fourcc=47504a4d [MJPG])
[mjpeg @ 0x7f032534fa20]Specified pix_fmt is not supported
Could not open codec.
FATAL: Cannot initialize video driver.


Exiting...

---

### Post by timothylegg on 2015-03-16
> **ajgreeny said:**
> Just out of interest (mine, at any rate) try the command
```
avconv -i infile.mp4 -vcodec mpeg2video -q 6 -ab 128k outfile.mpg
```
which is what I use to convert mp4 files from get-iplayer to mpeg-2 files for playing on usb thumb drives on my TVs here in the UK.

You may need to deal with the resolution which in your case is lower than I use, and you may also need to use the .avi filetype in the outfile.avi name instead of outfile.mpg.

Television says format is not supported.

---

