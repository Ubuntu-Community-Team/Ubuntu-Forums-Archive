---
title: "USing a different volume for mythbuntu"
date: 2012-01-30
forum: Mythbuntu
---

### Post by johnvic on 2012-01-30
Hi all,

I am very new to mythbuntu and ubuntu. I have several drives in my PC. My boot drive is a 120 gig PATA. But that is not big enough for recording lots of TV, in fact I can't watch more than 10 minutes of HD. I also have a couple of 2 TB SATA drives and want to use that for video. Currently my mythtv is both frontend and backend. But in the near future, once I get my way around things, I'll use one or two small frontend net PC's. Maybe fanless. I am running mytbuntu 11.10

Anyway, I have a few questions.

I created a directory structure for livetv, recordings, etc. on a 2 TB drive and changes the owner to mythtv. Then I went into backend setup and pointed the directory's to my larger drive's directories. It's working, but I have only started using this. Am I missing something?

Can I easily make a RAID-0 out of my two 2 TB drive's in ubuntu? Previously this PC acted as a FreeNAS server and that was easy.

If I want to share my volumes on my network do I just share or do I want to make a NAS? I don't really see the advantage of a NAS if I can easily share on the network. Is that correct?

One last question. I want to put the PC in a closet so I don't have to hear the noise. Any advice on a VNC program that I can use with my macbook pro to access the mythbuntu backend machine? 

I know that's a lot of questions but I do appreciate any pointers.

---

### Post by wyliecoyoteuk on 2012-01-30
You can use storage groups which allows easier management

[http://www.mythtv.org/wiki/Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups)

You can use gparted (it should be in the repos) to set up RAID

Sharing is fine, but unnecessary if you are only intending to use front-ends.

Sorry, can't recommend any VNC clients for Mac, but they should be fairly easy to find.

[Chicken of the VNC]("http://sourceforge.net/projects/cotvnc/") seems popular.

---

### Post by johnvic on 2012-02-02
Thanks for the info!

---

