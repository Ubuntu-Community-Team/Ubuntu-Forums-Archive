---
title: "DVD mastering"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by Dr Eigen on 2007-06-19
Video editing noob help request: [-o<

I've a heap of avi files I want to chop up in various ways, then burn onto DVD for viewing in a DVD player.  Can anyone suggest some appropriate software?

Thanks in advance.

---

### Post by timcredible on 2007-06-19
qdvdauthor will do all that.

---

### Post by vanadium on 2007-06-19
I am not sure qdvdauthor will recode your video to DVD compliant format (I have yet to use it). You first need to convert your clips to (PAL or NTSC) DVD compliant mpeg video files. You can then use the mpg's to author the DVD.

For converting video formats to DVD, you can use avidemux. Take a look at the wiki on the avidemux homepage for how to proceed.

Finally, qdvdauthor will give you a DVD structure, or probably it can directly generate an ISO thet you need to burn to a DVD using your favourite burning app. Thus, there are three steps

1) Convert the video to DVD compliant mpegs (separate m2v and audio streams, wav, mp2 or ac3 can also be used)

2) Author the DVD (with qDVDauthor you can even create simple menus)

3) Burn the DVD

---

### Post by bayvista on 2008-06-05
I would like to find some documentation on qdvdauthor. So far, only very  basic stuff.

If anyone out there has used this package and know how it works, pls advise :

I have a number of mpeg2 video clips and want to create a dvd where each clip has its own menu item. The clips are from a camcorder recorded over 12 months. I can't see how to create a menu item.

Thanks in advance

---

### Post by smilliken on 2008-06-06
You could give kdenlive a try. You add your AVI files to the project and drag them into the timeline. Once in there you go to Render>Export to DVD. I've used it on occasions and had good luck with it. Just a thought.

---

### Post by bayvista on 2008-06-06
Thanks,

But how do I create menus for each clip , 30 in all?

I have been able to create DVDs before, but they only have the Main Menu with one item for the whole DVD. Think about the Scenes that you get with a commercial DVD. That is what I am trying to achieve.

OK: Problem solved. DVDSTYLER does everything I want. It even has documentation!!!

---

