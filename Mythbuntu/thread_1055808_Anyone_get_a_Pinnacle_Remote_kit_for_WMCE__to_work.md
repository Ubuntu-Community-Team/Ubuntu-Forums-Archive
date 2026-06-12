---
title: "Anyone get a Pinnacle Remote kit for WMCE  to work in Mythbuntu 8.10?"
date: 2009-01-31
forum: Mythbuntu
---

### Post by Ductilemelon on 2009-01-31
Hi this is my first time posting on this forum. I am hoping that someone can help with the abundance of configuration questions that I have for Mythbuntu 8.10. 

I'll start with the question: Does anyone have a working Pinnacle Remote Kit for Windows Media Center (plus IR blaster)? The remote looks almost exactly like the black remote in the picture at [http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote).

I have tried the default MCE remote install (new and old) from the Mythbuntu Control Center with no luck.

The device appears to be recognized by the driver, the light lights on the receiver end when the remote buttons are pressed however it does not do anything in with the myth front end open. 

I tried following all of the instructions on the myth site linked above to redo the install manually with no luck (I probably really screwed it up now I'm kind of a noobee)

Please help! Thanks!

---

### Post by jeffc111 on 2009-03-26
Generally, I followed the instructions here:[InstallLIRC/Hardy in the Ubuntu Community Documentation]("https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes")

Instead of hand editing the lirc_mceusb2.c driver source (step 5), I instead downloaded the latest source (0.8.4a, at the time of writing) from [http://www.lirc.org/]("http://www.lirc.org/"), which I had found (in earlier meanderings) includes the pinnacle mce USB id's.  I extracted the package (gzip -d lirc-0.8.4a.tar.gz  then, tar -xvf lirc-0.8.4a.tar) and copied the file over the source that was acquired via the above Hardy instructions.  I then built the source via the remaining Hardy instructions (steps 6-8).  What those leave out, I believe, is that you still need a valid /etc/lirc/lircd.conf.  I acquired this by running the Mythbuntu Control Centre and selecting the Windows Media center Remotes (new version, Philips et al.).

run irw, and voila, key presses.

This thread is a bit stale, but it took me about 2.5 evenings to find the right instructions and figure this out, so I hope it helps someone else.  Now if I can just figure out why audio stopped working...

---

