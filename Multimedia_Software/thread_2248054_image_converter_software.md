---
title: "image converter software?"
date: 2014-10-12
forum: Multimedia Software
---

### Post by jesse21 on 2014-10-12
is there anything out there that would help me convert a .gif file to another type? .mkv? .wmv? .avi? So i can use the animation as an animated background? THANKS !!

J

---

### Post by ibjsb4 on 2014-10-12
What I believe your asking about is transcoding.  Something I do not do, but it looks like VLC and ffmpeg can.  Maybe the place to start looking.  Good luck  :)

---

### Post by Rob Sayer on 2014-10-12
1: search "ubuntu convert gif".  A quick look found a bunch of things that involved using ffmpeg or avconv in CLI mode.

2: Both ffmpeg and avconv are in the official repos.  Don't use 3rd party non tested repos unless you absolutely have to, and you shouldn't have to here.

---

### Post by SeijiSensei on 2014-10-13
If you are talking about converting an animated GIF to a video, I don't think that's really possible unless all the frames are intact.  Most animated GIFs consist of a background layer with the remaining frames stored as differences from the original.  Here's an example:

[img]http://www.takinganimeseriously.com/images/avatars/summer-wars-daisuke-fan.gif[/img]

Open that image in the GIMP (from the Ubuntu repositories), then hit Ctrl-L to display the "Layers" dialog.  You'll see there are nine frames in this image, but only the initial background image is complete.  The other eight frames contain only those pixels that differ from the original like this one:

[img]http://www.takinganimeseriously.com/images/summer-wars-daisuke-fan-9.gif[/img]

If you have an animated GIF like that, there is little you can do to convert it to another format, particularly a video format.

If all the frames in your GIF are intact, then you would need to disassemble it into separate frames and reassemble it as a video using Imagemagick and ffmpeg.  Here's a page that describes the steps involved: [http://www.itforeveryone.co.uk/image-to-video.html](http://www.itforeveryone.co.uk/image-to-video.html)

---

