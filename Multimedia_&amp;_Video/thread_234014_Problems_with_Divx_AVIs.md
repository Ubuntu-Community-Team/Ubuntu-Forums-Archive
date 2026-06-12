---
title: "Problems with Divx AVIs"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by cubdukat on 2006-08-10
Last night I upgraded my system to be able to handle most of the multimedia formats out there. 

it seems to work for the most part (the DVD image size seems somewhat small, but at least it plays with sound), but I am having one or two minor problems with Divx/XVid AVI files.

When I play them back in Totem, I get a picture but no sound, and when I use GXine, I get neither one. The audio on the files in question is MP3.

When I downloaded the gstreamer0.10-bad/ugly codecs, wouldn't those have the MP3 codecs included? If not, what should I download next?

---

### Post by VirtuAlex on 2006-08-10
Download everything you can. Try
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by cubdukat on 2006-08-12
Well, I solved the problem. Apparently I was supposed to download both the regular and multiverse packages of gstreamer0.10-plugins-ugly. I only downloaded the multiverse one.

I now have both video and audio in Totem. I haven't tried playing them back in GXine yet. Now all I have to do is figure out why the image is so small.

---

