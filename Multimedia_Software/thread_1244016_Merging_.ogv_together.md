---
title: "Merging .ogv together"
date: 2009-08-19
forum: Multimedia Software
---

### Post by PaulTR on 2009-08-19
Hello,

     I've just started an online class for website creation, and one of the requirements is that we make a screencast every week with a webcam introduction. Using Cheese, I'm able to make the webcam introduction with my mic for talking, and using recordmydesktop and the mic, I'm able to make the screencast. Now that I've got all those little details figured out for actually making the necessary parts, I was wondering how can I merge the two videos together into one? Using cat vid1.ogv vid2.ogv > vidend.ogv isn't working, nor does avidemux or winff work. Anyone able to give me a walkthrough for converting those files to .avi so I can cat them, or how to merge them as .ogv and then convert to .avi so I can upload to youtube? (or as is, since I think you can upload .ogv now) Thanks!

---

### Post by andrew.46 on 2009-08-19
Hi PaulTR,

The standard way to do this with FFmpeg is to convert to an intermediate format and then cat the files together. Details are here:

3.18 How can I join video files?
[http://ffmpeg.org/faq.html#SEC30](http://ffmpeg.org/faq.html#SEC30)

I have to admit that I have not tried this with *.ogv* files and I suspect you might be in for a little trial and error before you get a satisfactory result.

Andrew

---

