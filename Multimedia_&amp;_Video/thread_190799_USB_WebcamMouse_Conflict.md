---
title: "USB Webcam/Mouse Conflict"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by socialSavant on 2006-06-06
Hello,

I have, for the past couple weeks, been working on my nice new shiny Ubuntu system as a means of creating an HTPC. I finally got most all I need working (MythTV, IvyTV, nVidia Geforce/nForce, etc) that which doesn't necessarily come working "out-of-the-box." So lastly, I am trying to get my Creative Webcam Live! to work as well.

In doing so, I found this little tidbit:
[https://wiki.ubuntu.com/Spca5xx#head-48b871e312b6c98ba31970d0545d73b7f2fec9af](https://wiki.ubuntu.com/Spca5xx#head-48b871e312b6c98ba31970d0545d73b7f2fec9af)
Which states very quickly about a conflict between some USB Mice and the Webcams when on the same bus. I have determined for a certainty that I have this problem. So my question is: Can I work around this? Is there a way to set explicit mappings or something (I don't know what I am talking about here) to force the two to work in harmony if not together.

I have tried plugging both devices into all different slots, the only way the webcam works is when its alone (the kbd/mouse always works when plugged in). This is important to me, because the box sits in my livingroom and I pretty much REQUIRE the use of a wireless kbd/mouse. I willl be posting a similar thread in any Spca5xx related fora as well, but would appreciate any and all comments you might have.

Thanks,

---

### Post by socialSavant on 2006-06-06
Clarification:

Does the out-of-the-box Ubuntu support for webcams use the Spca5xx modules? 
This may sound like a strange/stupid question, but I ask becouse of this:
> "Luca Risolia" is setting a lot of drivers inside the main
Kernel tree, specially those chips supported by spca5xx... As a consequence, you have to choice between spca5xx or the others. The problem is, hotplug will detect, the in kernel driver
and maybe  reject spca5xx claim.
This is a quote from the README-KERNEL-UPTO-2.6.16 file found in the [spca5xx-20060501.tar.gz]("http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz") archive.
If the packaged Ubuntu uses "in kernel drivers" that are not "exactly" the same as Spca5xx, then might I benefit from trying to force those drivers instead? Or should I be barking up the USB tree?

Thanks again for your input,

---

### Post by socialSavant on 2006-06-10
Sorry but I have to... BUMP

Can't believe this got pushed back to page 11 in only a couple days!

Even if you don't have a clue, plz let me know. Otherwise, I may just have to keep bumping this one till I am certain all is hopeless. Thanks,

---

