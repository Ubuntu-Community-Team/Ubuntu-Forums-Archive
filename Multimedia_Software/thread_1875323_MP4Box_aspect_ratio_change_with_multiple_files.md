---
title: "MP4Box aspect ratio change with multiple files?"
date: 2011-11-04
forum: Multimedia Software
---

### Post by s1mple_M4N on 2011-11-04
HI guys,

After looking for such a long time for a way to solve the problem with the aspect ratio of videos recorded by my Samsung camcorder, I found MP4Box.

I tried the GUI on Windows for a bit, but found it time consuming.

Then I searched more and found an MP4Box terminal command that did exactly what I wanted with minimum effort, very quickly - MP4Box -par 1=64:45 "input".MP4.

I'm now wondering - is there a way to add multiple files to a single MP4Box command?

I have a folder with around 200 video files in it...

Thanks in advance,

RoyJ

---

### Post by andrew.46 on 2011-11-04
> **s1mple_M4N said:**
> I'm now wondering - is there a way to add multiple files to a single MP4Box command?

You can use the *-add* command for 20 files...

---

### Post by s1mple_M4N on 2011-11-04
andrew.46 - thanks.

Not sure how to do it, though.

If I have 6 files - SDV_0001 to SDV_0006 - could you give an example?

Would it look this way >> MP4Box -par 1=64:45 -add SDV_0001.mp4 -add SDV_0002.mp4??

GPac website documentation is a bit vague and I'm still getting my head round it, sorry.

RoyJ

---

### Post by andrew.46 on 2011-11-04
Indeed the documentation is not all that great :). The best instructions can be found [here]("http://gpac.wp.institut-telecom.fr/mp4box/mp4box-documentation/"). Have a look at a working example here:

[http://www.andrews-corner.org/fist.html#muxing](http://www.andrews-corner.org/fist.html#muxing)

This is my page and this syntax works well for me...

> Would it look this way >> MP4Box -par 1=64:45 -add SDV_0001.mp4 -add SDV_0002.mp4??

You need an output file of course and I have to admit I have not used the *-par* option before so I am not sure if this a global option or needs to be applied to each of the files you add, global makes more sense but some experimentation may be required.

---

### Post by s1mple_M4N on 2011-11-04
Thanks again mate, lots of help.

RoyJ

---

