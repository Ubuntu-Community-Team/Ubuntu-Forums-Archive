---
title: "Creating and editing DVDs"
date: 2009-01-01
forum: Multimedia Software
---

### Post by ctgbase on 2009-01-01
I am trying to edit some home movies that are on DVD, do some simple changes, and create a new DVD with menus.  I have tried Kino, but that seems to only take dv files.  I have tried DVDRip to convert to dv, but that isn't able to take DVD vob files as input.  I also tried ffmpeg to do the conversion, but I keep getting the error "Unsupported codec (id=86020) for input stream #0.2".  

It seems like I am just grabbing straws here.  Anybody have a suggestion how to accomplish this?
Thanks.

---

### Post by jsedwards on 2009-01-01
That is too funny, because I want to do almost the same thing and I am having no luck.  I got on here to post almost the question 15 seconds after you posted it.

I have 5 DVDs with little short home videos on them and I wanted to combine all 5 into 1 DVD with a menu.

(I originally wanted to edit them, but I have given up on that idea, I would be happy if I could just copy the 5 vobs to 1 DVD that will play on a standalone player.)

I have tried to use ffmpeg and I get a similar error.  I can convert them with mencoder (The videos I have don't have sound):

```
mencoder dvd://1 -dvd-device /media/cdrom0 -of avi -ovc lavc  -nosound -o test.avi
```

But they look horrible (all pixelated) after doing this and the file size is 66 megabytes instead of 330 megabytes.

I also tried to just use mencoder to copy the MPEG2 data like this:

```
mencoder dvd://1 -dvd-device /media/cdrom0 -of avi -ovc copy  -nosound -o test.avi
```

That screws around for a few seconds and then prints:

```
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  4000.0 kbps (500.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
videocodec: framecopy (720x480 24bpp fourcc=10000002)
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
test.avi: Error writing file.1.86fps Trem:   0min   0mb  A-V:0.000 [3891:0]

Exiting...

```

Then I thought perhaps I could just copy the VTS*.* files from each DVD and re-number them on the new DVD, but I can't figure out how to make the VIDEO_TS.* files.

Does anyone know of a way to just extract the MPEG2 video out of the .vob and put it into an .avi file or maybe just an .mpeg file?

---

### Post by secondstage on 2009-01-01
Try DeVeDe to make the DVDs once you have the video files. It will accept almost all formats. You can make menus and the such also. If you have a cmoputer with multiple cores (dual, quad ,etc), make sure to click on the Advance Options, and check to box next to "Use Optimizations for multicore CPUs". Good Luck.

EDIT: If you plan to make a DVD, choose the Video DVD option upon opening. Also, DeVeDe will make an ISO file. This is a disk image. you can burn it to a DVD by double-clicking. This will open Ubuntu's built-in disk burning utility.

---

### Post by jsedwards on 2009-01-01
This line seems to work better:

```
mencoder -vf harddup -vf-add smartblur=.6:-.5:0,unsharp=l5x5:.8:c5x5:.4 -xvidencopts fixed_quant=4:profile=dxnhtntsc -ovc xvid -nosound /work/dvd/test/VIDEO_TS/VTS_03_1.VOB -o test.avi
```

It took a long time to run (almost 3 times longer than the time it takes to play the video) and the output file is about 20% larger than the .vob file, but I think it might look better than the original (?).

I got that line from the web page: [http://bbs.archlinux.org/viewtopic.php?id=23889](http://bbs.archlinux.org/viewtopic.php?id=23889) and it had the following two options for sound that I didn't use:

```
-lameopts cbr:br=128:aq=0:vol=1 -oac mp3lame
```

---

### Post by Heeter on 2009-01-01
I use Devede as well, with no issues.

I create an iso image at the end and write to my dvd's by just right clicking on the image afterwards.

Hope this helps.

Heeter

---

### Post by ctgbase on 2009-01-04
I am trying the mencode command that was suggested above, which will create an avi file.  Then I will try DeVeDe to create my DVD.  However, I don't think this is going to give me the ability to edit the video.  I want to select portions of the video I already have on multiple DVDs, and create a single DVD with just those portions.  Is there a better way to do this?

---

