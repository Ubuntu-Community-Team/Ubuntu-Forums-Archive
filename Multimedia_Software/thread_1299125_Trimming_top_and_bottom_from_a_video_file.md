---
title: "Trimming top and bottom from a video file"
date: 2009-10-23
forum: Multimedia Software
---

### Post by Roger Allott on 2009-10-23
I wonder whether anyone here can help me with this.

I have a video file (format is wmv, although I could work on the avi files that preceded it) that is in 4:3 aspect ratio, but the actual movie seems to have been in widescreen (16:9, probably), so there are thick black strips at the top and bottom that are a bit pointless. If I use video editing software on the file, I have the option to save it as widescreen, but if I do that, all I end up with is a file with additional black strips on the left and right!

So, is there any app that can trim the top and bottom from a video file?

---

### Post by rwt911 on 2009-10-23
You may be able to with [Avidemux]("http://avidemux.sourceforge.net/"), not sure though, I am checking right now.

---

### Post by rwt911 on 2009-10-23
Yea you can, but I think you will have to convert it to AVI. I found [this ]("http://winff.org/html_new/")if you need to convert it.

Just download and install it from either the Ubuntu respiratories or the page given and open the program.

Open your video

Go to Video > Filters > Transform > Crop

It will bring up a windows that will allow you to crop it out.

Once done just save your video. :)

---

### Post by lisati on 2009-10-23
No Linux-specific solution comes to mind (I normally use Windows for my video editing) but here goes with one possible approach.

What I normally do in this kind of situation is start a new project with the aspect ratio I want, add the file with the "wrong" aspect ratio, and use pan/zoom options to "correct" the problem.

---

### Post by vinutux on 2009-10-23
> **rwt911 said:**
> You may be able to with [Avidemux]("http://avidemux.sourceforge.net/"), not sure though, I am checking right now.

+1 for avidemux

---

### Post by Roger Allott on 2009-10-23
> **rwt911 said:**
> Yea you can, but I think you will have to convert it to AVI. I found [this ]("http://winff.org/html_new/")if you need to convert it.

Just download and install it from either the Ubuntu respiratories or the page given and open the program.

Open your video

Go to Video > Filters > Transform > Crop

It will bring up a windows that will allow you to crop it out.

Once done just save your video. :)

Thanks, that's brilliant! I never knew that Avidemux was so powerful.

The filters are great, and cropping a file in the way I want seems very easy. 

However, there's one rather major problem. I can set up the filter and save it as a filter, but there doesn't seem to be a way of **applying** the filter to the video.

I'm sure there must be a way of applying the filter, so I'm probably just being incredibly dumb.

---

