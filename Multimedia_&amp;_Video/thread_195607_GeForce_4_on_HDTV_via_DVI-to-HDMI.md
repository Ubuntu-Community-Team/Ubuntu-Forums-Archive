---
title: "GeForce 4 on HDTV via DVI-to-HDMI"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by caecus314 on 2006-06-13
Hi.  I've been using Kubuntu for a little under a year now, and I've reached the point where I prefer it to Windows in virtually every way.  I run Dapper all the time on my two main computers, but I've had a third box that I've been working on as a bit of a side-project.  It's made up of the outdated parts that I've acquired from working on other people's computers--but that's OK because I only really use it to play ZSNES, StepMania, and DVDs.  It's got an nVidia GeForce 4 Ti4600, which I would like to use to hook it up to my Samsung HDTV through a DVI-to-HDMI converter.  I know it's possible, because it works fine in Windows.  I've tried downloading the latest nVidia drivers and, although I'm certainly no expert on the matter, I've made countless modifications to my xconf.org file, all to no avail.  Does anybody have any suggestions so I won't have to deal with Windows and its shortcomings anymore?  I wish I could tell you what resolutions my TV is capable of, but Windows just seems to pick one without telling me anything about it.  Any help would be greatly appreciated!

---

### Post by HankB on 2006-06-13
I can't speak to the DVI to HDMI aspect, but I've just set up my system do drive an HDTV via DVI. I did this by setting it up as a double headed X server. You can see portions of what I've done in this post: [http://ubuntuforums.org/showpost.php?p=1134782&postcount=660](http://ubuntuforums.org/showpost.php?p=1134782&postcount=660)

My original video card did not have a DVI output so I added a PCI video card that did.  I didn't need to figure out how to get both outputs on one card to work.

Now I'm wrestling with issues related to getting X-apps like gxine to display on the HDTV without logging in on the primary display. I think I need to figure out how to run a second X server.

HTH,
hank

---

