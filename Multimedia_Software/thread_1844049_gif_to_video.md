---
title: "gif to video"
date: 2011-09-14
forum: Multimedia Software
---

### Post by amulet on 2011-09-14
Hello.

Please can somebody help me with step by step convert an animated .gif  into a video format? 
The 24 frames are in a folder (/spinners/gifs/) named spin-1.gif, spin-2.gif,spin-3.gif etc. 

I have come across this command: 

convert test.gif test%05d.jpg
ffmpeg -r 25 -i *.jpg -y -an test.avi

But I don't know how to apply it.  :redface:

Many thanks

---

### Post by dniMretsaM on 2011-09-14
> **amulet said:**
> Hello.

Please can somebody help me with step by step convert an animated .gif  into a video format? 
The 24 frames are in a folder (/spinners/gifs/) named spin-1.gif, spin-2.gif,spin-3.gif etc. 

I have come across this command: 

convert test.gif test%05d.jpg
ffmpeg -r 25 -i *.jpg -y -an test.avi

But I don't know how to apply it.  :redface:

Many thanks

You would need to open Terminal and run this:

```
ffmpeg -i path/to/gif/filename.gif {options} filename.ogv
```Replace {options} with anything you want to specify for the conversion (there might be some specific ones you need for image-to-video, not sure). And the output can be any video format, not just .ogv. Hope that helps!

---

### Post by FakeOutdoorsman on 2011-09-14
How long do you want the output to be? For example, if you want it to be 5 seconds long, and you have 25 frames, then you will need to tell ffmpeg to show each frame for 0.2 seconds. Example:
```
ffmpeg -r 0.2 -i test%05d.jpg -r 25 -qscale 4 test.mpg
```
FFmpeg doesn't accept *, but it understands that test%05d.jpg means test00001.jpg to test00025.jpg. What the other junk means:
[list]
[*]**-r 0.2** - your input frame rate (any option before the input generally applies to the input).
[*]**-r 25 **- your output frame rate (any option after the input generally applies to the output).
[*]**-qscale 4** - a "rate control" option. A lower number is a higher quality output, but a larger file size. Think of it as a quality number.
[/list]

**Edit:** I missed dniMretsaM's reply. I guess I shouldn't open a reply to a thread and then come back to it 30 minutes later. Also, I missed that you already had your gif too, and FFmpeg can use that as an input too, as dniMretsaM displayed.

---

### Post by amulet on 2011-09-14
> **FakeOutdoorsman said:**
> How long do you want the output to be? For example, if you want it to be 5 seconds long, and you have 25 frames, then you will need to tell ffmpeg to show each frame for 0.2 seconds. Example:
ffmpeg -r 0.2 -i test%05d.jpg -r 25 -qscale 4 test.mpg[/code]


That's done it, thanks FakeOutdoorsman.  The main error I was making all along was in the file numbering.  My files were numbered  0001,0002 etc (4 digits), and when I changed the bit of code ```
05d
``` to ```
04d
```, the command flew! And thanks for the tip about the length of the output video.  :P

And thanks dniMretsaM for your response too.

---

