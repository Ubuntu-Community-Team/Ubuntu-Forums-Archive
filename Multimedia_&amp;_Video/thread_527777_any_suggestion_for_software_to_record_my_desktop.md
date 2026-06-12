---
title: "any suggestion for software to record my desktop??"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by AlexenderReez on 2007-08-17
i want to make a presentation in my class and i want to show the power of compiz fusion or in general = linux compare to windows.. i know that there is vidcap plugin in beryl that enable user to record desktop..but i want to record compiz fusion effects....i know there is software call 'istanbul' and 'record my desktop' ...but i not really used to it...any other software...or any tips to use istanbul or 'record my desktop' application?

---

### Post by jrusso2 on 2007-08-17
xvidcap is the only one I know of, I found a link that talks about the tools that you can use with it in Ubuntu 
[http://lxer.com/module/newswire/view/82744/index.html](http://lxer.com/module/newswire/view/82744/index.html)

---

### Post by eye208 on 2007-08-17
> **AlexenderReez said:**
> or any tips to use istanbul or 'record my desktop' application?
There is a graphical front end to recordmydesktop called "gtk-recordMyDesktop". It's very easy to use. You will find it in the "universe" repository.

In order to record OpenGL desktop effects you might need to enable the option "full shots at every frame" in the advanced settings dialog.

---

### Post by AlexenderReez on 2007-08-17
hm..i'm learning recordmydesktop right now....i will see that link...and i will use the best recoder that can provide the best record video for my system...any idea how to change ogg to avi format?..using mencoder or anything else?:

Thanks

---

### Post by eye208 on 2007-08-17
> **AlexenderReez said:**
> any idea how to change ogg to avi format?..using mencoder or anything else?
Keep in mind that choosing the AVI container format does not mean it's playable on Windows. You have to choose suitable stream formats too or install additional codecs on Windows. MEncoder can convert to H.264 video which is very efficient in terms of file size, but if the video has been captured at full screen resolution (e.g. 1280x1024) slower PCs will hardly be able to play it back. So in this case Xvid might be a better option than H.264. Or just scale the video down during conversion; MEncoder can do that too.

---

