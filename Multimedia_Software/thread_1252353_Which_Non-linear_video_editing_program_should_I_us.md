---
title: "Which Non-linear video editing program should I use?"
date: 2009-08-28
forum: Multimedia Software
---

### Post by epi 1:10,000 on 2009-08-28
does anyone have any experience with....
[Ingex]("http://en.wikipedia.org/wiki/Ingex")
[Cinelerra]("http://en.wikipedia.org/wiki/Cinelerra")
[Kino]("http://en.wikipedia.org/wiki/Kino_%28software%29")
[LiVES]("http://en.wikipedia.org/wiki/LiVES")
[OpenShot Video Editor]("http://en.wikipedia.org/wiki/OpenShot_Video_Editor")
[PiTiVi]("http://en.wikipedia.org/wiki/PiTiVi") ???

Does anyone know the advantages/disadvantages of one verses the other?

---

### Post by AlexanderDGreat on 2009-09-12
Hi, in my experience, kdenlive crashes and it has no transitions. I'm right now installing cinelerra, but having troubles using Ubuntu 64 bit, I'm currently looking for a solution.

---

### Post by bluenova on 2009-09-24
@AlexanderDGreat, kdenlive has plenty transitions... [http://en.wikibooks.org/wiki/Kdenlive/Transitions](http://en.wikibooks.org/wiki/Kdenlive/Transitions)
and recent versions are very stable.

All the editors are moving on so quickly at the moment, that it's difficult to comment on them and be careful reading past reviews as the projects you list have all moved on leaps and bounds over the past year, so any comments are likly outdated.

You are better off installing latest versions of them all and see what works for you. Bear in mind that some projects like Openshot, may not work exactly as it should, but that's fine the project is very young and maturing very well, when they get a stable version out I think it'll be very impressive.

---

### Post by AlexanderDGreat on 2009-09-24
Hi, due to my deadline, I was forced to use Cinelerra and watching youtube videos to use it: Basic Editing Cinelerra Parts 1 - 5. It only crashed 1-2 in my experience. I was editing 1gb videos. Anyway, thanks for the feedback.

---

### Post by BFG on 2009-09-24
I've been trying a few over the last week.  It's so frustrating!!!  All I was to do is top and tail some avi clips and put them together into one video with some simple transitions, and upload to youtube. Using help here...
[http://eaimag.blogspot.com/2009/01/best-ubuntu-video-editors.html](http://eaimag.blogspot.com/2009/01/best-ubuntu-video-editors.html)

Cinelerra.  The main site's help was frustrating and had gaps in the install process.  It gave cut / paste command lines to download the package, but none to install it.  Came back to it later.


Avidemux.  Ah, it doesn't allow me to work with multiple tracks. Never mind.
OpenShot Video Editor.  No transitions.  Whined about my avi source files.
PiTiVi. Rendered nothing but rubbish.

Tried a few others, forgotten names now.

KdenLive.  Love the interface, very intuitive, hundreds of file formats!  Transitions are cumbersome and limited, but OK.  However, after a few test projects, got into my task and I'm getting audio sync problems in the edit screen, and video dropouts on render.  Grrr!

Kino. Crashes.  Moaned about file formats more than any of the others. Gave up.

LiVES.  Not tried it yet.

Cinelerra.  Persevered and got it installed.  1st time run, holy crap what an ugly interface!  About 20yrs out of date.  So, not expecting it to be intuitive, I muddled on.  Not too bad actually and I got a result.  Render, limited to about 10 formats and 7 of those are audio only.  WTF?  Anyway - render - chug, chug, chug, jees this is about 1/10th the speed of kdenlive.  20 minutes later on my 64bit quad core machine with 8Gb ram, it crashes at 80% through. Damn.  Run again.  This time got a file.
Play in VLan, "codec not supported"  Gaaaaahhhh!!!  

These videos are taken on a Canon Powershot S3.  It's a digital camera with video capability which writes files directly onto the SD card in avi format.  I can top and tail the avi right there in the camera, and upload it to the PC,  whole process takes about 3 minutes for a 300Mb avi file.  Yet if I try and use the workstation to do the same operation it acts like I've asked it to go to mars!!!  Why is this so ******* hard!!!!!!!!!

:lolflag:

It's true though.  If a piece of throw-away firmware on a cheap camera can do this in seconds, why can't PCs do it?

---

### Post by wildhostile on 2009-09-24
> **BFG said:**
>  . 
Hi BFG,

What version of Cinelerra are you using?
What is the format(videocodec, audiocodec) of your videos taken from your Canon Powershot S3?

---

### Post by ejolson on 2009-09-27
> **BFG said:**
> Cinelerra.  Persevered and got it installed.  1st time run, holy crap what an ugly interface!  About 20yrs out of date.  So, not expecting it to be intuitive, I muddled on.  Not too bad actually and I got a result.  Render, limited to about 10 formats and 7 of those are audio only.  WTF?  Anyway - render - chug, chug, chug, jees this is about 1/10th the speed of kdenlive.  20 minutes later on my 64bit quad core machine with 8Gb ram, it crashes at 80% through. Damn.  Run again.  This time got a file.

Render using an external encoder and the yuv4mpeg pipe.  Reasonable external encoders are:  x264 for AVCHD, Blu-Ray and HD-DVD; mpjpegtools for DVD, SVCD and VCD; and ffmpeg for everything else.  Examples of how to do this may be found at

[http://www.renomath.org/ejolson/video/hddvd/264wf.html](http://www.renomath.org/ejolson/video/hddvd/264wf.html)

---

