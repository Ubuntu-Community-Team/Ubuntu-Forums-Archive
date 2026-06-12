---
title: "Enable Nvidia restricted driver for LiveCD"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by mburris on 2007-06-29
Let me give you guys a little history on my situation here so you can better understand what/why i want this.  

I am building a LiveCD (liveUSB actually, but close enough) for my parents and grandparents.  Want it does is basically allow them full use of Ubuntu without them worrying about messing anything up.  I am using a non-writable configuration here... ie not persistent USB, so that if they have a problem, they restart the PC, and their PC is good as new.  

I have been reading everything I could find that was even remotely related to LiveCD / LiveUSB / SquashFS / Casper customization.  Until this point there has been (or at least I have been able to find) enough documentation to figure out almost everything I needed.  Here's what I am able to do now:

(at first I did try using UCK - ubuntu customization kit and reconstructor, but I found them limiting me, and I was able to learn (and do) a lot more by doing all the steps manually)
- Mount the SquashFS of a LiveCD
- Copy the squashed filesystem to a folder for customization
- Chroot into the extracted squashFS to make changes (ie install / remove / command line changes / and now, even run GUI application in the chroot'ed environment
- customize all aspects of the GUI including uSplash startup and shutdown animations
- re-compress (mksquashfs) the customized live filesystem
- package it all back up in an ISO or USB stick and boot to it
(keep in mind 3 weeks ago, when I started this project I was strictly a Windows guy and had really never even booted Linux of any kind) quick study i guess...

**Now one of the last things I would like to do is add proprietary Nvidia video driver support to my rofs (read only file system).  **Why? couple reasons: 1. I want them to be visually comforted by the GUI, beryl will do that.  2. I would like to make the menu as easy to use as possible and I have set my sights on a graphic rich OSX like dock that requires beryl like 3D effects.  

I read somewhere (i believe it was on the Linux-mint or mint-Linux forum) that someone was able to disable the hooks in Casper that allowed the restricted modules required to automatically support the Nvidia video driver.  There was no other information he provided in that or any other post I could find.

Can someone point me in the direction of some documentation or give me a little hint as to how I can allow the Nvidia proprietary drive to automatically work in a LiveCD / USB system?  I'm not afraid to get dirty doing this... lord knows I already have.

---

### Post by Dead-Locked on 2007-07-18
I was curious if you'd found anything else about this. I'm really interested in doing something that's similiar. Let me know. Thanks.

---

