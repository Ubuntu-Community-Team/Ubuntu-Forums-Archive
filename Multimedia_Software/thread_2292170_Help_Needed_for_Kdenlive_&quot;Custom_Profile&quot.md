---
title: "Help Needed for Kdenlive &quot;Custom Profile&quot; Coding"
date: 2015-08-25
forum: Multimedia Software
---

### Post by mark bower on 2015-08-25
I would like help to get the following ffmpeg code modified to use in Kdenlive as a Custom Profile.  The code works just fine when executed with ffmpeg on the cmd line.  The goal is to take a prores(HQ).mov file in Kdenlive and output it to H264/MPEG-4, and in the process add extra frames.  Thus the use of "setpts". 

```
ffmpeg -i input.mov -vf setpts=1.333*PTS -c:v libx264  -preset slow -pix_fmt yuv420p -crf 17 output.mp4
```

I have tried many syntax changes, but cannot get the setpts filter parameter to work.

---

### Post by mark bower on 2015-09-02
In the Kdenlive "Custom Profile" I have entered variations of: ```
 setpts=1.333*PTS vcodec=libx264 -pix_fmt yuv420p crf 17
```  
I can change crf to different values and get different resultant files sizes; this suggests that the libx264 parameters are invoked.  If I precede setpts with vf, resultant file sizes are reduced which suggest that setpts is then not taken into account and "vf" is not helping.  The bottom line is that setpts is not increasing the number of frames in the 24/18 ratio.  

What is the proper syntax for using "setpts" in Kdenlive's Custom Profile?

---

### Post by mark bower on 2015-09-04
bump for help please

---

### Post by FakeOutdoorsman on 2015-09-05
See [Kdenlive Profile Parameters](https://userbase.kde.org/Kdenlive/Manual/Project_Menu/Render/Render_Profile_Parameters).

---

### Post by mark bower on 2015-09-05
Well, over many days of googling and trying to get something to work (but limited understanding), I have read that Kde "Parameters" page at least 5 times.  It does not help me to figure out how to get either the syntax for the ffmpeg filter "-vf setpts=1.333*PTS" to work in the Custom Profile, or what the equivalent code (MLT) would be that would perform the same function.

So, I need more help.

---

### Post by mark bower on 2015-09-07
bumped for more help please

---

### Post by mark bower on 2015-09-11
bumping again to try and draw attention for help.  still need the equivalent of the ffmpeg code "setpts=(1.333)*PTS" that can be used in a Kdenlive Custom Profile.  Its use would allow me to edit ProRes in Kdenlive, then render directly to mp4 in Kdenlive.  Versus storing the edited ProRes, then reopening in ffmpeg and rendering to mp4.

---

### Post by FakeOutdoorsman on 2015-09-11
You should probably ask at the Kdenlive help resources. A quick look doesn't show any filtering options available in the [MLT Consumer: avformat documentation](http://www.mltframework.org/bin/view/MLT/ConsumerAvformat).

However, as I mentioned before, I don't think using "-vf setpts=1.333*PTS" is the proper solution.

---

### Post by mark bower on 2015-09-12
In fact, I have requested help over at the Kdenlive forum some weeks ago, but no response that goes anywhere.

I believe what you are saying is that "setpts" is not the best "form" to use, in spite of the fact that it does the job. (sort of like program coding where a given command and argument is superior to others in getting the same result).  However, I do not see how to do it?  At first, -vf -r looks good, but it maintains the same video length(runtime) as I understand it, by removing or adding frames?  But it will not make something shown at 24fps appear to be running at 18fps, ie, increase the "runtime".

So, I need some hand holding here to make a step forward.  However, FakeOutdoorsman, I remain appreciative of your earlier help in putting me onto the Custom Profile wherein Kdenlive would save my edited files in ProRes(HQ).

---

### Post by mark bower on 2015-09-21
With this reply I am saying goodbye to this thread and will not be returning.

---

### Post by FakeOutdoorsman on 2015-09-22
Sorry I couldn't be of more help. I simply didn't have an answer. I looked briefly, but didn't invest more time to try to find one.

---

