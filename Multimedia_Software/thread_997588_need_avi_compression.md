---
title: "need avi compression"
date: 2008-11-30
forum: Multimedia Software
---

### Post by Smiley Coyote on 2008-11-30
I have already spent hours looking for what I need and if it is already posted in Ubuntu forums then I simply cannot find it.

I have vob files that I have converted into some rather huge avi files (8GB converted from four and a half GB of VOB) but what I need is a prog to take that very same file and make it into a smaller (700mb or less would be great) file.  I have seen full length features in avi format of this size that didn't sacrifice much for video quality.  I have seen lots of reference to how Avidemux can do it but either the instructions were in techie talk (i.e. way beyond me) or they simply didn't work or, in some cases, options that instructions said to exercise within the program simply weren't there.

I am quite new to Linux.  I can enter code into the terminal and download and install deb packages but other forms of installation I am having difficulty with.  I have no idea if I am using Gutsy or any of these other terms for differentiating different forms of Ubuntu.  I took 8.10 from the new install page and used that if that helps.

There was some talk of converting using DivX but I don't see that in my options for output format in Avidemux.

I really like Linux for a wide variety of reasons but my primary computer uses seem to involve things that are difficult to enable on this OS.  I would love to hear I am wrong.

Please help!

---

### Post by shirilover on 2008-11-30
You can always try MPEG-4 ASP (Xvid4) in avidemux instead of DivX.
Encoding settings will vary based on the source material, your quality desires, and length of the overall project.
If you want good results, your best choice is two use a 2-pass encode(will obviously take longer, but gives better results).
You can then choose between 2-pass average bitrate or 2-pass final size(final size of the video stram only).

---

### Post by Smiley Coyote on 2008-11-30
I just noticed something strange.  At the bottom of the Avidemux display, on the left, where it says "format" is selected avi.  I expected that to be the spot where I selected the output format but when I click on "open" it says that I should select an avi file.  Still, it does allow me to select a vob file instead without giving any error indication.  Is that the output format or not?  Is that actually the input format?

I don't see anything in the list under that for vob.  In fact, I don't see vob as a valid selection for any menu in the program.

I am starting out with vob files.  Will Avidemux convert vob files at all?

I used Avidemux to convert in the first place, giving me my initial avi file of eight GB but I never actually ran the file to see if it functioned as a video.

---

### Post by shirilover on 2008-11-30
The drop-dowm list under format is used for the output file.
You should try opening the large AVI file you created and encode that instead.
Alas, I have been using windows to do my DVD rips, since there are several avisynth filters I tend to use.

---

