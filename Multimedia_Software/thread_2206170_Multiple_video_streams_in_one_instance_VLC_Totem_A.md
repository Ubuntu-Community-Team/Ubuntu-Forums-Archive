---
title: "Multiple video streams in one instance? VLC? Totem? Anything?"
date: 2014-02-17
forum: Multimedia Software
---

### Post by Roasted on 2014-02-17
Hello friends. I'm on 13.10 and I want to create a way so I can view multiple video streams at once on my LAN for use with my video surveillance cameras. I read about VLC's Mosaic and tried to set it up, but the forum/wiki help has been uh... to be blunt... bad. It just doesn't exist. I'm unsure of what else I can do with VLC, but for now I'm considering other (any?) options in the event somebody has an idea.

Basically, I want to pull in video streams from some cameras on my network to create something like this:

[https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcTlpinyhFISbqjpUNKHxqbisq4FOMRgCiq5WOEK7z3XbvILm3Gx](https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcTlpinyhFISbqjpUNKHxqbisq4FOMRgCiq5WOEK7z3XbvILm3Gx)

I went as far as to create a custom HTML page for use with a web browser. There are two problems with this though.

Chrome - Flat out doesn't work. Just blank feeds.
Firefox - has some sort of memory leak. If I watch my system monitor, my RAM is eaten up by about 10-20 MB a second. Once maxed, the system (of course) runs terrible until I close Firefox.

Any ideas? Anything at all?

---

### Post by Yellow Pasque on 2014-02-18
Tried zoneminder?

---

### Post by Roasted on 2014-02-18
> **Temüjin said:**
> Tried zoneminder?

Yes. Zoneminder has been problematic over the years, largely due to the fact its code stagnated while cameras were updated/new models released/etc. That said, ZM has had a recent undertaking of a new development team of (great) developers. Based on discussions with them, it sounds like a new version of ZM on the horizon should open some working doors for my cameras. If that's the case, I'd use ZM in a hot second. Until then, I am using the GUI-less, rather featureless Motion, which is admittedly very inferior of ZM in terms of features, but dangit, it works SO well and it's so reliable.

That said, I just realized what my problem was. In a custom HTML page, I simply wrote up a few <img src= lines for the streams to my camera. In Chrome, this did not work, while in Firefox it would maximize my RAM usage and bring my system to a crawl in a matter of 2 minutes. Come to find out both browsers just seem to have issues when you reference an <a href= link as a camera stream.

Roughly translated:

<a href="cameraurl:5000"><img src=cameraurl:5000 />

Would work until I clicked on the camera, thereby fullscreening it. Once full screened, Firefox ate memory at an alarming rate, while Chrome did not work. Instead, I simply removed the <a href= tags. So now I have a simple 5-or-so line custom HTML file with only the <img src= entries. These are not clickable, but I can size them accordingly (width=49%, etc) to align them in a grid the way I like.

In short, this works, and better yet it works in both Firefox and Chrome. Somewhat bummed I cannot click on each camera to get a full screen view, but dangit, this runs without any issues on either browser, so I'll run with it until ZM's development hits a pinnacle in support and stability that I can switch to indefinitely. I feel like it'll be coming pretty darn soon. :D

---

