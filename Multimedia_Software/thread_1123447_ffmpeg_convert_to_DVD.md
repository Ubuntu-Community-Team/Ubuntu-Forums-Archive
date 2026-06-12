---
title: "ffmpeg convert to DVD"
date: 2009-04-12
forum: Multimedia Software
---

### Post by Geffers on 2009-04-12
I have some movie files that I would like to convert (using ffmpeg) for burning to a DVD so that I can play them via a DVD player onto my older CRT TV.

The video details of the files involved show the following;

> .asf extension 
Type ASF video
MIME Type video/x-ms-asf

Video dimensions 512x288
Codec MS Windows Media 9
Framerate 25 fps
Bitrate (No details)

Audio Codec WMA Version 8
Channels Stereo
Sample Rate 48000 Hz
Bitrate (No details)


My initial simple attempt (ffmpeg -i file.asf file.mpg) resulted in a poor quality mpeg1 video so I am wondering if I need to use different codecs

Geffers

---

### Post by lovinglinux on 2009-04-12
You could use [WinFF](http://code.google.com/p/winff/), which is basically a GUI for ffmpeg and provides easy presets. If you want to use the command-line, try installing [WinFF](http://code.google.com/p/winff/) then click "Edit >>> Presets". It will display the preset commands, so you can copy them to use in the terminal.

---

### Post by lovinglinux on 2009-04-12
continuing from the previous post:

This is an example I took from WinFF "NTSC DVD HQ (16:9)" preset:

```
ffmpeg -i original.avi -target ntsc-dvd -r 29.97 -s 720x480 -aspect 16:9 -b 8000k -g 12 -mbd rd -flags +trell -mv0 -cmp -subcmp 2 output.mpeg
```

The result is very good.

---

### Post by Geffers on 2009-04-12
> **lovinglinux said:**
> You could use [WinFF](http://code.google.com/p/winff/), which is basically a GUI for ffmpeg and provides easy presets. If you want to use the command-line, try installing [WinFF](http://code.google.com/p/winff/) then click "Edit >>> Presets". It will display the preset commands, so you can copy them to use in the terminal.

That looks interesting, the best way to learn a program is via the command line.

Thanks.

Geffers

---

### Post by lovinglinux on 2009-04-12
I forgot to mention that you can also run the man command to see an application  command-line options:

```
man ffmpeg
```

It's not easy as copying a preset from WinFF, but if you really want to learn the command options, then the man page is a good place to start.

---

### Post by FakeOutdoorsman on 2009-04-12
Since your input video is 25 fps, or PAL, you may want to keep the same frame rate for your output as well:
```
ffmpeg -i input.asf -target pal-dvd output.mpg
```
Now you can use this file to make a DVD:
```
dvdauthor -t -o youroutputdirectory -f output.mpg
dvdauthor -o youroutputdirectory -T
mkisofs -dvd-video -o dvdimage.iso youroutputdirectory
growisofs -speed=4 -dvd-compat -Z /dev/dvd=dvdimage.iso
```
You can also verify by comparing MD5SUMs from the ISO and DVD.  First the ISO:
```
md5sum dvdimage.iso
```
Now the DVD:
```
echo $(( $(ls -l dvdimage.iso | awk '{ print $5 }') / 2048 ))
```
This gives a number, for example: 828368.  This gets used in the next command (this can take a while):
```
dd if=/dev/dvd bs=2048 count=828368 | md5sum
```

---

