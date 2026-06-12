---
title: "HD backend requirements (noob)"
date: 2008-06-26
forum: Mythbuntu
---

### Post by schromnc on 2008-06-26
Hey there,

I've been looking around trying to figure out if I can use one of my older systems as a Myth HD back end and was hoping to get some advice with my issue. 

The system I have has a 1.6Ghz mobile p4, 1GB RAM, and 400GB HDD space. I was wondering if I could use two combo tvtuners (for a total of 2 standard def and 2 hi def) in the system. Please note that I also intend to use hardware encoding on the standard def and that the tuners would either be PCI or PCI-express as the motherboard is a mobile on desktop variety. And FYI, the system works flawlessly with Hardy. 

My question to the community is, is this a reasonable plan? Or am I simply wasting my time trying to use this machine as a myth back end. 

The reason I ask this is because I have been reading through the requirements and the forums, perhaps i missed it, but I have not found anything that states the requirements for the back end to record 2 SD sources and HD sources. 

I thank you in advance for your help and support.

---

### Post by uopjohnson on 2008-06-26
There aren't a lot of requirements out there for HD recording because most of the owrk needs to be done by the frontened during playback.  You should probalby indicate what yoru recording source is goign to be for HD so that someone who is using that will be able to indicate exactly what their CPU requirements are. I think your biggest problem with this system is going to be IO bottleneck on the disk drives.  It is going to be even more of a problem when you try and read from the disks at the same time in order to watch what you've recorded.  However, this is a failry easy problem to fixe with a raid controller card, so you may just want to try it out and see if it works.  
I am willing to bet that after a few months you are going to want to upgrade your setup anyway.  most of us started on scrap hardware, but after a while myth becomes so usefull that you start buying the good stuff to keep it running.

---

