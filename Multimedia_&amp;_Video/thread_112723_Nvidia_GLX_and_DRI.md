---
title: "Nvidia GLX and DRI"
date: 2006-01-04
forum: Multimedia &amp; Video
---

### Post by DrBair on 2006-01-04
Just what it sounds like, I have a Nvidia 6600 and a Radeon 9200.  I currently have them both running on separate X servers with separate keyboards and mice and its working out ok.  The only issue is that I don't have direct rendering on the Radeon which is using the xorg driver.  

The issue is nvidia's glx drivers take over the joint when you install them.  So when I start the second xserver, it tries to use nvidia glx drivers on the radeon which doesn't work out so well.  At least this is my hypothesis.

I found this guide on the web on the topic: [http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/pdf/XFree-Local-multi-user-HOWTO.pdf]("http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/pdf/XFree-Local-multi-user-HOWTO.pdf")

Any idea if I could pull something like this off on ubuntu? I'm not sure what files would need to go where.

---

### Post by DrBair on 2006-01-08
TTT :p 

Also, does ati's proprietary driver overwrite the xorg drivers like nvidias does? If not I'd imagine that would work too.

---

### Post by DrBair on 2006-01-17
For all those interested, I did get DRI and nvidia GLX running at the same time a few minutes ago.  So it is possible, and its not too bad once you know what direction to go in.

I ended up removing the ubuntu nvidia drivers and using the nvidia installer with some of the options from the above article.  After an afternoon of playing around with it, everything works as well as I hoped for. 

Perhaps this is something that should be a default for Dapper? Its nothing too exotic, really.  Let me know if you're interested in more info on this.

---

