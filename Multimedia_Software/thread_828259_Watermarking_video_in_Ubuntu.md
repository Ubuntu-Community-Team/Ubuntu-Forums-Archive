---
title: "Watermarking video in Ubuntu?"
date: 2008-06-13
forum: Multimedia Software
---

### Post by ticopelp on 2008-06-13
Is there a utility or command of some kind that will let me add watermarks to video in Ubuntu?

Even a freeware utility that runs in Wine would be great at this point. 

Thanks.

---

### Post by xc3RnbFO8P on 2008-06-13
You can add a logo in Avidemux (png)
just use brightnes and blur.

---

### Post by ticopelp on 2008-06-13
> **Ringi said:**
> You can add a logo in Avidemux (png)
just use brightnes and blur.

Thanks, I downloaded Avidemux. Would you happen to have any guidance on next steps? Is there an easy way to add the logo?

---

### Post by xc3RnbFO8P on 2008-06-13
Open a video
choose codec on the left side
under video open filter> misc> logo
You have to make the logo (in Gimp?)
If got a picture of a logo, I will
gladly make it for you, it is much easier than trying to explain it :)

---

### Post by ticopelp on 2008-06-13
> **Ringi said:**
> Open a video
choose codec on the left side
under video open filter> misc> logo
You have to make the logo (in Gimp?)
If got a picture of a logo, I will
gladly make it for you, it is much easier than trying to explain it :)

I did manage to make a transparent PNG logo in GIMP, and now I'm trying to figure out how to add it. 

Under Video > Filters > Misc I only have:

Blend remover
Hard pulldown removal
Whirl
Mosaic
MPlayer delogo
Animated menu

Am I missing something?

Thanks for your continued help.

---

### Post by xc3RnbFO8P on 2008-06-13
Did you install Avidemux from Add/Remove (the GTK+)

---

### Post by ticopelp on 2008-06-13
> **Ringi said:**
> Did you install Avidemux from Add/Remove (the GTK+)

Actually it appears I was using an old version. I installed a newer version and this one has the Logo filter.

Now I am just trying to get the logo to show up properly. 

Thanks, this was very helpful.

---

### Post by brvercast on 2009-12-18
Sorry for bringing this thread UP after so many time but this solution is still one of the best I founded to add a logo into a video.

My question is: did you find something newer and better to do the same (in command line only please)?

If not, could you please explain me how to to it with Avidemux in command line? That's really what I need :)

Thanx!

Brice

---

### Post by emarkay on 2010-05-19
Yes, Avidemux is** still **not able to do this anymore! 
No more watermarking!
See this post: [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9327772](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9327772)

---

### Post by brvercast on 2010-05-19
Best solution I finally found for video online editing : melt (the CLI for MLT Framework)

[http://www.mltframework.org/twiki/bin/view/MLT/](http://www.mltframework.org/twiki/bin/view/MLT/)

CRAZY soft ;)

---

### Post by Jose Catre-Vandis on 2010-05-19
Or try this:

[http://www.commandlinefu.com/commands/view/3559/use-heading-subtitle-file-as-watermark-using-mencoder](http://www.commandlinefu.com/commands/view/3559/use-heading-subtitle-file-as-watermark-using-mencoder)

---

### Post by emarkay on 2010-05-19
Also, the newest version (via GetDeb) 2.5.3 still crashes, as originally noticed.

---

### Post by xc3RnbFO8P on 2010-05-20
Try **Open Shot** (Synaptic Package Manager)
[http://www.openshotvideo.com/2009/04/linux-video-editing-plus-compositing.html]("http://www.openshotvideo.com/2009/04/linux-video-editing-plus-compositing.html")

---

### Post by emarkay on 2010-05-25
Anyone else?

---

### Post by conualfy on 2013-02-16
Although this is an old topic, I am going to reply as it might help others coming after me.

I was looking for video editors for Ubuntu for a while and I found Cinelerra to be very advanced, also capable to add watermarks. But, after some time, when I finally got to know Cinelerra (good enough for my purposes), it does not work well (or at all) in Quantal (Ubuntu 12.10).
And I got here again.

The solution I just figured it out is to use Openshot.
My watermark is my logo, so I had it as .png file. I extended the file canvas (in GIMP) to be as large as my clips (1280x720), having the logo on the lower right side.

Then, import clips and the full size resolution .png, use the logo file as top layer and clips below it. Add some titles (Title menu) and export it. For titles you might want to install Inkscape and Blender, as some tasks need these programs (advanced editing of a title or 3D rendering in case you want 3D titles).


For me it works just great to use the Youtube HD presets at 29.97 fps.

Hope this help others not to spend too much timp looking for solutions.

---

### Post by sandyd on 2013-02-16
**Necromancing - thread closed**

Please do not post in threads more than one year old.

Thanks!

---

